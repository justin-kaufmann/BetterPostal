# BetterPostal

**Smarter mailbox addon for World of Warcraft.**  
**Intelligentes Post-Addon für World Of Warcraft Retail (Midnight)**

---

# English

BetterPostal makes the World of Warcraft mailbox easier to manage with configurable collection, message selection, category filters, progress recovery, and a compact settings dashboard. It is designed to automate routine collection while keeping potentially risky mail actions under the player's control.

## Highlights

- **Open All:** Process eligible mail without opening each message manually.
- **Choose what gets collected:** Filter mail by Auction House outcome, Postmaster deliveries, regular mail with attachments, or regular mail containing money.
- **Filter attachment types:** Choose which item categories to collect: gold, equipment, consumables, trade goods, recipes, quest items, and other items.
- **Select your way:** Select messages on the current page, select eligible messages across pages, or mark individual messages. A manual selection takes priority over the default bulk-selection behavior.
- **Adjust collection speed:** Configure the delay between collection actions, from 0.01 to 5 seconds.
- **Resume interrupted work:** Optionally remember progress if bags fill up or the mailbox closes, then attempt to resume when the mailbox is available again.
- **Safety-conscious C.O.D. handling:** C.O.D. mail is not paid automatically. It is routed to manual review instead.
- **Optional cleanup:** Choose whether to delete mail that is empty after collection, where the WoW client permits deletion.
- **First/last-page navigation:** Jump to the first or last inbox page using dedicated double-arrow buttons.
- **Settings dashboard:** See processing status, mailbox status, selection, collection speed, language, and relevant settings in one place.
- **English and German UI:** Switch between automatic language selection, English, and German.
- **Convenient access:** Open settings from the mailbox gear or minimap button; use slash commands for quick control.

## Mail filters

The mail-type filters include:

- Auction cancelled
- Auction expired
- Auction outbid
- Auction sale successful
- Auction won
- Postmaster deliveries
- Regular mail with items
- Regular mail with money

Attachment-type filters include:

- Gold
- Equipment
- Consumables
- Trade goods
- Recipes
- Quest items
- Other items

If no mail-type filter is enabled, the addon's documented behavior is to make all supported mail types eligible. A manual message selection takes precedence for which messages are processed. C.O.D. mail is excluded from automatic payment and is handled manually.

## Safety notes

- **C.O.D. mail is never paid automatically.**
- Deleting mail is optional and disabled by default.
- Cleanup only targets messages that are empty after collection and that WoW allows the addon to delete.
- If bags are full, collection stops rather than continuing to collect items it cannot store.
- Automatic resume can be disabled in settings.

Please review the selected mail and filter settings before starting a bulk collection run.

## Installation

1. Download or clone this repository.
2. Place the `BetterPostal` folder in your World of Warcraft Retail add-ons directory:
   `World of Warcraft/_retail_/Interface/AddOns/BetterPostal/`
3. Make sure `BetterPostal.toc` is directly inside the `BetterPostal` folder and keep the bundled `Libs` directory.
4. Start or reload the game and enable **BetterPostal** in the AddOns list.

Do not add an older monolithic version of the addon alongside this modular version. The `.toc` file defines the modules loaded by the game.

## Controls

- `/betterpostal` or `/bp` — open settings/help.
- `/bp settings` — open or close the settings panel.
- `/bp start` — start processing eligible mail.
- `/bp stop` — stop processing and cancel a saved resume request.
- `/bp lang auto` — follow the game language.
- `/bp lang en` — use English.
- `/bp lang de` — use German.

The legacy `/prv3` slash-command alias is also retained for existing macros.

## Settings at a glance

| Setting | What it does |
|---|---|
| Mail-type filters | Choose which categories of mail are eligible for bulk collection. |
| Attachment-type filters | Choose which types of attachments to collect. |
| Collection speed | Set the delay between collection actions. Server responses may still affect actual speed. |
| Auto-resume | Remember interrupted progress and attempt to resume when possible. |
| Delete empty mail | Optionally delete messages after their contents have been collected, if allowed by WoW. |
| Language | Automatic, English, or German. |

## Project layout

```text
BetterPostal/
├── Assets/              # First/last page button textures
├── Core/Bootstrap.lua   # Defaults, namespace, localization helpers
├── Libs/                # Bundled support libraries
├── Mail/
│   ├── Actions.lua      # Single-message actions and guarded C.O.D./delete flows
│   ├── Processor.lua    # Collection engine, filters, progress and resume
│   ├── Selection.lua    # Message selection and selection controls
│   └── Setup.lua        # Mailbox layout and UI hooks
├── UI/
│   ├── MailFrame.lua    # Mail frame integration and localization
│   ├── Minimap.lua      # Settings/minimap access
│   ├── Navigation.lua   # Page jumps and main-button integration
│   └── Settings.lua     # Settings dashboard
├── Events.lua           # Lifecycle, events, slash commands
├── localize.lua         # English and German strings
└── BetterPostal.toc     # Addon metadata and load order
```

## Versioning

The release version is defined in `BetterPostal.toc` by the `## Version:` metadata line. The settings panel reads that metadata and displays it automatically; normally, you do **not** need to hard-code the version in `UI/Settings.lua`.

## Known limitations

- Collection is subject to the mailbox state, bag space, server responses, and what the WoW client/API permits.
- Automatic resume can only restore a message selection when a message can be identified safely.
- This project should be tested in-game with representative mail types before relying on bulk collection for important mail.

## Contributing and feedback

Bug reports and feature requests are welcome. Include the WoW version, BetterPostal version, steps to reproduce, relevant error messages, and whether mail filters or manual selections were enabled.

---

# Deutsch

BetterPostal erleichtert die Verwaltung des World-of-Warcraft-Postfachs mit konfigurierbarem Einsammeln, Nachrichtenauswahl, Kategorienfiltern, Wiederaufnahme unterbrochener Vorgänge und einem übersichtlichen Einstellungsfenster. Routineaufgaben werden automatisiert, während potenziell riskante Aktionen bewusst abgesichert bleiben.

## Die wichtigsten Funktionen

- **Alle öffnen:** Verarbeitet geeignete Post, ohne jeden Brief einzeln öffnen zu müssen.
- **Bestimmen, was eingesammelt wird:** Filter für Auktionen, Postmeister-Lieferungen, normale Briefe mit Gegenständen und normale Briefe mit Geld.
- **Beutearten filtern:** Gold, Ausrüstung, Verbrauchsgüter, Handelswaren, Rezepte, Questgegenstände und sonstige Gegenstände lassen sich getrennt steuern.
- **Flexible Auswahl:** Aktuelle Seite markieren, geeignete Briefe über alle Seiten auswählen oder einzelne Briefe markieren. Eine manuelle Auswahl hat Vorrang.
- **Sammeltempo einstellen:** Die Wartezeit zwischen Sammelaktionen lässt sich von 0,01 bis 5 Sekunden einstellen.
- **Unterbrochene Vorgänge fortsetzen:** Optional wird der Fortschritt bei vollen Taschen oder geschlossenem Postfach gespeichert und beim nächsten möglichen Zeitpunkt wieder aufgenommen.
- **Sicherer Umgang mit Nachnahme:** Nachnahmebriefe werden niemals automatisch bezahlt, sondern zur manuellen Prüfung geöffnet.
- **Optionale Bereinigung:** Briefe, die nach dem Einsammeln leer sind, können – sofern WoW das Löschen erlaubt – automatisch gelöscht werden.
- **Direkt zur ersten/letzten Seite:** Eigene Doppelpfeil-Buttons springen zur ersten oder letzten Postfachseite.
- **Einstellungs-Dashboard:** Status, Postfach, Auswahl, Sammeltempo, Sprache und wichtige Optionen an einem Ort.
- **Deutsch und Englisch:** Automatische Sprachauswahl oder manuelle Umschaltung auf Deutsch bzw. Englisch.
- **Schneller Zugriff:** Einstellungen über das Zahnrad im Postfach, den Minimap-Button oder Slash-Befehle öffnen.

## Nachrichtenfilter

Folgende Nachrichtentypen können gefiltert werden:

- Auktion abgebrochen
- Auktion abgelaufen
- Überbotene Auktion
- Erfolgreicher Auktionsverkauf
- Gewonnene Auktion
- Postmeister-Lieferungen
- Normale Post mit Gegenständen
- Normale Post mit Geld

Zusätzlich können die einzusammelnden Gegenstandsarten eingeschränkt werden:

- Gold
- Ausrüstung
- Verbrauchsgüter
- Handelswaren
- Rezepte
- Questgegenstände
- Sonstige Gegenstände

Wenn kein Nachrichtenfilter aktiviert ist, gelten alle unterstützten Nachrichtentypen als zulässig. Eine manuelle Auswahl bestimmt, welche markierten Briefe verarbeitet werden. Nachnahmebriefe werden von der automatischen Bezahlung ausgeschlossen und manuell behandelt.

## Sicherheitsfunktionen

- **Nachnahme wird niemals automatisch bezahlt.**
- Das Löschen von Briefen ist optional und standardmäßig deaktiviert.
- Die Bereinigung betrifft nur Briefe, die nach dem Einsammeln leer sind und von WoW gelöscht werden dürfen.
- Bei vollen Taschen wird das Einsammeln angehalten, statt Gegenstände ohne freien Platz weiter anzufordern.
- Die automatische Fortsetzung kann in den Einstellungen deaktiviert werden.

Prüfe vor einem Sammellauf die aktivierten Nachrichtenfilter und die Auswahl.

## Installation

1. Lade dieses Repository herunter oder klone es.
2. Lege den Ordner `BetterPostal` in deinem WoW-Retail-Addon-Verzeichnis ab:
   `World of Warcraft/_retail_/Interface/AddOns/BetterPostal/`
3. `BetterPostal.toc` muss direkt im Ordner `BetterPostal` liegen. Der mitgelieferte Ordner `Libs` muss erhalten bleiben.
4. Starte das Spiel neu oder lade die Benutzeroberfläche neu und aktiviere **BetterPostal** in der AddOn-Liste.

Lege keine ältere, monolithische Version zusätzlich zu dieser modularen Version ab. Die `.toc`-Datei legt fest, welche Lua-Module geladen werden.

## Befehle

- `/betterpostal` oder `/bp` — Hilfe anzeigen bzw. Einstellungen öffnen.
- `/bp settings` — Einstellungsfenster öffnen oder schließen.
- `/bp start` — Verarbeitung geeigneter Post starten.
- `/bp stop` — Verarbeitung stoppen und eine gespeicherte Fortsetzung abbrechen.
- `/bp lang auto` — Sprache des Spiels verwenden.
- `/bp lang de` — Deutsch verwenden.
- `/bp lang en` — Englisch verwenden.

Der ältere Slash-Befehl `/prv3` bleibt aus Kompatibilitätsgründen für bestehende Makros verfügbar.

## Einstellungen im Überblick

| Einstellung | Funktion |
|---|---|
| Nachrichtenfilter | Legt fest, welche Kategorien beim Sammeln berücksichtigt werden. |
| Gegenstandsfilter | Bestimmt, welche Arten von Anhängen eingesammelt werden. |
| Sammeltempo | Legt die Pause zwischen Sammelaktionen fest. Serverantworten können das tatsächliche Tempo beeinflussen. |
| Automatische Fortsetzung | Speichert unterbrochenen Fortschritt und versucht, später fortzufahren. |
| Leere Briefe löschen | Löscht optional leere Briefe nach dem Einsammeln, sofern WoW dies erlaubt. |
| Sprache | Automatisch, Deutsch oder Englisch. |

## Projektstruktur

```text
BetterPostal/
├── Assets/              # Grafiken für Erste-/Letzte-Seite-Buttons
├── Core/Bootstrap.lua   # Standardwerte, Namespace, Lokalisierungshilfen
├── Libs/                # Mitgelieferte Bibliotheken
├── Mail/
│   ├── Actions.lua      # Einzelaktionen und abgesicherte Nachnahme-/Löschabläufe
│   ├── Processor.lua    # Sammel-Engine, Filter, Fortschritt und Fortsetzung
│   ├── Selection.lua    # Nachrichtenauswahl und Auswahlsteuerung
│   └── Setup.lua        # Postfachlayout und UI-Anbindung
├── UI/
│   ├── MailFrame.lua    # Postfachintegration und Lokalisierung
│   ├── Minimap.lua      # Zugriff über Einstellungen/Minimap
│   ├── Navigation.lua   # Seitensprünge und Hauptbutton-Anbindung
│   └── Settings.lua     # Einstellungs-Dashboard
├── Events.lua           # AddOn-Lebenszyklus, Events und Slash-Befehle
├── localize.lua         # Deutsche und englische Texte
└── BetterPostal.toc     # AddOn-Metadaten und Ladereihenfolge
```

## Version einstellen

Die Versionsnummer wird in `BetterPostal.toc` über die Metadatenzeile `## Version:` festgelegt. Das Einstellungsfenster liest diesen Wert automatisch aus und zeigt ihn an. Normalerweise muss die Version **nicht zusätzlich in `UI/Settings.lua` fest eingetragen** werden.

## Bekannte Einschränkungen

- Das Einsammeln hängt vom Postfachzustand, freien Taschenplätzen, Serverantworten und den Möglichkeiten der WoW-API ab.
- Eine gespeicherte manuelle Auswahl kann nur dann wiederhergestellt werden, wenn sich der betreffende Brief sicher identifizieren lässt.
- Teste das AddOn vor dem Einsatz bei wichtigen Briefen mit unterschiedlichen Nachrichtentypen direkt im Spiel.

## Mitwirken und Fehler melden

Fehlermeldungen und Feature-Wünsche sind willkommen. Gib dabei bitte die WoW-Version, BetterPostal-Version, Reproduktionsschritte, relevante Fehlermeldungen und den Status der Nachrichtenfilter bzw. manuellen Auswahl an.
