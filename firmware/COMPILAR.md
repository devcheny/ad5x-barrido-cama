# Cómo se compiló `klipper_uno_v0.12.0.hex`

Sistema: Ubuntu, con `gcc-avr` 7.3 y `avr-libc` instalados.

```bash
git clone --depth 1 --branch v0.12.0 https://github.com/Klipper3d/klipper.git
cd klipper
```

En el ATmega328P (32 KB de flash) no cabe Klipper completo. En `src/Kconfig`, cambia a `default n` las opciones
`WANT_DISPLAYS`, `WANT_SENSORS`, `WANT_LIS2DW`, `WANT_SOFTWARE_I2C` y `WANT_SOFTWARE_SPI`.
Deja `WANT_GPIO_BITBANGING` en `y`, porque incluye los botones que usa el sensor Hall.

```bash
cat > .config <<'CFG'
CONFIG_MACH_AVR=y
CONFIG_MACH_atmega328p=y
CONFIG_CLOCK_FREQ=16000000
CONFIG_SERIAL=y
CONFIG_SERIAL_BAUD=250000
CFG
make olddefconfig
make
```

Con la versión de binutils de Ubuntu (2.26), el enlazado final da un falso error:
`section .bss is not within region data`. En realidad el firmware solo usa unos 400 bytes de RAM
(`.data` 42 + `.bss` 360). Para generarlo, se repite el comando de enlace de `make V=1` añadiendo
`-Wl,--noinhibit-exec`, y luego se convierte a hex:

```bash
avr-objcopy -j .text -j .data -O ihex out/klipper.elf out/klipper.elf.hex
```

Con un `avr-gcc`/binutils más modernos (por ejemplo los de Debian), ese paso no debería hacer falta.
