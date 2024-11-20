# Mechatronik-3-MCT

### Datasheets

Für fast jedes Technische Modul ist das Datasheet die primäre Informationsquelle.

Für den STM32F4 existieren unter anderem ein [Reference Manual](./datasheets/rm0090-stm32f405415-stm32f407417-stm32f427437-and-stm32f429439-advanced-armbased-32bit-mcus-stmicroelectronics.pdf) und ein [Programming Manual](./datasheets/pm0214-stm32-cortexm4-mcus-and-mpus-programming-manual-stmicroelectronics.pdf).

Beide wurden von [st.com](https://www.st.com/en/microcontrollers-microprocessors/stm32f407vg.html#documentation) heruntergeladen.

Das Reference Manual beschreibt alle Hardwareeinheiten und Register.

Das Programming Manual enthält allgemeinere Informationen über die Programmierung der ARM Kerne wie die Liste der Instruktionen, Power Managegement, Fehlerbehandlung, ...


### Setup, Umgebung

 * [STM32 Cube IDE auf macOS einrichten](./setup-cube-ide/setup.md)
 * [Ein neues Projekt in STM32 Cube IDE erstellen](./setup-cube-ide/new_project.md)

### Dokumentation

 * [Was ist ein Register?](./doc/01-registers.md)
 * [Die RNG Einheit](./doc/03-rng.md)
 * [Ausgaben mit printf](./doc/04-printf.md)
