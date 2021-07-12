# Data-Exploration-Profit-prediction

## Teammitglieder
Marius Kiskemper

Marvin Vielmeyer

Jonah Jäger

## Struktur des Projekts
Im Ordner src liegen die beiden Ordner "Exploration" und "Modell". Beide beinhalten die Notebook(.ipynb) Dateien, mit denen wir gearbietet haben. (Da wir auf github teilweise Probleme damit haben, die .ipynb Dateien anzeigen zu lassen, haben wir PDF Versionen der Notebooks daneben abgelegt. Diese können in jedem Fall angesehen werden. Natürlich können die .ipynb Dateien auch einfach in einer Jupyter Notebook Umgebung ausgeführt und somit angesehen werden)
Die Notebooks von der "Exploration" beinhalten die gesamte Datenvorverarbeitung. Hier werden alle Attribute auf ihre Korrelation mit dem Profit geprüft. Nicht-relevante Attribute werden gelöscht.
Im Notebook des Ordners "Modell" wird mit dem fertig bereinigten Datensatz eine Regression trainiert, die am Ende einen Profit Wert vorhersagt.

## Der Datensatz
Der Datensatz ist von Kaggle und kann [hier](https://www.kaggle.com/apoorvaappz/global-super-store-dataset "hier") gefunden werden. Hier sind Daten von Nutzer Transaktionen auf E-Commerce Seiten gespeichert. Die Daten sind für unseren Sachzusammenhang gelabeled, da jede Zeile einen Wert für den Profit der Transaktion beinhaltet.

## Ziel des Projekts
Es soll möglich sein einem trainierten Machine Learning Modell eine Kombination aus verschiedenen Parametern der Transaktionen zu übergeben. Das Modell gibt anhand der Parameter einen Profit-Wert aus. Wenn die Parameter andere Werte annehmen, sollte sich auch der Profit-Wert ändern. Auf dem Weg zu diesem Modell sollte eine detaillierte Datenexploration stattfinden, die die relevanten Attribute, im Bezug auf den Profit, herausstellt.

## Umsetzung
Die Exploration wurde in vier Notebooks aufgeteilt, da sich so die Laufzeit eines Notebooks in Grenzen hält. Jedes Attribut wurde auf die gleiche Art mit dem Profit in Verbindung gesetzt: Es wurden mit Hilfe von plotly und pandas Diagramme zur grafischen Überprüfung erstellt. Diese geben einen Eindruck, ob es eine Korrelation zwischen dem Untersuchungsattribut und dem Profit gibt. Anschließend wird diese Annahme durch eine Berechnung der statistischen Abhängigkeit mit scipy und Dython bestätigt oder widerlegt.
Anschließend wird das Modell (die Regression) durch sklearn trainiert. Dieses Modell kann dann zur Vorhersage genutzt werden.

## Anwendung
Zur Anwendung des betriebswirtschaftlichen Zusammenhangs kann einfach das Notebook 5_Modell_aufsetzen.ipynb ausgeführt und eine neue Zelle erstellt werden. Dafür müssen zuerst alle libraries aus der requirements.txt Datei installiert sein. Der Befehl reg.predict() bekommt als Parameter alle relevanten Attribute übergeben, die für die Vorhersage benötigt werden. Alle Attribute werden numerisch übergeben. Beispiele, wie die kategorischen Attribute numerisch gemacht werden, finden sich auch in diesem Notebook. 
Damit kann dann die Funktion umgesetzt werden, dass nur ein bestimmtes Parameter verändert wird, um zu überprüfen, welche Auswirkung dieses Parameter auf den Profit hat.


Eine detailliertere Dokumentation ist im Dokument report.md zu finden.
