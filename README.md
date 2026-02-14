# 🎯 CRN Corne Keyboard - FINALE VERSION (Ohne Studio)

## ✅ Was ist in diesem Paket

### Pin-Konfiguration (wie gelötet):

**Linke Hälfte:**
- Rows: 21, 20, 19, 18
- Cols: 2, 7, 6, 5, 4, 3

**Rechte Hälfte:**
- Rows: 21, 20, 19, 18
- Cols: 3, 4, 5, 6, 7, 2

### Dateien:

```
boards/shields/crn/
├── crn.dtsi              # Haupt-Devicetree
├── crn_left.overlay      # Linke Hälfte (deine Pins!)
├── crn_right.overlay     # Rechte Hälfte (deine Pins!)
├── crn_left.conf         # Linke Konfiguration
├── crn_right.conf        # Rechte Konfiguration
├── Kconfig.shield        # Shield-Definition
└── Kconfig.defconfig     # Default-Konfiguration

config/
├── crn.keymap            # Deine Keymap (3 Layer)
├── crn.conf              # Globale Settings
└── west.yml              # ZMK v0.3 (stabil!)

build.yaml                # Build-Konfiguration
```

## 🚀 Installation

### Schritt 1: Alle Dateien ersetzen

Ersetze **ALLES** in deinem Repository mit den Dateien aus diesem ZIP:

```bash
# Lösche das alte Zeug
rm -rf boards/ config/ build.yaml

# Entpacke das neue ZIP
# Kopiere alle Ordner ins Repository
```

### Schritt 2: Commit & Push

```bash
git add -A
git commit -m "Clean setup - pins as soldered, no Studio"
git push
```

### Schritt 3: Warte auf Build (~2 Minuten)

GitHub Actions wird bauen:
- ✅ `crn_left-nice_nano_v2.uf2`
- ✅ `crn_right-nice_nano_v2.uf2`

## 🎮 Keymap-Übersicht

### Layer 0 (Default):
```
┌─────┬─────┬─────┬─────┬─────┬─────┐       ┌─────┬─────┬─────┬─────┬─────┬─────┐
│ TAB │  Q  │  W  │  E  │  R  │  T  │       │  Y  │  U  │  I  │  O  │  P  │BSPC │
├─────┼─────┼─────┼─────┼─────┼─────┤       ├─────┼─────┼─────┼─────┼─────┼─────┤
│CTRL │  A  │  S  │  D  │  F  │  G  │       │  H  │  J  │  K  │  L  │  ;  │  '  │
├─────┼─────┼─────┼─────┼─────┼─────┤       ├─────┼─────┼─────┼─────┼─────┼─────┤
│SHIFT│  Z  │  X  │  C  │  V  │  B  │       │  N  │  M  │  ,  │  .  │  /  │ ESC │
└─────┴─────┴─────┼─────┼─────┼─────┤       ├─────┼─────┼─────┼─────┴─────┴─────┘
                  │ GUI │ LWR │ SPC │       │ ENT │ RSE │ ALT │
                  └─────┴─────┴─────┘       └─────┴─────┴─────┘
```

### Layer 1 (Lower - Zahlen & Navigation):
- Zahlen 1-0
- Pfeiltasten (←↓↑→)
- Bluetooth-Steuerung

### Layer 2 (Raise - Symbole):
- Sonderzeichen (!@#$%^&*())
- Klammern ([{()}])
- Mehr Symbole

## 🔧 Firmware Flashen

### Für LINKE Hälfte:
1. Nice!Nano in Bootloader-Modus versetzen (2× Reset-Button)
2. `crn_left-nice_nano_v2.uf2` auf USB-Laufwerk kopieren
3. Automatischer Neustart

### Für RECHTE Hälfte:
1. Nice!Nano in Bootloader-Modus versetzen
2. `crn_right-nice_nano_v2.uf2` auf USB-Laufwerk kopieren
3. Automatischer Neustart

## 🔌 Verbindung

1. **Beide Hälften flashen**
2. **Linke Hälfte** (Central) mit PC via USB verbinden
3. **Rechte Hälfte** einschalten - verbindet sich automatisch
4. Fertig! 🎉

## 🧪 Testen

### Matrix-Test:
Teste jede Taste systematisch:
```
Row 0: Q W E R T Y | Y U I O P Backspace
Row 1: A S D F G H | H J K L ; '
Row 2: Z X C V B N | N M , . / ESC
Row 3: (nur Thumbs) | GUI LWR SPC | ENT RSE ALT
```

### Bluetooth-Test:
1. Drücke `Lower` + `BT_CLR` (2. Reihe, ganz links)
2. Warte 3 Sekunden
3. PC sollte "Corne CRN" in Bluetooth-Geräten sehen

## 📝 Keymap Anpassen

Bearbeite `config/crn.keymap`:

```c
// Beispiel: TAB zu ESC ändern
bindings = <
    &kp ESC   &kp Q &kp W ...  // <- Hier TAB zu ESC geändert
```

Nach jeder Änderung: Commit → Push → Warte auf Build → Flash neu

## ⚙️ Zusätzliche Optionen

### Sleep-Modus aktivieren:
In `config/crn.conf`:
```
CONFIG_ZMK_SLEEP=y
```

### BLE-Leistung erhöhen:
```
CONFIG_BT_CTLR_TX_PWR_PLUS_8=y
```

## 🐛 Troubleshooting

### Taste reagiert nicht:
1. Prüfe die Lötstelle
2. Teste mit Multimeter: Row-Pin zu Col-Pin beim Tastendruck
3. Vergleiche mit Pin-Nummern in `.overlay` Dateien

### Rechte Hälfte verbindet nicht:
1. Beide Hälften resetten (BT_CLR)
2. Rechte Hälfte zuerst einschalten
3. Dann linke Hälfte
4. Warte 10 Sekunden

### Falsche Tasten:
Deine Matrix könnte gespiegelt sein - sag mir welche Tasten falsch sind!

## 🎉 Das war's!

**Kein Studio.**  
**Keine Komplikationen.**  
**Einfach ein funktionierendes Keyboard.**

Du kannst Studio **später** immer noch aktivieren, wenn du willst. Aber jetzt hast du erstmal ein Keyboard das FUNKTIONIERT! 🚀

Viel Spaß beim Tippen! 😊
