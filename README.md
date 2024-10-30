# Extraktion stilistischer Merkmale in Texten

## Projektübersicht

Dieses Projekt zielt darauf ab, stilistische Merkmale in Texten zu extrahieren und diese Merkmale anhand eines Regelwerks und einer Vektorisierungsmethode zu analysieren. Dabei wurden zwei Ansätze verfolgt:

1. **Regelbasierte Merkmalsextraktion**: Merkmale werden auf Basis von Attributen abgeleitet, die aus einem (Open)Thesaurus stammen.
2. **Vektorisierung mit TF-IDF und Berechnung von Cosinus-Ähnlichkeiten**: Ähnlichkeit zwischen Texten wird durch Vektorisierung und Ähnlichkeitsberechnungen analysiert, um stilistisch ähnliche Bücher ohne kategorische Zuordnung zu finden.

## Aufgabenstellung

### Ziel
Im Rahmen der Hörbuchinhalte sollen nicht nur semantische, sondern auch stilistische Merkmale extrahiert werden, die dem Zuhörer ein besseres Verständnis der Sprach- und Stilmittel vermitteln können.

### Anforderungen
1. Regelbasierte Extraktion stilistischer Merkmale:
   - Implementierung eines Regelwerks zur Klassifizierung von Merkmalen (gleichgewichtet).
   - Das Regelwerk basiert auf Attributen aus einem Thesaurus und kann flexibel angepasst werden.
   - Evaluierung anhand eines kleinen Textkorpus (ca. 10 Beispiele pro Merkmal) mit explorativer Sortierung nach Stärke des Merkmals.

2. Vektorisierung und Ähnlichkeitsanalyse:
   - Vektorisierung der Texte mittels TF-IDF.
   - Berechnung der Cosinus-Ähnlichkeit zwischen den Texten, um stilistisch ähnliche Bücher zu identifizieren, ohne Kategorien festzulegen.

## Implementierung

### 1. Regelbasierte Merkmalsextraktion

#### Ziel
Mit dem regelbasierten Ansatz werden stilistische Merkmale extrahiert, die bestimmte Stile und Sprachmuster kennzeichnen. Jedes Wort wird mit spezifischen Attributen versehen und abhängig vom Thesaurus in eine Kategorie eingeordnet.

#### Schritte
1. **Parsing des Thesaurus**:
   - Eingelesen wird eine Datei, die Synonyme und stilistische Attribute enthält. Wörter mit und ohne Attribute werden getrennt erfasst.
   
2. **Regelwerk**:
   - Das Regelwerk in `regelbasierte_suche.json` definiert positive und negative Attribute für jede Kategorie, z.B. "Plauderhaft", "Scherzhaft".
   
3. **Scoring und Sortierung**:
   - Ein Scoring-System analysiert die Satzstärke je Kategorie und sortiert Sätze von stärkstem bis schwächstem Vertreter.

#### Ergebnisse
Die Ergebnisse werden in einer JSON-Datei gespeichert und bieten eine Übersicht der Top- und Bottom-Sätze pro Merkmal. Zusätzlich wird eine Visualisierung der stärksten Sätze für jede Kategorie bereitgestellt.

### 2. Vektorisierung und Cosinus-Ähnlichkeit

#### Ziel
Durch die Vektorisierung von Texten (Genres) mittels TF-IDF sollen stilistisch ähnliche Texte identifiziert werden, ohne dass diese in Kategorien zugeordnet werden müssen.

#### Schritte
1. **Datenvorbereitung**:
   - Für jedes Genre in `results.array.json` werden die Sätze zu einem Text kombiniert, um den gesamten Stil des Genres darzustellen.

2. **TF-IDF-Vektorisierung**:
   - Mittels `TfidfVectorizer` werden die Texte in Vektoren umgewandelt.
   
3. **Berechnung der Cosinus-Ähnlichkeit**:
   - Die Cosinus-Ähnlichkeit zwischen allen Genres wird berechnet und in einem DataFrame gespeichert, um stilistisch ähnliche Genres zu identifizieren.

4. **Visualisierung der Top-Paare**:
   - Die 10 Genre-Paare mit der höchsten Ähnlichkeit werden in einem Balkendiagramm dargestellt, um stilistische Ähnlichkeiten aufzuzeigen.

#### Ergebnisse
Die Cosinus-Ähnlichkeiten zwischen Genres bieten eine Übersicht der stilistisch ähnlichsten Texte und unterstützen eine explorative Analyse der stilistischen Nähe.

## Nutzungshinweise

### Voraussetzungen
- `scikit-learn` und `matplotlib` müssen installiert sein.
- JSON-Dateien mit Thesaurus- und Textdaten (`results.array.json`, `regelbasierte_suche.json`) sind erforderlich.

### Ausführung
1. **Regelbasierte Analyse**:
   - Die Funktionen für die Merkmalsextraktion und das Scoring sind im Notebook `style_classifier.ipynb` beschrieben. Dort können die Ergebnisse in einer JSON-Datei gespeichert und visualisiert werden.
   
2. **Vektorisierung und Ähnlichkeitsanalyse**:
   - Die Vektorisierung und Cosinus-Ähnlichkeit wird ebenfalls in `style_classifier.ipynb` durchgeführt. Die Ähnlichkeitsergebnisse werden als DataFrame ausgegeben und grafisch dargestellt.

## Zusammenfassung der Ergebnisse

- **Regelbasierter Ansatz**: Die stilistischen Merkmale bieten eine erste explorative Einsicht in die Kategorien und ermöglichen eine geordnete Einteilung der Sätze.
- **Vektorisierung und Ähnlichkeitsanalyse**: Die Cosinus-Ähnlichkeit zwischen Genres unterstützt die Identifikation von stilistisch ähnlichen Texten, ohne diese in vordefinierte Kategorien zu zwängen.

## Anpassung und Weiterentwicklung

Das Regelwerk kann für eine genauere Analyse angepasst und erweitert werden. Der TF-IDF-Ansatz lässt sich auf größere Textmengen und verschiedene Textarten anwenden, um umfassendere stilistische Vergleiche durchzuführen.
