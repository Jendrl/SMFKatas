## Agenda
1. Was ist ein Coding Dojo?
2. Coding Dojo Prinzipien
3. Was machen wir heute
4. Heutiges Thema - Clean Code
5. Clean Code: Functions
6. Heutiges Ziel
7. Katas
8. Tools
9. Coden!
10. Retrospektive

## Was ist ein Coding Dojo?
* Im Coding Dojo geht es darum, Coding bewusst zu üben und uns zu verbessern
	* z.B. TDD, Design von guten Test Cases, SOLID principles, Pair Programming etc.
* wir üben anhand von Coding Katas
* jedes Team ist im Grunde frei in der Wahl von Programmiersprache und Tools
* danach reflektieren wir darüber, was wir gelernt haben

## Coding Dojo Prinzipien
* Keiner ist Schüler oder Meister
* Feedback-Kultur: Feedback sollte konstruktiv sein, das Dojo soll ein sicherer Ort sein, um zu lernen
* Offenheit für alle Niveaus und Ideen
* nicht getesteter Code wird nicht gezeigt bzw. existiert nicht
* wenn die Aufgabe nicht "abgeschlossen" wird, dann ist es nicht schlimm; das Ziel ist es zu üben
* Las Vegas Prinzip: Was im Coding Dojo gesagt und entwickelt wird, bleibt im Coding Dojo. Nichts wird veröffentlicht

## Was machen wir während diesem Dojo?
* Zusammenfinden in Teams von 2, wenn wir eine ungerade Anzahl haben, dann eine 3er Gruppe
	* TDD Ping Pong / Randori in Pairs:
		* die erste Person entwickelt einen fehlschlagenden Test
		* die andere Person entwickelt Code bis der Test durchläuft
		* die selbe Person entwickelt den nächsten fehlschlagenden Test und der andere Entwickler ist wieder dran
		* entsprechend Red-Green-Refactor Cycle den Refactor Schritt nicht vergessen
* Katas: dieses Mal 3 zur Auswahl
	* Manhattan Distance
	* Balanced Paranthesis
	* LCD Digits
	* einige dieser Katas haben Constraints
		* Contraints sollen am Ende, nicht unbedingt während Entwicklung, eingehalten sein
	* wenn ihr schnell mit einem Kata durchkommt, könnt ihr ein anderes anfangen
* am Ende stellt jedes Team kurz seine Ergebnisse vor und was sie gelernt haben

## Heutiges Thema - Clean Code
* Was versteht man unter Clean Code?
	* Begriff, welcher durch das Buch von Robert C. Martin popularisiert wurde
	* darin befinden sich Richtlinien und Meinungen von ihm und seinen Kollegen
	* Zielsetzung: Code so schreiben, dass er für andere Entwickler in Monaten noch verständlich ist
	* elegant, effizient, wenige Dependencies, übersichtlich
	* "Clean Code does one thing well" - Bjarne Stroustrup
	* "Clean code reads like well-written prose" - Grady Booch

![](https://www.osnews.com/images/comics/wtfm.jpg)

* Warum Clean Code?
	* Code soll langfristig wartbar sein
	* Nicht-sauberer Code hat Kosten
		* Produktivität
		* Unzufriedenheit von Entwicklern
		* Spätere Redesigns sind unrealistisch, Kosten werden immer größer
	* "Wir sind Autoren": Wir schreiben Code für Leser, die unsere Mühe bewerten

* Wie schreibt man Clean Code?
	* Techniken und Prinzipien müssen diszipliniert angewandt werden
	* Nach einer Weile sollen Entwickler einen "Sinn" für (un)sauberen Code entwickeln

## Clean Code: Functions
* Do One Thing: `Functions should do one thing. They should do it well. They should do it only`
	* Was ist "One Thing"?
	* Hilfestellung: Ist die Funktion beschreibbar mit einem kurzen "TO"-Paragraph? `To [Funktionsname], we ...`
	* Bsp.: `TO RenderPageWithSetupsAndTeardowns, we check to see whether the page is a test page
and if so, we include the setups and teardowns. In either case we render the page in
HTML.`
* Ein Abstraktionslevel pro Funktion
	* Abstraktionslevel vermischen ist verwirrend
	* Solche Funktionen haben Tendenz immer mehr Details zu vermischen
	* Beispiel User
		* hohe Abstraktion: User Update
		* niedrige Abstraktion: Hashen des User Passworts
* Stepdown Rule
	* Code soll von oben nach unten lesbar sein
	* Funktionen sollten Funktionen niedrigerer Abstraktion verwenden
* Switch Statements
	* es ist oft schwer, ein kleines switch Statement zu machen, wachsen mit der Zeit
	* Verhindern oder Verstecken via Polymorphism: Gefahr, SRP/OCP zu brechen
	* Open/Closed-Principle: "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"
	* Single Responsibility Principle: "Gather together the things that change for the same reasons. Separate those things that change for different reasons"
* Descriptive Names
	* lange, beschreibende Namen sind besser als kurze, welche den Sinn nicht beschreiben können
	* langer Name ist besser als langer Kommentar
	* im gleichen Zuge Abkürzungen vermeiden
* Function Arguments
	* Ideale Anzahl an Argumenten ist 0, häufig sehr einfach zu verstehen
	* viele Argumente erhöhen Testaufwand
	* 1 Argument: häufig 2 Fälle
		* eine Frage: `fileExists(fileName)`
		* eine Transformation: `fileOpen(fileName)` &rarr; string zu File
	* 2 Argumente:
		* etwas schwerer zu lesen und zu verstehen
		* Argumente könnten vertauscht werden, z.B. `assertEquals(expected, actual)` oder `Point(1, 2)`
	* 3 Argument:
		* wesentlich schwerer zu verstehen
		* bei ähnlichen Parametertypen noch mehr Gefahr zu vertauschen
	* allerhöchstens 3 Argumente
	* Falls mehr Argumente benötigt werden, sollten verwandte Parameter gewrapped werden
		* z.B. `makeCircle(double x, double y, double radius)` &rarr; `makeCircle(Point center, double radius)`
* Flag Arguments
	* sollten vermieden werden
	* Methoden wie `render(true)` signalisieren, dass sie mehr als eine Sache macht und von außen ist nicht sichtbar, was gesetzt wird
* Output Arguments vermeiden, wenn es geht
	* Ergebnis als Parameter wird normalerweise nicht erwartet
* Verbs and Keywords
	* Functions werden üblich als Verben/Nomen Paare benannt, z.B. `writeField(name)`
	* Es gibt auch die `keyword`-Form: Enkodieren von Parametern in den Funktionsnamen
	* `assertEquals(expected, actual)` &rarr; `assertExpectedEqualsActual(expected, actual)`
* Side Effects
	* Side Effects ist Logik die nicht initial von der Methode erwartet werden, Lügen!
	* z.B. unerwartete Mutation von Klassen- oder globalen Variablen
	* bricht "Do One Thing"
* Extract try/catch blocks
	* Error Handling ist "One Thing"!
* Don't Repeat Yourself
	* viele Prinzipien dienen dazu, wiederholten Code zu reduzieren
	* OOP selbst dient dazu

## Zusammenfassung / Ziel
* Funktionen sollen "One Thing" machen
* Die Signatur sollte verständlich und lesbar sein
* Funktionen sollen wenige Parameter besitzen
* Der gesamte Code soll per Stepdown Rule lesbar sein

# Katas
https://github.com/Jendrl/SMFKatas

## Tools
* Schnelle IDE mit vielen Sprachen mit Test Template:
	* https://cyber-dojo.org/creator/home
* Repositories zum Klonen: https://github.com/lean-mind/coding-dojo-templates
