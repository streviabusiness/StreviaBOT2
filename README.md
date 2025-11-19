Discord Message Cooldown Bot
Ein Discord Bot, der message-basierte Cooldowns für bestimmte Rollen in bestimmten Channels verwaltet.

Features
✅ /set-window Slash Command zur Konfiguration
✅ Automatische Nachrichtenüberwachung
✅ Per-Message Cooldown-System
✅ Automatisches Löschen von Nachrichten während der Cooldown-Phase
✅ Benutzerfreundliche Zeitanzeige auf Deutsch
✅ JSON-basierte Speicherung
Setup
1. Discord Bot erstellen
Gehe zu Discord Developer Portal
Klicke auf "New Application"
Gib deinem Bot einen Namen
Gehe zu "Bot" im linken Menü
Klicke auf "Add Bot"
Aktiviere folgende Privileged Gateway Intents:
✅ Message Content Intent
✅ Server Members Intent
Kopiere den Bot Token (unter "TOKEN" → "Reset Token" oder "Copy")
2. Bot Token in Replit hinzufügen
Klicke auf "Secrets" (Schloss-Symbol) in der linken Leiste
Füge ein neues Secret hinzu:
Key: DISCORD_BOT_TOKEN
Value: [Dein Bot Token]
3. Bot zu deinem Server einladen
Erstelle eine Einladungs-URL mit folgenden Berechtigungen:

applications.commands (Slash Commands)
bot (Bot User)
Berechtigungen:
✅ Manage Messages (Nachrichten verwalten)
✅ Send Messages (Nachrichten senden)
✅ Read Message History (Nachrichtenverlauf lesen)
Einladungs-URL Format:

https://discord.com/api/oauth2/authorize?client_id=DEINE_CLIENT_ID&permissions=76800&scope=bot%20applications.commands

Ersetze DEINE_CLIENT_ID mit der Application ID aus dem Developer Portal.

4. Bot starten
Klicke auf "Run" in Replit. Der Bot sollte online gehen und "ist online und bereit!" ausgeben.

Verwendung
Cooldown-Fenster erstellen
Verwende den /set-window Slash Command:

/set-window role:@Member channel:#ideen interval:3d

Parameter:

role: Die Rolle, für die das Cooldown gelten soll (z.B. @Member)
channel: Der Channel, in dem das Cooldown aktiv ist (z.B. #ideen)
interval: Das Cooldown-Intervall
3d = 3 Tage
7d = 7 Tage
12h = 12 Stunden
30m = 30 Minuten
Wie es funktioniert
User sendet eine Nachricht im konfigurierten Channel
Bot prüft:
Hat der User die konfigurierte Rolle?
Ist der User noch im Cooldown?
Wenn Cooldown aktiv:
❌ Nachricht wird gelöscht
⏳ Warnung wird angezeigt: "Du kannst erst in X Zeit wieder schreiben!"
Warnung verschwindet nach 5 Sekunden
Wenn kein Cooldown:
✅ Nachricht wird akzeptiert
⏱️ Cooldown startet für diesen User
Beispiel-Szenario
/set-window role:@Member channel:#ideen interval:3d

Ergebnis:

User mit Rolle @Member können im Channel #ideen nur alle 3 Tage eine Nachricht senden
Nach dem Senden einer Nachricht beginnt der 3-Tage-Countdown
Versuche während des Cooldowns zu schreiben werden automatisch gelöscht
Dateien
main.py - Haupt-Bot-Code
config.json - Speichert Cooldown-Konfigurationen
cooldowns.json - Speichert aktive User-Cooldowns
README.md - Diese Datei
Technische Details
Sprache: Python 3.11
Library: discord.py
Speicherung: JSON
Cooldown-Tracking: Pro User, pro Channel
