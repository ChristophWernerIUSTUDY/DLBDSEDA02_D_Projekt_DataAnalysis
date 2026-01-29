# NLP-basierte Analyse unstrukturierter Beschwerdedaten

Dieses Projekt entwickelt einen automatisierten NLP-Workflow (Natural Language Processing), um aus einer großen Anzahl unstrukturierter Texte die zentralen Anliegen von Bürgern zu extrahieren. Als repräsentative Datenquelle dient die „Consumer Complaint Database“ (CFPB https://www.kaggle.com/datasets/selener/consumer-complaint-database), die als Transfer-Modell für kommunale Beschwerdesysteme fungiert.

## Kernfeatures & Methodik

### 1. Erweiterte Vorverarbeitung (Preprocessing)
Um eine hohe Analysepräzision zu erreichen, durchlaufen die Texte eine mehrstufige Pipeline:
* **Bereinigung:** Entfernung von Sonderzeichen und Zahlen mittels Regex sowie Konvertierung in Kleinschreibung.
* **Erweiterte Stopword-Filterung:** Neben Standard-Stopwords wurden spezifische Platzhalter aus der Anonymisierung (z. B. "xxxx", "xxxxxxxx") entfernt, um Datenrauschen zu minimieren.
* **Lemmatisierung:** Rückführung der Wörter auf ihren Grundstamm zur Reduktion der Dimensionalität.

### 2. Vektorisierung & Semantische Analyse
Es werden zwei Ansätze zur Texttransformation und Themenextraktion verglichen:
* **Vektorisierung:** Vergleich von **Bag-of-Words** (Häufigkeitsbasiert) und **TF-IDF** (Relevanzbasiert).
* **Themenmodellierung:** Gegenüberstellung von **Latent Dirichlet Allocation (LDA)** und **Non-negative Matrix Factorization (NMF)**.

### 3. Bestimmung der optimalen Themenanzahl (K)
Die Anzahl der zu extrahierenden Themen wurde nicht subjektiv gewählt, sondern mathematisch hergeleitet. Mittels einer Perplexity-Evaluation wurde ein Score-Verlauf für verschiedene Werte von K erstellt. Das mathematische Optimum (Minimum der Perplexity) wurde bei **K = 7** identifiziert und für die finale Modellierung verwendet.

---

## Verwendete Technologien
Die Umsetzung erfolgt in Python unter Einsatz folgender Bibliotheken:
* **pandas**: Aufbereiten der Daten.
* **re & nltk**: Textvorverarbeitung (z. B. Bereinigung, Tokenisierung)
* **scikit-learn**: Umwandlung von Text in Vektoren und Themenmodellierung.
* **matplotlib**: Visualisierung der Ergebnisse.

## Projektstruktur
* `NLP-Analyse_KundenBeschwerden.ipynb`: Haupt-Notebook mit dem vollständigen Workflow.
* `requirements.txt`: Liste der notwendigen Python-Bibliotheken.
* `rows_sample.csv`: Beispieldatensatz (Auszug der CFPB Database).

---

Installation & Ausführung

1. Repository klonen
Öffne dein Terminal und lade das Projekt mit folgendem Befehl herunter:

git clone [https://github.com/ChristophWernerIUSTUDY/DLBDSEDA02_D_Projekt_DataAnalysis.git]
cd DLBDSEDA02_D_Projekt_DataAnalysis

2. Abhängigkeiten installieren
`pip install -r requirements.txt`.

3. Das Jupyter Notebook öffnen mit 'jupyter notebook' und die Zellen nacheinander ausführen.