# Docker-Staging

Docker-Staging bedeutet: Ein Projekt bekommt eine lokale, wiederholbare
Testumgebung, die nah genug an Staging oder Live ist, um Updates vorab sicherer
zu prüfen.

## Ziele

- Gleiche Dienste lokal reproduzierbar starten.
- Datenbank, Mail und API isolieren.
- Keine Live-Secrets verwenden.
- Testdaten wiederherstellbar machen.
- Agenten klare Start-, Test- und Reset-Befehle geben.

## Empfohlene Reihenfolge

1. Projektprofil ausfüllen.
2. Live-/Staging-Stack notieren.
3. Minimal nötige Docker-Dienste festlegen.
4. `.env.staging.example` schreiben.
5. `.env.staging.local` lokal anlegen und ignorieren.
6. Datenbank-Seed oder anonymisierten Dump vorbereiten.
7. Smoke-Test definieren.
8. Erst danach komplexere Dienste wie Queue, Cron oder Adminer ergänzen.

## Gute lokale Dienste

- `mailpit` für E-Mails.
- `mariadb` oder `postgres` passend zum Projekt.
- `nginx` oder `caddy` als lokaler Proxy.
- `php-fpm`, `node` oder projektspezifische Runtime.
- `adminer` nur lokal, nie öffentlich.

## Schlechte Muster

- Live-Secrets in Compose-Dateien.
- Produktive Datenbank-Dumps ohne Anonymisierung.
- Container, die beim Start automatisch Live-Migrationen ausführen.
- Unklare Ports und magische lokale Domains.
- Keine Reset-Strategie.
