Der STM32-F4 verfügt über eine Hardware RNG (Randon Number Generator) Einheit.

## Excel Tool

Im Excel Tool muss der Haken bei RNG gesetzt werden (unten links).

## Header

Alle Hardwareeinheiten haben entsprechende Header, für RNG muss ``stm32f4xx_rng.h`` eingebunden werden:

```c
#include "stm32f4xx_rng.h"
```

## Initialisierung

Beim Programmstart muss der RNG einmalig initialisiert werden.

Dies besteht aus zwei Schritten, zuerst muss die Taktquelle verbunden werden, danach die RNG Einheit selber aktiviert werden.

```c

void Init_RNG() {

    /* Enable RNG clock source */
    RCC->AHB2ENR |= RCC_AHB2ENR_RNGEN;

    /* RNG Peripheral enable */
    RNG->CR |= RNG_CR_RNGEN;
}

void main() {

    // ...

    Init_RNG();

    // ...

    while(true) {
        // ...
    }
}

```

## RNG auslesen

Die RNG Einheit benötigt etwas Zeit um eine Zufallszahl zu erzeugen. Sobald eine neue Zahl bereit ist, wird das bit ``RNG_SR_DRDY``im Register ``RNG->SR`` gesetzt.

Danach kann die Zufallszahl aus dem Register ``RNG->DR`` ausgelesen werden.

```c

uint32_t Get_RNG() {
    /* Wait until one RNG number is ready */
    while (!(RNG->SR & (RNG_SR_DRDY)));

    /* Get a 32-bit Random number */
    return RNG->DR;
}

void main() {

    // ...

    while(true) {

        // ...

        uint32_t rnd_value = Get_RNG();

        // ..
    }
}

```

Hinweis: ``Get_RNG``ist die simple Version, der RNG Generator kann auch Fehler zurückmelden, eigentlich müssten dafür u.a. im Register ``RNG->SR`` die Bits ``RNG_SR_SECS`` (Seed Error Current Status) und ``RNG_SR_CECS`` (Clock Error Current Status) geprüft werden.


# Alternative

## No HAL

Da direkte Registermanipulation immer etwas umständlich ist, gibt es vordefinierte Hilfsfunktionen:

```c
void Init_RNG() {

    // Clock für RNG aktivieren
    RCC_AHB2PeriphClockCmd(RCC_AHB2Periph_RNG, ENABLE);
    
    // RNG einschalten
    RNG_Cmd(ENABLE);
}

uint32_t Get_RNG() {
    while(RNG_GetFlagStatus(RNG_FLAG_DRDY) == RESET) ;

    RNG_GetRandomNumber()
}
```

## HAL

Falls der HAL verwendet wird, können für ``Init``die beiden Funktionen ``__HAL_RCC_RNG_CLK_ENABLE`` und ``HAL_RNG_Init`` verwendet werden; und dann zum auslesen ``HAL_RNG_GenerateRandomNumber``.

