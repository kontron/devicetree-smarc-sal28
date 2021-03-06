# Device tree overlays for SMARC-sAL28

This repository provides device tree overlays which can be loaded on top
the base device tree.

## Variant overlays

There are multiple variants of the SMARC-sAL28 in respect of the network
and audio functionality.

## Carrier overlays

Kontron supports two different carriers. One generic "SMARC evaluation
carrier 2.0" (`carrier-ads2.dtso`) and a "KBox A-230-LS" tailored to the
SMARC-sAL28 board (`carrier-s1914.dtso`). These overlays provide nodes for
the devices provided by these carriers.

## Additional overlays

### Embedded display port

The board provides a display port which can also be used as a embedded
display port. Loading `embedded-display-port.dtso` reconfigures the port as
eDP.

### CPLD update mode

Due to pin restrictions the CPLD shares GPIOs which are needed during CPLD
update. By default, the device tree contains nodes for the CPLD. Loading
`no-cpld.dtso` disables all CPLD devices in the device tree. Thus, the
GPIOs are free again and can be used to update the CPLD.

### CAN1

The second CAN port can be enabled if both the carrier and the module
supports it. Load `can1.dtso` to enable it. Please note, that this also
requires a modified RCW, because CAN1 shares pins with the I²C PM bus.

### 400kHz for I²C GP and PM

The I²C GP and PM bus can be switched to 400kHz by using either
`i2c-gp-400khz.dtso` or `i2c-pm-400khz.dtso`.

### Second ethernet link to the internal switch

By default, only one 2.5Gb/s link to the internal switch is active. This
acts as a sepecial CPU port. A second port can be enabled by loading the
overlay `eno3-swp5.dtso`.

### KBox A-230-LS carrier specific overlays

Also the KBox is available in different flavours and configurations.  The
first serial port can be in RS-232 mode (`carrier-s1914-ser0-rs232.dtso`),
in RS-485 mode (`carrier-s1914-ser0-rs485.dtso`) and RS-485 full duplex
mode (`carrier-s1914-ser0-rs485-fd.dtso`). Also the second CAN port can be
enabled if both the carrier and the module supports it
(`carrier-s1914-can1.dtso`).
