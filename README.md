# 5401_Creational_Patterns

## Aufgabe:
Erstelle Interfaces und Klassen für die Veranschaulichung der erzeugenden Entwurfsmuster 'Singleton', 'Factory Method', 'Abstract Factory' und 'Prototype'.

### Singleton
- definiere ein einfaches Logger-Interface 'Logger' mit der Methode 'log(String message)'
- implementiere dieses Interface in einer einfachen Logger-Klasse 'TextLogger', die in eine Textdatei protokolliert
- baue diese Logger-Klasse zu einem Singleton aus (get-Methode, privater Konstruktor, lazy instantiation)

### Factory Method
- erstelle eine zweite Logger-Implementierung 'ObjectLogger', die zur Protokollierung Object-Streams nutzt
- entwickle eine primitive Testklasse 'TesterBase' zum Testen eines Loggers (Template Method 'test' mit wenigen log-Aufrufen)
- die Logger-Erzeugung soll in eine Factory-Methode (abstract) 'getLogger' gekapselt/ausgelagert werden
- leite die zwei Klassen 'TextTester' und 'ObjectTester' von dieser Klasse 'TesterBase' ab und implementiere darin 'getLogger' entsprechend ('TextLogger' bzw. 'ObjectLogger' erzeugen)

### Abstract Factory
- erstelle ein Interface 'Transmitter' mit den Methoden 'writeString' und 'connect'
- erstelle ein Interface 'Receiver' mit den Methoden 'readString' und 'connect'
- erstelle die Implementierungen 'ObjectTransmitter/-Receiver' - nutzen intern ObjectOutput-/InputStream
- erstelle die Implementierungen 'TextTransmitter/-Receiver' - nutzen intern BufferedWriter/-Reader
- diese Implementierungen verwenden zur Vereinfachung die Klassen PipedInput-/-OutputStream anstatt Sockets für das Übertragen von Text ('Text\*'-Implementierungen) bzw. Objekten ('Object\*'-Implementierungen)
- erzeuge eine abstrakte Klasse 'TransRecvFactory' mit den beiden Methoden 'getTransmitter' und 'getReceiver'
- leite davon eine Klasse 'ObjectTransRecvFactory' ab, und lasse diese ObjectTransmitter/-Receiver-Objekte liefern
- leite davon eine Klasse 'TextTransRecvFactory' ab, und lasse diese TextTransmitter/-Receiver-Objekte liefern
- Achtung: Piped-Streams müssen über 'connect' miteinander verbunden werden, dies soll in den Transmitter-/Receiver-Implementierungen erfolgen
- erzeuge eine Testklasse und nutze darin je Testlauf eine der beiden Factory-Implementierungen
- optional: optimal verfeinert wird die Abbildung von 'Abstract Factory' durch eine Realisierung des 'Singleton'-Musters für das einzige Factory-Objekt

### Prototype
- erstelle eine Prototype-Implementierung für die AbstractFactory-Implementierungen der vorigen Aufgabe
- die zu erzeugenden Objekttypen sollen in einer Protperties-Datei (name=Klassenname, Schlüssel: 'receiver', 'transmitter') festgelegt werden
- das Erzeugen der Prototyp-Instanzen soll über 'Class'- und 'Constructor'-Objekte erfolgen und das Erzeugen der Instanzen über die 'clone'-Methode des jeweiligen Prototyp-Objekts
- in der Factory soll dazu eine Map von Prototypen verwaltet und für die get-Aufrufe genutzt werden
- die Einhaltung der Kompatibilität (entweder TextReceiver/-Transmitter oder ObjectReceiver/-Transmitter) muss nun über die Konfiguration gewährleistet werden

## Tip:
- erstelle ein Projekt mit mehreren Packages z.B. ```singltn```, ```factMeth```, ```abstFact``` und ```prototp```
