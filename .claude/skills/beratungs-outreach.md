---
name: beratungs-outreach
description: Schreibt personalisierte, fundierte Erst-Nachrichten an Partner und Führungskräfte von Beratungsunternehmen (McKinsey, BCG, Bain, Roland Berger, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman etc.). Jede Nachricht folgt dem Aufbau Hook → substanzielle fachliche Frage/Anregung → Call-to-Action (30-Min-Call). Nutze diesen Skill immer, wenn der Nutzer Outreach-, Akquise-, Kontakt- oder Anschreibe-Nachrichten an Berater/Partner verfassen will, eine Kontaktliste (CSV/Spreadsheet mit Namen, Firma, LinkedIn) mitbringt und um "Nachrichten", "Anschreiben", "Cold Outreach", "Erstansprache" oder "Feedback-Mail" zu einer Studie/Präsentation/einem LinkedIn-Post bittet — auch wenn das Wort "Skill" nicht fällt. Der Skill recherchiert per WebSearch/WebFetch die öffentliche Arbeit der Zielperson und entwirft assistierte Vorschläge, die der Nutzer final nachschärft.
---

# Beratungs-Outreach

## Zweck

Dieser Skill hilft dabei, personalisierte Erst-Nachrichten an Partner/Führungskräfte großer Beratungen zu schreiben. Das Ziel ist nicht Masse, sondern dass jede einzelne Nachricht wie **ehrliches, fachlich fundiertes Interesse** wirkt — nicht wie Cold-Mass-Outreach. Der entscheidende Hebel dafür ist ein konkreter, belegter fachlicher Bezug zur Arbeit der Zielperson.

Der Skill arbeitet **assistiert**: Er recherchiert und entwirft, aber der Nutzer prüft den fachlichen Kern und schärft ihn nach, bevor die Nachricht rausgeht. Das ist bewusst so — der substanzielle Mittelteil entscheidet über Erfolg oder Misserfolg, und ein Mensch mit Domänenwissen fängt Ungenauigkeiten ab, die eine vollautomatische Nachricht generisch oder falsch wirken lassen würde.

## Der Nachrichtenaufbau

Jede Nachricht hat **drei Teile**, immer in dieser Reihenfolge:

**1. Hook — die Verbindung.** Ein konkreter Aufhänger, warum du dich meldest. Am besten ein Bezug zu einer *spezifischen, öffentlich sichtbaren Arbeit* der Person: eine Studie/Report, eine Präsentation, ein Vortrag, ein Whitepaper, eine Projektreferenz auf der Firmenwebseite oder ein LinkedIn-Post. Der Hook zeigt: „Ich habe mich wirklich mit deiner Arbeit beschäftigt." Generische Hooks („Ich bin auf Ihr Profil gestoßen") sind schwach und zu vermeiden.

**2. Substanzielle Frage / Anregung — der Kern.** Hier liegt die Arbeit. Eine oder zwei *konkrete, fachlich durchdachte* Anmerkungen, Fragen oder Ergänzungen zum Thema der Person. Das muss echten Gehalt haben: eine spezifische Ergänzung, ein belegtes Beispiel, eine differenzierte Rückfrage. Vage Komplimente („sehr spannende Arbeit") allein reichen nicht — sie dürfen den Einstieg bilden, aber der Kern braucht Fleisch. Wenn die Person ausdrücklich um Feedback bittet (z.B. am Ende eines Reports), ist das der stärkste denkbare Anker — dann direkt daran anknüpfen.

**3. Call-to-Action — der Abschluss.** Eine niederschwellige, konkrete Einladung zum Gespräch: der Wunsch, sich kurz auszutauschen, idealerweise ein 30-minütiger Call. Freundlich, ohne Druck, mit offener Terminfrage („Wann würde es dir passen?" / „Hättest du in den nächsten zwei Wochen 30 Minuten?").

## Stil und Ton

Orientiere dich eng an der Referenznachricht in `.claude/skills/beratungs-outreach/assets/referenznachricht.md`. Kernmerkmale:

- **Deutsch, per Du**, sofern der Nutzer nichts anderes vorgibt. (Bei sehr formellen Kontexten oder auf Wunsch: Sie-Form — frag im Zweifel den Nutzer.)
- **Warm und respektvoll**, aber auf Augenhöhe — nicht anbiedernd, nicht unterwürfig.
- **Präzise und konkret** statt schwammig. Konkrete Beispiele, Zahlen, Eigennamen schlagen Allgemeinplätze.
- **Kompakt.** Eine gute Nachricht ist so kurz wie möglich und so lang wie nötig. Der fachliche Kern darf Raum bekommen, der Rest bleibt knapp.
- **Kein Marketing-Sprech, keine Buzzwords, keine Superlative.** Ehrlich und sachlich.
- Anrede mit Vornamen, Abschluss mit „Viele Grüße" + Absendername (aus den Nutzer-Angaben).

## Ablauf

### Schritt 1 — Kontaktliste einlesen

Der Nutzer liefert eine Liste als Datei (CSV/XLSX) im Arbeitsverzeichnis oder nennt den Pfad. Lies sie ein (bei CSV direkt; bei XLSX ggf. mit einem kurzen Python/pandas-Snippet). Erwartete Spalten (siehe Vorlage `.claude/skills/beratungs-outreach/assets/kontaktliste_vorlage.csv`):

- `name` — Voller Name der Zielperson (Pflicht)
- `beratung` — Firma (Pflicht)
- `rolle` — z.B. Partner, Principal, Senior Partner (optional, hilft beim Ton)
- `thema_oder_link` — Konkreter Aufhänger: URL zu Studie/Report/LinkedIn-Post, oder Themen-Stichwort (sehr empfohlen — je konkreter, desto besser die Nachricht)
- `notizen` — Freitext des Nutzers: eigene fachliche Andockpunkte, persönliche Verbindung, gewünschte Stoßrichtung (optional, aber sehr wertvoll)

Wenn die Liste fehlende Pflichtfelder hat, weise darauf hin, statt zu raten. Fehlt `thema_oder_link`, ist Recherche in Schritt 2 nötig — sag dazu, dass die Trefferqualität dann stärker schwankt.

### Schritt 2 — Recherche pro Kontakt

Ziel: einen **konkreten, belegbaren Aufhänger** und genug fachlichen Kontext finden, um eine substanzielle Anmerkung zu formulieren. Nutze `WebSearch` und `WebFetch`. Recherchiere in dieser Reihenfolge (stoppe, sobald du genug Substanz hast):

1. **Wenn ein Link/Thema angegeben ist:** Zuerst dort ansetzen. `WebFetch` auf die Studie/den Report/die Seite und lies Kernaussagen, Methodik, Indikatoren, Grenzen — und ob explizit um Feedback gebeten wird.
2. **Publikationen der Beratung:** `WebSearch` nach Reports, Studien, Artikeln, in denen die Person als Autor/Co-Autor auftaucht. Beratungswebseiten (mckinsey.com/insights, bcg.com/publications etc.) sind gut zugänglich.
3. **Profilseite auf der Firmenwebseite:** Rolle, Fokusthemen, Branchen, genannte Projekte.
4. **LinkedIn-Posts:** Nur nutzbar, wenn der Nutzer den Post-Link oder den Text mitgeliefert hat. LinkedIn lässt sich **nicht** zuverlässig/automatisiert auslesen — versuche kein Scraping und keine Umgehung. Wenn nur ein Profilname vorliegt, verlasse dich auf öffentlich auffindbare Beiträge über die Websuche und markiere Unsicherheit.

Halte pro Kontakt fest: **Was ist der Aufhänger, und woher stammt er (Quelle/URL)?** Diese Quelle kommt später in den Entwurf, damit der Nutzer sie prüfen kann.

Wenn du keinen tragfähigen fachlichen Anker findest, erfinde keinen. Sag es offen und schlage vor, dass der Nutzer einen Anker beisteuert oder den Kontakt zurückstellt.

### Schritt 3 — Entwurf schreiben (assistiert)

Schreibe pro Kontakt einen Nachrichtenentwurf nach dem Drei-Teile-Aufbau. Dabei gilt:

- **Der fachliche Kern muss mindestens eine konkrete, belegte Anmerkung enthalten.** Lieber eine starke, präzise Anregung als drei schwammige.
- **Nichts erfinden.** Wenn du eine Aussage über den Report/das Thema machst, muss sie durch die Recherche gedeckt sein. Bist du dir bei einem fachlichen Punkt unsicher, formuliere ihn als offene Frage („Habt ihr X bewusst ausgeklammert, oder …?") statt als Behauptung — das ist ehrlicher und einladender.
- **Passe Länge und Tiefe an den Anker an.** Ein feedback-suchender Report verträgt zwei ausgearbeitete Punkte (wie in der Referenz); ein LinkedIn-Post eher eine prägnante Rückfrage.

### Schritt 4 — Ergebnis ausgeben

Weil der Modus **assistiert** ist, gib pro Kontakt nicht nur den Text aus, sondern auch das, was der Nutzer zum Nachschärfen braucht. Schreibe das Ergebnis in eine Datei im Arbeitsverzeichnis, z.B. `outreach-entwuerfe.md` (bei vielen Kontakten zusätzlich eine `outreach-entwuerfe.csv` mit Spalten `name,beratung,entwurf,quelle,pruefpunkte` anbieten). Nutze pro Kontakt dieses Format:

```
### [Name] — [Beratung]

**Aufhänger:** [1 Satz, worauf sich die Nachricht bezieht]
**Quelle:** [URL oder woher der Bezug stammt]

**Entwurf:**
[Die vollständige Nachricht, sendefertig formuliert]

**⚠️ Bitte prüfen:** [Die fachlichen Aussagen, bei denen der Nutzer mit seinem Domänenwissen gegenchecken sollte — z.B. „Aussage zur CO₂-Bilanz von Biokraftstoffen stammt aus Recherche, bitte fachlich verifizieren." Wenn nichts Kritisches: „Keine kritischen Punkte."]
```

## Wichtige Prinzipien

- **Qualität vor Menge.** Fünf wirklich fundierte Nachrichten schlagen fünfzig generische. Wenn die Recherche für einen Kontakt dünn bleibt, ist es besser, das zu sagen, als die Nachricht mit Floskeln zu füllen.
- **Der Nutzer ist die fachliche Instanz.** Der Skill entwirft, der Nutzer verantwortet. Deshalb immer die Prüfpunkte ausweisen — versteck fachliche Unsicherheit nicht in glattem Text.
- **Ehrlich bleiben.** Keine erfundenen Bezüge, keine gefakten Zitate, keine behauptete persönliche Verbindung, die es nicht gibt. Das fliegt auf und verbrennt den Kontakt.

## Referenzdateien

- `.claude/skills/beratungs-outreach/assets/referenznachricht.md` — Die vom Nutzer gelieferte Musternachricht (McKinsey Energiewende-Index). Maßstab für Ton, Aufbau und fachliche Tiefe.
- `.claude/skills/beratungs-outreach/assets/kontaktliste_vorlage.csv` — Vorlage für die Eingabeliste.
