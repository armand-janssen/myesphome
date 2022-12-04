# EspHome Watermeter
1. Get arduino with wifi (Wemos D1 Mini Pro).
2. Install EspHome somewhere.
3. Add the `esphome-secrets.yaml` to the EspHome secrets with correct values.
4. Load `esphome-watermeter.yaml` and modify the `initial_value` of `initial_water_usage` to match your actual watermeter value.
5. Flash `esphome-watermeter.yaml` onto arduino.
6. Add utility meter entries from `home-assistant-utility-meter.yaml` to Home Assistant configuration.
7. Create a new helper in Home Assistant:
   1. Settings -> Devices & Services -> helpers
   2. Type: `Number`
   3. Name:`Water tarief`
   4. Icon: `mdi:water`
   5. Minimum value: `0`
   6. Maximum value: `100`
   7. Display mode: `Input field`
   8. Step size: `0.0001`
   9. Unit of measurement: `EUR/m³`
   10. Entity id: `input_number.water_tarief`
8.  Add `input_tarief` to a dashboard and add set the correct value. Example: `0.8024`
9.  Add the Watermeter to Home Assistant:
    1.  Settings -> Devices & Services
    2.  Add the watermeter
10. Set Energy Dashboard:
    1.  Settings -> Dashboards -> Energy
    2.  Add `sensor.watermeter_totaal` to the `Water Consumption` section
    3.  Select `Use an entity with current price` 
    4.  Use entity: `input_number.water_tarief`