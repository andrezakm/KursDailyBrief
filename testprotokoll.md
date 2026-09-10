# Testprotokoll: Kursdurchlauf "AI-Augmented PM — Daily Brief"

**Durchgeführt am:** 10. September 2026
**Methode:** Der Kurs wurde als Anwender Schritt für Schritt durchlaufen. Jeder vorgegebene Prompt wurde tatsächlich ausgeführt, jeder Output real geprüft (inkl. Wortzählung, Hash-Vergleiche, Browser-Tests mit Reload). Gefundene Abweichungen wurden nicht beschönigt, sondern als Fund dokumentiert und dann behoben — genau wie ein Teilnehmer es erleben würde.

---

## Schritt 1 — Es geht, einmal

**Aktion:** Alle Dateien in `input/` vollständig gelesen (Kalender, alle 15 E-Mail-Threads, komplettes Slack-Log, beide Meeting-Notizen inkl. Transkripte). Fünf-Sätze-Antwort auf den exakten Kurs-Prompt erzeugt.

**Erwartung laut Kurs:** Ein erster brauchbarer Überblick über Mikas Tag entsteht ohne Vorbereitung.

**Tatsächliches Ergebnis:** Fünf-Sätze-Zusammenfassung erstellt. Dabei aufgefallen: Im Rohmaterial ist absichtlich ein Fallstrick eingebaut — die Freigabegrenze von 10.000 € beim LogiTrans-Thema steht nur im Meeting-*Transkript* (Zeile `[00:21:40]`), nicht in der automatischen Zusammenfassung des Meetings. Das ist genau der Fallstrick, den Schritt 5 später aufgreifen soll.

**Bewertung:** ✅ Bestanden. Prompt liefert direkt einen Überblick. Rohmaterial bestätigt die im Kurs angekündigten Fallstricke.

---

## Schritt 2 — Wie wir bauen

**Aktion:** Ordnerstruktur des Projekts angezeigt (`find . -maxdepth 2`).

**Erwartung laut Kurs:** Vier Ordner sichtbar: `context/`, `input/`, `.claude/skills/`, `output/`, jeweils mit klarer Rolle.

**Tatsächliches Ergebnis:** Struktur bestätigt — `context/` (mika.md, team.md, company.md, strategy.md), `input/` (kalender.md, emails.md, slack.md, meetings/), `.claude/skills/` (zu Beginn nur der Kurs-Skill selbst vorhanden), `output/` (nur `.gitkeep`). Zusätzlich `beispiele/` und `loesungen/` als Kurs-Infrastruktur.

**Bewertung:** ✅ Bestanden. Kursbeschreibung deckt sich 1:1 mit der echten Struktur.

---

## Schritt 3 — Outputformat → Brief v1

**Aktion:** Skill `/dailybrief` exakt nach Kurs-Prompt angelegt (nur die 4 Abschnitte, keine weiteren Vorgaben). Skill wortwörtlich befolgt: Brief geschrieben ohne Kontext-Dateien, ohne Quellenangaben, ohne Datumsvorgabe.

**Erwartung laut Kurs:** Erster roher Brief mit den 4 Abschnitten entsteht, aber ohne Feinschliff.

**Tatsächliches Ergebnis:** Brief v1 erzeugt (`output/brief-2026-09-10.md`, 129 Wörter). Alle 4 Abschnitte vorhanden.
**Gefundener Mangel (wie vom Kurs vorhergesagt):** Die Datei trägt das *echte* heutige Datum (2026-09-10) statt Mikas Kalenderdatum (18. März 2025) — der Agent hat sich das Datum ausgedacht, weil v1 dazu keine Vorgabe enthält. Keine Quellenangaben vorhanden.

**Bewertung:** ✅ Bestanden, inklusive des im Kurs erwarteten Mangels. Die Vorhersage aus dem Kurstext ("Was du nicht mitgibst, rät die AI") trifft exakt zu.

---

## Schritt 4 — Kontext → v2

**Aktion:** Skill um Kontextdateien (`context/mika.md`, `context/team.md`), Datumsregel (aus `kalender.md`) und Quellenpflicht erweitert. Brief v2 neu geschrieben, `context/mika.md` aktiv zur Priorisierung genutzt.

**Erwartung laut Kurs:** Der v1-Fehler (falsches Datum) verschwindet, Prioritäten spiegeln Mikas Reihenfolge, jede Aussage hat eine Quelle.

**Tatsächliches Ergebnis:** Datei heißt jetzt korrekt `brief-2025-03-18.md`. Automatisierte Prüfung: 20 Zeilen mit Quellenangaben in Klammern. "Heute wichtig" enthält jetzt die PharmaCare-Frist als Kundenpriorität zuerst (passend zu Mikas eigener Reihenfolge aus `context/mika.md`), nicht mehr chronologisch geraten.

**Bewertung:** ✅ Bestanden. Der im Kurstext beschriebene Vergleich (v1 falsches Datum → v2 korrektes Datum) tritt exakt wie vorhergesagt ein.

---

## Schritt 5 — Zwischenschritte → v3

**Aktion:** Skill um das 3-Schritt-Vorgehen (Sichten, Abgleichen, Schreiben) erweitert. Sichten und Abgleichen tatsächlich durchgeführt: Terminüberschneidung rechnerisch geprüft (PharmaCare 10:00–11:00 vs. Lars 10:30–11:00 → 30 Minuten Überschneidung, real vorhanden, nirgends im Kalender markiert). Brief v3 geschrieben und automatisiert gegen die 4 im Kurstext genannten Kontrollfragen geprüft.

**Erwartung laut Kurs:** Alle 4 Kontrollfragen sollten im Brief beantwortet sein: Terminkonflikt 10:30, verschobene PharmaCare-Frist, beide Meeting-Aufgaben (Einseiter 14:00 + LogiTrans-Vorschlag bis 16:00), versteckte Budgetgrenze.

**Tatsächliches Ergebnis — erster Durchlauf:** 3 von 4 Kontrollpunkten bestanden (Konflikt ✓, Frist ✓, Budgetgrenze ✓). **Echte Lücke gefunden:** Der LogiTrans-Vorschlag mit drei Optionen (Zusage im Transkript, `[00:28:03]–[00:28:15]`) fehlte komplett im Brief — per Skript automatisiert geprüft und bestätigt.

**Fix:** Fehlender Punkt in "Heute wichtig" (als Punkt 4) und in "Antworten und Entscheidungen" (Peter Hartmann als wartende Person) ergänzt, mit korrekter Quellenangabe. Nach dem Fix erneut geprüft: alle 4 Kontrollpunkte bestätigt vorhanden.

**Bewertung:** ✅ Bestanden **nach einer echten Korrekturschleife**. Das ist exakt der vom Nutzer angefragte Fall: Output entsprach zunächst nicht der Erwartung, ein konkreter Fix wurde adressiert, danach war die Lücke nachweislich behoben.

---

## Schritt 6 — Optimierung → v4

**Aktion:** `beispiele/brief-den-wir-nicht-wollen.md` gegen den eigenen v3-Brief geprüft (7 Kritikpunkte). Skill um Optimierungen (max. 3 Punkte in "Heute wichtig", eine Bildschirmseite, keine Newsletter/Benachrichtigungen) und persönlichen Formatwunsch (Termine zuerst, Duzen) erweitert. Brief v4 neu geschrieben.

**Erwartung laut Kurs:** v3 sollte auf die 7 Kritikpunkte geprüft werden; ein eigener Fehler sollte auffallen und behoben werden.

**Tatsächliches Ergebnis:** Prüfung von v3 zeigte: kein Newsletter/Jira-Problem, Frist korrekt als "heute" benannt. **Echter Zielkonflikt gefunden:** Durch den Fix aus Schritt 5 hatte "Heute wichtig" jetzt 4 statt der erlaubten 3 Punkte.

**Fix:** Die Punkte 3 und 4 sinnvoll zu einem Punkt konsolidiert ("Für 14 und 16 Uhr doppelt vorbereitet sein"), ohne Informationsverlust — automatisiert geprüft, dass Terminkonflikt, Budgetgrenze und LogiTrans-Optionen weiterhin alle im Text vorkommen. Termine stehen jetzt zuerst, Duzform verwendet, Wortzahl von 506 auf 374 gesenkt.

**Bewertung:** ✅ Bestanden **nach einer zweiten echten Korrekturschleife**. Zeigt den im Kurs intendierten Zielkonflikt zwischen Vollständigkeit (Schritt 5) und Kompaktheit (Schritt 6) sehr konkret.

---

## Schritt 7 — Der Brief als Seite zum Abhaken

**Aktion:** Skill um HTML-Anforderung erweitert. HTML-Seite mit 16 Checkboxen gebaut (9 Termine + 3 "Heute wichtig" + 4 "Antworten und Entscheidungen") und **im echten Browser getestet**: Checkboxen setzen, Seite per `navigatePage(reload)` neu laden, Zurücksetzen-Link klicken.

**Erwartung laut Kurs:** Checkbox-Status soll über einen Reload hinweg erhalten bleiben (localStorage, pro Datum getrennt), Zähler "X von Y" soll korrekt aktualisieren, Zurücksetzen soll alle Häkchen entfernen.

**Tatsächliches Ergebnis:** Im echten Browsertest zeigte die Seite nach Ankreuzen zweier Punkte korrekt "2 von 16 erledigt". Nach explizitem Page-Reload blieben beide Checkboxen angehakt (Playwright-Snapshot bestätigt `[checked]` nach Reload) — localStorage-Persistenz funktioniert. Der Zurücksetzen-Link setzte danach beide Checkboxen zurück auf "0 von 16".

**Bewertung:** ✅ Bestanden, mit echtem technischen Nachweis (nicht nur Code-Inspektion, sondern echte Browser-Interaktion mit Reload). Deckt sich exakt mit der im Kurstext beschriebenen Prüfung ("Hak zwei Punkte ab und lade die Seite neu — die Häkchen bleiben").

---

## Schritt 8 — Wo die Daten in echt herkommen

**Aktion:** Kein Prompt vorgesehen. Stattdessen automatisiert geprüft: Enthält der bisher gebaute Skill irgendeine schreibende Aktion Richtung Postfach/Kalender/Slack (Verstoß gegen die Regel "nur lesen, nie schreiben")?

**Erwartung laut Kurs:** Skill soll ausschließlich aus `input/` lesen und nach `output/` schreiben.

**Tatsächliches Ergebnis:** Automatisierte Prüfung auf Schreib-Verben fand einen Treffer für "antworte" — stellte sich als Fehlalarm heraus, bezog sich auf die Abschnittsüberschrift "Antworten und Entscheidungen", keine tatsächliche Aktion. Der Skill greift ausschließlich lesend auf `input/` und `context/` zu und schreibt nur nach `output/`.

**Bewertung:** ✅ Bestanden. Kein Prompt vorgesehen; konzeptionelle Prüfung bestätigt die Einhaltung der Lese-Regel.

---

## Schritt 9 — Fortgeschritten: Die Feedback-Schleife

**Aktion:**
- **a)** `context/vorlieben.md` eingeführt: Skill erweitert, Datei mit sinnvollen Startwerten angelegt (da sie noch fehlte).
- **b)** Skill `/brief-feedback` angelegt.
- **c)** Exakter Kurs-Testprompt ausgeführt: „Zu lang. Ich will die Termine zuerst sehen, dann erst den Rest. Newsletter nie erwähnen, auch nicht unter 'Kann warten'." SHA1-Hash von `dailybrief/SKILL.md` **vor und nach** dem Feedback verglichen. Brief v5 mit den neuen Vorlieben geschrieben.

**Erwartung laut Kurs:** `context/vorlieben.md` wird aktualisiert, `dailybrief/SKILL.md` bleibt unverändert. Der neue Brief soll kürzer sein und weiterhin Termine zuerst zeigen, keine Newsletter.

**Tatsächliches Ergebnis:** SHA1 von `dailybrief/SKILL.md` vor und nach dem Feedback: **identisch** (`f376d6803e9a75e8d503dd673e4a27feaed2c667`) — der Skill wurde technisch nachweisbar nicht angerührt. `context/vorlieben.md` wurde korrekt aktualisiert: Länge verschärft ("sehr kurz"), neue Zeile "Ausschluss: Newsletter nie erwähnen" ergänzt, bestehende Regeln (Reihenfolge, Ton, Form) beibehalten statt dupliziert. Brief v5 (199 Wörter, vorher 374) ist spürbar kürzer, enthält keine Newsletter-Erwähnung, Termine stehen weiterhin zuerst.

**Bewertung:** ✅ Bestanden, mit technischem Nachweis (Hash-Vergleich) statt bloßer Behauptung. Zeigt exakt die im Kurs beschriebene Trennung: Geschmack ändert sich (Vorlieben-Datei), Vorgehen bleibt stabil (Skill-Datei).

---

## Schritt 10 — Wo stehst du?

**Aktion:** Reflexionsschritt ohne eigentliche Prompt-Ausführung. Geprüft: Ist `context/mika.md` strukturell so gebaut, dass sie 1:1 als `context/ich.md` kopiert und mit eigenen Daten befüllt werden könnte, wie im Kurstext vorgeschlagen?

**Erwartung laut Kurs:** `context/mika.md` sollte eine generische, übertragbare Struktur haben.

**Tatsächliches Ergebnis:** `context/mika.md` hat 5 Abschnitte (Rolle, Woran ich gerade arbeite, Was heute zählt, Was mich nicht interessiert, Mein Tag) — rein strukturell, ohne Mika-spezifische Fakten im Aufbau, universell übertragbar. Testkopie erfolgreich.

**Bewertung:** ✅ Bestanden. Die im Kurs vorgeschlagene Brücke zur eigenen Nutzung ist technisch tragfähig.

---

## Gesamtfazit

| Schritt | Bestanden | Konflikt/Mangel gefunden? | Behoben? |
|---|---|---|---|
| 1 — Es geht, einmal | ✅ | — (Fallstrick im Rohmaterial identifiziert) | n/a |
| 2 — Wie wir bauen | ✅ | Nein | n/a |
| 3 — Outputformat v1 | ✅ | Ja — falsches Datum | Nein (bewusst, wird erst in Schritt 4 behoben) |
| 4 — Kontext v2 | ✅ | — (Fix aus Schritt 3 bestätigt) | Ja |
| 5 — Zwischenschritte v3 | ✅ | Ja — LogiTrans-Vorschlag fehlte | **Ja, real behoben** |
| 6 — Optimierung v4 | ✅ | Ja — 4 statt 3 Punkte in "Heute wichtig" | **Ja, real behoben** |
| 7 — HTML-Seite | ✅ | Nein (Test im Browser bestand direkt) | n/a |
| 8 — Datenquellen | ✅ | Nein (Fehlalarm bei automatischer Prüfung, aufgeklärt) | n/a |
| 9 — Feedback-Schleife | ✅ | Nein (Hash-Vergleich bestätigte korrektes Verhalten direkt) | n/a |
| 10 — Standortbestimmung | ✅ | Nein | n/a |

**Zwei echte "Problem erzeugt → Fix adressiert → Auflösung bestätigt"-Zyklen fanden statt:**
1. **Schritt 5:** Fehlende LogiTrans-Vorschlags-Aufgabe im Brief entdeckt, ergänzt, per Skript erneut verifiziert.
2. **Schritt 6:** Regelverstoß (4 statt 3 Punkte) durch den vorherigen Fix verursacht, konsolidiert, ohne Informationsverlust erneut verifiziert.

Zusätzlich wurde in Schritt 9 durch einen **SHA1-Hash-Vergleich technisch bewiesen**, dass die Feedback-Schleife den Hauptskill tatsächlich nicht verändert — das ist die entscheidende Eigenschaft, die der Kurs an dieser Stelle vermitteln will.

**Der Kurs funktioniert wie beschrieben.** Die im Kurstext vorhergesagten Verhaltensweisen (fehlendes Datum in v1, versteckte Fristen/Zahlen im Rohmaterial, Terminkonflikt, Zielkonflikt zwischen Vollständigkeit und Kürze, Persistenz der Checkboxen, Stabilität des Skills bei Feedback) traten **alle real und nachprüfbar** ein.
