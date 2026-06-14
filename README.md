# AI Project Updater Skill

Ein wiederverwendbarer Skill und Arbeitsstandard für sichere lokale Staging-,
Test- und Update-Workflows über verschiedene Softwareprojekte hinweg.

Der Skill richtet sich an Menschen, die mit Claude Code, ChatGPT Codex, anderen
KI-Agenten oder menschlichen Entwicklerinnen und Entwicklern an echten Projekten
arbeiten. Er soll helfen, Projekte kontrolliert weiterzuentwickeln, ohne auf
Live-Systemen zu experimentieren.

Wichtig: Dieses Repository ist zuerst als privates Arbeitsrepository gedacht.
Es soll erst öffentlich werden, wenn Struktur, Beispiele, Sicherheitsregeln und
Workflows ausreichend geprüft sind.

## Warum es diesen Skill gibt

Viele Projekte wachsen mit der Zeit: Websites, Apps, Shops, APIs, interne Tools,
WordPress-Plugins, Flutter-Apps, Symfony-Backends oder kleine statische Seiten.
Wenn echte Menschen diese Projekte nutzen, wird jedes Update riskanter.

Das Ziel dieses Skills ist deshalb:

- lokal oder auf Staging entwickeln,
- Änderungen vor Live sauber testen,
- Docker-Umgebungen projektübergreifend standardisieren,
- KI-Agenten klare Regeln für sichere Updates geben,
- Backups, Migrationen, Tests und Freigaben nicht vergessen,
- Live-Systeme nur noch gezielt aktualisieren,
- Menschen auch ohne tiefes DevOps-Wissen Orientierung geben.

Der Skill ist kein magischer Autopilot. Er ist ein vorsichtiger Arbeitsrahmen.
Er soll Agenten und Menschen daran hindern, zu früh zu deployen, Secrets zu
veröffentlichen, Datenbanken ungesichert zu verändern oder Live-Nutzerdaten für
Tests zu missbrauchen.

## Für wen ist das gedacht?

Für:

- Einzelentwicklerinnen und Einzelentwickler mit mehreren Projekten,
- kleine Teams mit KI-Coworkern,
- Agenten-Workflows mit Claude Code, Codex oder ähnlichen Tools,
- Projekte mit lokaler Entwicklung und manuellem Live-Deployment,
- Projekte, bei denen Datenschutz, Backups und Nachvollziehbarkeit wichtig sind,
- Menschen, die Docker nutzen wollen, ohne jedes Projekt komplett neu zu
  erfinden.

Typische Projektarten:

- PHP/Symfony-Projekte,
- WordPress- oder Shopware-Projekte,
- Flutter-Web-Apps,
- Node-/TypeScript-Projekte,
- statische Websites,
- REST-APIs,
- Admin-Oberflächen,
- kleinere Tools mit Datenbank.

## Grundidee

Der Skill unterscheidet konsequent zwischen vier Ebenen:

| Ebene | Zweck | Regel |
| --- | --- | --- |
| Lokal | Entwicklung im Arbeitsordner | frei, aber versioniert und nachvollziehbar |
| Lokale Staging-Umgebung | Docker-nahe Prüfung mit Testdaten | keine echten Secrets, keine echten Kundendaten |
| Externe Staging-Umgebung | möglichst live-naher Test vor Veröffentlichung | Backup, Smoke-Test, klare Freigabe |
| Live | echtes Produktivsystem | keine Experimente, nur geprüfte Updates |

Live ist nicht der Ort zum Probieren. Live ist nur das Ziel eines geprüften
Stands.

## Was der Skill einem KI-Agenten beibringt

Ein Agent, der diesen Skill nutzt, soll:

1. zuerst Projektregeln und Dokumentation lesen,
2. lokale, Staging- und Live-Umgebungen unterscheiden,
3. vorhandene Docker-, Test- und Deployment-Dateien erkennen,
4. niemals echte Secrets ausgeben oder ins Repository schreiben,
5. keine produktiven Änderungen ohne ausdrückliche Freigabe durchführen,
6. lokale Staging-Umgebungen bevorzugen,
7. vor Migrationen und Deployments Backups verlangen,
8. Tests und Smoke-Checks dokumentieren,
9. am Ende knapp sagen, was geprüft wurde, was sicher ist und was offen bleibt.

## Was dieser Skill nicht ersetzt

Der Skill ersetzt nicht:

- Rechtsberatung,
- Datenschutzprüfung,
- Security-Audit,
- Restore-Test,
- menschliche Live-Freigabe,
- professionelle Betriebsüberwachung,
- projektspezifische Deployment-Dokumentation.

Er hilft aber, diese Punkte nicht zu übersehen.

## Installation in ChatGPT Codex oder Codex Desktop

Klone das Repository in einen Skill-Ordner und kopiere den eigentlichen Skill:

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

In einem Projekt kannst du zum Beispiel schreiben:

```text
/ai-project-updater
Prüfe dieses Projekt und entwirf eine lokale Docker-Staging-Umgebung.
Noch nichts umsetzen, nur analysieren und planen.
```

Oder:

```text
Nutze den AI Project Updater Skill.
Vergleiche lokalen Stand, GitHub, Staging und Live nur lesend.
Keine Deployments, keine Datenbankänderungen, keine Secrets ausgeben.
```

Oder:

```text
/ai-project-updater
Bereite einen sicheren Update-Ablauf vor:
lokal testen, Staging prüfen, Backup planen, Live-Deploy erst nach Freigabe.
```

## Typischer Ablauf

Der Skill führt Agenten durch diese Reihenfolge:

1. **Projektkontext laden**  
   Agenten lesen README, AGENTS.md, CLAUDE.md, Projektregeln, Deployment-Doku,
   vorhandene Docker-Dateien, Testbefehle und GitHub-Kontext.

2. **Umgebungen erkennen**  
   Agenten unterscheiden lokal, lokale Docker-Staging-Umgebung, externe
   Staging-Umgebung und Live.

3. **Risiken einordnen**  
   Auth, Zahlung, personenbezogene Daten, Uploads, Admin-Funktionen,
   Datenbankmigrationen und Cronjobs gelten als sensibel.

4. **Docker-Staging planen**  
   Agenten schlagen Services, Volumes, Netzwerke, lokale Domains, Testdaten,
   Mail-Testsysteme und Datenbankstrategie vor.

5. **Tests definieren**  
   Agenten suchen vorhandene Tests und ergänzen nur, was wirklich fehlt:
   Syntaxchecks, Unit-Tests, Build-Tests, Browser-Smokes, API-Smokes.

6. **Update vorbereiten**  
   Agenten erstellen einen nachvollziehbaren Plan mit Backup, Migrationen,
   Rollback und Freigabegrenzen.

7. **Live schützen**  
   Agenten führen keine Live-Schreibaktionen aus, solange keine ausdrückliche
   Freigabe, kein Backup und kein geprüfter Teststand vorhanden sind.

8. **Ergebnis berichten**  
   Agenten fassen kurz zusammen: geprüft, bestanden, offen, riskant, nächste
   sinnvolle Aktion.

## Docker-Staging-Prinzipien

Eine gute lokale Staging-Umgebung soll:

- mit `docker compose up -d` startbar sein,
- klar benannte Services haben,
- keine echten Live-Secrets enthalten,
- Testdaten statt echter Nutzerdaten nutzen,
- E-Mails in Mailpit oder einem ähnlichen lokalen Tool abfangen,
- Datenbankdaten in benannten Volumes halten,
- Reset- und Seed-Befehle dokumentieren,
- möglichst ähnliche PHP-/Node-/DB-Versionen wie Staging oder Live nutzen,
- Logs lokal halten und keine sensiblen Daten veröffentlichen,
- ohne Live-Verbindung funktionieren, wenn nicht ausdrücklich anders gewünscht.

Beispielhafte Services:

```text
proxy        lokaler Web-Einstieg oder Reverse Proxy
app          Frontend, Flutter-Web-Build oder statische App
admin        Admin-Oberfläche
api          Backend/API, zum Beispiel Symfony oder Node
db           MariaDB/PostgreSQL
mailpit      lokaler Mailfänger
queue        optionaler Worker
cron         optionaler Scheduler
adminer      optionaler DB-Browser nur lokal
```

## Datenschutz und Sicherheit

Der Skill folgt einer konservativen Sicherheitslogik:

- Keine `.env`-Dateien committen.
- Keine echten Passwörter, Tokens, API-Keys oder Sessiondaten dokumentieren.
- Keine echten Zahlungsdaten in lokalen Tests.
- Keine echten Nutzerdaten in Demo-Dumps.
- Produktive Dumps nur anonymisiert oder stark eingeschränkt lokal verwenden.
- Logs vor Weitergabe auf personenbezogene Daten prüfen.
- KI-Agenten dürfen Secrets erkennen, aber nicht ausgeben.
- Agenten sollen bei Unsicherheit stoppen und fragen.

## Projektprofil

Für jedes Projekt sollte ein kleines Projektprofil gepflegt werden. Eine Vorlage
liegt unter:

```text
templates/project-profile.md
```

Dieses Profil erklärt:

- Projektname,
- Stack,
- lokale Startbefehle,
- Testbefehle,
- Staging-URLs,
- Live-URLs,
- Deployment-Art,
- Backup-Regeln,
- sensible Bereiche,
- erlaubte und verbotene Agentenaktionen.

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
│   ├── project-profile.md
│   ├── docker-compose.staging.example.yml
│   └── release-checklist.md
└── examples/
    └── README.md
```

## Verhältnis zu anderen Skills

Dieser Skill ergänzt andere Skills:

- **DEV-Skill**: allgemeiner Projekt-Sync, Tests, Deploy-Vorbereitung,
  Dokumentation.
- **ProjectClean-Skill**: Abschluss, Version, Backup, Cleanup.
- **AI-PlayTest-Skill**: Nutzertests aus echten Rollen.
- **AI-Basic-Projektordner**: Grundstruktur für neue KI-gestützte Projekte.

Der AI Project Updater Skill fokussiert stärker auf lokale Staging-Umgebungen,
Docker-Organisation und sichere Update-Pipelines über mehrere Projekte hinweg.

## Gute erste Aufgaben für Agenten

```text
Nutze den AI Project Updater Skill.
Analysiere dieses Projekt nur lesend und erstelle ein Projektprofil.
Keine Dateien ändern.
```

```text
Nutze den AI Project Updater Skill.
Entwirf eine lokale Docker-Staging-Umgebung für dieses Projekt.
Noch keine Umsetzung, nur Architektur und Risiken.
```

```text
Nutze den AI Project Updater Skill.
Prüfe, ob dieses Projekt bereit für ein Staging-Update ist.
Keine Live-Aktionen.
```

```text
Nutze den AI Project Updater Skill.
Vergleiche lokal, GitHub, Staging und Live und schreibe einen Ampelbericht.
```

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
