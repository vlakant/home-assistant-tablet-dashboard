# Kitchen Atlas — Home Assistant tablet dashboard

A custom, permanently dark Home Assistant dashboard designed for a landscape kitchen tablet. It uses one local Web Component instead of a grid of standard Lovelace cards.

![Dashboard preview](docs/dashboard-preview.svg)

## Highlights

- responsive landscape layout tested at 960 × 600 and 1280 × 800 CSS pixels
- clock with seconds, date, indoor/outdoor temperature and seven-day cost chart
- three live camera areas, dimmable lights, appliance and household states
- three server-side kitchen timers with notes, phone targets and a tablet alarm
- custom notification-reason modal
- no cloud assets, web fonts, tracking code or bundled credentials

![Timer dialog](docs/timer-preview.svg)
![Notification dialog](docs/call-preview.svg)

## Repository contents

- `dashboard/dashboard-tablet.yaml` — anonymized three-view Lovelace dashboard
- `www/kitchen-atlas.js` — the custom dashboard component
- `packages/tablet_minutka.yaml` — optional timer helpers, script and automation
- `docs/ENTITIES.md` — entity mapping and expected states
- `docs/*.svg` — illustrative previews made with fictional data

## Install

1. Copy `www/kitchen-atlas.js` to `/config/www/tablet-atlas/kitchen-atlas.js`.
2. Add `/local/tablet-atlas/kitchen-atlas.js?v=1` as a **JavaScript Module** under Settings → Dashboards → Resources.
3. Replace every `example_*` entity in both the YAML and JavaScript. See [the entity map](docs/ENTITIES.md).
4. Create a YAML-mode dashboard and paste `dashboard/dashboard-tablet.yaml` into its raw configuration editor.
5. For the timers, copy `packages/tablet_minutka.yaml` into your packages directory, enable packages in `configuration.yaml`, edit the two placeholder `notify.mobile_app_phone_*` services, validate configuration and restart Home Assistant.
6. In `www/kitchen-atlas.js`, replace `mobile_app_phone_1` with the notification service used by the alert modal.
7. Reload the tablet page. Increment the `?v=` resource parameter after later JavaScript updates.

Example packages configuration:

```yaml
homeassistant:
  packages: !include_dir_named packages
```

The additional Heating view uses [multiple-entity-row](https://github.com/benct/lovelace-multiple-entity-row) and [card-mod](https://github.com/thomasloven/lovelace-card-mod). The main view needs only the bundled component and Home Assistant's camera stream element. For a fullscreen tablet view, [kiosk-mode](https://github.com/NemesisRE/kiosk-mode) is optional; append `?kiosk` to your own dashboard path.

## Privacy and safety

This repository contains fictional preview values and placeholder entity IDs. It contains no dashboard backups, live camera frames, LAN addresses, user IDs, notification targets, tokens or credentials. Review your own fork before publishing it because replacing placeholders can introduce private data.

The alert choices are intentionally easy to customize in `CALL_REASONS`. A tap sends immediately; there is no second confirmation.

## Language and customization

The UI is Czech and the currency is CZK. Labels and entities are grouped near the top of `kitchen-atlas.js`. Date and time follow the Home Assistant time zone. Narrow portrait phones are outside the design target.

Český návod je v [README.cs.md](README.cs.md).

## License

MIT — see [LICENSE](LICENSE).
