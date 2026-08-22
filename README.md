# ESPHome Serial Proxies

This repo hosts YAML configurations for a curated selection of known, tested devices that can serve as Serial Proxies for Home Assistant.

If a device is not included here it may have a suitable configuration in the [ESPHome Device Configuration Repository](https://devices.esphome.io/).

## Devices

- [M5Stack Atom Lite](https://docs.m5stack.com/en/core/ATOM%20Lite) with [ATOMIC RS485 Base](https://docs.m5stack.com/en/atom/Atomic%20RS485%20Base) — [`atom-lite-rs485`](atom-lite-rs485/atom-lite-rs485.yaml) — serial port `RS-485`
- [M5Stack AtomS3 Lite](https://docs.m5stack.com/en/core/AtomS3%20Lite) with [ATOMIC RS485 Base](https://docs.m5stack.com/en/atom/Atomic%20RS485%20Base) — [`atoms3-lite-rs485`](atoms3-lite-rs485/atoms3-lite-rs485.yaml) — serial port `RS-485`

## Connecting to the serial port

Home Assistant finds the serial port on its own. It shows the port wherever an integration asks you to pick a serial device.

Other software must address the port with a URL:

```text
esphome://<host>[:<api-port>]/?port_name=<serial-port>
```

- `<host>` is the hostname or IP address of the device.
- `<api-port>` is the ESPHome API port. It defaults to `6053`.
- `<serial-port>` is the serial port name listed above.

Add `&noise_psk=<key>` if the device uses API encryption. Add `&password=<password>` if the device uses an API password.

Percent-encode the key and the password. A URL reads `+` as a space, and a base64 key often contains `+`, so write each one as `%2B`.

For example, an Atom Lite RS485 with hostname `atom-lite-rs485-a1b2c3`:

```text
esphome://atom-lite-rs485-a1b2c3.local/?port_name=RS-485
```
