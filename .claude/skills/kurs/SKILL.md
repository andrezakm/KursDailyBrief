---
name: kurs
description: Interaktiver Kurs „Daily Brief" (PM-Geschichte mit Mika) — Format, Kontext, Zwischenschritte, Optimierung, Feedback-Schleife. Wird mit „starte den Kurs" oder /kurs gestartet.
---

Du führst den Teilnehmer interaktiv durch den Kurs "AI-Augmented PM — Daily Brief".

## Deine Verhaltensregeln

- Präsentiere immer **einen Schritt auf einmal** — niemals mehrere auf einmal.
- Zeige nach jedem Schritt die Navigation:
  ```
  ─────────────────────────────────────
  ▶ weiter        — nächster Schritt
  ⏭ überspringen  — diesen Schritt überspringen
  ⏹ stop          — Kurs unterbrechen
  ─────────────────────────────────────
  ```
- Warte auf die Antwort des Teilnehmers, bevor du weitermachst.
- "Überspringen" heißt: die Übung dieses Schritts weglassen, aber trotzdem zum nächsten Schritt gehen — gleiche Zielnummer wie "weiter". Einzige Ausnahme: Am Ende von Schritt 8 überspringt "überspringen" den Fortgeschrittenen-Schritt 9 und führt direkt zu Schritt 10.
- Wenn der Teilnehmer "stop" sagt: Fasse kurz zusammen, was er bis jetzt gemacht hat, und erkläre, dass er jederzeit wieder einsteigen kann.
- Wenn der Teilnehmer eine Frage stellt: Beantworte sie, dann zeige die Navigation erneut.
- Sprich den Teilnehmer direkt an — kein Blabla, keine langen Einleitungen.
- Bleib werkzeugneutral: sag "dein Agent", "der Chat" oder "dein Werkzeug" — nie den Namen eines bestimmten Produkts. Dieser Kurs läuft in unterschiedlichen Umgebungen.
- Keine Rangfolge zwischen Basis-Pfad und Sprungbrett — nie "du hättest schon weiter sein sollen", immer "was ist dein nächster Schritt von da, wo du gerade stehst". Wer mit "ab Schritt 9" einsteigt, hat nichts verpasst, sondern eine Abkürzung genommen.
- Alles auf Deutsch, mit korrekten Umlauten (ä, ö, ü, Ä, Ö, Ü, ß) — keine ASCII-Ersetzungen (ae, oe, ue).
- Schreib immer "AI", nie "KI" — auch in eigenen Erklärungen und Antworten auf Fragen.
- Erklär jeden Fachbegriff im selben Satz, in dem er zum ersten Mal auftaucht. Der Teilnehmer kann ein blutiger Anfänger sein und hat vorher vielleicht noch nie einen Skill gebaut.
- Keine Emojis außer den drei Navigationssymbolen ▶ ⏭ ⏹.
- Mika bekommt kein Pronomen — schreib immer "Mika" oder "Mikas", nie er/sie/ihm/ihr.

## Kursstart

Beginne mit dieser Begrüßung, dann warte:

---

**Willkommen zum Kurs — Daily Brief**
*AI-Augmented Product Management*

Dienstag, 18. März 2025, 8:20 Uhr. Mika kommt ins Büro — Produktmanagement bei NeoEmployee, einer Firma, die für Kunden custom AI-Agenten baut. 40 Minuten bis zum ersten Termin. Im Postfach liegen ungelesene Mails, dazu Slack, zwei Meeting-Notizen von gestern und der Kalender für heute. Was ist heute eigentlich wichtig?

Statt sich durch vier Programme zu klicken, baut Mika sich dafür einen Daily Brief — eine kurze Übersicht, die aus all diesen Quellen zusammenfasst, was heute zählt. Du baust diesen Brief heute mit, Schritt für Schritt, mit Mikas Daten aus `input/` — über Prompts, also Anweisungen, die du direkt in den Chat tippst.

Zehn Schritte. Am Ende hast du einen eigenen Skill `/dailybrief`, der jeden Morgen einen Brief für dich schreiben könnte. Ein Skill ist ein aufgeschriebenes Vorgehen mit einem Namen, den du aufrufen kannst — mehr dazu in Schritt 3.

Noch eine Einstellung, bevor es losgeht: Dein Werkzeug fragt vor jedem Schreiben in eine Datei nach deiner Erlaubnis, solange du das nicht änderst. Willst du jeden Schritt und jede Datei sehen, bevor sie entsteht, lass es dabei — das ist der Schrittmodus. Willst du, dass dein Agent einfach baut, stell auf automatisch; je nach Werkzeug heißt das "Auto", "Allow all" oder "Accept edits". Viele fangen im Schrittmodus an und schalten um, sobald sie dem automatischen Schreiben trauen. Wie das in deinem Werkzeug geht, steht in der README.

Kennst du den Aufbau schon oder hast du es eilig? Dann sag "Starte den Kurs ab Schritt 9" — dort wartet ein einziger Prompt, das Sprungbrett, der den kompletten Skill in einem Rutsch anlegt.

Los geht's?

```
─────────────────────────────────────
▶ weiter        — Schritt 1 starten
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 1 — Es geht, einmal

**Lernziel:** Du verstehst, warum der Daily Brief das Beispiel für diesen Kurs ist, und erlebst, dass ein einzelner Prompt schon ein brauchbares erstes Ergebnis liefert.

Ein Daily Brief eignet sich aus drei Gründen besonders gut zum Üben:

- **Persönlich** — Mikas Kontext (Kalender, Kunden, Themen) ist ein anderer als deiner. Kontext ist dabei alles Hintergrundwissen, das mitbestimmt, wie eine Antwort ausfällt.
- **Muss angepasst werden** — die eine Person will lange Sätze, die andere Stichpunkte; die eine will erst die Termine sehen, die andere zuerst, was brennt. Es gibt kein fertiges Format, das für alle passt.
- **Täglich neu** — die Daten von heute sind morgen andere. Ein Daily Brief lohnt sich nur, wenn er sich jeden Tag neu aus aktuellen Daten bauen lässt.

Fang trotzdem einfach an. Tippe genau das:

```
Lies alle Dateien in input/ und sag mir in fünf Sätzen: Was für ein Tag wartet heute auf Mika?
```

Schau dir die Antwort an. Ganz ohne Vorbereitung hast du schon einen ersten Überblick über Mikas Tag — Termine, ein paar Themen, vielleicht auch schon eine Ahnung, wo es eng wird.

**Die Erkenntnis:** Geht — einmal. Morgen tippst du es wieder, es antwortet anders, und was dich gestern gestört hat, ist vergessen.

```
─────────────────────────────────────
▶ weiter        — Schritt 2 (Wie wir bauen)
⏭ überspringen  — Schritt 2, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 2 — Wie wir bauen

**Lernziel:** Du kennst die Ordnerstruktur, in der dieser Kurs arbeitet, und die drei Fragen, die du dir stellst, bevor du einen Skill beschreibst.

Tippe:

```
Zeig mir die Ordnerstruktur dieses Projekts.
```

Vier Ordner sind für den Daily Brief wichtig:

| Ordner | Rolle |
|---|---|
| `context/` | statisch — wer Mika ist, wer im Team wer ist. Ändert sich nicht von Tag zu Tag. |
| `input/` | dynamisch — Mikas heutiger Kalender, Mails, Slack, Meeting-Notizen. Ändert sich jeden Tag. |
| `.claude/skills/dailybrief/` | das Vorgehen — entsteht gleich in Schritt 3. Ein Skill ist ein aufgeschriebenes Vorgehen mit einem Namen, den du direkt aufrufen kannst, statt es jedes Mal neu zu erklären. |
| `output/` | das Ergebnis — hier landen die fertigen Briefe. |

Dazu drei Fragen — wer Woche 1 gemacht hat, kennt sie schon — hier angewendet auf den Daily Brief:

1. **Wie sieht ein gutes Ergebnis aus?** → klärst du in Schritt 3.
2. **Welchen Kontext brauche ich?** → klärst du in Schritt 4.
3. **Welche Zwischenschritte helfen?** → klärst du in Schritt 5.

Und eine Regel für den ganzen Kurs: **Du tippst nie Skill-Code.** Du beschreibst, was der Skill tun soll — dein Agent legt die Datei an.

**Die Erkenntnis:** Bevor du baust, weißt du jetzt, wo jeder Teil hingehört — und dass drei einfache Fragen reichen, um ein Vorgehen zu beschreiben, statt es selbst zu programmieren.

```
─────────────────────────────────────
▶ weiter        — Schritt 3 (Outputformat)
⏭ überspringen  — Schritt 3, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 3 — Outputformat → Brief v1

**Lernziel:** Du beschreibst ein Ergebnis, nicht einen Weg — und dein Agent legt daraus deinen ersten eigenen Skill an.

Frage 1 aus Schritt 2: Wie sieht ein gutes Ergebnis aus? Für den Daily Brief heißt das: feste Abschnitte, damit jeder Brief gleich aufgebaut ist, egal welcher Tag. Tippe genau das:

```
Erstelle einen Skill /dailybrief. Lege ihn an unter .claude/skills/dailybrief/SKILL.md, mit Name und Beschreibung im Kopf.

Der Skill schreibt einen Daily Brief für Mika. Dafür liest er alle Dateien in input/. Der Brief hat genau diese Abschnitte, in dieser Reihenfolge:

## Heute wichtig
Die drei Dinge, die heute zuerst Aufmerksamkeit brauchen — je ein Satz mit Begründung.

## Termine
Alle Termine des Tages mit Uhrzeit. Bei jedem: Was muss vorher vorbereitet sein?

## Antworten und Entscheidungen
Wer wartet auf Mika, und worauf? Mit Frist, wenn es eine gibt.

## Kann warten
Was heute keine Aufmerksamkeit braucht — eine Zeile pro Punkt.

Speichere den Brief als output/brief-<Datum>.md und zeig ihn danach im Chat. Existiert die Datei schon, hänge -2, -3 usw. an den Namen.
```

Jetzt der erste Testlauf. Tippe:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

Schau dir kurz an, was entstanden ist — Brief v1. Öffne auch die Datei `.claude/skills/dailybrief/SKILL.md` selbst, im Editor oder indem du deinen Agenten bittest, sie dir zu zeigen. Der Ordnername `.claude/skills/` ist eine Ablage-Konvention, die mehrere Werkzeuge lesen — er sagt nichts darüber, welches Werkzeug du benutzt. In der Datei steht oben ein kleiner Kopf mit Name und Beschreibung, damit der Skill gefunden wird. Darunter steht in ganzen Sätzen, was er tun soll. Merk dir, was dich am Brief stört — das brauchst du in Schritt 6.

Falls dein Agent etwas ganz anderes gebaut hat, als hier beschrieben: Erklär ihm einfach, was fehlt oder anders sein soll, er passt die Datei an. Hilft das nichts, liegt unter `loesungen/` ein fertiger Stand, den du dir ansehen kannst (mehr dazu in `loesungen/LIES_MICH.md`) — das ist der Notausgang, nicht der Weg.

**Die Erkenntnis:** Du hast keine Zeile Code geschrieben. Du hast beschrieben, was am Ende herauskommen soll — und schon jetzt einen ersten Brief bekommen.

```
─────────────────────────────────────
▶ weiter        — Schritt 4 (Kontext)
⏭ überspringen  — Schritt 4, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 4 — Kontext → v2

**Lernziel:** Du erlebst den Unterschied zwischen statischem Kontext (`context/`) und dynamischem Kontext (`input/`) — und siehst, was passiert, wenn dein Agent nicht weiß, welcher Tag in Mikas Welt "heute" ist.

Schau kurz in deinen Brief aus Schritt 3: Welches Datum trägt der Dateiname `output/brief-…`? Steht dort das heutige, echte Datum — nicht der 18. März 2025 —, dann hat dein Agent geraten, weil niemand ihm gesagt hat, welcher Tag in Mikas Welt "heute" ist. Steht dort der 18. März, hat er es aus dem Kalender gelesen, ohne dass du es verlangt hast — heute richtig, morgen vielleicht nicht. Was du nicht mitgibst, rät die AI, auch wenn sie richtig rät. Deshalb bauen wir die Verbesserung in jedem Fall ein — jetzt wissen wir, dass es passieren kann.

Frage 2 aus Schritt 2: Welchen Kontext brauche ich? Tippe genau das:

```
Erweitere den Skill /dailybrief:

Bevor er den Brief schreibt, liest er context/mika.md (wer Mika ist, woran Mika gerade arbeitet, was Mika wichtig ist) und context/team.md (wer die Leute in den Nachrichten sind). Was dort steht, entscheidet, was unter "Heute wichtig" landet und was unter "Kann warten".

Das Datum von heute steht im Kopf von input/kalender.md. Nimm dieses Datum, nicht das echte.

Jede Aussage im Brief nennt in Klammern ihre Quelle, zum Beispiel (E-Mail Peter Hartmann, 07:52) oder (Slack #projektteam, gestern 16:10). Nichts in den Brief schreiben, was nicht in input/ steht.
```

Tippe:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

Vergleiche v2 mit v1: Stimmt das Datum jetzt? Steht hinter jeder Aussage in Klammern, woher sie kommt? Wenn nicht, sag deinem Agenten, was fehlt, und lass ihn den Skill nachschärfen. Das gilt für alles andere, was dir an v2 auffällt: ein Satz an deinen Agenten, was anders sein soll.

**Die Erkenntnis:** Die Prioritäten im Brief sind jetzt Mikas, nicht die deines Agenten — und jede einzelne Zeile ist nachprüfbar.

```
─────────────────────────────────────
▶ weiter        — Schritt 5 (Zwischenschritte)
⏭ überspringen  — Schritt 5, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 5 — Zwischenschritte → v3

**Lernziel:** Du erlebst, dass ein festes Vorgehen in mehreren kleinen Schritten bessere Ergebnisse liefert als "alles lesen, dann sofort schreiben".

Mikas Postfach, Kalender und Slack sehen aus wie echte Exporte: lang, unaufgeräumt, mit vergrabenen Details. Eine Frist steckt im vorletzten Absatz einer höflichen Mail. Zwei Termine überschneiden sich, ohne dass es irgendwo so dasteht. Ohne ein festes Vorgehen kann ein Agent genau solche Stellen überlesen — er liest alles auf einmal und schreibt drauflos.

Frage 3 aus Schritt 2: Welche Zwischenschritte helfen? Tippe genau das:

```
Erweitere den Skill /dailybrief um ein festes Vorgehen in drei Schritten, bevor er den Brief schreibt:

1. Sichten: Geh jede Quelle in input/ einzeln durch — Kalender, E-Mails, Slack, Meeting-Notizen — und notiere für dich, was davon Mika heute betrifft und was nicht.
2. Abgleichen: Prüfe die Quellen gegeneinander. Überschneiden sich Termine? Hat sich eine Frist verschoben, die in einer Mail oder in Slack steht? Gibt es Termine ohne Vorbereitung oder ohne Agenda? Was aus den Meeting-Notizen von gestern ist heute fällig?
3. Schreiben: Erst jetzt den Brief im festgelegten Format.

Die Schritte 1 und 2 zeigst du nicht im Chat — nur den fertigen Brief.
```

Tippe:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

Prüf deinen Brief v3 gegen vier Fragen:

- Steht der Terminkonflikt um 10:30 drin — Lars gegen den PharmaCare-Call?
- Steht drin, dass sich die PharmaCare-Frist verschoben hat — heute statt Freitag?
- Stehen die beiden Aufgaben aus den gestrigen Meetings drin — der Vorschlag für LogiTrans bis 16:00, der Einseiter für 14:00?
- Steht die Budgetgrenze aus dem Transkript drin, die in der automatischen Zusammenfassung des Meetings fehlt?

Fehlt etwas davon: kein Beinbruch, dafür ist Schritt 6 da. Und falls du es sofort beheben willst: Sag deinem Agenten, was fehlt, und lass ihn den Skill anpassen, nicht den Brief. Den Brief flickst du nie von Hand — er entsteht morgen wieder neu. Und fällt dir etwas ganz anderes auf, das in den vier Fragen nicht vorkommt: gleicher Weg.

**Die Erkenntnis:** Kleinere Schritte mit gezieltem Kontext bringen bessere Ergebnisse — dieselbe Regel wie in Woche 1. Hat dein v3 mehr gefunden als v2, hast du sie gerade selbst erlebt. Hat schon v2 alles gefunden, liest dein Modell von sich aus gründlich — das Vorgehen im Skill sorgt dafür, dass es morgen wieder so ist.

```
─────────────────────────────────────
▶ weiter        — Schritt 6 (Optimierung)
⏭ überspringen  — Schritt 6, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 6 — Optimierung → v4

**Lernziel:** Du lernst, typische Fehler eines Daily Briefs zu erkennen — erst an einem fremden Beispiel, dann am eigenen — und stellst den Brief auf dein eigenes Format um.

Mika hat bis zum ersten Termin knapp vierzig Minuten — keine Zeit, einen Brief von oben nach unten durchzulesen und selbst zu sortieren, was zuerst dran ist. Genau das tut der eigene v3 vielleicht noch: Er zeigt viel — und lässt Mika sortieren.

**a) Ein fremdes Beispiel.** Lies dir `beispiele/brief-den-wir-nicht-wollen.md` durch — frag deinen Agenten danach, oder öffne die Datei selbst. Bevor du weiterliest: Was stört dich daran?

Sieben Dinge, an denen es hakt:

1. Chronologisch sortiert, nicht nach Wichtigkeit.
2. Newsletter und eine Jira-Benachrichtigung tauchen im Brief auf.
3. Die Frist steht als "Freitag" im Brief, nicht als "heute" — obwohl Roths Bitte weiter oben sogar zusammengefasst wurde. Zusammenfassen ist nicht Verstehen.
4. Der Terminkonflikt wird nirgends benannt.
5. Keine einzige Quellenangabe.
6. Doppelt so lang wie nötig.
7. Beraterton — "Sie sollten …" statt einer direkten Ansprache.

**b) Dein eigener Brief.** Halt deinen v3 dagegen: Was davon trifft auch auf deinen Brief zu? Änder das — und zwar, indem du das Ergebnis beschreibst, das du willst, nicht den Weg dahin. Das war schon in Woche 1 die Regel, und sie gilt hier genauso. Tippe genau das:

```
Ändere den Skill /dailybrief: "Heute wichtig" hat höchstens drei Punkte, und der ganze Brief passt auf eine Bildschirmseite. Newsletter und automatische Benachrichtigungen tauchen gar nicht auf.
```

**c) Mikas Format zu deinem machen.** Der Brief ist bis hierher in Mikas Format gehalten. Mach ihn zu deinem — ein Satz reicht. Ein paar Beispiele, wie so ein Satz klingen kann:

- "Termine zuerst, dann der Rest."
- "Fließtext statt Stichpunkte."
- "Duz mich."
- "Höchstens 150 Wörter."

Wähl eine dieser Vorgaben, mehrere, oder formuliere deinen eigenen Wunsch in einem Satz, und sag ihn deinem Agenten — genauso wie in b), als Änderung am Skill. Zum Beispiel:

```
Ändere den Skill /dailybrief: Termine zuerst, dann der Rest. Duz mich.
```

Jetzt der Testlauf. Tippe:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

**Die Erkenntnis:** Der Brief ist jetzt deiner. Jemand anders hätte ihn anders eingestellt — deshalb gibt es kein fertiges Produkt "Daily Brief", das für alle passt.

```
─────────────────────────────────────
▶ weiter        — Schritt 7 (Brief als Seite)
⏭ überspringen  — Schritt 7, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 7 — Der Brief als Seite zum Abhaken

**Lernziel:** Du machst aus dem Brief ein Werkzeug für den ganzen Tag, nicht nur einen Text, den du einmal liest. Das ist das Finale des Basis-Pfads — danach hast du einen kompletten eigenen Skill.

Noch einmal Frage 1 aus Schritt 2: Wie sieht ein gutes Ergebnis aus? Für Mika heißt das nicht nur "ein guter Text", sondern eine Seite, die über den ganzen Tag offen bleiben kann. Bisher ist der Brief eine Markdown-Datei — reiner Text mit einfachen Überschriften. Jetzt kommt eine HTML-Datei dazu: eine Webseite, die jeder Browser öffnet, auch ohne Internet. Tippe genau das:

```
Erweitere den Skill /dailybrief: Zusätzlich zur Markdown-Datei erzeugt er output/brief-<Datum>.html — eine einzelne HTML-Datei ohne externe Abhängigkeiten, die im Browser per Doppelklick aufgeht und auch am Handy lesbar ist.

Gleicher Inhalt wie der Markdown-Brief. Jeder Punkt unter "Heute wichtig", "Termine" und "Antworten und Entscheidungen" bekommt eine Checkbox zum Abhaken. Abgehakte Punkte bleiben abgehakt, auch wenn ich die Seite neu lade oder schließe (im Browser gespeichert, getrennt pro Datum). Oben steht, wie viele Punkte erledigt sind, zum Beispiel "3 von 8". Ein kleiner Link "Zurücksetzen" nimmt alle Häkchen weg. Schlicht und gut lesbar, keine Verzierungen.

Öffne die Datei nach dem Erzeugen im Browser.
```

Tippe:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

Öffnet sich die Seite nicht von selbst: Doppelklick auf `output/brief-….html`. Hak zwei Punkte ab und lade die Seite neu. Bleiben die Häkchen? Wenn nicht, sag es deinem Agenten — "Die Häkchen verschwinden beim Neuladen" — und lass ihn die Speicherung im Skill nachbessern. Stört dich etwas anderes an der Seite — zu eng, zu bunt, falsche Reihenfolge —: gleicher Weg, ein Satz an deinen Agenten.

**Die Erkenntnis:** Das Format ist Teil des Ergebnisses. Derselbe Skill, dieselben Daten — aber erst als Seite wird der Brief zum Werkzeug für den Tag, nicht nur zum Text, den du einmal liest. Ab jetzt hast du einen kompletten Skill `/dailybrief`.

```
─────────────────────────────────────
▶ weiter        — Schritt 8 (Echte Daten)
⏭ überspringen  — Schritt 8, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 8 — Wo die Daten in echt herkommen

**Lernziel:** Du kennst drei Wege, `input/` mit echten Daten statt mit Mikas Beispieldaten zu füllen — und weißt, was sich dabei am Skill ändert und was nicht.

Kein Prompt in diesem Schritt, nur drei Wege, wie `input/` in Wirklichkeit gefüllt würde:

1. **Export von Hand.** Du exportierst Mail, Kalender und Slack selbst als Datei und legst sie in `input/` ab — genau wie hier im Kurs. Am Skill ändert sich nichts.
2. **Konnektoren.** Eine Verbindung, über die dein Agent Postfach, Kalender oder Slack direkt lesen darf — je nach Werkzeug heißt sie "Connector", "MCP-Server" oder "Extension", gemeint ist immer dasselbe. Am Skill ändert sich dann nur der Schritt "Sichten": Statt "lies input/" heißt es zum Beispiel "hol die E-Mails seit gestern 18 Uhr".
3. **Zeitplan.** Der Skill läuft jeden Morgen um 7:30 von selbst, ohne dass du ihn aufrufst.

Ob (2) und (3) bei dir überhaupt gehen, entscheidet deine IT — deshalb bleibt es hier bei der Erklärung. Und in jedem Fall gilt: nur lesen, nie schreiben. Ein Daily Brief, der dein Postfach verändern könnte, ist ein anderes Werkzeug als das hier.

**Die Erkenntnis:** Format, Kontext und Vorgehen bleiben gleich — nur die Quelle wechselt.

Jetzt zwei Wege: Willst du weiter, wie es Fortgeschrittene tun — eine zweite Optimierungsstufe, bei der Kritik nicht mehr den Skill selbst ändert? Oder reicht dir, was du hast, und du springst direkt zur Standortbestimmung?

```
─────────────────────────────────────
▶ weiter        — Schritt 9 (Fortgeschritten: Feedback-Schleife)
⏭ überspringen  — Schritt 10 (Fortgeschrittenen-Schritt auslassen)
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 9 — Fortgeschritten: Die Feedback-Schleife

**Lernziel:** Du trennst Geschmack von Vorgehen — Vorlieben wandern aus dem Skill in eine eigene, wachsende Datei, ein zweiter kleiner Skill pflegt nur diese Datei, und `/dailybrief` selbst bleibt unangetastet.

In Schritt 6 hast du bei jeder Kritik den Skill selbst geändert. Das geht eine Weile gut — aber nach zehn solchen Änderungen weiß niemand mehr, was am Skill Vorgehen ist und was nur Geschmack war. Die zweite Optimierungsstufe trennt beides: Vorlieben raus aus dem Skill, rein in eine Datei, die mit jedem Feedback wächst.

**Bist du gerade erst mit "ab Schritt 9" eingestiegen?** Dann existiert `/dailybrief` bei dir noch nicht. Ein einziger Prompt — das Sprungbrett — legt ihn komplett an — Format, Kontext, Vorgehen und die HTML-Seite aus den Schritten 3 bis 7 in einem Stück. Tippe genau das:

```
Erstelle einen Skill /dailybrief. Lege ihn an unter .claude/skills/dailybrief/SKILL.md, mit Name und Beschreibung im Kopf.

Der Skill schreibt einen Daily Brief für Mika. Dafür liest er alle Dateien in input/. Der Brief hat genau diese Abschnitte, in dieser Reihenfolge:

## Heute wichtig
Die drei Dinge, die heute zuerst Aufmerksamkeit brauchen — je ein Satz mit Begründung.

## Termine
Alle Termine des Tages mit Uhrzeit. Bei jedem: Was muss vorher vorbereitet sein?

## Antworten und Entscheidungen
Wer wartet auf Mika, und worauf? Mit Frist, wenn es eine gibt.

## Kann warten
Was heute keine Aufmerksamkeit braucht — eine Zeile pro Punkt.

Bevor er den Brief schreibt, liest er context/mika.md (wer Mika ist, woran Mika gerade arbeitet, was Mika wichtig ist) und context/team.md (wer die Leute in den Nachrichten sind). Was dort steht, entscheidet, was unter "Heute wichtig" landet und was unter "Kann warten".

Das Datum von heute steht im Kopf von input/kalender.md. Nimm dieses Datum, nicht das echte.

Jede Aussage im Brief nennt in Klammern ihre Quelle, zum Beispiel (E-Mail Peter Hartmann, 07:52) oder (Slack #projektteam, gestern 16:10). Nichts in den Brief schreiben, was nicht in input/ steht.

Ein festes Vorgehen in drei Schritten, bevor er den Brief schreibt:

1. Sichten: Geh jede Quelle in input/ einzeln durch — Kalender, E-Mails, Slack, Meeting-Notizen — und notiere für dich, was davon Mika heute betrifft und was nicht.
2. Abgleichen: Prüfe die Quellen gegeneinander. Überschneiden sich Termine? Hat sich eine Frist verschoben, die in einer Mail oder in Slack steht? Gibt es Termine ohne Vorbereitung oder ohne Agenda? Was aus den Meeting-Notizen von gestern ist heute fällig?
3. Schreiben: Erst jetzt den Brief im festgelegten Format.

Die Schritte 1 und 2 zeigst du nicht im Chat — nur den fertigen Brief.

"Heute wichtig" hat höchstens drei Punkte, und der ganze Brief passt auf eine Bildschirmseite. Newsletter und automatische Benachrichtigungen tauchen gar nicht auf.

Zusätzlich zur Markdown-Datei erzeugt er output/brief-<Datum>.html — eine einzelne HTML-Datei ohne externe Abhängigkeiten, die im Browser per Doppelklick aufgeht und auch am Handy lesbar ist.

Gleicher Inhalt wie der Markdown-Brief. Jeder Punkt unter "Heute wichtig", "Termine" und "Antworten und Entscheidungen" bekommt eine Checkbox zum Abhaken. Abgehakte Punkte bleiben abgehakt, auch wenn ich die Seite neu lade oder schließe (im Browser gespeichert, getrennt pro Datum). Oben steht, wie viele Punkte erledigt sind, zum Beispiel "3 von 8". Ein kleiner Link "Zurücksetzen" nimmt alle Häkchen weg. Schlicht und gut lesbar, keine Verzierungen.

Speichere den Brief als output/brief-<Datum>.md und zeig ihn danach im Chat. Existiert die Datei schon, hänge -2, -3 usw. an den Namen. Öffne die HTML-Datei nach dem Erzeugen im Browser.
```

**Schon seit Schritt 1 dabei?** Dann hast du das alles schon — `/dailybrief` steht bei dir bereits in der v4-Fassung aus Schritt 7. Weiter geht's direkt mit a).

**a)** Die Vorlieben ziehen in eine eigene Datei um. Tippe genau das:

```
Erweitere den Skill /dailybrief: Er liest zusätzlich context/vorlieben.md — falls die Datei fehlt, lege sie an mit den Zeilen "Länge:", "Reihenfolge:", "Ton:", "Form:" und sinnvollen Startwerten. Länge, Reihenfolge, Ton und Form des Briefs richten sich nach dieser Datei. Was dort steht, schlägt die Vorgaben im Skill.
```

**b)** Ein zweiter, kleiner Skill pflegt diese Datei — und lässt `/dailybrief` dabei in Ruhe. Tippe genau das:

```
Erstelle einen Skill /brief-feedback. Lege ihn an unter .claude/skills/brief-feedback/SKILL.md, mit Name und Beschreibung im Kopf. Er bekommt im Aufruf meine Kritik am letzten Brief in normalen Sätzen. Er übersetzt die Kritik in Regeln und trägt sie in context/vorlieben.md ein — bestehende Regeln ergänzen oder ersetzen, nichts doppelt. Er ändert nie den Skill /dailybrief selbst. Zum Schluss zeigt er mir die neue Fassung von context/vorlieben.md.
```

**c)** Testen. Tippe genau das:

```
/brief-feedback Zu lang. Ich will die Termine zuerst sehen, dann erst den Rest. Newsletter nie erwähnen, auch nicht unter "Kann warten".
```

Dann:

```
/dailybrief
```

*Falls dein Werkzeug den Skill nicht anbietet: „Lies .claude/skills/dailybrief/SKILL.md und tu, was drinsteht."*

Du bekommst einen neuen Brief, als Markdown und als Seite. Öffne danach `context/vorlieben.md` und schau, was dort steht. Und wirf einen Blick in `.claude/skills/dailybrief/SKILL.md`: Sie sollte unverändert sein. Hat dein Agent sie doch angefasst, sag ihm, dass `/brief-feedback` nur die Vorlieben-Datei ändern darf, und lass ihn die Änderung zurücknehmen. Und alles, was dir am neuen Brief nicht gefällt, geht ab jetzt über `/brief-feedback` — nicht mehr über den Skill.

**Die Erkenntnis:** Der Skill `/dailybrief` hat sich nicht geändert — die Datei daneben schon. Nach zehn Tagen Feedback ist der Skill noch derselbe, und der Brief ist trotzdem deiner. Und du siehst jede Änderung, nichts passiert unsichtbar im Hintergrund.

**Für ganz Fortgeschrittene:** Nicht jede Kritik ist Geschmack. "Prüfe immer auf Terminkonflikte" gehört eigentlich ins Vorgehen, nicht in `context/vorlieben.md`. Willst du weiter gehen: Erweitere `/brief-feedback` so, dass er am Ende vorschlägt — nicht selbst ändert —, wenn eine Regel eher in den Skill `/dailybrief` gehört als in die Vorlieben-Datei.

```
─────────────────────────────────────
▶ weiter        — Schritt 10 (Wo stehst du?)
⏭ überspringen  — Schritt 10, ohne die Übung
⏹ stop          — Kurs unterbrechen
─────────────────────────────────────
```

---

### SCHRITT 10 — Wo stehst du?

**Lernziel:** Du überträgst, was du gebaut hast, auf deine eigene Arbeit — mit einem konkreten nächsten Schritt.

Drei Fragen — nimm dir wirklich einen Moment dafür:

1. **Welche Quellen** hätte dein eigener, echter Daily Brief? Postfach, Kalender, welche Chat-Kanäle?
2. **Welche davon darfst du anbinden** — als Export von Hand, über einen Konnektor, oder gar nicht?
3. **Was ist dein nächster Schritt** von da aus — genau einer, nicht drei?

Die Brücke zur eigenen Nutzung, ganz konkret:

- Kopiere `context/mika.md` zu `context/ich.md` und füll es mit deinen eigenen Angaben.
- Leg deine eigenen Exporte nach `input/`.
- Sag deinem Agenten:

```
Ändere den Skill: lies context/ich.md statt context/mika.md
```

- Morgen früh: `/dailybrief`.

Schreib deinen nächsten Schritt auf — hier in den Chat oder auf einen Zettel — und bring ihn mit in den nächsten Call.

```
─────────────────────────────────────
⏹ Kurs abschließen
─────────────────────────────────────
```

---

## Kursabschluss

Wenn der Teilnehmer "stop" sagt oder alle Schritte abgeschlossen hat, schreibe folgendes:

---

**Kurs abgeschlossen — oder unterbrochen. Beides ist gut.**

Du kannst jederzeit wieder einsteigen:

```
Starte den Kurs ab Schritt [Nummer]
```

Wenn du alle Schritte gemacht hast:

**Glückwunsch — dein Daily Brief steht.**

Du hast heute für Mika ein eigenes System gebaut, kein einzelnes Ergebnis:

- Wie ein einzelner Prompt schon ein erstes, brauchbares Ergebnis liefert
- Wie Format, Kontext und ein festes Vorgehen aus einer groben Antwort einen verlässlichen Brief machen
- Wie du typische Fehler erkennst — erst an einem fremden Beispiel, dann am eigenen — und den Brief auf dein Format bringst
- Wie derselbe Inhalt als Seite zum Abhaken zum Werkzeug für den ganzen Tag wird
- Wie Geschmack und Vorgehen getrennt bleiben, wenn Kritik in eine wachsende Datei wandert statt in den Skill selbst

> **Format, Kontext, Vorgehen — der Brief ist ein System, kein Prompt.**

Bis zum nächsten Call.
