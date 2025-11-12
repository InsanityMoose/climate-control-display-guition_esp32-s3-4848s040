# Climate Control Display with ESPHome and LVGL
An ESPHome-based smart climate control interface for Home Assistant using Guition ESP32-S3-4848S040 display.

[![ESPHome: 2025.7.5](https://img.shields.io/badge/ESPHome-2025.7.5-blue.svg)](https://esphome.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

![Device Preview](images/climate.jpg)

## Table of Contents
- [Hardware Requirements](#hardware-requirements)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
- [GPIO Pinout](#gpio-pinout)
- [Dependencies](#dependencies)
- [Development](#development)
- [References](#references)

## Hardware Requirements
- **Display Module**: [Guition ESP32-S3-4848S040]([https://robu.in/product/wireless-tag-wt32-sc01-plus-esp32s3-based-3-5-inch-iot-display/](https://devices.esphome.io/devices/guition-esp32-s3-4848s040/)) 
  - 4.0 inch 480x480 LCD
  - Screen Resolution: 480 x 480
  - ST7701S driver with MCU8080 8Bit interface
  - GT911 touchscreen controller
  - MCU: ESP32-S3 ( ESP32-S3-WROOM-1U-N16R8)
  - WiFi + BT + BLE
  - 16MB SPI flash
  - 8MB PSRAM

## Features

### Core Functionality
- Real-time temperature monitoring and control
- Multiple HVAC modes:
  - Auto
  - Cool
  - Heat
  - Dry
  - Fan Only
- Fan speed control modes
  - Auto
  - Low
  - Medium
  - Diffuse
- Touch-sensitive interface

### Display Features
- Auto-dimming display
- Time display with AM/PM format
- WiFi status indication

## Setup Steps

### Prerequisites
1. Home Assistant with ESPHome installed
2. ESP32-S3-4848S040
3. USB-C cable for flashing

1. Install ESPHome in your Home Assistant instance
2. Create a new ESPHome device
3. Copy the configuration files:
   ```bash
   git clone https://github.com/InsanityMoose/climate-control-display-guition_esp32-s3-4848s040.git
   cd climate-control-display-guition_esp32-s3-4848s040
   ```

4. Update `secrets.yaml`:
   ```yaml
   # filepath: secrets.yaml
   wifi_ssid: "Your_WiFi_SSID"
   wifi_password: "Your_WiFi_Password"
   fallback_password: "AP_Fallback_Password"
   ota_password: "OTA_Update_Password"
   api_key: "Your_API_Key"
   ```

5. Configure your device in `master-ac-display.yaml`:
   ```yaml
   # filepath: master-ac-display.yaml
   substitutions:
     device_name: 'master-ac-display'
     friendly_name: 'master-ac-display'
     climate_entity: climate.master_ac  # Your HA climate entity
   ```

## Configuration

### Home Assistant Settings

After flashing the device, Home Assistant will discover automatically.

Nake sure the at you have enabled `Allow the device to perform Home Assistant Actions`

![ESPHome Device Configure](images/device-configure.png)

![Allow HA Actions](images/ha-action-submit.png)

#### Device Controls 

![Device Controls](images/device-info.png)

### Display Settings
| Setting | Range | Default | Description |
|---------|--------|---------|-------------|
| Brightness | 5-100% | 50% | Screen brightness |
| Timeout | 10-300s | 300s | Screen timeout |

### Temperature Control
- Range: 16°C - 34°C
- Step: 1°C increments
- Visual circular gauge feedback

### Fan Modes
| Mode | Icon | Description |
|------|------|-------------|
| Off | ⭘ | Fan disabled |
| Auto | ⟲ | Automatic control |
| Low | ① | Low speed |
| Medium | ② | Medium speed |
| High | ③ | High speed |
| Diffuse | ⟳ | Diffuse mode |

## GPIO Pinout

## Dependencies

### Required Software
- ESPHome 2025.7.5+
- Home Assistant Core
- LVGL UI Components

### Optional Tools
- PlatformIO
- Visual Studio Code with ESPHome extension

## Development

### Build and Upload
```bash
esphome run master-ac-display.yaml
```

### Building
```bash
esphome compile master-ac-display.yaml
```

### Uploading
```bash
esphome upload master-ac-display.yaml
```

### Debugging
```bash
esphome logs master-ac-display.yaml
```

### Clean
```bash
esphome clean master-ac-display.yaml
```

## References

### Documentation
- [ESP32-S3-4848S040](https://devices.esphome.io/devices/guition-esp32-s3-4848s040/)
- [LVGL Cookbook](https://esphome.io/cookbook/lvgl.html)
- [ESP32 Forum Discussion](https://www.esp32.com/viewtopic.php?t=39219)

## License

MIT License

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

---

Thanks to kpr and everyone else
