# Entity map

Every `example_*` ID is a placeholder. Replace it in both `dashboard/dashboard-tablet.yaml` and `www/kitchen-atlas.js`. Timer entities are created by the optional package.

| Placeholder | Purpose |
| --- | --- |
| `light.example_light_1` | Dimmable light 1 |
| `light.example_light_2` | Dimmable light 2 |
| `light.example_light_3` | Dimmable light 3 |
| `camera.example_camera_1` | Live camera 1 |
| `camera.example_camera_2` | Live camera 2 |
| `camera.example_camera_3` | Live camera 3 |
| `sensor.example_room_1_temperature` | Room 1 temperature |
| `sensor.example_room_1_humidity` | Room 1 humidity |
| `sensor.example_room_2_temperature` | Room 2 temperature |
| `sensor.example_room_2_humidity` | Room 2 humidity |
| `sensor.example_fridge_temperature` | Fridge temperature |
| `sensor.example_freezer_temperature` | Freezer temperature |
| `sensor.example_outdoor_temperature` | Outdoor temperature and history |
| `sensor.example_indoor_temperature` | Indoor temperature and history |
| `sensor.example_indoor_humidity` | Indoor humidity |
| `sensor.example_daily_total_cost` | Daily total cost and history |
| `sensor.example_daily_electricity` | Daily electricity |
| `sensor.example_daily_gas` | Daily gas |
| `sensor.example_daily_water` | Daily water |
| `sensor.example_daily_electricity_cost` | Daily electricity cost |
| `sensor.example_daily_gas_cost` | Daily gas cost |
| `sensor.example_daily_water_cost` | Daily water cost |
| `binary_sensor.example_heating_active` | Heating state |
| `sensor.example_heating_level` | Heating output |
| `binary_sensor.example_window_open` | Window contact |
| `sensor.example_washer_state` | Washer state |
| `sensor.example_washer_remaining_minutes` | Washer remaining minutes |
| `sensor.example_dryer_state` | Dryer state |
| `sensor.example_dryer_remaining_minutes` | Dryer remaining minutes |
| `switch.example_light_4` | Switch controlled light |
| `binary_sensor.example_internet_online` | Internet connectivity |
| `binary_sensor.example_low_tariff` | Low tariff state |
| `switch.example_pool_filter` | Filter switch |
| `sensor.example_pool_temperature` | Water temperature |
| `sensor.example_tablet_battery` | Tablet battery |
| `input_boolean.example_bin_ready` | Bin reminder |
| `input_boolean.example_bio_bin_ready` | Bio bin reminder |
| `input_button.example_notification_button` | Notification modal trigger |
| `sensor.example_monthly_electricity` | Monthly electricity |
| `sensor.example_yearly_electricity` | Yearly electricity |
| `sensor.example_monthly_gas` | Monthly gas |
| `sensor.example_yearly_gas` | Yearly gas |
| `sensor.example_outdoor_aux_temperature` | Auxiliary outdoor temperature |
| `sensor.example_outdoor_aux_humidity` | Auxiliary outdoor humidity |
| `sensor.example_room_3_temperature` | Room 3 temperature |
| `sensor.example_room_3_humidity` | Room 3 humidity |
| `sensor.example_room_4_temperature` | Room 4 temperature |
| `sensor.example_room_4_humidity` | Room 4 humidity |
| `climate.example_thermostat` | Main thermostat |
| `climate.example_secondary_thermostat` | Secondary thermostat |

## Timer entities

The package creates `timer.tablet_minutka_1` through `_3` plus matching note, recipient, deadline and phase helpers. Do not rename them unless you also update every reference in the component, script and automation.
