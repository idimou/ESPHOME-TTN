# ESPHOME-TTN

ESPHome component to send data from ESP32 to The Things Network (TTN) via LoRaWAN.

## Supported devices

All TTN gateways supporting v3 stack are supported. 

## Tested with ESP32 LORA capable boards

  * ESP32 TTGO LoRa32 V1.0

## Requirements

* [ESPHome 2021.10 or higher](https://github.com/esphome/esphome/releases).
* Generic ESP32 or ESP8266 board

## Installation

You can install this component with [ESPHome external components feature](https://esphome.io/components/external_components.html) like this:
```yaml
external_components:
  - source: https://github.com/idimou/ESPHOME-TTN@main

victron:
  id: victron0
  uart_id: uart_0

sensor:
  - platform: victron
    victron_id: victron0
    panel_voltage:
      name: "Panel voltage"
    battery_voltage:
      name: "Battery voltage"
    battery_current:
      name: "Battery current"
```

or just use the `esp8266-example.yaml` as proof of concept:

```bash
# Install esphome
pip3 install esphome

# Clone this external component
git clone https://github.com/idimou/ESPHOME-TTN.git
cd ESPHOME-ΤΤΝ

# Create a secret.yaml containing some setup specific secrets
cat > secrets.yaml <<EOF
AppEUI: MY_APPEUI
DevEUI: MY_DEVEUI
AppKey: MY_APPKEY

wifi_ssid: MY_WIFI_SSID
wifi_password: MY_WIFI_PASSWORD
EOF

# Validate the configuration, create a binary, upload it, and start logs
esphome run esp32-example.yaml
```

## Debugging

If this component doesn't work out of the box for your device please flash the `debug-esp32-example.yaml` and create an issue providing the full ESPHome log.

```
esphome run debug-esp32-example.yaml
```
