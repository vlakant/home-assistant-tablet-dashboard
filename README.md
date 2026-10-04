# Kitchen Atlas — tabletový dashboard pro Home Assistant

Vlastní trvale tmavý dashboard určený pro tablet položený na šířku. Hlavní pohled vykresluje lokální Web Component bez skládání běžných Lovelace karet.

[English version](README.en.md)

![Skutečné rozložení dashboardu s anonymizovanými kamerami a ukázkovými hodnotami](docs/dashboard-preview.jpg)

## Co obsahuje

- hodiny se sekundami, datum a vnitřní i venkovní teplotu
- tři kamery, tři světla, spotřeby, teploty a stav domácnosti
- tři kuchyňské minutky běžící v Home Assistantu
- zvuk alarmu přímo na tabletu a volitelné mobilní notifikace
- vlastní modal s důvody pro rychlé upozornění
- jediný hlavní pohled Tablet; ovládání topení a kamery se otevírá v modalech
- responzivní rozložení ověřené při 960 × 600 a 1280 × 800 CSS pixelech
- žádné cloudové prvky, webová písma, sledovací kód ani přibalené přihlašovací údaje

![Skutečný dialog minutky](docs/timer-preview.png)
![Skutečný dialog upozornění](docs/call-preview.png)

## Obsah repozitáře

- `dashboard/dashboard-tablet.yaml` — anonymizovaný Lovelace dashboard s jedním hlavním pohledem
- `www/kitchen-atlas.js` — vlastní komponenta dashboardu
- `packages/tablet_minutka.yaml` — volitelná konfigurace minutek, skript a automatizace
- `docs/ENTITIES.md` — mapa entit a očekávaných stavů
- `docs/*.png` — náhledy vyrenderované přímo z komponenty s anonymizovanými kamerami a ukázkovými údaji

## Instalace

1. Zkopírujte `www/kitchen-atlas.js` do `/config/www/tablet-atlas/kitchen-atlas.js`.
2. V Nastavení → Nástěnky → Zdroje přidejte `/local/tablet-atlas/kitchen-atlas.js?v=1` jako JavaScript Module.
3. Podle [docs/ENTITIES.md](docs/ENTITIES.md) nahraďte všechna `example_*` ID v YAML i JavaScriptu vlastními entitami.
4. Vytvořte YAML dashboard a do editoru nezpracované konfigurace vložte `dashboard/dashboard-tablet.yaml`.
5. Chcete-li minutky, zkopírujte `packages/tablet_minutka.yaml` do adresáře balíčků, povolte packages v `configuration.yaml`, změňte služby `notify.mobile_app_phone_1` a `notify.mobile_app_phone_2`, zkontrolujte konfiguraci a restartujte HA.
6. Pro modal Upozornit změňte v `www/kitchen-atlas.js` zástupnou službu `mobile_app_phone_1`.
7. Po změnách obnovte stránku; při další aktualizaci JS zvyšte parametr `?v=`.

```yaml
homeassistant:
  packages: !include_dir_named packages
```


## Soukromí a bezpečnost

Ukázkové obrázky zachycují skutečné rozložení a dialogy komponenty. Hodnoty jsou ukázkové a obraz kamer je nahrazen anonymní maskou. Repozitář neobsahuje lokální adresy, živé kamery, uživatelská ID, cíle notifikací, tokeny, hesla ani zálohy Home Assistantu.

Před zveřejněním vlastní upravené verze ji znovu zkontrolujte, protože dosazením skutečných entit můžete přidat soukromé údaje. Možnosti v upozorňovacím dialogu lze upravit v `CALL_REASONS`; klepnutí na důvod odešle zprávu ihned bez dalšího potvrzení.

## Jazyk a přizpůsobení

Rozhraní je v češtině a používá měnu CZK. Popisky a entity jsou soustředěné poblíž začátku souboru `www/kitchen-atlas.js`. Datum a čas respektují časovou zónu Home Assistantu. Rozložení se přizpůsobuje tabletu i telefonu na výšku a na šířku.

## Licence

MIT — viz [LICENSE](LICENSE).

## Aktualizace 1.1

- Karta Sklep rozlišuje chodbu a čtyři místnosti; stálá ikona pohybu se při detekci probarví. Klepnutí otevře samostatné ovládání pěti světel.
- Okénko Kotel otevírá hlavní termostat, aktuální a cílovou teplotu, zapnutí/vypnutí a historii teplot i modulace hořáku v procentech za 24 hodin nebo 7 dní. Grafy používají vestavěné history-graph karty HA.
- Volitelný balíček `packages/cellar_lights.yaml` po hodině souvislého svícení v místnosti odešle interaktivní notifikaci ANO/NE; chodbu nesleduje. ANO vypne pouze danou místnost, NE ponechá světlo svítit. Na iPhonu zobrazíte akce podržením notifikace. Nahraďte služby a entity podle mapy, zapněte packages a ověřte konfiguraci před restartem HA. Restart/reload resetuje časové čekání a čekající reakce.
- `HEATING_ENTITY`, `CELLAR_LIGHTS` a `CELLAR_MOTION` v JS slouží k vlastnímu mapování. Ovládání teploty dodržuje meze termostatu a platnou změnu odešle automaticky po krátké pauze.

![Cellar controls / Ovládání sklepa](docs/cellar-preview.jpg)

Dashboard obsahuje pouze hlavní stránku. Samostatné záložky Topení a Kamera byly odstraněny; jejich ovládání je dostupné v modalech hlavní stránky.

## Aktualizace 1.2

Telefon na výšku skládá panely pod sebe a kamery lze posouvat do stran. Dotykové ovladače a dialogy se přizpůsobují malé obrazovce. Ověřeno v prohlížeči na šířkách 393, 852 a 960 CSS pixelů; skutečné zařízení může vyžadovat obnovení stránky.
