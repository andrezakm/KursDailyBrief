# Kursumgebung: AI-Augmented PM — Modul Daily Brief

## Wer wir sind

NeoEmployee baut custom AI Agenten, die Mitarbeiterfähigkeiten in Unternehmen ersetzen. Wir arbeiten als Beratung auf Time-&-Material-Basis, wir sind bootstrapped — Revenue ist Runway. Details zur Firma und zur Strategie stehen in `context/company.md` und `context/strategy.md`, wer bei NeoEmployee und bei den Kunden wer ist in `context/team.md`, und wer Mika ist — Rolle, aktuelle Themen, was heute zählt — in `context/mika.md`.

## Pfadkonventionen

- `input/` — Mikas Tag: `kalender.md`, `emails.md`, `slack.md` und `input/meetings/` mit den Notizen der gestrigen Meetings. Ändert sich jeden Tag.
- `context/` — statischer Kontext: wer NeoEmployee ist, wer im Team wer ist, wer Mika ist. Ändert sich nicht von Tag zu Tag.
- `.claude/skills/` — die Skills, die im Kurs entstehen.
- `beispiele/` — ein Negativbeispiel, an dem sichtbar wird, was ein Brief nicht sein soll.
- `loesungen/` — Musterlösungen. Wird nicht automatisch geladen, nur bei Bedarf zu öffnen.
- `output/` — hier landen alle Briefe.

## Sprache

Alle Outputs auf Deutsch, mit korrekten Umlauten: ä, ö, ü, Ä, Ö, Ü, ß. Keine ASCII-Ersetzungen (ae, oe, ue). Es heißt „AI", nicht „KI".

## Qualitätsstandard

Nichts in einen Brief schreiben, was nicht in `input/` steht. Jede Aussage nennt ihre Quelle. Fehlt etwas — ein Anhang, eine Sprachnachricht —, wird das benannt, nicht erfunden.

## Kurs starten

Sobald der Nutzer „starte den Kurs", „los geht's" oder Ähnliches sagt — führe `/kurs` aus, ohne Vorrede. Kannst du den Skill nicht selbst aufrufen, lies `.claude/skills/kurs/SKILL.md` vollständig ein und folge den Anweisungen darin.

„Starte den Kurs ab Schritt X" springt direkt zu Schritt X.

Sagt der Nutzer nur „weiter", führe den laufenden Kurs fort.
