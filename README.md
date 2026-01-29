# NLP-basierte Analyse unstrukturierter Beschwerdedaten

[cite_start]Dieses Projekt entwickelt einen automatisierten NLP-Workflow (Natural Language Processing), um aus einer großen Anzahl unstrukturierter Texte die zentralen Anliegen von Bürgern zu extrahieren[cite: 3, 4]. [cite_start]Als repräsentativer Datensatz dient die „Consumer Complaint Database“ (CFPB https://www.kaggle.com/datasets/selener/consumer-complaint-database), die als Transfer-Modell für kommunale Beschwerdesysteme fungiert[cite: 5, 6].

## Kernfeatures & Methodik

### 1. Erweiterte Vorverarbeitung (Preprocessing)
[cite_start]Um eine hohe Analysepräzision zu erreichen, durchlaufen die Texte eine mehrstufige Pipeline[cite: 8]:
* [cite_start]**Bereinigung:** Entfernung von Sonderzeichen und Zahlen mittels Regex sowie Konvertierung in Kleinschreibung[cite: 9].
* **Erweiterte Stopword-Filterung:** Neben Standard-Stopwords wurden spezifische Platzhalter aus der Anonymisierung (z. B. "xxxx", "xxxxxxxx") entfernt, um Datenrauschen zu minimieren.
* [cite_start]**Lemmatisierung:** Rückführung der Wörter auf ihren Grundstamm zur Reduktion der Dimensionalität[cite: 11].

### 2. Vektorisierung & Semantische Analyse
[cite_start]Es werden zwei Ansätze zur Texttransformation und Themenextraktion verglichen[cite: 13, 14]:
* **Vektorisierung:** Vergleich von **Bag-of-Words** (Häufigkeitsbasiert) und **TF-IDF** (Relevanzbasiert).
* **Themenmodellierung:** Gegenüberstellung von **Latent Dirichlet Allocation (LDA)** und **Non-negative Matrix Factorization (NMF)**.

### 3. Bestimmung der optimalen Themenanzahl (K)
Die Anzahl der zu extrahierenden Themen wurde nicht subjektiv gewählt, sondern mathematisch hergeleitet. Mittels einer **Perplexity-Evaluation** wurde ein Score-Verlauf für verschiedene Werte von $K$ erstellt. Das mathematische Optimum (Minimum der Perplexity) wurde bei **$K=7$** identifiziert und für die finale Modellierung verwendet.

## Verwendete Technologien
[cite_start]Die Umsetzung erfolgt in **Python** unter Einsatz folgender Bibliotheken[cite: 16]:
* [cite_start]`pandas`: Datenmanagement und Strukturierung[cite: 17].
* [cite_start]`re` & `nltk`: Linguistische Vorverarbeitung und Mustererkennung[cite: 18].
* [cite_start]`scikit-learn`: Vektorisierung und mathematische Themenmodellierung[cite: 19].
* `matplotlib`: Visualisierung der Evaluationsmetriken.

## Projektstruktur
* `NLP-Analyse_KundenBeschwerden.ipynb`: Haupt-Notebook mit dem vollständigen Workflow.
* `requirements.txt`: Liste der notwendigen Python-Bibliotheken.
* `rows_sample.csv`: Beispieldatensatz (Auszug der CFPB Database).

## Installation & Ausführung
1. Repository klonen.
2. Abhängigkeiten installieren: `pip install -r requirements.txt`.
3. Das Jupyter Notebook öffnen und die Zellen nacheinander ausführen.