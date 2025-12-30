# Catamaran CMS - Quickstart Guide

Willkommen! Diese Anleitung führt Sie in 15 Minuten durch die ersten Schritte mit Catamaran CMS.

## Inhaltsverzeichnis

- [Für Redakteure: Ersten Inhalt erstellen](#für-redakteure-ersten-inhalt-erstellen)
- [Für Administratoren: Erstes Model erstellen](#für-administratoren-erstes-model-erstellen)
- [Für Entwickler: API nutzen](#für-entwickler-api-nutzen)
- [Checkliste: System ist startklar](#checkliste-system-ist-startklar)

---

## Für Redakteure: Ersten Inhalt erstellen

**Ziel:** Einen Blog-Artikel erstellen und veröffentlichen

**Dauer:** 5 Minuten

### Schritt 1: Einloggen

1. Öffnen Sie die Admin-URL in Ihrem Browser:
   ```
   http://localhost:8000/admin
   ```
   oder für Produktionsumgebung:
   ```
   https://ihre-domain.de/admin
   ```

2. Geben Sie Ihre Zugangsdaten ein

### Schritt 2: Zur Content-Verwaltung navigieren

1. Klicken Sie im linken Menü auf **"Content"**
2. Sie sehen eine Liste aller vorhandenen Inhalte

### Schritt 3: Neuen Inhalt erstellen

1. Klicken Sie rechts oben auf **"Neuer Inhalt erstellen"** (oder "+ Create Content")

2. **Wählen Sie das Model:**
   - Im Dropdown "Model" wählen Sie **"Blog"**
   - Das Formular zeigt jetzt alle Blog-Felder an

### Schritt 4: Felder ausfüllen

**Pflichtfelder (mit * markiert):**

```
Titel:          Mein erster Blog-Artikel
URL-Slug:       mein-erster-blog-artikel
Inhalt:         ## Willkommen

                Dies ist mein erster Artikel im Catamaran CMS!

                ### Was ich gelernt habe
                - Catamaran ist ein Headless CMS
                - Inhalte werden zentral verwaltet
                - Models definieren die Struktur
```

**Optionale Felder:**

```
Teaser:         Eine kurze Einführung in mein erstes CMS-Projekt
Autor:          Ihr Name
Datum:          [Heutiges Datum auswählen]
Tags:           Tutorial, Erste Schritte, CMS
```

### Schritt 5: Titelbild hinzufügen (optional)

1. Klicken Sie auf das Feld **"Featured Image"**
2. Wählen Sie ein vorhandenes Bild ODER
3. Klicken Sie auf "Upload" um ein neues Bild hochzuladen
4. Bild auswählen und bestätigen

### Schritt 6: Speichern und veröffentlichen

1. **Status:** Setzen Sie auf **"Published"** (veröffentlicht)
2. Klicken Sie unten auf **"Speichern"**
3. ✅ Erfolg! Ihr Artikel ist jetzt im System

### Schritt 7: Inhalt ansehen

**Option A: Im Backend prüfen**
- Gehen Sie zurück zur Content-Liste
- Ihr Artikel erscheint in der Übersicht

**Option B: Per API abrufen**
- Öffnen Sie: `http://localhost:8000/api/v1/content`
- Suchen Sie Ihren Artikel in der JSON-Antwort

**Option C: Im Frontend** (wenn eingerichtet)
- Besuchen Sie Ihre Website
- Artikel sollte in der Blog-Liste erscheinen

---

## Für Administratoren: Erstes Model erstellen

**Ziel:** Ein "Veranstaltung"-Model mit allen nötigen Feldern erstellen

**Dauer:** 10 Minuten

### Schritt 1: Zum Model-Builder navigieren

1. Im Admin-Bereich: Klicken Sie auf **"Models"** im Menü
2. Klicken Sie auf **"Neues Model erstellen"**

### Schritt 2: Model-Grunddaten

```
Name:           Veranstaltung
Beschreibung:   Verwaltung von Events und Terminen
Slug:           veranstaltung
```

**Hinweis:** Der Slug wird für die API verwendet (`/api/v1/models/veranstaltung`)

### Schritt 3: Felder hinzufügen

Klicken Sie auf **"Feld hinzufügen"** und erstellen Sie folgende Felder:

#### Feld 1: Event-Titel
```
Feldname:       title
Label:          Event-Titel
ElementType:    Text
Pflichtfeld:    ✓ Ja
Validierung:    Min: 3, Max: 200 Zeichen
```

#### Feld 2: URL-Slug
```
Feldname:       slug
Label:          URL-Slug
ElementType:    Text
Pflichtfeld:    ✓ Ja
Validierung:    Regex: ^[a-z0-9-]+$
Hilfetext:      Nur Kleinbuchstaben, Zahlen und Bindestriche
```

#### Feld 3: Event-Datum
```
Feldname:       event_date
Label:          Veranstaltungsdatum
ElementType:    Date
Pflichtfeld:    ✓ Ja
```

#### Feld 4: Veranstaltungsort
```
Feldname:       location
Label:          Veranstaltungsort
ElementType:    Text
Pflichtfeld:    ✓ Ja
Validierung:    Max: 255 Zeichen
```

#### Feld 5: Beschreibung
```
Feldname:       description
Label:          Beschreibung
ElementType:    Markdown
Pflichtfeld:    ✗ Nein
Hilfetext:      Detaillierte Event-Beschreibung mit Formatierung
```

#### Feld 6: Event-Bild
```
Feldname:       featured_image
Label:          Event-Bild
ElementType:    Asset
Pflichtfeld:    ✗ Nein
```

#### Feld 7: Anmeldung erforderlich
```
Feldname:       registration_required
Label:          Anmeldung erforderlich
ElementType:    Boolean
Pflichtfeld:    ✗ Nein
Standardwert:   false
```

#### Feld 8: Max. Teilnehmer
```
Feldname:       max_participants
Label:          Maximale Teilnehmerzahl
ElementType:    Number
Pflichtfeld:    ✗ Nein
Validierung:    Min: 1, Max: 1000
```

#### Feld 9: Kategorien
```
Feldname:       category
Label:          Kategorie
ElementType:    Select
Pflichtfeld:    ✓ Ja
Optionen:       - Konzert
                - Workshop
                - Konferenz
                - Networking
                - Sonstiges
```

### Schritt 4: Model speichern

1. Klicken Sie auf **"Speichern"**
2. ✅ Ihr Model "Veranstaltung" ist jetzt aktiv!

### Schritt 5: Erstes Event anlegen (Test)

1. Gehen Sie zu **"Content"** → **"Neuer Inhalt erstellen"**
2. Wählen Sie Model **"Veranstaltung"**
3. Füllen Sie alle Felder aus:

```
Event-Titel:            Catamaran CMS Workshop
URL-Slug:               catamaran-workshop-2025
Veranstaltungsdatum:    31.01.2025
Veranstaltungsort:      Online (Zoom)
Beschreibung:           ## Workshop-Inhalte
                        - Headless CMS Grundlagen
                        - Models erstellen
                        - API nutzen
Anmeldung erforderlich: Ja
Max. Teilnehmer:        50
Kategorie:              Workshop
```

4. Speichern und Status auf **"Published"** setzen

### Schritt 6: Model per API abrufen

**Testen Sie die API:**

```bash
# Model-Details abrufen
curl http://localhost:8000/api/v1/models/veranstaltung

# Alle Events abrufen
curl http://localhost:8000/api/v1/models/veranstaltung/content
```

✅ **Fertig!** Ihr erstes eigenes Model ist einsatzbereit.

---

## Für Entwickler: API nutzen

**Ziel:** Inhalte per API abrufen und im Frontend anzeigen

**Dauer:** 5 Minuten

### Schritt 1: API-Basis-URL prüfen

**Entwicklungsumgebung:**
```
http://localhost:8000/api/v1
```

**Produktionsumgebung:**
```
https://ihre-domain.de/api/v1
```

### Schritt 2: Alle Models abrufen

**Request:**
```bash
curl -X GET http://localhost:8000/api/v1/models
```

**Response:**
```json
{
  "data": [
    {
      "id": 4,
      "name": "Blog",
      "slug": "blog",
      "description": "Blog-Artikel mit Markdown-Editor",
      "fields": [...],
      "views": [...]
    }
  ]
}
```

### Schritt 3: Inhalte eines Models abrufen

**Request:**
```bash
curl -X GET http://localhost:8000/api/v1/models/blog/content
```

**Response:**
```json
{
  "data": [
    {
      "id": 12,
      "title": "Mein erster Blog-Artikel",
      "slug": "mein-erster-blog-artikel",
      "status": "published",
      "created_at": "2025-12-30T10:30:00+00:00",
      "updated_at": "2025-12-30T10:30:00+00:00",
      "data": {
        "title": "Mein erster Blog-Artikel",
        "slug": "mein-erster-blog-artikel",
        "featured_image": 5,
        "excerpt": "Eine kurze Einführung...",
        "content": "## Willkommen\n\nDies ist mein erster...",
        "author": "Max Mustermann",
        "published_date": "2025-12-30",
        "tags": "Tutorial, Erste Schritte, CMS"
      }
    }
  ]
}
```

### Schritt 4: Einzelnen Inhalt abrufen

**Request:**
```bash
curl -X GET http://localhost:8000/api/v1/content/12
```

### Schritt 5: Frontend-Integration (Beispiel: JavaScript)

**Einfaches Beispiel mit fetch:**

```javascript
// Alle Blog-Artikel abrufen
async function fetchBlogPosts() {
  const response = await fetch('http://localhost:8000/api/v1/models/blog/content');
  const json = await response.json();
  return json.data;
}

// Artikel anzeigen
fetchBlogPosts().then(posts => {
  posts.forEach(post => {
    console.log(`${post.data.title} - ${post.data.published_date}`);
  });
});
```

**Svelte-Beispiel:**

```svelte
<script>
  import { onMount } from 'svelte';

  let posts = [];
  let loading = true;

  onMount(async () => {
    const response = await fetch('http://localhost:8000/api/v1/models/blog/content');
    const json = await response.json();
    posts = json.data;
    loading = false;
  });
</script>

{#if loading}
  <p>Lade Blog-Artikel...</p>
{:else}
  <ul>
    {#each posts as post}
      <li>
        <h2>{post.data.title}</h2>
        <p>{post.data.excerpt}</p>
        <small>{post.data.published_date}</small>
      </li>
    {/each}
  </ul>
{/if}
```

### Schritt 6: Neuen Inhalt per API erstellen

**Request:**
```bash
curl -X POST http://localhost:8000/api/v1/content \
  -H "Content-Type: application/json" \
  -d '{
    "model_id": 4,
    "slug": "api-test-artikel",
    "status": "published",
    "data": {
      "title": "Per API erstellt",
      "slug": "api-test-artikel",
      "excerpt": "Dieser Artikel wurde per API erstellt",
      "content": "## Test\n\nInhalt hier...",
      "author": "API Bot",
      "published_date": "2025-12-30",
      "tags": "API, Test"
    }
  }'
```

**Response:**
```json
{
  "data": {
    "id": 13,
    "title": "Per API erstellt",
    "slug": "api-test-artikel",
    "status": "published",
    "created_at": "2025-12-30T11:00:00+00:00",
    "data": {...}
  }
}
```

### Schritt 7: Inhalt aktualisieren

**Request:**
```bash
curl -X PUT http://localhost:8000/api/v1/content/13 \
  -H "Content-Type: application/json" \
  -d '{
    "data": {
      "title": "Aktualisierter Titel"
    }
  }'
```

### Schritt 8: Inhalt löschen (Soft Delete)

**Request:**
```bash
curl -X DELETE http://localhost:8000/api/v1/content/13
```

**Hinweis:** Content wird auf Status "archived" gesetzt, nicht physisch gelöscht.

---

## Checkliste: System ist startklar

### Backend-Installation

- [ ] Symfony läuft erfolgreich
- [ ] Datenbank ist verbunden
- [ ] EasyAdmin ist erreichbar unter `/admin`
- [ ] Mindestens ein Benutzer-Account existiert
- [ ] API ist erreichbar unter `/api/v1`

**Test:**
```bash
curl http://localhost:8000/api/v1/models
# Sollte JSON mit Models zurückgeben
```

### Erste Konfiguration

- [ ] Mindestens eine Site ist angelegt
- [ ] Mindestens ein Model existiert (z.B. "Blog")
- [ ] ElementTypes sind synchronisiert
- [ ] CORS ist konfiguriert (für Frontend-Entwicklung)

**Test:**
```bash
php bin/console app:sync-element-types
# Sollte ElementTypes synchronisieren
```

### Content-Management

- [ ] Mindestens ein Test-Inhalt wurde erstellt
- [ ] Content kann per API abgerufen werden
- [ ] Bilder/Assets können hochgeladen werden
- [ ] Markdown-Editor funktioniert

### API-Zugriff

- [ ] GET /api/v1/models funktioniert
- [ ] GET /api/v1/models/{slug}/content funktioniert
- [ ] POST /api/v1/content funktioniert
- [ ] PUT /api/v1/content/{id} funktioniert
- [ ] DELETE /api/v1/content/{id} funktioniert

### Frontend (optional)

- [ ] Frontend-Projekt ist erstellt
- [ ] API-URL ist konfiguriert (`.env` Datei)
- [ ] Erste API-Calls funktionieren
- [ ] Inhalte werden angezeigt

---

## Häufige Probleme und Lösungen

### Problem: "API gibt 404 zurück"

**Lösung:**
```bash
# Cache leeren
php bin/console cache:clear

# Routen prüfen
php bin/console debug:router | grep api
```

### Problem: "CORS-Fehler im Browser"

**Lösung:**
Prüfen Sie `config/packages/nelmio_cors.yaml`:
```yaml
nelmio_cors:
    defaults:
        origin_regex: true
        allow_origin: ['http://localhost:5173']
        allow_methods: ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS']
        allow_headers: ['Content-Type']
```

### Problem: "Validation failed - Slug is required"

**Lösung:**
Bei Blog-Posts brauchen Sie zwei Slugs:
```json
{
  "model_id": 4,
  "slug": "artikel-slug",        // Content-Entity Slug
  "data": {
    "slug": "artikel-slug",      // Auch im data-Objekt!
    "title": "..."
  }
}
```

### Problem: "Model fields not visible in admin"

**Lösung:**
```bash
# Schema aktualisieren
php bin/console doctrine:schema:update --force

# ElementTypes synchronisieren
php bin/console app:sync-element-types
```

### Problem: "Cannot find package '@sveltejs/adapter-static'"

**Lösung:**
```bash
cd catamaran-frontend
npm install -D @sveltejs/adapter-static
```

---

## Nächste Schritte

### Als Redakteur
1. ✅ Ersten Artikel erstellt
2. ➡️ Weitere Artikel anlegen und Workflow kennenlernen
3. ➡️ Bilder und Assets verwalten
4. ➡️ Markdown-Formatierung üben

### Als Administrator
1. ✅ Erstes Model erstellt
2. ➡️ Views für Models erstellen (Template-Rendering)
3. ➡️ Weitere Models anlegen (Produkte, Events, etc.)
4. ➡️ Multi-Site konfigurieren (falls nötig)
5. ➡️ Benutzer und Rollen verwalten

### Als Entwickler
1. ✅ API-Zugriff getestet
2. ➡️ Frontend-Projekt aufsetzen (SvelteKit, React, Vue)
3. ➡️ API-Client-Library erstellen
4. ➡️ Komponenten für Content-Darstellung bauen
5. ➡️ CRUD-Funktionen im Frontend implementieren
6. ➡️ Deployment vorbereiten

---

## Wichtige Befehle (Cheat Sheet)

### Symfony-Befehle

```bash
# Cache leeren
php bin/console cache:clear

# Datenbank-Schema aktualisieren
php bin/console doctrine:schema:update --force

# ElementTypes synchronisieren
php bin/console app:sync-element-types

# Routen anzeigen
php bin/console debug:router

# Entwicklungsserver starten
symfony server:start
```

### API-Befehle (cURL)

```bash
# Alle Models
curl http://localhost:8000/api/v1/models

# Model mit Content
curl http://localhost:8000/api/v1/models/blog/content

# Einzelner Content
curl http://localhost:8000/api/v1/content/12

# Content erstellen
curl -X POST http://localhost:8000/api/v1/content \
  -H "Content-Type: application/json" \
  -d @test_create.json

# Content aktualisieren
curl -X PUT http://localhost:8000/api/v1/content/12 \
  -H "Content-Type: application/json" \
  -d '{"data":{"title":"Neuer Titel"}}'

# Content löschen
curl -X DELETE http://localhost:8000/api/v1/content/12
```

### Frontend-Befehle (SvelteKit)

```bash
# Abhängigkeiten installieren
npm install

# Entwicklungsserver
npm run dev

# Production Build
npm run build

# Preview Production Build
npm run preview
```

---

## Support und Hilfe

### Dokumentation
- **Grundlagen:** `GRUNDLAGEN_CATAMARAN_CMS.md`
- **API-Dokumentation:** `API_DOCUMENTATION.md`
- **Dieser Guide:** `QUICKSTART.md`

### API-Testing
- **Postman Collection:** `Catamaran_CMS_API.postman_collection.json`
- **Environments:** `Catamaran_CMS_DEV.postman_environment.json`

### Bei Problemen
1. Cache leeren: `php bin/console cache:clear`
2. Logs prüfen: `var/log/dev.log` oder `var/log/prod.log`
3. Browser-Konsole prüfen (bei Frontend-Problemen)
4. API mit Postman testen (Isolierung des Problems)

---

**Viel Erfolg mit Catamaran CMS!** 🚀

*Letzte Aktualisierung: 2025-12-30*
