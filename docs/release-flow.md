# Sicherer Update-Flow

Ein sicherer Update-Flow trennt Entwicklung, Staging und Live.

## Ablauf

1. Lokale Änderung auf Branch oder Worktree.
2. Lokale Tests.
3. Lokales Docker-Staging.
4. Review des Diffs.
5. Staging-Backup.
6. Staging-Deploy.
7. Staging-Smoke.
8. Live-Freigabe.
9. Live-Backup.
10. Live-Deploy.
11. Live-Smoke.
12. Dokumentation und Version aktualisieren.

## Ampelbericht

Agenten sollen Updates am Ende so einordnen:

- Grün: Tests bestanden, keine Blocker, Live kann nach Freigabe folgen.
- Gelb: nutzbar, aber offene Risiken oder manuelle Prüfung nötig.
- Rot: nicht deployen, Blocker vorhanden.

## Besonders sensible Änderungen

- Auth und Session-Management.
- Datenbankmigrationen.
- Zahlungsfunktionen.
- Admin-Rechte.
- Uploads und Medien.
- personenbezogene Daten.
- E-Mail-Versand.
- Cronjobs und Hintergrundprozesse.
