# stechlinnetzwerke

Das Repository enthält Daten und Code, um Figurennetzwerke für Theodor Fontanes Roman Der Stechlin zu erstellen. Die zugrundeliegende Fragestellung und die Ergebnisse werden in einem Blogpost im Blog des Fontane Archivs beschrieben: https://www.fontanearchiv.de/blogbeitrag/2021/06/2/der-stechlin-vernetzt?cHash=c427eb77b055cf88deb60b37fab3d115 

Grundsätzlich sind aufgrund der Daten zwei verschiedene Arten von Netzwerken erstellbar:
-	Wer spricht mit wem? – ein Netzwerk mit Figurennamen als Knoten und Sprechakten zwischen Figuren als Kanten
-	Wer spricht über wen? ¬– ein Netzwerk mit Figurennamen als Knoten und Aussagen über andere Figuren als Kanten

## Guidelines

Die Datei „guidelines.pdf“ beschreibt die Richtlinien, die bei der Annotation des Romans befolgt wurden.

## Data

Der Ordner „data“ enthält die für die Erstellung der Netzwerke notwendigen Daten.
-	Die Datei „stechlin.txt“ enthält den Roman Der Stechlin in der auf TextGrid zur Verfügung gestellten Form
-	Die Datei „figurenuebersicht.csv“ enthält eine Liste mit den Namen aller Figuren, deren Geschlecht, Wohnort und gesellschaftlichem Stand
-	Die Datei „sprechakt_sprecher.csv“ enthält die annotierten Sprechakte, deren ids und jeweiligen Sprecher
-	Die Datei „sprechakt_sprecher.csv“ enthält die annotierten Sprechakte, deren ids und die Figuren, denen gegenüber der Sprechakt erfolgt ist
-	Die Datei „referenz_referierende_Figuren.csv“ enthält annotierte Sprechakte, in denen Figuren Aussagen über andere Figuren treffen, deren ids und den Sprecher des jeweiligen Sprechakts
-	Die Datei „referenz_referierte_Figuren.csv“ enthält annotierte Sprechakte, in denen Figuren Aussagen über andere Figuren treffen, deren ids und den Namen der Figur, über die etwas gesagt wird

## Notebook

Die Datei „stechlinnetzwerke.ipynb“ enthält den Code, um die Netzwerke zu erstellen. 

1. Netzwerktyp: Wer spricht mit wem? Dafür werden die Dateien „sprechakt_sprecher.csv“ und „sprechakt_sprecher.csv“ aus dem Ordner „data“ als pandas DataFrame eingelesen und anhand der ids gemerged. Anschließend werden die Knoten (Figurennamen) und Kanten (Sprechakte zwischen Figuren) ausgelesen. Anschließend werden verschiedene Typen von Netzwerken (gerichtet, gewichtet, eingefärbt nach verschiedenen Parametern) erstellt und als html-Dateien im Ordner „networks“ abgelegt. Für die erstellten Netzwerke werden verschiedene Zentralitätsmaße errechnet und als Barcharts visualisiert. Diese Barcharts werden im Ordner „figures“ gespeichert. 

2. Netzwerktyp: Wer spricht über wen? Im zweiten Netzwerktyp repräsentieren die Kanten die Information, welche Figuren über welche anderen Figuren sprechen. Dafür werden die Dateien „referenz_referierte_Figuren.csv“ und „referenz_referierende_Figuren.csv“ aus dem Ordner „data“ als pandas DataFrame eingelesen und anhand der ids gemerged. Anschließend werden wie oben die Knoten und Kanten ausgelesen und die html-Dateien der Netzwerke im „networks“-Ordner abgelegt. Zudem werden wieder die Zentralitätsmaße ermittelt, visualisiert und im Ordner „figures“ abgelegt.


## Pakete

Folgende Pakete werden zum Ausführen des Notebooks benötigt:
-	pandas
-	networkx 
-	pyvis== 0.3.1 (bei neueren Versionen kann es zu Problemen kommen)
-	operator
-	matplotlib

