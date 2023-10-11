# Recomender-Systems
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/beckceline/Recomender-Systems/HEAD)

Die beiden am häufigsten verwendeten Methoden für Empfehlungssysteme sind Content-Based und Collaborative Filtering (CF).

* Content-based Empfehlungssysteme konzentrieren sich auf die Eigenschaften von Objekten und erstellen die Empfehlungen anhand derer Ähnlichkeit.

* Collaborative Filtering erstellt Emfehlungen basierend auf dem Wissen, welche Einstellung ein Nutzer gegenüber Objekten hat. Es nutzt also die "Weisheit der Masse" um passende Objekte zu empfehlen. CF kann darüberhinaus in Memory-based CF und Model-based CF unterteilt werden.

Im Allgemeinen werden CF Systeme häufiger verwendet als Content-based Systeme. Das liegt daran, dass sie üblicherweise für den Nutzer relevantere Ergebnisse erzeugen. Außerdem ist es relativ einfach zu verstehen (betrachtet man die Implementierung im Allgemeinen). Der Algorithmus hat die Fähigkeit selbstständig "Feature-Learning" zu betreiben und so mehr darüber zu lernen, welche Eigenschaften er verwenden soll.

In diesem Projekt werden wir ein Model-based CF System implimentieren indem wir Single Value Decomposition (SVD) verwenden. Das Momory-based CF System bauen wir durch die Berechnung von Kosinus-Ähnlichkeiten auf.

Wir werden den berühmten MovieLens Datensatz verwenden, der einer der am häufigsten verwendeten Datansaätze zum Implementieren und Testen von Empfehlungssystemen ist. Er enthält 100k Filmbewertungen von 943 Nutzern für eine Auswahl an insgesamt 1682 Filmen.

### Schritte: 

3. Train-Test-Aufteilung: 
Wir teilen die Daten in Trainings- und Testdaten auf, um die Leistung des Empfehlungssystems zu bewerten. Dabei verwenden wir die Funktion train_test_split aus Scikit-Learn.

4. Memory-Based Collaborative Filtering: 
Memory-Based CF-Ansätze können in zwei Hauptkategorien unterteilt werden: user-item filtering und item-item filtering. Bei user-item filtering werden ähnliche Nutzer gefunden, um Empfehlungen für den Nutzer zu erstellen. Bei item-item filtering werden ähnliche Objekte gefunden, um Empfehlungen für ein bestimmtes Objekt zu erstellen.
Wir erstellen eine User-Item-Matrix für Trainings- und Testdaten und berechnen die Kosinusähnlichkeiten zwischen den Nutzern und den Objekten.

5. Berechnung der Vorhersagen: 
Wir verwenden die erstellten Ähnlichkeitsmatrizen, um Vorhersagen zu treffen. Für User-based CF verwenden wir eine gewichtete Durchschnittsberechnung, um Vorhersagen zu treffen. Für Item-based CF verwenden wir die Ähnlichkeiten zwischen den Objekten und den Bewertungen der Nutzer, um Vorhersagen zu treffen.

6. Auswertung: 
Die Leistung des Empfehlungssystems wird anhand des Root Mean Squared Error (RMSE) gemessen, der die Genauigkeit der vorhergesagten Bewertungen bewertet.

7. Model-Based Collaborative Filtering:
Model-based CF basiert auf Matrix-Faktorisierung (MF) und wird häufig in Empfehlungssystemen verwendet. Es zielt darauf ab, die latenten Präferenzen von Nutzern und die latenten Merkmale von Objekten aus den gegebenen Bewertungen zu lernen.
In diesem Tutorial verwenden wir Singular Value Decomposition (SVD) für die Matrix-Faktorisierung.

### Ergebnis

Empfehlungssysteme sind mächtige Werkzeuge, um personalisierte Empfehlungen für Nutzer basierend auf deren Vorlieben und Verhaltensweisen zu erstellen. Sie sind in vielen Anwendungen von großer Bedeutung, wie z. B. in E-Commerce-Plattformen, sozialen Medien und Streaming-Diensten. Das Verständnis der verschiedenen Methoden und deren Implementierung in Python kann wertvoll sein, um personalisierte Empfehlungssysteme zu erstellen und zu verbessern.
