## Zukünftige mögliche Erweiterungen:
- In Thesaurus existieren auch zusammengesetzte Wörter mit Attributen (Bsp.: "in Handeln übersetzen")

- Integration von Uhrzeit (hh:mm) zu Hochdeutsch / Formal?
- (Pluspunkte / Minuspunkte) statt (Pluspunte - Minuspunkte)?
- Innovative Wörter für die Kategorie "Innovativ filtern" (IDF)

- Fallen dir weitere Ausnahmen ein? Definiere bitte Regeln dafür.
- Vorschlag: Fokussier dich erstmal nur auf die Unterscheidung informell ("plauderhaft") vs. formell ("hochdeutsch") und verfeinere sie soweit, dass du die Ergebnisse selber interpretierbar findest.
- Nutze gerne folgenden Datensatz als Benchmark (Ziel ist es mindest Spearman > 0.6 zu erreichen): https://github.com/ee-2/in_formal_sentences/blob/master/in_formal_sentences.tsv
- Schau dir auch gerne die zugehörige Publikation an: https://aclanthology.org/2023.findings-eacl.42.pdf (Transformer Modelle und sonstige KI-Modelle sind aber für die Aufgabe verboten ;)


_________________________________________________________________________________________________________

Done (19.11.):
- Normalisierung des Scores über Länge des Satzes (längere Sätze hatten davor automatisch höheren Score)
 
- Angepasste Tokenisierung nach Satzzeichen
- Trennung von Pronomen in informell / formell: .lower() spielt hier eine Rolle: du/dein, Sie/Ihr.
    - Ein Pronomen am Satzanfang wird zwar erkannt, aber nicht gewertet.
- Neue Hilfsmerkmale, die selber in openthesaurus.txt nicht vorkommen: Formelle_Pronomen, Informelle Pronomen, Satzzeichen, Interjektionen, Verkürzungen, Neologismen
- Regelerweiterungen für Plauderhaft(Informelle_Pronomen, Satzzeichen, Interjektionen, Verkürzungen, Neologismen) und Hochdeutsch(Formelle_Pronomen, Substantivierung, geh., wissenschaftlich, juristisch, Amtsdeutsch)
- Final Scores gerundet