# AI Project Updater Skill

Der **AI Project Updater Skill** ist ein geführter Assistent für sichere
Projekt-Updates.

Er ist für Menschen gedacht, die mehrere Softwareprojekte betreuen und dabei
mit KI-Agenten wie Claude Code, ChatGPT Codex, ChatGPT Cowork oder anderen
Coding-Assistenten arbeiten.

Die wichtigste Idee ist einfach:

> Wir probieren nicht auf Live-Systemen herum. Wir bauen, prüfen und verstehen
> Änderungen zuerst lokal oder auf Staging. Erst wenn alles nachvollziehbar
> funktioniert, wird Live aktualisiert.

Dieses Repository ist zuerst privat gedacht. Es soll erst öffentlich werden,
wenn der Assistent wirklich gut funktioniert, verständlich genug erklärt ist und
in echten Projekten getestet wurde.

## Ganz Einfach Erklärt

Stell dir ein Projekt wie ein echtes Geschäft vor.

- **Live** ist der Laden, in dem echte Kundinnen und Kunden gerade einkaufen.
- **Staging** ist der Proberaum hinter dem Laden.
- **Lokal** ist deine Werkbank zu Hause.
- **Docker** ist eine Kiste mit kleinen nachgebauten Maschinen, damit deine
  Werkbank dem echten Laden ähnlicher wird.

Der AI Project Updater Skill sorgt dafür, dass ein KI-Agent nicht einfach in den
echten Laden rennt und dort an der Kasse, am Regal oder am Stromkasten
herumprobiert. Stattdessen führt er dich ruhig durch die Vorbereitung:

1. Was ist das für ein Projekt?
2. Wo wird lokal gearbeitet?
3. Gibt es eine Staging-Umgebung?
4. Was ist live und wird von echten Menschen genutzt?
5. Was muss getestet werden?
6. Gibt es Backups?
7. Was darf der Agent tun und was nicht?
8. Ist ein Update wirklich bereit für Live?

## Was Der Assistent Macht

Der Skill ist nicht nur eine Liste mit Regeln. Er soll wie ein Assistent
arbeiten, der dich Schritt für Schritt begleitet.

Er fragt zum Beispiel:

```text
Welches Projekt möchtest du vorbereiten?
```

Dann:

```text
Soll ich erstmal nur lesen und ein Projektprofil erstellen,
oder soll ich später auch eine lokale Docker-Staging-Umgebung planen?
```

Und später:

```text
Gibt es echte Nutzerinnen oder Nutzer auf Live?
Wenn ja, behandle ich Live als besonders geschützten Bereich.
```

Der Assistent erklärt dabei, was passiert. Er soll nicht nur technische Befehle
ausgeben, sondern verständlich sagen, warum ein Schritt wichtig ist.

## Wofür Der Skill Gedacht Ist

Der Skill hilft bei:

- lokalen Staging-Umgebungen,
- Docker-Organisation über mehrere Projekte hinweg,
- Update-Vorbereitung,
- GitHub- und Branch-Übersicht,
- Staging- und Live-Vergleich,
- Backup- und Rollback-Planung,
- sicheren Deployments,
- Zusammenarbeit mit mehreren KI-Agenten,
- verständlicher Dokumentation für Nicht-Programmierer.

Typische Projekte:

- Websites,
- WordPress-Projekte,
- Shopware- oder Shopify-nahe Projekte,
- Symfony-/PHP-Backends,
- Flutter-Web-Apps,
- Node-/TypeScript-Projekte,
- REST-APIs,
- Admin-Oberflächen,
- interne Tools,
- kleine und große Kundenprojekte.

## Was Der Skill Nicht Macht

Der Skill ist bewusst vorsichtig.

Er macht nicht automatisch:

- Live-Deployments,
- Datenbankmigrationen auf echten Servern,
- Löschen von Dateien oder Backups,
- Pushes auf wichtige Branches,
- Änderungen an Zahlungsfunktionen,
- Veröffentlichung von Secrets,
- Tests mit echten Zahlungsdaten,
- Nutzung echter Kundendaten als Demo-Daten.

Wenn so etwas nötig sein könnte, soll der Assistent stoppen und dich klar fragen.

## Die Vier Bereiche

Der Assistent unterscheidet vier Bereiche.

| Bereich | Einfach gesagt | Risiko |
| --- | --- | --- |
| Lokal | Dein Arbeitsordner auf deinem Computer | niedrig |
| Lokales Staging | Nachgebaute Testumgebung, oft mit Docker | niedrig bis mittel |
| Externes Staging | Testserver im Internet oder beim Hoster | mittel |
| Live | Echtes System mit echten Menschen | hoch |

Diese Trennung ist wichtig. Ein Agent darf lokal viel mehr ausprobieren als auf
Live.

## Der Geführte Ablauf

Der Assistent führt durch neun Phasen.

### 1. Start

Der Assistent klärt, was du erreichen willst.

Beispiele:

- nur Projekt verstehen,
- lokale Docker-Staging-Umgebung planen,
- Update vorbereiten,
- Staging mit Live vergleichen,
- Live-Update vorbereiten,
- mehrere Projekte in einheitliche Abläufe bringen.

### 2. Projekt Lesen

Der Assistent liest vorhandene Projektdateien, zum Beispiel:

- `README.md`,
- `AGENTS.md`,
- `CLAUDE.md`,
- `DEPLOYMENT.md`,
- `SECURITY.md`,
- Docker-Dateien,
- Testkonfiguration,
- Dokumentation.

Er erklärt danach in einfacher Sprache, was er verstanden hat.

### 3. Sicherheitsstufe Festlegen

Der Assistent fragt, was erlaubt ist.

Beispiele:

- nur lesen,
- lokale Dateien ändern,
- Docker-Dateien vorbereiten,
- Tests ausführen,
- GitHub prüfen,
- Staging prüfen,
- Live nur ansehen,
- Live verändern nur nach ausdrücklicher Freigabe.

### 4. Projektprofil Erstellen

Der Assistent sammelt die wichtigsten Informationen:

- Projektname,
- Technik,
- Datenbank,
- lokale Startbefehle,
- Testbefehle,
- Staging-URLs,
- Live-URLs,
- sensible Bereiche,
- Backup-Regeln,
- was KI-Agenten dürfen.

Eine Vorlage liegt unter:

```text
templates/project-profile.md
```

### 5. Lokale Staging-Umgebung Planen

Wenn Docker sinnvoll ist, erklärt der Assistent die Umgebung einfach:

```text
Wir bauen eine kleine lokale Server-Werkstatt.
Die Datenbank läuft in einem Container.
E-Mails gehen nicht an echte Menschen, sondern in Mailpit.
Die App und API können lokal getestet werden.
```

Er schlägt nur Dienste vor, die das Projekt wirklich braucht.

Typische Dienste:

```text
proxy        lokaler Web-Einstieg
app          App oder Frontend
admin        Admin-Oberfläche
api          Backend/API
db           Datenbank
mailpit      lokaler Mailfänger
queue        Hintergrundjobs, falls nötig
cron         geplante Aufgaben, falls nötig
adminer      lokaler Datenbank-Browser, falls sinnvoll
```

### 6. Tests Erklären Und Ausführen

Der Assistent erklärt Tests nicht als Zauberei, sondern als Sicherheitsprüfung.

Beispiele:

- Lädt die Startseite?
- Antwortet die API?
- Funktioniert der Login grundsätzlich?
- Werden E-Mails nur lokal abgefangen?
- Läuft die Datenbankmigration?
- Gibt es JavaScript-Fehler?
- Stimmen Versionen zusammen?

### 7. Staging Prüfen

Wenn es eine externe Staging-Umgebung gibt, wird dort zuerst geprüft.

Der Assistent soll sagen:

- was erreichbar ist,
- welche Version läuft,
- ob geschützte Bereiche wirklich geschützt sind,
- ob Staging nicht versehentlich indexiert wird,
- ob Tests bestanden haben.

### 8. Live Vorbereiten

Live wird nicht nebenbei aktualisiert.

Vor Live braucht es:

- grünen lokalen Test,
- grünen Staging-Test,
- Backup,
- Rollback-Idee,
- klare Freigabe,
- kurze Liste der Änderungen,
- Plan für den Live-Smoke danach.

### 9. Abschlussbericht

Am Ende gibt der Assistent einen Ampelbericht.

```text
Grün:
- lokale Tests bestanden
- Staging erreichbar
- keine Secret-Funde

Gelb:
- Docker fehlt noch
- Backup-Restore wurde nicht getestet

Rot:
- Live-Update nicht freigeben, solange Migration unklar ist
```

## Beispiel-Dialog

So kann eine Sitzung aussehen:

```text
Mensch:
Nutze den AI Project Updater Skill.
Führe mich durch DungeonJournal. Erstmal nur lesen und erklären.

Assistent:
Alles klar. Ich prüfe zuerst nur lesend.
Ich ändere keine Dateien, starte kein Deployment und gebe keine Secrets aus.
Zuerst lese ich README, Projektregeln, Deployment-Doku und Git-Status.

Assistent:
Ich habe verstanden:
- Das Projekt hat eine Plattform, App, Admin und API.
- Live wird von echten Menschen genutzt.
- Staging existiert separat.
- Docker ist lokal noch nicht eingerichtet.

Meine erste Frage:
Soll ich jetzt ein Projektprofil erstellen oder zuerst erklären,
welche lokale Docker-Staging-Umgebung sinnvoll wäre?
```

## Installation in ChatGPT Codex Oder Codex Desktop

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/MichaelGahnDESIGN/AI-Project-Updater-Skill.git ~/.codex/skills/AI-Project-Updater-Skill
cp -R ~/.codex/skills/AI-Project-Updater-Skill/ai-project-updater ~/.codex/skills/ai-project-updater
```

Optional, wenn deine Umgebung einen gemeinsamen Agenten-Skill-Ordner nutzt:

```bash
mkdir -p ~/.agents/skills
cp -R ~/.codex/skills/AI-Project-Updater-Skill/ai-project-updater ~/.agents/skills/ai-project-updater
```

Update:

```bash
cd ~/.codex/skills/AI-Project-Updater-Skill
git pull
rm -rf ~/.codex/skills/ai-project-updater
cp -R ai-project-updater ~/.codex/skills/ai-project-updater
```

## Installation in Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/MichaelGahnDESIGN/AI-Project-Updater-Skill.git ~/.claude/skills/AI-Project-Updater-Skill
cp -R ~/.claude/skills/AI-Project-Updater-Skill/ai-project-updater ~/.claude/skills/ai-project-updater
```

Update:

```bash
cd ~/.claude/skills/AI-Project-Updater-Skill
git pull
rm -rf ~/.claude/skills/ai-project-updater
cp -R ai-project-updater ~/.claude/skills/ai-project-updater
```

## Nutzung

Zum Start:

```text
/ai-project-updater
Führe mich Schritt für Schritt durch dieses Projekt.
Erkläre alles einfach. Erstmal nur lesen.
```

Für eine Docker-Staging-Planung:

```text
Nutze den AI Project Updater Skill.
Entwirf mit mir eine lokale Docker-Staging-Umgebung.
Frag mich Schritt für Schritt und setze noch nichts um.
```

Für einen Update-Check:

```text
Nutze den AI Project Updater Skill.
Prüfe, ob dieses Projekt bereit für ein Staging-Update ist.
Keine Live-Aktionen.
```

Für einen Live-Vorbereitungscheck:

```text
Nutze den AI Project Updater Skill.
Bereite ein Live-Update vor, aber führe es nicht aus.
Erkläre mir, welche Prüfungen und Backups vorher nötig sind.
```

## Was Der Assistent Dokumentieren Kann

Für längere Sitzungen kann der Agent ein Sitzungsprotokoll führen.

Vorlage:

```text
templates/assistant-session.md
```

Darin stehen:

- Ziel der Sitzung,
- erlaubte Aktionen,
- gelesene Dateien,
- getroffene Annahmen,
- offene Fragen,
- nächste sichere Schritte.

## Datenschutz Und Sicherheit

Der Assistent soll immer nach diesen Regeln arbeiten:

- keine echten `.env`-Dateien in Git,
- keine Passwörter in Markdown,
- keine Tokens in Logs,
- keine echten Kundendaten als Testdaten,
- keine Zahlungsdaten außerhalb einer Sandbox,
- keine Live-Datenbankänderung ohne Backup,
- keine Screenshots mit sensiblen Daten veröffentlichen,
- keine Agentenentscheidung als menschliche Freigabe ausgeben.

Wenn der Assistent unsicher ist, soll er nicht raten. Er soll fragen.

## Repository-Struktur

```text
AI-Project-Updater-Skill/
├── README.md
├── LICENSE
├── .gitignore
├── .claude/
│   └── commands/
│       └── ai-project-updater.md
├── .codex/
│   └── commands/
│       └── ai-project-updater.md
├── ai-project-updater/
│   ├── SKILL.md
│   └── agents/
│       └── openai.yaml
├── docs/
│   ├── docker-staging.md
│   └── release-flow.md
├── templates/
│   ├── assistant-session.md
│   ├── project-profile.md
│   ├── docker-compose.staging.example.yml
│   └── release-checklist.md
└── examples/
    └── README.md
```

## Verhältnis Zu Anderen Skills

Der Skill ergänzt:

- **DEV-Skill** für Projekt-Sync, Tests und Deploy-Vorbereitung,
- **ProjectClean-Skill** für Abschluss, Version, Backup und Cleanup,
- **AI-PlayTest-Skill** für Nutzertests,
- **AI-Basic-Projektordner** als Projektgrundlage.

Der AI Project Updater Skill ist der geführte Assistent davor und dazwischen:
Er hilft zu verstehen, zu ordnen, sicher zu planen und erst danach umzusetzen.

## Lizenz

MIT Lizenz. Siehe [LICENSE](LICENSE).

## Impressum

Angaben gemäß § 5 DDG (Digitale-Dienste-Gesetz)

Michael Gahn DESIGN<br>
Michael Gahn<br>
Dr.-Theodor-Brugsch Str. 12<br>
08529 Plauen<br>
Sachsen<br>
Deutschland

Tel.: +49 (0) 176 557 647 48<br>
E-Mail: Anfrage@Michael-Gahn.de

Umsatzsteuer-Identifikationsnummer gemäß § 27a Umsatzsteuergesetz:<br>
Steuernummer: 223/222/02451<br>
USt-ID: DE288143343
