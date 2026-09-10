---
name: brief-feedback
description: Nutze diesen Skill, wenn der Nutzer Kritik oder Wünsche zum letzten Daily Brief äußert, die dauerhaft als Vorliebe hinterlegt werden sollen.
---

Du bekommst im Aufruf Kritik oder Wünsche zum letzten Daily Brief, in normalen Sätzen — keine fertigen Regeln.

## Vorgehen

Lies `context/vorlieben.md`. Falls die Datei fehlt, lege sie an mit den Zeilen „Länge:", „Reihenfolge:", „Ton:", „Form:" und diesen Startwerten: Länge: passt auf eine Bildschirmseite · Reihenfolge: Heute wichtig, Termine, Antworten und Entscheidungen, Kann warten · Ton: sachlich, neutral · Form: kurze Absätze mit Stichpunkten.

Übersetze die Kritik in kurze Regeln. Betrifft eine Regel Länge, Reihenfolge, Ton oder Form, ersetze den Wert der passenden der vier festen Zeilen. Alles andere trägst du unter „Weitere Regeln" ein, jede Regel als eigene Zeile mit dem heutigen Datum in Klammern. Ergänze oder ersetze bestehende Regeln, wenn die neue Kritik ihnen widerspricht. Trage nichts doppelt ein, und streiche keine Regel, der nicht widersprochen wurde.

Du änderst nie `.claude/skills/dailybrief/SKILL.md`. Der Skill `/dailybrief` bleibt unangetastet — nur `context/vorlieben.md` wächst.

Gehört eine Kritik nicht zum Geschmack, sondern ins Vorgehen (zum Beispiel „Terminkonflikte immer prüfen"), trägst du sie trotzdem nur in `context/vorlieben.md` ein, wie jede andere Regel. Schlage am Ende zusätzlich in einem Satz vor, dass diese Regel eher in den Skill `/dailybrief` gehört — ändere dafür aber nichts.

Zeig zum Schluss die vollständige neue Fassung von `context/vorlieben.md` im Chat.

## Aufbau von context/vorlieben.md

Oben die vier festen Zeilen „Länge:", „Reihenfolge:", „Ton:", „Form:". Darunter ein Abschnitt „Weitere Regeln" als Liste; jede Regel eine Zeile, jede mit Datum in Klammern, zum Beispiel:

- Newsletter und automatische Benachrichtigungen nie erwähnen, auch nicht unter „Kann warten" (2025-03-18)
