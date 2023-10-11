# Recomender-Systems
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/beckceline/Recomender-Systems/HEAD)

Die beiden am häufigsten verwendeten Methoden für Empfehlungssysteme sind Content-Based und Collaborative Filtering (CF).

* Content-based Empfehlungssysteme konzentrieren sich auf die Eigenschaften von Objekten und erstellen die Empfehlungen anhand derer Ähnlichkeit.

* Collaborative Filtering erstellt Emfehlungen basierend auf dem Wissen, welche Einstellung ein Nutzer gegenüber Objekten hat. Es nutzt also die "Weisheit der Masse" um passende Objekte zu empfehlen. CF kann darüberhinaus in Memory-based CF und Model-based CF unterteilt werden.

Im Allgemeinen werden CF Systeme häufiger verwendet als Content-based Systeme. Das liegt daran, dass sie üblicherweise für den Nutzer relevantere Ergebnisse erzeugen. Außerdem ist es relativ einfach zu verstehen (betrachtet man die Implementierung im Allgemeinen). Der Algorithmus hat die Fähigkeit selbstständig "Feature-Learning" zu betreiben und so mehr darüber zu lernen, welche Eigenschaften er verwenden soll.

In diesem Projekt werden wir ein Model-based CF System implimentieren indem wir Single Value Decomposition (SVD) verwenden. Das Momory-based CF System bauen wir durch die Berechnung von Kosinus-Ähnlichkeiten auf.

Wir werden den berühmten MovieLens Datensatz verwenden, der einer der am häufigsten verwendeten Datansaätze zum Implementieren und Testen von Empfehlungssystemen ist. Er enthält 100k Filmbewertungen von 943 Nutzern für eine Auswahl an insgesamt 1682 Filmen.

### Schritte: 

1. Daten laden und Überblick verschaffen: Zu Beginn importieren wir die erforderlichen Bibliotheken, darunter numpy und pandas, um mit den Daten zu arbeiten. Anschließend lesen wir die "u.data"-Datei ein, die den vollständigen Datensatz enthält. Die Daten in dieser Datei sind in einem bestimmten Format, weshalb wir Tab als Trennzeichen festlegen. Nach dem Einlesen der Daten haben wir eine Datenstruktur, die die Nutzer, Filme, Bewertungen und Zeitstempel enthält.

2. Datenüberblick: Wir werfen einen ersten Blick auf die Daten, um sicherzustellen, dass sie korrekt eingelesen wurden. Dies hilft uns, die Daten besser zu verstehen.
Nach der Datenerfassung haben wir jetzt den Nutzer- und Filmtitel als "item_id". Um die Filmtitel anzuzeigen, fügen wir die entsprechenden Titelinformationen aus der Datei "Movie_Id_Titles.csv" zu unserem DataFrame hinzu. Wir stellen auch fest, wie viele eindeutige Nutzer und Filme im Datensatz vorhanden sind. Dies ist wichtig, um die Dimensionen der Empfehlungsmatrizen festzulegen.

3. Train-Test-Split: Um die Leistung unseres Empfehlungssystems zu bewerten, teilen wir den Datensatz in Trainings- und Testdaten auf. Dies ermöglicht es uns, die Vorhersagen auf den Testdaten zu überprüfen und die Qualität des Modells zu beurteilen. Es ist jedoch wichtig zu beachten, dass Empfehlungssysteme aufgrund ihrer Natur schwer zu bewerten sind. Daher ist der Train-Test-Split in diesem Fall anders als bei herkömmlichen Machine-Learning-Aufgaben.

4. Memory-Based Collaborative Filtering
Memory-Based Collaborative Filtering-Ansätze können in zwei Hauptkategorien unterteilt werden: user-item filtering und item-item filtering. 
* User-Item Filtering: Empfiehlt Objekte, die von Nutzern gemocht wurden, die ähnliche Bewertungen abgegeben haben.
* Item-Item Filtering: Empfiehlt Objekte, die von Nutzern gemocht wurden, die dasselbe Objekt gemocht haben.
Die Grundlage für diese Ansätze ist die Erstellung einer User-Item-Matrix für Trainings- und Testdaten, die auf den verfügbaren Bewertungen basiert.

5. Berechnung der Vorhersagen
Um Empfehlungen zu treffen, müssen wir die Ähnlichkeitsmatrizen zwischen Nutzern und Objekten berechnen. Für User-based CF verwenden wir eine gewichtete Durchschnittsberechnung, für Item-based CF verwenden wir die Ähnlichkeiten zwischen den Objekten und den Bewertungen der Nutzer, um Vorhersagen zu treffen. Dies erfolgt durch die Berechnung der Kosinus-Ähnlichkeit, die auf den vorhandenen Bewertungen basiert.

7. Model-Based Collaborative Filtering
Im Gegensatz zum Memory-Based Collaborative Filtering basiert Model-Based Collaborative Filtering auf Matrix-Faktorisierung (MF). Dieser Ansatz verwendet latente Variablen und Dimensionsreduktion, um Empfehlungen zu erstellen.
Es ist wichtig zu verstehen, dass Model-Based CF nur auf vorhandenen Daten basiert, um latente Merkmale zu lernen. Je mehr Daten verfügbar sind, desto besser kann das Modell lernen und Empfehlungen generieren. In diesem Projekt verwenden wir Singular Value Decomposition (SVD) für die Matrix-Faktorisierung. Ein bekannter Ansatz, der sich in der Praxis bewährt hat. Er lernt latente Nutzerpräferenzen und Objekteigenschaften aus vorhandenen Bewertungen.

### Ergebnis

Um die Leistung unseres Empfehlungssystems zu bewerten, verwenden wir den Root Mean Squared Error (RMSE). Ein niedriger RMSE zeigt an, dass unsere Vorhersagen den tatsächlichen Werten nahe kommen.

Memory-basierte CF-Algorithmen sind einfach zu implementieren, liefern vernünftige Vorhersagen, haben jedoch Schwierigkeiten bei der Skalierbarkeit und dem Umgang mit neuen Nutzern oder Objekten. Model-based CF-Methoden sind skalierbarer, können mit weniger Daten arbeiten, aber stehen ebenfalls vor Herausforderungen bei neuen Einträgen.

Die Bewertung des Seltenheitsniveaus der Daten zeigt, wie gut das Modell mit den gegebenen Daten umgeht. Hybride Empfehlungssysteme kombinieren CF- und Inhaltsbasierte Modelle, um die Vorhersagegenauigkeit zu erhöhen.

Zusammenfassend zeigt diese Auswertung, wie die Wahl des Empfehlungssystems und die Verwendung von Modellen wie SVD die Vorhersagegenauigkeit beeinflussen können. Die Verwendung von RMSE und ähnlichen Metriken ermöglicht die Bewertung und Verbesserung der Leistung solcher Systeme.

Fortgeschrittene Empfehlungssysteme sind komplex, erfordern Verständnis von Memory-Based und Model-Based Collaborative Filtering und bieten Möglichkeiten zur personalisierten Empfehlung. Es ist wichtig, die Vor- und Nachteile dieser Ansätze zu verstehen und die Leistung der Modelle zu bewerten, um optimale Empfehlungen zu generieren.


