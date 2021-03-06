# Placa STM32F103C8T6 (BluePill) con herramientas GNU

## Puesta en marcha
(De: [A template project for STM32 on Linux](https://blog.gypsyengineer.com/en/diy-electronics/a-template-project-for-stm32f103-on-linux.html))

1. Instalar el Toolchain:
```
sudo apt install gcc-arm-none-eabi
```
1. Descargar e instalar las herramientas de grabación:
```
git clone https://github.com/texane/stlink.git
cd stlink
make release
```
1. Copiar la regla de udev:
```
sudo cp stlink/config/udev/rules.d/49-stlinkv2.rules /etc/udev/rules.d/
```
1. Descargar y descomprimir las bibliotecas [STM32F10x standard peripheral library](https://www.st.com/content/st_com/en/products/embedded-software/mcu-mpu-embedded-software/stm32-embedded-software/stm32-standard-peripheral-libraries/stsw-stm32054.html).
1. Descargar aplicación de ejemplo `Blink`:
```
git clone https://github.com/artem-smotrakov/stm32f103-template
```

1. Modificar el archivo `Makefile`:
   - Fijar la variable `STD_PERIPH_LIBS` a la ruta de las bibliotecas antes descomprimidas.
   - Fijar la variable `ST_FLASH` a la ruta de la herramienta STLink construídas (subdirectorio `build/Release/bin/`)
1. Construir la aplicación de ejemplo y grabar:
```
make
make burn
```

