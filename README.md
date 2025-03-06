# Softener Salt Level Sensor (Package-Based)

This **Softener Salt Level Sensor** is published as an **ESPHome package**, allowing you to include it directly from GitHub without copying YAML files locally.

## Usage
In your **own** ESPHome YAML, add:
```yaml
esphome:
  name: my_softener_sensor

packages:
  remote_package_files:
    url: https://github.com/DBR-it/Softener-Salt-level
    files: [softener_level.yaml]
    ref: main
    refresh: 1d
```

### How It Works
- The **`packages`** section pulls the YAML configuration directly from GitHub.
- **`my_softener_sensor`** is the custom name for your device in Home Assistant.
- The configuration is updated automatically based on the `refresh` interval (e.g., `refresh: 1d`).

## Customizing the Sensor
You can override default **substitutions** in your local YAML file:
```yaml
substitutions:
  device_name: "my_custom_sensor"
  tank_height: "50.0"        # Set your tank height in inches
  distance_sensor_name: "Salt Distance Sensor"
  percentage_sensor_name: "Salt Level Percentage"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```

### Example Setup
```yaml
esphome:
  name: my_softener_sensor

packages:
  remote_package_files:
    url: https://github.com/DBR-it/Softener-Salt-level
    files: [softener_level.yaml]
    ref: main
    refresh: 1d

substitutions:
  device_name: "my_custom_sensor"
  tank_height: "50.0"
  distance_sensor_name: "Salt Distance Sensor"
  percentage_sensor_name: "Salt Level Percentage"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```

## What This Sensor Does
- Uses an **ESP8266** (e.g., D1 Mini) with an **ultrasonic sensor**.
- Measures **salt level** as a percentage based on your tank's height.
- Provides a **web server** on port 80 for local access.
- Supports **OTA updates** for easy firmware management.
- Creates a **fallback hotspot** if Wi-Fi fails.

This approach keeps your local configuration clean and allows automatic updates through the remote package. Feel free to expand on this README or add project-specific details as needed!

