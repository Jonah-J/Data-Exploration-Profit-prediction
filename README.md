# Data-Exploration: Profit-prediction

## Teammitglieder
Marius Kiskemper

Marvin Vielmeyer

Jonah Jäger

## Struktur des Projekts
Im Ordner src liegen die Ordner "Exploration" und "Modell" neben dem Ordner "data", der den Datensatz beinhaltet. Beide beinhalten die Notebook(.ipynb)-Dateien, mit denen wir gearbeitet haben. (Wir hatten auf Github teilweise Probleme mit der Ansicht der .ipynb Dateien. Falls das bei Ihnen auch der Fall ist, müssen Sie sich die Notebooks einfach in einer Jupyter Notebook-Umgebung ablegen und anschleßend laufen lassen (entsprechend den Schritten aus dem Punkt "Anwendung"))
Die Notebooks von der "Exploration" beinhalten den gesamten Prozess von Datensatzbereinigung bis hin zur Vorverarbeitung und Entfernen von Attributen. Hier werden alle Attribute auf ihre Korrelation mit dem Profit geprüft. Nicht-relevante Attribute werden gelöscht. Die vier Explorations-Notebooks und das Modell-Notebook sind jeweils eigenständig und nicht voneinander abhängig.
Im Notebook des Ordners "Modell" wird mit dem fertig bereinigten Datensatz eine Regression trainiert, die am Ende einen Profit-Wert vorhersagt. Dieses Notebook kann also alleinstehend ausgeführt und erweitert werden. Dennoch ist zu empfehlen die Notebooks der Nummerierung nach durchzugehen und die detaillierte Kommentierung des Codes nachzuvollziehen, um das Modell-Notebook optimal anwenden und verstehen zu können.

## Der Datensatz
Der Datensatz ist von Kaggle und kann [hier](https://www.kaggle.com/apoorvaappz/global-super-store-dataset "hier") gefunden werden. Es wurden Daten von Nutzer-Transaktionen auf E-Commerce Seiten gespeichert. Die Daten sind für unseren Sachzusammenhang gelabeled, da jede Zeile einen Wert für den Profit der Transaktion beinhaltet.

## Ziel des Projekts
Es soll möglich sein, einem trainierten Machine Learning Modell eine Kombination aus verschiedenen Parametern der Transaktionen zu übergeben. Das Modell gibt anhand der Parameter einen Profit-Wert aus. Wenn die Parameter andere Werte annehmen, sollte sich auch der Profit-Wert ändern. Auf dem Weg zu diesem Modell sollte eine detaillierte Datenexploration stattfinden, die die relevanten Attribute, im Bezug auf den Profit, herausstellt.

## Umsetzung
Die Exploration wurde in vier Notebooks aufgeteilt, da sich so die Laufzeit eines Notebooks in Grenzen hält. Jedes Attribut wurde auf die gleiche Art mit dem Profit in Verbindung gesetzt: Es wurden mit Hilfe von Plotly und Pandas Diagramme zur grafischen Überprüfung erstellt. Diese geben einen Eindruck, ob es eine Korrelation zwischen dem Untersuchungsattribut und dem Profit gibt. Anschließend wird diese Annahme durch eine Berechnung der statistischen Abhängigkeit mit Scipy und Dython bestätigt oder widerlegt.
Danach wird das Modell (die Regression) durch Sklearn trainiert. Dieses Modell kann dann zur Vorhersage genutzt werden. 

## Anwendung
Zur Anwendung des betriebswirtschaftlichen Zusammenhangs kann einfach das Notebook 5_Modell_aufsetzen.ipynb ausgeführt und eine neue Zelle erstellt werden. Dafür müssen zuerst alle libraries aus der requirements.txt-Datei installiert sein. Außerdem muss der Ordner "data" aus src neben den .ipynb Dateien liegen, damit diese die csv-Datei finden. Dann kann im Notebook der Befehl reg.predict() eingegeben werden, der als Parameter alle relevanten Attribute übergeben bekommt, die für die Vorhersage benötigt werden. Alle Attribute werden numerisch übergeben. Beispiele, wie die kategorischen Attribute numerisch gemacht werden, finden sich auch in diesem Notebook. 
Damit kann dann die Funktion umgesetzt werden, dass nur ein bestimmtes Parameter verändert wird, um zu überprüfen, welche Auswirkung dieses Parameter auf den Profit hat.


Eine detailliertere Dokumentation ist im Dokument report.md (bzw. project_report_Die_Elite.pdf) zu finden.
