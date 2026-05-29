# Warmes Tagebuch — Jekyll-Version für GitHub Pages

Dieser Ordner ist die statische Version deines Blogs, optimiert für **kostenloses Hosting auf GitHub Pages**.

Statt eines klassischen Admin-Backends schreibst du Beiträge als **Markdown-Dateien** im Ordner `_posts/`. Sobald du sie auf GitHub pushst (oder direkt im Browser im Repo bearbeitest), wird die Seite automatisch neu gebaut und ist live.

---

## Schritt 1 — Repo auf GitHub anlegen

1. Auf [github.com](https://github.com) einloggen → oben rechts auf **+ → New repository**.
2. **Wichtig**: wenn die Seite unter `dein-username.github.io` laufen soll, muss das Repo **genau so** heißen — z.B. `jonasweiler.github.io`. Sonst landet sie unter `dein-username.github.io/repo-name`.
3. Sichtbarkeit: **Public** (Privat geht nur mit GitHub Pro).
4. **"Create repository"** klicken.

## Schritt 2 — Dateien hochladen

**Variante A — direkt im Browser (einfach):**
1. Im leeren Repo auf **"uploading an existing file"** klicken.
2. Den **kompletten Inhalt** des `jekyll-site/`-Ordners reinziehen (nicht den Ordner selbst, sondern was drin ist — `_config.yml`, `index.html`, `_posts/`, usw.).
3. Unten **"Commit changes"**.

**Variante B — per Git (für später, wenn du Routine hast):**
```bash
cd jekyll-site
git init
git add .
git commit -m "Erste Version"
git branch -M main
git remote add origin https://github.com/DEIN-USERNAME/DEIN-REPO.git
git push -u origin main
```

## Schritt 3 — GitHub Pages aktivieren

1. Im Repo oben auf **Settings**.
2. Links auf **Pages**.
3. Unter "Source" auswählen: **Deploy from a branch**.
4. Branch: `main`, Folder: `/ (root)` → **Save**.
5. Nach ca. 1–2 Minuten ist die Seite unter `https://DEIN-USERNAME.github.io/` (oder `.../REPO-NAME/`) erreichbar.

> Wenn dein Repo nicht `dein-username.github.io` heißt: trage in `_config.yml` bei `baseurl:` den Repo-Namen ein, z.B. `baseurl: "/warmes-tagebuch"` — sonst sind CSS und Links kaputt.

---

## Inhalte bearbeiten

Alles, was du im Browser auf GitHub bearbeiten kannst — keine Software nötig:

### Einen neuen Beitrag schreiben

1. Im Repo in den Ordner `_posts/` gehen → **Add file → Create new file**.
2. Dateiname nach dem Schema: `YYYY-MM-DD-titel-mit-bindestrichen.md`
   Beispiel: `2026-06-12-sommernachmittag.md`
3. Oben in die Datei den sogenannten **Front Matter** schreiben (zwischen den `---`):

```markdown
---
layout: post
title: "Mein neuer Beitrag"
date: 2026-06-12 15:00:00 +0200
categories: [Persönliches]
reading_time: 4
excerpt: "Ein kurzer Teaser-Text, der auf der Startseite erscheint."
---

Hier kommt dein eigentlicher Text. **Fett** geht so, *kursiv* so.

## Eine Zwischenüberschrift

- Listen
- gehen
- auch

> Zitate sehen so aus.
```

4. Unten **"Commit new file"** → in 30 Sekunden ist der Beitrag live.

### Eine Seite ändern (z.B. "Über mich")

1. Im Repo auf `ueber-mich.md` (oder `impressum.md`, `datenschutz.md`) klicken.
2. Rechts oben aufs **Stift-Icon**.
3. Ändern → **Commit changes**.

### Titel, Beschreibung, Navigation

Alles steht in `_config.yml`. Bearbeiten, committen, fertig.

### Farben & Design

In `assets/css/style.css` ganz oben unter `:root` — z.B. `--color-accent` für den Akzent-Ton.

---

## Bilder einfügen

1. Im Repo Ordner `assets/images/` anlegen (oder vorhandenen nutzen).
2. Bild hochladen (per **Add file → Upload files**).
3. Im Beitrag einbinden:

```markdown
![Beschreibung](/assets/images/mein-foto.jpg)
```

Für ein **Titelbild oben über dem Beitrag** im Front Matter ergänzen:

```yaml
image: /assets/images/mein-foto.jpg
```

---

## Lokal testen (optional, für später)

Wenn du Änderungen sehen willst, bevor du sie pushst, brauchst du Ruby + Jekyll auf dem Mac:

```bash
brew install ruby
gem install bundler jekyll
cd jekyll-site
bundle install
bundle exec jekyll serve
```

Dann öffnet sich die Seite unter `http://localhost:4000`.

Aber: für den Anfang reicht es, einfach im GitHub-Browser zu editieren und die Seite live anzuschauen.

---

## Eigene Domain (optional)

Wenn du z.B. `jonas-weiler.de` statt `username.github.io` willst:

1. Domain bei einem Registrar kaufen (Namecheap, INWX, Hetzner — ca. 12 €/Jahr).
2. Im Repo `Settings → Pages → Custom domain` deine Domain eintragen.
3. Bei deinem Domain-Anbieter einen `CNAME`-Eintrag auf `dein-username.github.io` setzen.
4. **Enforce HTTPS** ankreuzen.

---

## Häufige Probleme

| Problem | Lösung |
|---------|--------|
| Seite zeigt nur Plain HTML ohne Styles | `baseurl` in `_config.yml` falsch — prüfen, ob er zum Repo-Namen passt |
| 404-Fehler | GitHub Pages braucht 1–2 Minuten nach jedem Commit. Außerdem prüfen ob unter Settings → Pages der richtige Branch ausgewählt ist |
| Beitrag erscheint nicht | Datumsformat im Dateinamen prüfen (`YYYY-MM-DD-`), und das Datum im Front Matter darf nicht in der Zukunft liegen |
| Sonderzeichen verschwinden | Datei muss UTF-8 sein — der GitHub-Editor macht das automatisch |

---

*Viel Freude beim Schreiben.* 🍂
