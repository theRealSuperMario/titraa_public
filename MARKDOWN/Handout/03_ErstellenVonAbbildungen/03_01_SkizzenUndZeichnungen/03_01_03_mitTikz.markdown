# 03 01 03 mitTikz
Created Montag 30 Januar 2017

Ein kleines Vorwort
-------------------

* **t**ikz **i**st **k**ein **Z**eichenprogramm
* tikz ist nicht einfach **ABER** extrem mächtig
	* man kann extrem viel erreichen, wenn man mit google+dokumentation+copy/paste+ausprobieren arbeitet
	* das ist das Ziel
* die hilfreichsten Unterlagen wurden hier zusammengeschrieben 



Zuerst: EXTREM gute Youtube-Tutorials von ShareLaTex
----------------------------------------------------


* sharelatex hat extrem gute youtube-tutorials zu so gut wie allen themen online
	* mit live-code, flüssig gesprochen und kurz (5 minuten pro video)
	* Link zum Kanal: <https://www.youtube.com/user/ShareLaTeX/videos>
	* Playlist mit den unten aufgeführten videos:
		* <https://www.youtube.com/watch?v=pcIzeN46ETc&index=1&list=PLCRFsOKSM7eN6jPk0wSopXb37RKW93PM3>

 
| Thema                              | YoutubeLink                                          | Blogpost auf sharelatex.com                                       | Interaktiver Editor und Code                                  |
|:-----------------------------------|:-----------------------------------------------------|:------------------------------------------------------------------|:--------------------------------------------------------------|
| Basic Drawing Using TikZ           | <https://www.youtube.com/watch?v=pcIzeN46ETc&t=4s>   | <https://www.sharelatex.com/blog/2013/08/27/tikz-series-pt1.html> | <https://www.sharelatex.com/project/521b4a1206bf09190f129751> |
| Circuit Diagrams using CircuitTikz | <https://www.youtube.com/watch?v=WRTELZP1l0Y>        | <https://de.sharelatex.com/blog/2013/09/02/tikz-series-pt4.html>  | <https://www.sharelatex.com/project/5220bce944fe707038212c94> |
| MindMaps                           | <https://www.youtube.com/watch?v=V9vQ118o2kk>        | <https://de.sharelatex.com/blog/2013/09/04/tikz-series-pt5.html>  | <https://www.sharelatex.com/project/5226fa6444fe70703827d849> |
| Creating Flowcharts                | <https://www.youtube.com/watch?v=LoBC8zIB-3k&t=349s> | <https://www.sharelatex.com/blog/2013/08/29/tikz-series-pt3.html> | <https://www.sharelatex.com/project/52205bbce77a8bec1415bf38> |
| Generating TikZ Code from GeoGebra |                                                      | <https://www.sharelatex.com/blog/2013/08/28/tikz-series-pt2.html> |                                                               |




* *Basic Drawing using Tikz * <https://www.youtube.com/watch?v=pcIzeN46ETc>

![](./03_01_03_mitTikz/pasted_image.png)


* *Flowcharts *<https://www.youtube.com/watch?v=LoBC8zIB-3k>

![](./03_01_03_mitTikz/pasted_image001.png)

Quellcode am Ende des Videos
	\documentclass{article}
	\usepackage[utf8]{inputenc}
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows}
	
	\tikzstyle{startstop} = [rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black, fill=red!30]
	\tikzstyle{io} = [trapezium, trapezium left angle=70, trapezium right angle=110, minimum width=3cm, minimum height=1cm, text centered, 
					draw=black, fill=blue!30]
	\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, text width=3cm, draw=black, fill=orange!30]
	\tikzstyle{decision} = [diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=green!30]
	\tikzstyle{arrow} = [thick,->,>=stealth]
	
	\begin{document}
	
	\begin{tikzpicture}[node distance=2cm]
	
	\node (start) [startstop] {Start};
	\node (in1) [io, below of=start] {Input};
	\node (pro1) [process, below of=in1] {Process 1};
	\node (dec1) [decision, below of=pro1, yshift=-0.5cm] {Decision 1};
	\node (pro2a) [process, below of=dec1, yshift=-0.5cm] {Process 2a text text text text text text text text text text};
	\node (pro2b) [process, right of=dec1, xshift=2cm] {Process 2b};
	\node (out1) [io, below of=pro2a] {Output};
	\node (stop) [startstop, below of=out1] {Stop};
	
	\draw [arrow] (start) -- (in1);
	\draw [arrow] (in1) -- (pro1);
	\draw [arrow] (pro1) -- (dec1);
	\draw [arrow] (dec1) -- node[anchor=east] {yes} (pro2a);
	\draw [arrow] (dec1) -- node[anchor=south] {no} (pro2b);
	\draw [arrow] (pro2b) |- (pro1);
	\draw [arrow] (pro2a) -- (out1);
	\draw [arrow] (out1) -- (stop);
	
	
	\end{tikzpicture}
	
	\end{document}



Aufgabe
-------

Verwende den Code aus dem Youtube-Tutorial zu Flowcharts und wandle ihn ab, sodass es nachher so aussieht:
![](./03_01_03_mitTikz/pasted_image003.png)

**Tipp:**

* Versuche es in einem leeren Latex-Dokument



* füge den Code dann in deine Ausarbeitung ein mit

	\begin{figure}[ht]
	  \centering
	    \input{bilder/drawings/tikz_flowchart.tikz}
	  \caption{Mit TikZ erstelltes Flussdiagramm.}
	  \label{fig:tikz_flow}
	\end{figure}



Wo gibt es mehr Beispiele?
--------------------------
<http://www.texample.net/tikz/examples/feature/node-positioning/>

PGF- und Tikz-Dokumentation
---------------------------
Die Dokumentation ist 1162 Seiten lang. Es empfiehlt sich daher, genau zu wissen was man sucht.
<http://mirror.utexas.edu/ctan/graphics/pgf/base/doc/pgfmanual.pdf>
Das PDF ist bereits im Titraa Ordner eingecheckt.

### shapes Library

S. 693


### shapes.geometric - rectangle, diamond, circle

* bei ``rectangle`` gibt es keinen ``aspect``-key, bei ``diamond`` schon


#### shape.north south east west
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
	[
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (left)	[myrect] at (-2,0)	{ left };
	  \node (right)	[myrect] at (2,0)	{ right };
	  \draw [line cap=butt] (2,2) -- (-2,2);	%% a line connecting nodes at absolute coordinates
	  \draw [line cap=butt] (left.east) --(right.south west);
	  \draw [arrow] (right.west) -- (left.south east);
	\end{tikzpicture}
	\end{document}

![](./03_01_03_mitTikz/pasted_image009.png)


### Basic node placement

#### left, right, above, below of
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
	[
	  node distance=3cm,
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (center) 	[myrect]		{ center };
	  \node (left)	[myrect, left of=center]	{ left };
	  \node (right)	[myrect, right of=center]	{ right };
	  \node (above) [myrect, above of=center]	{ above};
	  \node (below)	[myrect, below of=center]	{ below };
	\end{tikzpicture}
	\end{document}

![](./03_01_03_mitTikz/pasted_image007.png)

#### mit absoluten Koordinaten - at
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document
	\begin{tikzpicture}
	[
	  node distance=3cm, %% node distnace eigentlich egal, weil ja at () benutzt wird
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (center) 	[myrect] at (0,0)	{ center };
	  \node (left)	[myrect] at (-2,0)	{ left };
	  \node (right)	[myrect] at (2,0)	{ right };
	  \node (above) [myrect] at (0,2)	{ above};
	  \node (below)	[myrect] at (0,-2){ below };
	\end{tikzpicture}
	\end{document}

![](./03_01_03_mitTikz/pasted_image008.png)


Line and arrow basics
---------------------

### -| vs |- vs --
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
	[
	  node distance=3cm, %% node distnace eigentlich egal, weil ja at () benutzt wird
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (center) 	[myrect] at (0,0)	{ center };
	  \node (left)		[myrect] at (-2,0)	{ left };
	  \node (right)		[myrect] at (2,0)	{ right };
	  \node (above) 	[myrect] at (0,2)	{ above};
	  \node (below)		[myrect] at (0,-2){ below };
	  
	  \draw [arrow] 	(center) -- (above);
	  \draw [arrow]		(below.east) -|  (right.south);		%erst waagrecht, dann senkrecht.
	  \draw [arrow] 	(left.north) |-  (above.west);		%erst senkrecht, dann waagrecht. 
	\end{tikzpicture}
	\end{document}
	

![](./03_01_03_mitTikz/pasted_image011.png)


### Linien und Pfeile beschriften
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
	[
	  node distance=3cm, %% node distnace eigentlich egal, weil ja at () benutzt wird
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (left)	[myrect] at (-2,0)	{ left };
	  \node (above) [myrect] at (0,2)	{ above};
	  
	  \draw [arrow] (left.north) |- 
	  				node{\colorbox{red}{1}} 
					node[below left]{\colorbox{green}{2}} 
					node[above right]{\colorbox{cyan}{3}} 
					node[near start, left]{\colorbox{yellow}{4}}
					node[near start, right]{\colorbox{magenta}{5}}
					node[near end, above right]{\colorbox{blue}{6}}
					node[near end, below right]{\colorbox{gray}{7}}
					(above.west);
	\end{tikzpicture}
	\end{document}
	

![](./03_01_03_mitTikz/pasted_image013.png)


\usetikzlibrary{calc} zur Berechnung von Koordinaten
----------------------------------------------------

* mit ``$...$`` kann eine Berechnung durchgeführt werden.  Dazu muss aber ``\usetikzlibrary{calc}``  in der Präambel stehen
* mit ``$(foo.north)$`` erhält man die Koordinaten von ``\node (foo)``. ``foo.north`` ist abhängig von der ``shape``
* mit ``$(foo.north) + (1,0)$`` wird der Vektor (1,0) hinzuaddiert.


### Beispiel 1
	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
	[
	  myrect/.style = {rectangle, minimum width = 3cm ,minimum height=1cm,text centered, draw=black,},
	  arrow/.style = {thick,->,>=stealth}
	]
	  \node (foo)		[myrect] {\texttt{do}$(\ldots)$};
	  \draw [line cap=butt] ($(foo.north east) + (-0.1,0)$)  -- ($(foo.south east) + (-0.1,0)$);
	  \draw [line cap=butt] ($(foo.north west) + (0.1,0)$)  -- ($(foo.south west) + (0.1,0)$);
	\end{tikzpicture}
	\end{document}

![](./03_01_03_mitTikz/pasted_image010.png)


### Beispiel 2 - Pfeile mit vielen Ecken
``\draw [arrow] (left.north) |- ($(left) + (0,1)$) -| (right.north)`` fügt einen Zwischenknoten ein, über den der Pfeil geht.
	\begin{tikzpicture}
	[
	  node distance=3cm, %% node distnace eigentlich egal, weil ja at () benutzt wird
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (left)	[myrect] at (-2,0)	{ left };
	  \node (right)		[myrect] at (2,0)	{ right };
	  
	  \draw [arrow] (left.north) |- ($(left) + (0,1)$) -| (right.north);
	\end{tikzpicture}

![](./03_01_03_mitTikz/pasted_image015.png)


### unnötig kompliziertes Beispiel (mit viel Lerneffekt)

* man kann beliebig viele Zwischenpunkte einfügen
* ``$(left)!0.5!(right)$`` bedeutet mische die Koordinaten ``left`` und ``right`` mit Verhältnis **0.5**

	\begin{tikzpicture}
	[
	  node distance=3cm, %% node distnace eigentlich egal, weil ja at () benutzt wird
	  myrect/.style = {rectangle, rounded corners, minimum width = 2cm ,minimum height=1cm,text centered, draw=black, aspect=3},
	  arrow/.style = {thick,->,>=stealth}
	]
	  \node (left)	[myrect] at (-2,0)	{ left };
	  \node (right)		[myrect] at (2,0)	{ right };
	  
	  \draw [arrow] (left.north) |- ($(left) + (0,1)$) 
				     -| ($(left)!0.5!(right)$)
				     |- ($(right) + (0,-1)$) -| (right.south);
	\end{tikzpicture}

![](./03_01_03_mitTikz/pasted_image014.png)


### Anonymes \tikzstyle innerhalb \begin{tikzpicture}
der obere und untere Code sind äquivalent:
__WICHTIG:__

* oben eckige Klammern nach dem Gleichheitszeichen: ``\tikzstyle{startstop} = [rectangle, ...]``
* unten eckige Klammern nach dem Gleichheitszeichen: ``startstop/.style = {rectangle,...}``'


	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\tikzstyle{startstop} = [rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black]
	\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, text width=3cm, draw=black]
	\tikzstyle{decision} = [diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, aspect=2]
	\tikzstyle{arrow} = [thick,->,>=stealth]
	%...
	
	\begin{document}
	\begin{tikzpicture}
	%....
	\end{tikzpicture}
	\end{document}

	\usepackage{tikz}
	\usetikzlibrary{shapes.geometric, arrows, calc}
	
	\begin{document}
	\begin{tikzpicture}
		[	
			node distance=2cm,
			startstop/.style = {rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black},
		  	process/.style = {rectangle, minimum width=3cm, minimum height=1cm, text centered, text width=3cm, draw=black},
		  	decision/.style = {diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, aspect=2},
		  	arrow/.style = {thick,->,>=stealth}
		]
		
		%...
	\end{tikzpicture}
	\end{document}


Vorteil: der Style ist nur lokal gültig und kann in jedem ``tikzpicture`` neu gewählt werden.



Lösung
------

* alternativen sind möglich
* es wurde absichtlich viel code wiederverwendet. Es geht aber auch schöner und schlanker

	\begin{tikzpicture}
	[node distance=2cm,
	  startstop/.style = {rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black},
	  process/.style = {rectangle, minimum width=3cm, minimum height=1cm, text centered, text width=3cm, draw=black},
	  decision/.style = {diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, aspect=2},
	  arrow/.style = {thick,->,>=stealth}
	]
	
	  \node (eingang) 	[startstop] 			{ Eingang };
	  \node (i) 		[process, below of=eingang] 	{ $i=0$ };
	  \node (do) 		[process, below of=i] 		{ \texttt{do}$(\ldots)$ };
	  \node (decision)	[decision, below of=do] 	{ $i>i_\mathrm{th}$? };
	  \node (next_i)		[process, right of=do,
					    xshift=2cm]		{ $i=i+1$ };
	  \node (ausgang)	[startstop, below of=decision]	{ Ausgang };
	
	
	  % \draw [arrow] (start) -- (in1);
	  % \draw [arrow] (in1) -- (pro1);
	  % \draw [arrow] (pro1) -- (dec1);
	  % \draw [arrow] (dec1) -- node[anchor=east] {yes} (pro2a);
	  % \draw [arrow] (dec1) -- node[anchor=south] {no} (pro2b);
	  % \draw [arrow] (pro2b) |- (pro1);
	  % \draw [arrow] (pro2a) -- (out1);
	  % \draw [arrow] (out1) -- (stop);
	
	  \draw [arrow] (eingang) -- (i);
	  \draw [arrow] (i) -- (do);
	  \draw [arrow] (do) -- (decision);
	  \draw [arrow] (decision) -- node[near start,left] {true} (ausgang);
	  \draw [arrow] (decision) -| node[near start, anchor=south] {false} (next_i);
	  \draw [arrow] (next_i) |- ($(i)!0.5!(do) + (1,0)$) -- ($(do.north) + (1,0)$);
	
	  \draw [line cap=butt] ($(do.north east) + (-0.1,0)$)  -- ($(do.south east) + (-0.1,0)$);
	  \draw [line cap=butt] ($(do.north west) + (0.1,0)$)  -- ($(do.south west) + (0.1,0)$);
	
	\end{tikzpicture}


Einbinden in Latex mit \input{.../zeichnung.tikz}
-------------------------------------------------


* einbinden in latex mit ``\input{.../zeichnung.tikz}``
* __Satzpunkt in der Caption nicht vergessen__

	\begin{figure}[ht]
	  \centering
	    \input{bilder/drawings/tikz_drawing.tikz}
	  \caption{Einfache TikZ-Zeichnung.}
	\end{figure}



