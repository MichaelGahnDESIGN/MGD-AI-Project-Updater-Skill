# Release-Checkliste

## Vor dem Update

- [ ] Git-Status verstanden.
- [ ] Keine unbekannten fremden Änderungen überschrieben.
- [ ] Lokale Tests gelaufen.
- [ ] Lokale Staging-/Docker-Umgebung geprüft.
- [ ] Datenbankmigrationen lokal getestet.
- [ ] Keine Secrets im Diff.
- [ ] Dokumentation aktualisiert.
- [ ] Backup-Plan vorhanden.
- [ ] Rollback-Plan vorhanden.

## Staging

- [ ] Staging-Backup erstellt.
- [ ] Staging-Deployment durchgeführt.
- [ ] Migrationen auf Staging erfolgreich.
- [ ] API-Health geprüft.
- [ ] App/Admin-Smoke geprüft.
- [ ] Logs auf harte Fehler geprüft.
- [ ] Testdaten bereinigt.

## Live

- [ ] Menschliche Freigabe liegt vor.
- [ ] Live-Backup erstellt und geprüft.
- [ ] Deployment durchgeführt.
- [ ] Migrationen erfolgreich.
- [ ] Cache/Build korrekt.
- [ ] API-Health geprüft.
- [ ] App/Admin/Login-Smoke geprüft.
- [ ] Rollback bleibt verfügbar.
- [ ] Version und Changelog dokumentiert.
