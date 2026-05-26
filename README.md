# ALLNET Home Assistant Integration

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://hacs.xyz)
[![GitHub Release](https://img.shields.io/github/release/polsa/ha-allnet.svg)](https://github.com/polsa/ha-allnet/releases)
[![License](https://img.shields.io/github/license/polsa/ha-allnet.svg)](LICENSE)

A Home Assistant custom integration for **ALLNET MSR** monitoring and control devices, including the **ALL3500** series.

This integration communicates with ALLNET devices via their local JSON API and exposes all configured channels as Home Assistant entities — no cloud required.

---

## Supported Devices

| Model    | Description                        |
|----------|------------------------------------|
| ALL3500  | MSR monitoring and control device  |

Other ALLNET MSR devices with a compatible JSON API may also work.

---

## Supported Entities

| Platform        | Description                                                  |
|-----------------|--------------------------------------------------------------|
| `sensor`        | Analog measurement channels (temperature, humidity, CO2, voltage, current, power, energy, pressure, illuminance, and more) |
| `binary_sensor` | Digital input channels (motion, contact, smoke, moisture)   |
| `switch`        | Digital output / relay channels                             |

---

## Installation

### Via HACS (Recommended)

1. Open **HACS** in your Home Assistant instance.
2. Click the three-dot menu in the top right corner and select **Custom repositories**.
3. Enter the repository URL:
   ```
   https://github.com/polsa/ha-allnet
   ```
4. Select **Integration** as the category and click **Add**.
5. Search for **ALLNET** in HACS and click **Download**.
6. Restart Home Assistant.
7. Go to **Settings → Devices & Services → Add Integration** and search for **ALLNET**.

### Manual Installation

1. Download the latest release from the [Releases page](https://github.com/polsa/ha-allnet/releases).
2. Extract the ZIP file and copy the `allnet` folder into your Home Assistant `custom_components` directory:
   ```
   <config>/custom_components/allnet/
   ```
3. Restart Home Assistant.
4. Go to **Settings → Devices & Services → Add Integration** and search for **ALLNET**.

---

## Configuration

The integration is configured via the Home Assistant UI (config flow). No YAML configuration is required.

| Field            | Required | Default | Description                                                    |
|------------------|----------|---------|----------------------------------------------------------------|
| **Host**         | Yes      | —       | Hostname or IP address of the ALLNET device                    |
| **Username**     | No       | —       | Username for the web interface (if authentication is enabled)  |
| **Password**     | No       | —       | Password for the web interface (if authentication is enabled)  |
| **Use SSL**      | No       | Off     | Enable if the device is configured for HTTPS                   |
| **Device profile** | No    | Auto    | `Auto`, `MSR`, or `Managed Switch` — leave on Auto in most cases |

### Options (after setup)

| Option                   | Default | Description                                      |
|--------------------------|---------|--------------------------------------------------|
| **Polling interval (s)** | 30      | How often to poll the device (10–3600 seconds)   |

### mDNS / Zeroconf Auto-Discovery

ALLNET MSR devices advertise themselves via mDNS (`_http._tcp.local.`). If your device is on the same network as Home Assistant, it will be discovered automatically and you will be prompted to add it.

---

## Python Library

This integration is powered by the [python-allnet](https://github.com/polsa/python-allnet) library, available on PyPI:

- GitHub: [https://github.com/polsa/python-allnet](https://github.com/polsa/python-allnet)
- PyPI: [https://pypi.org/project/allnet/](https://pypi.org/project/allnet/)

---

## License

MIT License — see [LICENSE](LICENSE) for details.
