# Catamaran CMS - Grundlagen für Einsteiger

Willkommen beim Catamaran CMS! Diese Anleitung erklärt die wichtigsten Konzepte und Begriffe in einfacher Sprache - kein Vorwissen nötig.

## Inhaltsverzeichnis
1. [Was ist ein Headless CMS?](#was-ist-ein-headless-cms)
2. [Backend und Frontend](#backend-und-frontend)
3. [Catamaran als Data Hub](#catamaran-als-data-hub)
4. [Models - Ihre Inhaltstypen](#models---ihre-inhaltstypen)
5. [ElementTypes - Die Bausteine](#elementtypes---die-bausteine)
6. [Multi-Site - Mehrere Websites verwalten](#multi-site---mehrere-websites-verwalten)
7. [Zusammenfassung](#zusammenfassung)

---

## Was ist ein Headless CMS?

### Der Vergleich: Traditionelles CMS vs. Headless CMS

**Stellen Sie sich ein traditionelles CMS wie einen Fernseher vor:**
- Der Fernseher zeigt Ihnen Inhalte (Filme, Serien) direkt an
- Sie können nur auf diesem einen Gerät schauen
- Das Design (der Bildschirm) ist fest mit dem Inhalt verbunden

**Ein Headless CMS ist wie ein Streaming-Dienst (Netflix, Disney+):**
- Die Inhalte werden zentral gespeichert
- Sie können diese Inhalte auf vielen verschiedenen Geräten ansehen: Fernseher, Handy, Tablet, Computer
- Jedes Gerät zeigt die Inhalte anders an, aber der Inhalt bleibt gleich

### Was bedeutet "Headless"?

"Headless" bedeutet wörtlich "ohne Kopf". Der "Kopf" ist in diesem Fall die Darstellung (das Design) Ihrer Website.

**Catamaran CMS ist headless, weil:**
- Sie Ihre Inhalte einmal erstellen und verwalten
- Diese Inhalte dann auf beliebig vielen verschiedenen Websites, Apps oder Geräten angezeigt werden können
- Jede Website kann ein völlig anderes Design haben

**Praktisches Beispiel:**
Sie schreiben einen Blog-Artikel in Catamaran. Dieser Artikel kann dann:
- Auf Ihrer Hauptwebsite erscheinen
- In Ihrer mobilen App angezeigt werden
- Auf einem digitalen Bildschirm in Ihrem Geschäft gezeigt werden
- In einem Newsletter verwendet werden

---

## Backend und Frontend

Diese beiden Begriffe beschreiben die zwei Hauptteile eines jeden Web-Systems.

### Backend - Der Backstage-Bereich

**Das Backend ist wie der Backstage-Bereich eines Theaters:**
- Hier arbeiten Sie hinter den Kulissen
- Hier verwalten Sie alle Inhalte
- Hier legen Sie fest, wie Daten strukturiert werden
- Normale Besucher Ihrer Website sehen das Backend nicht

**Im Catamaran Backend können Sie:**
- Blog-Artikel schreiben und bearbeiten
- Bilder hochladen und verwalten
- Neue Inhaltstypen erstellen (z.B. "Produkte", "Veranstaltungen")
- Entscheiden, welche Felder ein Inhalt haben soll

**Zugriff:** Das Backend erreichen Sie über die Admin-Oberfläche (z.B. `https://ihre-domain.de/admin`)

### Frontend - Die Bühne

**Das Frontend ist wie die Bühne des Theaters:**
- Hier sehen Ihre Besucher die fertigen Inhalte
- Das Design und Layout wird hier sichtbar
- Die Darstellung ist optimiert für die Nutzererfahrung
- Dies ist die eigentliche Website, die Ihre Kunden besuchen

**Das Frontend zeigt:**
- Ihre Blog-Artikel in schönem Design
- Bilder in der richtigen Größe
- Navigation und Menüs
- Interaktive Elemente (Buttons, Formulare)

**Im Catamaran CMS:**
- Backend = Die Admin-Oberfläche (EasyAdmin), wo Sie Inhalte verwalten
- Frontend = Ihre öffentliche Website (z.B. gebaut mit SvelteKit, React oder Vue.js)

---

## Catamaran als Data Hub

### Was ist ein Data Hub?

Ein Data Hub (Daten-Zentrale) ist ein zentraler Ort, an dem alle Ihre Daten gespeichert und verwaltet werden.

**Stellen Sie sich eine moderne Bibliothek vor:**
- Alle Bücher (Daten) sind an einem Ort
- Verschiedene Leute können die gleichen Bücher lesen (verschiedene Frontends)
- Die Bücher können kopiert und in andere Filialen geschickt werden (APIs)
- Neue Bücher werden zentral katalogisiert

### Wie funktioniert Catamaran als Data Hub?

```
┌─────────────────────────────────────┐
│     CATAMARAN CMS (Data Hub)        │
│  ┌─────────────────────────────┐   │
│  │  Ihre Inhalte & Daten       │   │
│  │  - Blog-Artikel             │   │
│  │  - Produkte                 │   │
│  │  - Bilder                   │   │
│  │  - Veranstaltungen          │   │
│  └─────────────────────────────┘   │
└─────────────────┬───────────────────┘
                  │ API (Schnittstelle)
        ┌─────────┼─────────┬─────────┐
        │         │         │         │
        ▼         ▼         ▼         ▼
   Website    Mobile    Smart      News-
    (Web)      App      Watch     letter
```

**Vorteile dieses Konzepts:**

1. **Einmal erstellen, überall verwenden**
   - Sie schreiben einen Text einmal
   - Dieser erscheint automatisch auf allen Ihren Plattformen

2. **Konsistente Daten**
   - Wenn Sie einen Artikel aktualisieren, ist er überall aktuell
   - Keine doppelte Pflege nötig

3. **Flexibilität**
   - Sie können jederzeit neue Ausgabekanäle hinzufügen
   - Ohne die bestehenden Inhalte zu ändern

4. **Zukunftssicher**
   - Neue Technologien können einfach angebunden werden
   - Ihre Daten bleiben unabhängig von Design-Trends

---

## Models - Ihre Inhaltstypen

### Was sind Models?

Models (Modelle) sind wie **Vorlagen oder Schablonen** für Ihre Inhalte.

**Ein einfacher Vergleich:**

Stellen Sie sich vor, Sie füllen ein Formular aus:
- **Personalausweis-Formular:** Hat Felder für Name, Geburtsdatum, Adresse, Foto
- **Bewerbungsformular:** Hat Felder für Lebenslauf, Anschreiben, Zeugnisse
- **Rezept:** Hat Felder für Zutaten, Zubereitungszeit, Anleitung

Jedes Formular ist ein anderes "Model" mit unterschiedlichen Feldern.

### Models im Catamaran CMS

**Beispiel "Blog-Artikel" Model:**
```
┌──────────────────────────────┐
│   MODEL: Blog-Artikel        │
├──────────────────────────────┤
│ Felder:                      │
│  □ Titel                     │
│  □ URL-Slug                  │
│  □ Titelbild                 │
│  □ Teaser-Text               │
│  □ Haupttext                 │
│  □ Autor                     │
│  □ Veröffentlichungsdatum    │
│  □ Tags                      │
└──────────────────────────────┘
```

**Beispiel "Produkt" Model:**
```
┌──────────────────────────────┐
│   MODEL: Produkt             │
├──────────────────────────────┤
│ Felder:                      │
│  □ Produktname               │
│  □ Artikelnummer             │
│  □ Preis                     │
│  □ Produktbilder             │
│  □ Beschreibung              │
│  □ Verfügbarkeit             │
│  □ Kategorie                 │
└──────────────────────────────┘
```

### Warum sind Models wichtig?

1. **Struktur:** Alle Blog-Artikel haben die gleichen Felder
2. **Konsistenz:** Sie vergessen keine wichtigen Informationen
3. **Flexibilität:** Sie können beliebig viele verschiedene Models erstellen
4. **Übersichtlichkeit:** Jeder Content-Typ hat seine eigene Vorlage

### Models in der Praxis

**Als Administrator erstellen Sie ein Model einmal:**
- Legen fest: "Ein Blog-Artikel braucht Titel, Bild, Text"
- Definieren, welche Felder Pflichtfelder sind
- Bestimmen, welche Art von Inhalt in jedem Feld erlaubt ist

**Als Redakteur verwenden Sie dann das Model:**
- Klicken auf "Neuer Blog-Artikel"
- Füllen die vorgegebenen Felder aus
- System sorgt dafür, dass nichts fehlt

---

## ElementTypes - Die Bausteine

### Was sind ElementTypes?

ElementTypes sind die verschiedenen **Arten von Inhalts-Bausteinen**, die Sie in Ihre Models einbauen können.

**Der Vergleich: Werkzeugkasten**

Stellen Sie sich vor, Sie bauen ein Möbelstück. In Ihrem Werkzeugkasten haben Sie verschiedene Werkzeuge:
- Hammer (für Nägel)
- Schraubenzieher (für Schrauben)
- Säge (zum Schneiden)

ElementTypes sind wie diese Werkzeuge - jedes hat einen speziellen Zweck.

### Verfügbare ElementTypes im Catamaran CMS

#### 1. **Text / TextField**
- **Wofür:** Kurze Texte (Überschriften, Namen)
- **Beispiel:** Produktname, Titel eines Artikels
- **Besonderheit:** Meist eine einzige Zeile

#### 2. **Textarea / Textfeld**
- **Wofür:** Längere Texte ohne Formatierung
- **Beispiel:** Kurzbeschreibung, Teaser
- **Besonderheit:** Mehrere Zeilen, aber kein Fettdruck oder Listen

#### 3. **Markdown**
- **Wofür:** Texte mit Formatierung
- **Beispiel:** Blog-Artikel, Anleitungen
- **Besonderheit:** Sie können fett, kursiv, Listen, Überschriften verwenden
- **Wie es aussieht:**
  ```
  # Überschrift
  **Fetter Text**
  - Listenpunkt 1
  - Listenpunkt 2
  ```

#### 4. **Asset (Bilder/Dateien)**
- **Wofür:** Hochladen von Bildern, PDFs, Videos
- **Beispiel:** Produktfoto, Download-PDF
- **Besonderheit:** System verwaltet Dateien und Bildgrößen

#### 5. **Number (Zahlen)**
- **Wofür:** Numerische Werte
- **Beispiel:** Preis, Menge, Seitenzahl
- **Besonderheit:** Nur Zahlen erlaubt

#### 6. **Date (Datum)**
- **Wofür:** Datums- und Zeitangaben
- **Beispiel:** Veröffentlichungsdatum, Event-Termin
- **Besonderheit:** Kalender-Auswahl

#### 7. **Select (Auswahl)**
- **Wofür:** Auswahl aus vorgegebenen Optionen
- **Beispiel:** Kategorie (z.B. "News", "Tutorial", "Produkt")
- **Besonderheit:** Dropdown-Menü mit festen Werten

#### 8. **Boolean (Ja/Nein)**
- **Wofür:** Ein/Aus-Schalter
- **Beispiel:** "Kommentare erlauben", "Auf Startseite zeigen"
- **Besonderheit:** Nur zwei Zustände: an oder aus

### ElementTypes im Model-Builder

**Wenn Sie ein Model erstellen, wählen Sie die passenden ElementTypes:**

```
Model "Veranstaltung":
  ┌─────────────────────────────────────┐
  │ Feld: Titel                         │
  │ ElementType: Text                   │
  │ Pflichtfeld: Ja                     │
  └─────────────────────────────────────┘

  ┌─────────────────────────────────────┐
  │ Feld: Datum                         │
  │ ElementType: Date                   │
  │ Pflichtfeld: Ja                     │
  └─────────────────────────────────────┘

  ┌─────────────────────────────────────┐
  │ Feld: Beschreibung                  │
  │ ElementType: Markdown               │
  │ Pflichtfeld: Nein                   │
  └─────────────────────────────────────┘

  ┌─────────────────────────────────────┐
  │ Feld: Eventbild                     │
  │ ElementType: Asset                  │
  │ Pflichtfeld: Nein                   │
  └─────────────────────────────────────┘

  ┌─────────────────────────────────────┐
  │ Feld: Anmeldung erforderlich        │
  │ ElementType: Boolean                │
  │ Pflichtfeld: Nein                   │
  └─────────────────────────────────────┘
```

### Warum verschiedene ElementTypes?

1. **Benutzerfreundlichkeit:** Das richtige Eingabe-Element macht die Arbeit einfacher
2. **Validierung:** System prüft, ob der Inhalt passt (z.B. wirklich eine Zahl)
3. **Darstellung:** Frontend weiß, wie der Inhalt angezeigt werden soll
4. **Suchbarkeit:** Strukturierte Daten lassen sich besser durchsuchen

---

## Multi-Site - Mehrere Websites verwalten

### Was bedeutet Multi-Site?

Multi-Site bedeutet, dass Sie mit einer einzigen Catamaran-Installation **mehrere verschiedene Websites** verwalten können.

**Der Vergleich: Ein Unternehmen mit mehreren Filialen**

Stellen Sie sich ein Unternehmen mit drei Filialen vor:
- Filiale München
- Filiale Berlin
- Filiale Hamburg

Jede Filiale:
- Hat eigene Mitarbeiter
- Hat eigenes Sortiment
- Hat eigene Kunden
- Gehört aber zum gleichen Unternehmen
- Nutzt die gleiche Verwaltungssoftware

### Multi-Site im Catamaran CMS

```
┌─────────────────────────────────────────┐
│      EINE Catamaran Installation        │
├─────────────────────────────────────────┤
│                                         │
│  Site 1: www.meine-hauptseite.de       │
│  - Eigene Inhalte                      │
│  - Eigenes Design                      │
│  - Eigene Sprache (Deutsch)            │
│                                         │
│  Site 2: www.my-english-site.com       │
│  - Eigene Inhalte                      │
│  - Eigenes Design                      │
│  - Eigene Sprache (Englisch)           │
│                                         │
│  Site 3: www.mein-webshop.de           │
│  - Eigene Inhalte (Produkte)           │
│  - Shop-Design                         │
│  - Eigene Sprache (Deutsch)            │
│                                         │
└─────────────────────────────────────────┘
```

### Praktische Anwendungsfälle

#### Beispiel 1: Internationale Websites
```
Unternehmen "Global GmbH":
├── www.global.de (Deutsche Website)
├── www.global.com (Englische Website)
├── www.global.fr (Französische Website)
└── www.global.es (Spanische Website)
```
- Alle nutzen die gleiche Catamaran-Installation
- Jede hat eigene Inhalte in ihrer Sprache
- Manche Inhalte (z.B. Produktbilder) können geteilt werden

#### Beispiel 2: Marken-Portfolio
```
Holding-Gesellschaft:
├── www.marke-a.de (Lifestyle-Marke)
├── www.marke-b.de (Premium-Marke)
└── www.marke-c.de (Budget-Marke)
```
- Jede Marke hat eigenes Design und eigene Inhalte
- Zentrale Verwaltung durch ein Team
- Effiziente Ressourcennutzung

#### Beispiel 3: Hauptseite + Microsites
```
Hauptwebsite:
├── www.hauptseite.de (Unternehmenswebsite)
├── kampagne2024.hauptseite.de (Marketing-Kampagne)
└── blog.hauptseite.de (Unternehmensblog)
```

### Vorteile von Multi-Site

**1. Kosten sparen**
- Nur eine Installation nötig
- Ein Server statt mehrerer
- Ein Wartungsvertrag

**2. Effizienz steigern**
- Zentrale Verwaltung aller Websites
- Ein Login für alle Sites
- Gemeinsame Ressourcen (Bilder, Vorlagen)

**3. Konsistenz wahren**
- Gleiche Arbeitsprozesse
- Gleiche Qualitätsstandards
- Zentrale Updates

**4. Flexibilität gewinnen**
- Schnell neue Sites anlegen
- Inhalte zwischen Sites teilen (wenn gewünscht)
- Unterschiedliche Designs pro Site

### Wie funktioniert die Trennung?

**Jede Site ist komplett getrennt:**

```
Site "Hauptseite":
  - Blog-Artikel: 45 Stück
  - Produkte: 0 Stück
  - Bilder: 120 Dateien
  - Benutzer: Team A

Site "Webshop":
  - Blog-Artikel: 0 Stück
  - Produkte: 350 Stück
  - Bilder: 800 Dateien
  - Benutzer: Team B
```

**Die Blog-Artikel von "Hauptseite" erscheinen NICHT im "Webshop"** (es sei denn, Sie teilen sie bewusst).

### Multi-Site im Admin-Bereich

**Im Catamaran Backend:**
1. Wählen Sie oben die aktive Site aus (z.B. "Hauptseite")
2. Alle Inhalte, die Sie erstellen, gehören zu dieser Site
3. Um Inhalte für den Webshop zu erstellen, wechseln Sie zu Site "Webshop"
4. Systemeinstellungen gelten für alle Sites

---

## Zusammenfassung

### Die wichtigsten Konzepte auf einen Blick

#### **Headless CMS**
→ Inhalte zentral verwalten, überall anzeigen
→ Trennung von Inhalt und Design
→ Flexibel für verschiedene Ausgabekanäle

#### **Backend**
→ Ihre Arbeitsoberfläche (Admin-Bereich)
→ Hier verwalten Sie Inhalte
→ Nicht öffentlich sichtbar

#### **Frontend**
→ Die öffentliche Website
→ Zeigt Inhalte in schönem Design
→ Das sehen Ihre Besucher

#### **Data Hub**
→ Catamaran als zentrale Datenquelle
→ Ein Ort für alle Inhalte
→ Viele Ausgabekanäle möglich

#### **Models**
→ Vorlagen für Inhaltstypen
→ Definieren die Struktur (welche Felder)
→ Beispiele: Blog, Produkt, Event

#### **ElementTypes**
→ Bausteine für Model-Felder
→ Text, Markdown, Asset, Datum, etc.
→ Jeder Typ hat einen speziellen Zweck

#### **Multi-Site**
→ Mehrere Websites mit einer Installation
→ Jede Site ist getrennt
→ Zentrale Verwaltung, effizient

---

## Der Workflow: Vom Model zum fertigen Inhalt

### Schritt für Schritt

```
1. Model erstellen
   └─> "Ich brauche einen Inhaltstyp 'Rezept'"

2. Felder definieren (mit ElementTypes)
   ├─> Feld "Rezeptname" (ElementType: Text)
   ├─> Feld "Zubereitungszeit" (ElementType: Number)
   ├─> Feld "Zutaten" (ElementType: Textarea)
   ├─> Feld "Anleitung" (ElementType: Markdown)
   └─> Feld "Foto" (ElementType: Asset)

3. Inhalt erstellen
   └─> Redakteur füllt alle Felder aus

4. Im Backend speichern
   └─> Inhalt ist in der Datenbank (Data Hub)

5. Frontend greift per API zu
   └─> Website zeigt das Rezept an

6. Ergebnis für verschiedene Kanäle
   ├─> Auf der Website
   ├─> In der mobilen App
   └─> Im Newsletter
```

---

## Häufige Fragen (FAQ)

### Muss ich programmieren können?

**Nein, für die tägliche Arbeit nicht.**
- Models erstellen: Über Formulare im Backend, keine Programmierung
- Inhalte pflegen: Wie in einem normalen CMS
- **Aber:** Für das Frontend-Design brauchen Sie einen Entwickler

### Kann ich Catamaran ohne Frontend nutzen?

**Ja!** Catamaran funktioniert als reiner Data Hub.
- Sie pflegen Inhalte im Backend
- Andere Systeme können per API darauf zugreifen
- Frontend kann später ergänzt werden

### Wie unterscheidet sich Catamaran von WordPress?

| Feature | WordPress | Catamaran CMS |
|---------|-----------|---------------|
| Typ | Traditionelles CMS | Headless CMS |
| Frontend | Fest eingebaut | Frei wählbar |
| Design | Themes | Jede Technologie möglich |
| Flexibilität | Begrenzt | Sehr hoch |
| Lernkurve | Flach | Steiler (aber mächtiger) |

### Brauche ich technische Kenntnisse?

**Für verschiedene Rollen unterschiedlich:**

**Content-Redakteur:** ⭐ (sehr einfach)
- Formulare ausfüllen wie gewohnt
- Keine technischen Kenntnisse nötig

**Content-Administrator:** ⭐⭐ (einfach bis mittel)
- Models erstellen
- Felder definieren
- Grundverständnis für Datenstrukturen hilfreich

**System-Administrator:** ⭐⭐⭐⭐ (fortgeschritten)
- Server-Verwaltung
- PHP/Symfony-Kenntnisse
- Datenbank-Grundlagen

**Frontend-Entwickler:** ⭐⭐⭐⭐⭐ (expert)
- JavaScript-Framework (React, Vue, Svelte)
- API-Integration
- Webentwicklung

---

## Nächste Schritte

### Als Content-Redakteur
1. Lernen Sie die verfügbaren Models kennen
2. Erstellen Sie Ihren ersten Inhalt
3. Verstehen Sie, welche Felder Pflichtfelder sind

### Als Content-Administrator
1. Planen Sie, welche Inhaltstypen Sie brauchen
2. Erstellen Sie Ihr erstes Model
3. Testen Sie verschiedene ElementTypes

### Als Projektverantwortlicher
1. Überlegen Sie, welche Ausgabekanäle Sie bedienen wollen
2. Entscheiden Sie, ob Sie Multi-Site benötigen
3. Planen Sie die Zusammenarbeit mit Frontend-Entwicklern

---

## Weiterführende Ressourcen

- **Technische API-Dokumentation:** `API_DOCUMENTATION.md`
- **Entwickler-Guide:** Für Frontend-Integration
- **Admin-Oberfläche:** `/admin` - Login und direkt loslegen
- **Support:** Bei Fragen wenden Sie sich an Ihren Administrator

---

**Viel Erfolg mit Catamaran CMS!** 🚀

*Diese Dokumentation erklärt die Grundlagen. Für tiefergehende technische Details konsultieren Sie bitte die Entwickler-Dokumentation.*
