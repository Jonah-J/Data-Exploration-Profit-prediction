# Report der "Die Elite"-Gruppe

# Einführung und Ziel
Die Gruppe "Die Elite" besteht aus den Studenten Jonah Jäger, Marius Kiskemper und Marvin Vielmeyer. Das Projekt "Data-Exploration-Profit-Prediction" besitzt das Ziel, basierend auf einem Input-Vektor, der aus verschiedenen Parametern besteht, den Profit einer Transaktion vorherzusagen. Um dies zu erreichen wird ein Modell aufgesetzt, auf dem der ausgewählte Datensatz trainiert wird. 

Das Ziel ist es, den betriebswirtschaftlichen Zusammenhang umzusetzen. Dieser besteht darin, dass Unternehmen unsere Software zur Profit-Vorhersage nutzen können, um herauszufinden, welche Parameter des Datensatzes eine Auswirkung auf den Profit haben.

## Related Work


## Datensatz
Der Datensatz ist von Kaggle und kann [hier](https://www.kaggle.com/apoorvaappz/global-super-store-dataset "hier") gefunden werden. Hier sind Daten von Nutzer Transaktionen auf E-Commerce Seiten gespeichert, die im Zeitraum des 1.Januar.2011 und dem 31.Dezember.2014 stattgefunden haben. Im Genaueren sind hier Informationen zu den Attributen "Row-ID", "Order-ID, "Order-Date", "Ship-Date", "Ship Mode", "Customer ID", "Costumer Name", "Segment", "City", "State", "Product ID",	"Category",	
"Sub-Category",	"Product Name",	"Sales	Quantity",	"Discount",	"Profit",	"Shipping Cost"	und "Order Priority". Diese Menge an Attributen wird sich jedoch, aufgrund von Bereinung des Datensatzes, im Laufe des Projekts verkleinern.    

Ebenfalls sind die Daten für unseren Sachzusammenhang gelabeled, da jede Zeile einen Wert für den Profit der Transaktion beinhaltet. 

## Wissenschaftlche Vorgehensweise 
Die wissenschaftliche Vorgehensweise unserer Datenxploration sollte möglichst repräsentativ, vergleichbar, messbar und wiederholbar sein. Daher haben wir uns einen besonderen Ansatz für die Exploration überlegt. Das Ziel ist es ja, einen Algorithmus zu trainieren, der den Profit vorhersagt. Diese Vorhersage sollte anhand verschiedener Parameter passieren, die den Profit-Wert beeinflussen. Um dies zu ermöglichen, müssen zuerst alle Attribute herausgestellt werden, die eine Korrelation mit dem Profit haben (deren Veränderung den Profit also auch verändert). 
Wir haben folgende repräsentative Methodik angewendet, um diese Attribute zu finden: Alle Attribute werden auf genau die gleichen Kriterien getestet. Also egal, wie offensichtlich eine vermeintliche Korrelation mit dem Profit ist, werden trotzdem die gleichen Schritte wie bei allen anderen Attributen durchgeführt. Dies erzeugt eine sehr gute Vergleichbarkeit und Nachvollziehbarkeit der Ergebnisse.
Die Tests dieser Kriterien waren einerseits die Prüfung der grafischen Korrelation mittels Diagrammen, sowie andererseits die rechnerische Korrelation mittels statistischer Methoden. Zur genauen Umsetzung dieser Testmethoden jedoch später mehr.
Der gesamte Quellcode unseres Projekts ist auf diese Vorgehensweise ausgelegt. Denn jedes der Notebooks der Datenexploration ist jeweils nummiert. Hierbei spiegelt eine Nummer den Test eines Attributs wider. Dieser Test ist bei jedem Attribut gleich aufgebaut und durchgeführt. Außerdem hat auch jedes Attribut ein kleines Fazit im Dokument, welches begründet warum das Attribut entfernt oder beibehalten wird. Die wissenschaftliche Vorgehensweise findet sich also im Quellcode wieder.

# Die Datenexploration

Wie erläutert, durchläuft jedes Attribut den Prozess der grafischen Analyse der Auswirkung auf den Profit. Hier wird grundlegend zwischen den kategorischen und numerischen Attributen unetrschieden. 

Kategorische Variablen haben den Vorteil, dass hier die Transaktionen gruppiert werden können (z.B. Gruppierung nach Produkt-Kategorie: entweder Technologie, Möbel ). Es muss jedoch zunächst bei jedem gruppierten Attribut geprüft werden, ob die einzelnen Gruppen genug Transaktionen haben, um valide Vorhersagen treffen zu können. Denn wenn z.B. ein Attribut über 30000 verschiedene Ausprägungen hat, wobei jedes Attribut nur ein- oder maximal zweimal vorkommt, kann den Durchschnittswerten dieser Gruppe keine Aussagekraft zugewiesen werden. Denn die Gefahr wäre dann zu groß, dass diese ein oder zwei Werte für dieses Attribut nur Ausreißerwerte sind. Die optimalen kategorischen Attribute haben also möglichst wenige verschiedene Gruppen, die dafür dann jeweils viele Transaktionen haben. Anschließend an diese Prüfung wird für jede dieser Gruppen ein durchschnittlicher Profit gebildet. Im Idealfall ist der durchschnittliche Profit je nach Gruppe anders. Denn dann kann die Annahme getroffen werden, dass dieses Attribut den Profit beeinflusst.

Numerische Variablen hingegen erlauben keine Druchschnittsbildung. Daher werden hier vor allem Streudiagramme genutzt, um einen angenäherten linearen Zusammenhang zu überpüfen. Diese Art der grafischen Untersuchung kann also trotzdem genauso gut einen Aufschluss auf den Bezug zum Profit geben.

Die Interpreatation der der Diagramme ist jedoch subjektiv, sodass die Annahmen unterschiedlich ausfallen können. Um die Wissenschaftlichkeit beizubehalten wird jedes Attribut darüber hinaus noch einem statistischen Test unterzogen. Auch hier wird die Vorgehensweise zwischen kategorischen und numerischen Varaiblen leicht unterschieden.

Bei numerischen Variablen kann in Python Pandas einfach der Befehl "df.corr" ausgeführt werden, um die Korrelationen der Attribute untereinander herauzustellen. Die Interpretation dieses Werts ist naheliegend: ein Wert von -1 ist eine stark negative Korrelation, ein Wert von 0 keine Korrelation und ein Wert von 1 eine stark positive Korrelation. Die Ergebnisse dieses Befehls gleichen den Werten der numerischen Variablen der in unseren Notebooks verwendeten Korrelations-Heatmap von der Dython-library.

Kategorische Variablen müssen anders untersucht und analysiert werden. Hier ist es etwas komplizierter statistisch festzustellen, ob eine Korrelation zwischen dem Attribut und dem Profit vorliegt. Daher haben wir uns dazu entschieden zwei verschiedene statistische Tests bei jedem kategorischen Attribut durchzuführen. Einerseits wurden die Werte aus der Korrelations-Heatmap von der Dython-library genutzt. (Wie diese berechnet werden ist [hier](https://towardsdatascience.com/the-search-for-categorical-correlation-a1cf7f1888c9 "hier") erklärt) Darüber hinaus haben wir jedes kategorische Attribut dem Anova-Test unterzogen. (genaue Dokumentation dazu ist [hier](https://support.minitab.com/en-us/minitab-express/1/help-and-how-to/modeling-statistics/anova/how-to/one-way-anova/interpret-the-results/key-results/ "hier"), [hier](https://blog.minitab.com/de/grundlagen-der-varianzanalyse-anova-und-des-f-tests "hier") und [hier](https://www.statisticshowto.com/probability-and-statistics/f-statistic-value-test/ "hier") zu finden) Hierbei gilt, dass das Attribut eine statistisch signifikante Abhängigkeit zum Proft hat, wenn der p-Wert unter 0,05 und der F-Score möglichst hoch ist.

Wenn das jeweilige Attribut diese drei Schritte der Datenexploration (Prüfung auf Aussagekraft, grafische Analyse und statistische Analyse) durchlaufen hat, kann entschieden werden, ob das Attribut entfernt wird oder die Korrelation zum Profit stark genug ist, um für das folgende Training des Machine Learning Modells genutzt zu werden.

# Das Modell



# Der betriebswirtschaftliche Bezug/Ergebnisse


# Kritische Reflexion



