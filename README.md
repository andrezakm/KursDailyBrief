# Daily Brief — ein eigenes System bauen

*Modul des Kurses AI-Augmented Product Management*

In diesem Modul baust du einen eigenen Skill: `/dailybrief`, der aus E-Mails, Slack-Nachrichten, Kalendereinträgen und Meeting-Notizen einen persönlichen Daily Brief macht — eine kurze Übersicht, was heute wirklich wichtig ist. Der Daily Brief ist das Beispiel für dieses Modul, weil er sich besonders gut eignet: Er ist persönlich (dein Kontext ist ein anderer als der von allen anderen), er muss auf Vorlieben angepasst werden (lang oder kurz, Stichpunkte oder Fließtext, Reihenfolge), und er entsteht jeden Tag neu aus wechselnden Daten. Damit du sofort loslegen kannst, sind Beispieldaten mitgeliefert — ein Dienstag im Leben von Mika, Produktmanagement bei NeoEmployee — du brauchst dafür keine eigenen Konnektoren zu E-Mail, Slack oder Kalender. Wichtig für den ganzen Kurs: Du tippst deinem Agenten nie Skill-Code. Du beschreibst, was der Skill tun soll — dein Agent legt ihn an.

## Voraussetzungen

Für dieses Modul gibt es zwei Wege. **Beide sind gleichwertig** — nimm den, der bei dir schon eingerichtet ist.

### Weg A — Visual Studio Code mit GitHub Copilot

Deine Arbeitsumgebung steht schon: Visual Studio Code mit GitHub Copilot im Agent-Modus — genau so, wie du es in Modul 0 eingerichtet hast.

Falls du Modul 0 noch nicht gemacht hast: Die Anleitung mit Video findest du auf der Lernplattform unter „Woche 0 — Willkommen und Installation".

### Weg B — Claude Code

Du brauchst Claude Code — als Desktop-App oder im Terminal.

- **Desktop-App:** Wenn Claude Code bei dir schon installiert ist — in vielen Firmen wird die Desktop-App zentral ausgerollt — brauchst du nichts weiter: keine Installation, kein Terminal.
- **Terminal:** Claude Code installieren, falls noch nicht vorhanden → [claude.ai/code](https://claude.ai/code). Folge den Anweisungen auf der Seite für dein Betriebssystem. Dazu ein Terminal: **Mac** — das Programm heißt Terminal (Programme → Dienstprogramme → Terminal, oder `Cmd + Leertaste` → „Terminal"); **Windows** — PowerShell (Windows-Suche → „PowerShell").

## Installation

### Schritt 1 — Kursordner herunterladen

Klicke auf dieser GitHub-Seite auf den grünen **Code**-Button → **Download ZIP**.

Entpacke die ZIP-Datei:

- **Windows:** Rechtsklick auf die Datei → **„Alle extrahieren"** → **„Extrahieren"**. (Nicht nur doppelklicken — dann stecken die Dateien noch im Archiv.)
- **Mac:** Doppelklick genügt.

### Schritt 2 — Ordner öffnen

Der entpackte Ordner heißt `KursDailyBrief-main`. Wichtig: Es muss der Ordner sein, in dem direkt die Datei `CLAUDE.md` liegt — nicht eine Ebene darüber oder darunter.

**Weg A — VS Code mit Copilot**

- **File → Open Folder** → den Ordner `KursDailyBrief-main` wählen.
- Beim ersten Öffnen fragt VS Code nach Vertrauen: **„Yes, I trust the authors"**.
- Chat öffnen (Chat-Symbol oben, oder `Strg+Alt+I` unter Windows / `Ctrl+Cmd+I` auf dem Mac), im Chatfenster die Modus-Auswahl auf **„Agent"** stellen.

**Weg B — Claude Code**

- **Desktop-App:** Neue Session starten und in den entpackten Ordner `KursDailyBrief-main` lenken.
- **Terminal:** In den Ordner wechseln und Claude Code starten:

  Mac:
  ```bash
  cd ~/Desktop/KursDailyBrief-main
  claude
  ```

  Windows (PowerShell):
  ```powershell
  cd "$env:USERPROFILE\Desktop\KursDailyBrief-main"
  claude
  ```

  Falls du den Ordner woanders gespeichert hast, passe den Pfad entsprechend an.

## Schrittmodus oder automatisch

Dein Agent fragt vor jedem Schreiben in eine Datei nach Erlaubnis, solange du das nicht änderst. Willst du jede Datei sehen, bevor sie entsteht, lass es dabei. Willst du, dass er einfach baut, schalte um — jederzeit, auch mitten im Kurs:

- **Weg A (VS Code mit Copilot):** Beim ersten Schreiben erscheint ein Dialog. „Allow" bestätigt einmal; im Ausklappmenü daneben gibt es „Always allow" für den Rest der Sitzung. Alternativ die Einstellung `chat.tools.autoApprove`.
- **Weg B (Claude Code):** Im Terminal `Shift+Tab` drücken, bis „accept edits" angezeigt wird. In der Desktop-App den Auto-Modus einschalten.

Die genauen Bezeichnungen ändern sich mit den Versionen — gemeint ist immer dasselbe. Viele fangen im Schrittmodus an und schalten um, sobald sie dem automatischen Schreiben trauen.

## Kurs starten

Tippe im Chat:

```
/kurs
```

Oder sag einfach: „starte den Kurs" oder „los geht's".

Während des Kurses kannst du jederzeit:
- **weiter** sagen, um zum nächsten Schritt zu gehen
- **überspringen** sagen, um einen Schritt zu überspringen
- **stop** sagen, um den Kurs zu unterbrechen

Wieder einsteigen, an einer bestimmten Stelle:

```
Starte den Kurs ab Schritt 4
```

**Fortgeschrittene**, die den Basispfad schon kennen oder es eilig haben, springen direkt zum zweiten Optimierungsschritt:

```
Starte den Kurs ab Schritt 9
```

Dort wartet ein einziger Sprungbrett-Prompt, der den kompletten Skill `/dailybrief` in einem Rutsch anlegt — die Schritte 1–8 musst du dafür nicht einzeln durchgehen.

## Dateistruktur

| Pfad | Rolle |
|---|---|
| `README.md` | Diese Datei |
| `CLAUDE.md` | Projekt-Prinzipien, immer aktiv |
| `.claude/skills/kurs/` | Der Kurs selbst (`/kurs`) |
| `.claude/skills/dailybrief/` | entsteht im Kurs — dein Agent legt ihn an |
| `.claude/skills/brief-feedback/` | entsteht im Kurs — dein Agent legt ihn an |
| `context/company.md` | Wer ist NeoEmployee? |
| `context/strategy.md` | Was ist die Strategie? |
| `context/team.md` | Wer ist wer bei NeoEmployee und bei den Kunden |
| `context/mika.md` | Mikas Rolle, aktuelle Themen, was heute zählt |
| `input/kalender.md` | Mikas Termine heute |
| `input/emails.md` | Mikas Postfach |
| `input/slack.md` | Mikas Slack |
| `input/meetings/` | Notizen der gestrigen Meetings |
| `beispiele/` | Negativbeispiel für Schritt 6 — ein Brief, wie er nicht sein soll |
| `loesungen/` | Musterlösungen, Notausgang — siehe `loesungen/LIES_MICH.md` |
| `output/` | Hier landen deine Briefe: `brief-<datum>.md` und `.html` |

## Welches Modell?

Für dieses Modul reicht **jedes Modell** — auch ein schnelles oder günstiges. Der Skill liest vier Dateien aus `input/` und schreibt daraus einen Brief; das braucht kein besonders starkes Modell. Du musst hier also nichts umstellen.

## Nutzungslimits

**Weg A (Copilot):** Copilot arbeitet mit den Anfrage-Kontingenten deiner Copilot-Lizenz. Die Schritte in diesem Kurs sind klein. Bittet Copilot dich bei intensiver Nutzung kurz zu warten, ist das normal.

**Weg B (Claude Code):** Claude Code arbeitet mit einem Token-Limit, das alle 5 Stunden zurückgesetzt wird. Bei intensiver Nutzung kann es dich bitten, kurz zu warten.

**Tipp:** Der Kurstext liegt in `.claude/skills/kurs/SKILL.md` — im Editor öffnen und mitlesen, dann braucht der Chat nur die eigentliche Arbeit.

## Probleme?

- **Falscher Ordner geöffnet:** Achte darauf, dass direkt in deinem geöffneten Ordner die Datei `CLAUDE.md` liegt — nicht eine Ebene darüber oder darunter.
- **Skill wird nicht gefunden:** Der Ordnername unter `.claude/skills/` ist gleichzeitig der Befehl. Bietet dein Werkzeug einen frisch angelegten Skill nicht an, sag deinem Agenten: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."
- **Dein Agent hat etwas Kaputtes gebaut:** Notausgang `loesungen/` — sieh dir `loesungen/LIES_MICH.md` an.
- **Die HTML-Seite öffnet sich nicht:** Doppelklick auf die Datei in `output/`.
- Bei allem anderen: Nachricht an Markus.
