---
name: dailybrief
description: Nutze diesen Skill, wenn ein Daily Brief für Mika erstellt werden soll, der Kalender, E-Mails, Slack-Nachrichten und Meeting-Notizen aus input/ auswertet und zu einer priorisierten Übersicht für den Tag zusammenfasst.
---

Du schreibst den Daily Brief für Mika. Dafür liest du alle Dateien in `input/`, einschließlich der Meeting-Notizen in `input/meetings/`.

## Vorgehen

1. Lies `context/mika.md` (wer Mika ist, woran Mika gerade arbeitet, was zählt und was nicht) und `context/team.md` (wer die Leute in den Nachrichten sind). Lies außerdem `context/vorlieben.md`; falls die Datei fehlt, lege sie an mit den Zeilen „Länge:", „Reihenfolge:", „Ton:", „Form:" und diesen Startwerten: Länge: passt auf eine Bildschirmseite · Reihenfolge: Heute wichtig, Termine, Antworten und Entscheidungen, Kann warten · Ton: sachlich, neutral · Form: kurze Absätze mit Stichpunkten. Was in `context/vorlieben.md` steht, schlägt die Vorgaben in diesem Skill.
2. Das Datum von heute steht im Kopf von `input/kalender.md`. Nimm dieses Datum, nicht das echte — es entscheidet, welche Termine, Fristen und Nachrichten „heute" betreffen.
3. Sichten: Geh jede Quelle in `input/` einzeln durch — Kalender, E-Mails, Slack, Meeting-Notizen — und notiere für dich, was davon Mika heute betrifft und was nicht. Was in `context/mika.md` und `context/team.md` steht, entscheidet, was unter „Heute wichtig" landet und was unter „Kann warten".
4. Abgleichen: Prüfe die Quellen gegeneinander. Überschneiden sich Termine? Hat sich eine Frist verschoben, die nur in einer Mail oder in Slack steht? Gibt es Termine ohne Vorbereitung oder ohne Agenda? Was aus den Meeting-Notizen von gestern ist heute fällig? Bei Aufzeichnungen zählt das Transkript, nicht nur die automatische Zusammenfassung — die Zusammenfassung kann Details auslassen, die nur im Transkript stehen.
5. Schreiben: Erst jetzt den Brief, im Format weiter unten und mit den Werten aus `context/vorlieben.md`. Die Schritte 3 und 4 zeigst du nicht im Chat — nur den fertigen Brief.

## Format des Briefs

Genau diese Abschnitte, in dieser Reihenfolge — außer `context/vorlieben.md` gibt unter „Reihenfolge:" eine andere Reihenfolge vor, dann gilt diese:

## Heute wichtig
Höchstens drei Punkte, je ein Satz mit Begründung — die Dinge, die heute zuerst Aufmerksamkeit brauchen.

## Termine
Alle Termine des Tages mit Uhrzeit. Bei jedem: was vorher vorbereitet sein muss. Überschneidungen werden ausdrücklich benannt.

## Antworten und Entscheidungen
Wer wartet auf Mika, und worauf? Mit Frist, wenn es eine gibt.

## Kann warten
Was heute keine Aufmerksamkeit braucht — eine Zeile pro Punkt.

Der ganze Brief passt auf eine Bildschirmseite. Newsletter und automatische Benachrichtigungen tauchen gar nicht auf.

## Regeln

Jede Aussage im Brief nennt in Klammern ihre Quelle, zum Beispiel „(E-Mail Peter Hartmann, 07:52)", „(Slack #projektteam, gestern 16:10)" oder „(Transkript LogiTrans, 00:21:40)". Schreib nichts in den Brief, was nicht in `input/` steht. Fehlt etwas — ein Anhang, der nicht exportiert wurde, eine Sprachnachricht ohne Text —, benenne das, statt es zu erfinden.

## Speichern

Speichere den Brief als Markdown unter `output/brief-<Datum>.md`, Datum im Format JJJJ-MM-TT (zum Beispiel `output/brief-2025-03-18.md`). Existiert die Datei schon, hänge `-2`, `-3` usw. an den Dateinamen an. Erzeuge zusätzlich `output/brief-<Datum>.html` mit derselben Nummer und demselben Inhalt (zum Beispiel `brief-2025-03-18-2.html`, wenn der Markdown-Brief als `brief-2025-03-18-2.md` gespeichert wurde).

Zeig danach den Markdown-Brief im Chat und öffne die HTML-Datei im Browser. Kannst du keine Datei im Browser öffnen, nenne stattdessen den Pfad der HTML-Datei und weise auf Doppelklick zum Öffnen hin.

## HTML-Seite

Eine einzelne Datei ohne externe Abhängigkeiten — kein CDN, keine externen Schriften, kein Framework. Am Handy lesbar (viewport-Meta, max-width, Systemschrift), gleicher Inhalt wie der Markdown-Brief. Jeder Punkt unter „Heute wichtig", „Termine" und „Antworten und Entscheidungen" ist eine Checkbox-Zeile; „Kann warten" bleibt ohne Checkboxen. Abgehakte Punkte bleiben abgehakt, auch nach Neuladen oder Schließen — gespeichert im Browser (`localStorage`) unter einem Schlüssel, der das Datum enthält, damit ein anderer Tag frisch startet. Oben steht ein Zähler wie „3 von 8 erledigt", der sich sofort aktualisiert. Ein kleiner Link „Zurücksetzen" nimmt alle Häkchen weg. Schlicht, keine Verzierungen.

Nutze exakt diese Vorlage. Ersetze nur die Platzhalter (`{{...}}`), lass Struktur, CSS und JavaScript unverändert, damit die Seite bei jedem Lauf gleich aussieht und funktioniert:

```html
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Daily Brief {{DATUM}}</title>
<style>
body{font-family:-apple-system,"Segoe UI",Roboto,sans-serif;max-width:640px;margin:0 auto;padding:16px 20px 40px;line-height:1.5;color:#1a1a1a}
h1{font-size:1.3em;margin:0 0 4px}
h2{font-size:1.05em;margin-top:1.6em;border-bottom:1px solid #ddd;padding-bottom:4px}
#zaehler{color:#555;margin:0 0 1.2em}
.item{display:block;padding:7px 0;border-bottom:1px solid #eee;cursor:pointer}
.item input{margin-right:8px}
.item.done span{text-decoration:line-through;color:#888}
.warten{padding:5px 0;color:#333}
#reset{font-size:.85em;color:#555}
</style>
</head>
<body>
<h1>Daily Brief {{DATUM}}</h1>
<p id="zaehler"></p>

<h2>Heute wichtig</h2>
{{HEUTE_WICHTIG_ITEMS}}

<h2>Termine</h2>
{{TERMINE_ITEMS}}

<h2>Antworten und Entscheidungen</h2>
{{ANTWORTEN_ITEMS}}

<h2>Kann warten</h2>
{{KANN_WARTEN_ITEMS}}

<p><a href="#" id="reset">Zurücksetzen</a></p>

<script>
var KEY = "dailybrief-{{DATUM}}";
var boxes = Array.prototype.slice.call(document.querySelectorAll('.item input[type=checkbox]'));
function zaehlen(){
  var n = boxes.filter(function(b){return b.checked}).length;
  document.getElementById('zaehler').textContent = n + " von " + boxes.length + " erledigt";
}
function speichern(){
  var done = boxes.filter(function(b){return b.checked}).map(function(b){return b.dataset.id});
  localStorage.setItem(KEY, JSON.stringify(done));
}
function laden(){
  var done = [];
  try { done = JSON.parse(localStorage.getItem(KEY) || "[]"); } catch(e) {}
  boxes.forEach(function(b){
    b.checked = done.indexOf(b.dataset.id) !== -1;
    b.closest('.item').classList.toggle('done', b.checked);
  });
  zaehlen();
}
boxes.forEach(function(b){
  b.addEventListener('change', function(){
    b.closest('.item').classList.toggle('done', b.checked);
    speichern(); zaehlen();
  });
});
document.getElementById('reset').addEventListener('click', function(e){
  e.preventDefault();
  boxes.forEach(function(b){ b.checked = false; b.closest('.item').classList.remove('done'); });
  localStorage.removeItem(KEY);
  zaehlen();
});
laden();
</script>
</body>
</html>
```

`{{DATUM}}` wird überall durch denselben Wert ersetzt — das Datum aus dem Kopf von `input/kalender.md` im Format JJJJ-MM-TT —, damit Titel und Speicherschlüssel zusammenpassen. Gibt `context/vorlieben.md` unter „Reihenfolge:" eine andere Reihenfolge vor, ordne die vier `<h2>`-Blöcke samt ihren Zeilen entsprechend um — CSS und JavaScript bleiben unverändert.

Jeder Punkt unter „Heute wichtig", „Termine" und „Antworten und Entscheidungen" wird zu einer Zeile

```html
<label class="item"><input type="checkbox" data-id="EINDEUTIGE-ID"><span>Text (Quelle)</span></label>
```

mit einer über die Seite eindeutigen `data-id` — zum Beispiel `hw-1`, `hw-2` für „Heute wichtig", `t-1`, `t-2` für „Termine", `ae-1`, `ae-2` für „Antworten und Entscheidungen". Setze `{{HEUTE_WICHTIG_ITEMS}}`, `{{TERMINE_ITEMS}}` und `{{ANTWORTEN_ITEMS}}` aus so vielen dieser Zeilen zusammen, wie der Brief in dem jeweiligen Abschnitt Punkte hat.

Jeder Punkt unter „Kann warten" wird zu einer Zeile ohne Checkbox:

```html
<div class="warten">Text (Quelle)</div>
```

Setze `{{KANN_WARTEN_ITEMS}}` aus so vielen dieser Zeilen zusammen, wie der Brief unter „Kann warten" Punkte hat.
