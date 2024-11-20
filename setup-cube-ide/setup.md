Für macOS gibt es nur die STM32 CubeIDE, nicht die Ayatollah IDE welche in der Uni verwendet wird.

## Download

https://www.st.com/en/development-tools/stm32cubeide.html#get-software


## Setup

 * Installieren

 * ST Account erstellen und Einloggen

 ![](./_content/login.png)

 * Check For Target Selector Device Database Updates

 * Check for Embedded Software Packages Updates

![](./_content/image.png)

 * Manage Embedded Software Packages

 ![](./_content/manage_embedded.png)


## ST-Link

 * ST-Link auf Dev-Board updaten
   
   (ST-Link ist der auf dem Entwicklungsboard integrierte Programmer / Debugger)

   ![](./_content/st_link_upgrade_1.png)

   Dann Entwicklungsboard USB Trennen, RESET Button gedrückt halten und USB neu verbinden. Dann kann RESET losgelassen werden.

   Im Update Tool auf "Open in Update Mode" klicken, dann "Upgrade".


## Firmware & Treiber

 * Firmware und Demos herunterladen und in einen passenden Ordner kopieren

 https://www.st.com/en/embedded-software/stsw-stm32068.html


## Neues Projekt

 * [Neues Projekt erstellen](./new_project.md)


