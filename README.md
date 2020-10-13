# Projekt_6 Taster - Lorena & Álvaro 10c

Hallo, wir sind Álvaro und Lorena aus der 10c. Hiermit werdet ihr eine von uns ausführliche Erklärung zum Projekt Taster bekommen.  

Die Aufgabe bei diesem Projekt ist es, ein Programm zu schreiben, mit dem man mit drei Tastern jeweils eine Glühlampe und zwei Motoren ein- und ausschalten kann.

Als erstes, erklären wir euch die unterschiedlichen Strukturen und Funktionen, die für dieses Projekt spezifisch innerhalb der Funktion void setup() wissenswert sind und was ihr bei der Funktion void loop() können muss.

> Wir haben ein Video über das Thema gemacht, wo wir die verschiedene Funktionen des Codes erklären. Wenn ihr das Video nochmal sehen möchtet, clicke [HIER](https://youtu.be/ne3wZrqCxOM)
---
Wir werden die Funktionen in der folgenden Reihenfolge erklären:
1. `pinMode()`
1. `if(){}`
1. `digitalRead()`
1. `== Operator`
1. `! Operator`
1. `Zeile des Codes`
1. `Zussamenfassung`
---
## pinMode()

```arduino
pinMode(pin, mode);
```

Die Funktion `pinMode()` konfiguriert den spezifierten Digitalpin als Input oder Output.  Zwei Parameter sind notwendig, die jeweilige Pinnummer und den zugehörigen Modus. 

```arduino
//Beispiel:
pinMode(13, OUTPUT);
```

Im obigen Beispiel deklarieren wir den Pin `13` als `OUTPUT`. Das heißt, der Arduino sendet ein Signal nach außen. 

Allerdings, kann aber auch ein Pin als `INPUT` konfiguriert werden. Wenn wir einen Pin als `INPUT` deklarieren werden den Arduino Signale von außen gesendet werden.

```arduino
//Beispiel:
pinMode(13, INPUT);
```

>Denkt daran:                                             
> OUTPUT: Der Arduino sendet ein Signal nach außen.               
> INPUT: Signale, Informationen und Werte werden den Arduino gesendet.

In diesem Projekt müsst ihr zusätzlich den Modus `INPUT_PULLUP` verwenden. 
Was bedeutet `INPUT_PULLUP`? 
Mit diesem Modus werden eingebaute Widerstände innerhalb der Arduino-Platine aktiviert.
Dieser Modus, genau so wie bei `INPUT`, sagt dem Arduino, dass der Komponent, der mit dem betreffenden Pin verbunden ist, Signale an den Arduino sendet.

```arduino
//Beispiel:
pinMode(13, INPUT_PULLUP);
```
Der einzige Unterschied zum `INPUT` Modus ist es, dass die empfangenen Werte umgekehrt werden d.h. der Verhalten der Pins wird invertiert. 
Sagen wir, wir haben einen Sensor, der `HIGH`- oder `LOW`-Signale an den Arduino sendet.
Wenn der Sensor aktiviert ist, sendet er `HIGH`-Signale. Dies geschieht, wenn der Pin als `INPUT` deklariert wird. Wenn wir den Pin als `INPUT_PULLUP` deklarieren, geschieht das Gegenteil. Also ist der Sensor eingeschaltet, wird er `LOW`-Signale an den Arduino senden.

> Denkt daran:                           
> Wenn ein Taster, verbunden mit einem als `INPUT` deklarierten Pin, `LOW`-Signale an den Arduino sendet, sendet der Komponent, wenn es mit einem als `INPUT_PULLUP` deklarierten Pin verbunden ist, `HIGH`-Signale, d. h. das Gegenteil.

---
## if(){}

```arduino
if(Bedingung){Anweisungen;}

//oder

if(Bedingung){
    Anweisungen;
}
```
Die `if(){}` Funktion testet ob eine bestimmte Bedingung wahr ist oder nicht. Das Format für eine `if`-Abfrage wird im obigen Beispiel vorgestellt.

Wenn die Bedingungen in den runden`()` Klammern erfüllt sind, wird der Code in den geschweiften`{}` Klammern ausgeführt. Wenn die Bedingung nicht erfüllt ist, wird der Code in den geschweiften`{}` Klammern einfach übersprungen. 

```arduino
//Beispiel:
if(1 == 1){
    //Anweisungen
    Serial.println("Anweisungen werden ausgeführt")
}
```
Die Anweisung bei diesem Beispiel lautet, druckt die Daten `("Anweisungen werden ausgeführt")`an den seriellen Anschluss als von Menschen lesbarer Text, d.h. schreibt es einfach am PC Monitor. 
In diesem Fall wird die Anweisung ausgeführt, weil die Bedingung in den runden`()` Klammern erfüllt ist, denn 1 ist gleich 1. 

```arduino
//Beispiel:
if(1 == 2){
    //Anweisungen
    Serial.println("Anweisungen werden nicht ausgeführt")
}
```

Im Gegenteil dazu, wird die Bedingung in diesem zweiten Beispiel nicht erfüllt, weil 1 nicht gleich 2 ist, deshalb wird den Code innerhalb der geschweiften`{}` Klammern übersprungen. 
 
 ---
 ## digitalRead()
 ```arduino
digitalRead(pin);
```
Die Funktion digitalRead() liest nur einen Wert von einem vorgegebenen Digitalpin ein, der als `INPUT` oder `INPUT_PULLUP` konfiguriert wurde. Als Parameter wird daher nur die Nummer des Arduino-Digitalpins benötigt.

Ist am Pin `10`ein Taster verbunden, würde die Funktion wie folgt aussehen: 

```arduino
//Beispiel
pinMode(10, INPUT);
digitalRead(10);
```
Wenn der Taster gedrückt wird, liest `digitalRead()` den Wert `HIGH` ein, und wenn nicht, den Wert `LOW`. Einfach, oder? 

Die Dinge werden etwas komplizierter, wenn wir den Pin-Modus ändern. Wir haben vorhin darüber gesprochen, dass man Pins als `INPUT` oder `INPUT_PULLUP` setzen kann, aber um Störungen zu verhindern, es besser ist, die eingebaute Widerstände zu aktivieren.  

Im folgenden Beispiel deklarieren wir den Pin als `INPUT_PULLUP`:
```arduino
//Beispiel
pinMode(10, INPUT_PULLUP);
digitalRead(10);
```
Wenn ein Pin als `INPUT_PULLUP` deklariert ist, werden seine Werte umgekehrt. Das heißt, wenn der Taster früher `HIGH`-Signale gab, als es gedrückt war, sendet er jetzt `LOW`-Signale.

> Also merkt ihr euch:  
> Wenn ein Pin als `INPUT_PULLUP` deklariert wird, entsprechen seine Werte den Gegenwerten eines als `INPUT` deklarierten Pins.

 ---
 ## == Operator
  ```arduino
x == y
```
Der Vergleichsoperator mit den beiden Gleichheitszeichen vergleicht hier die linke Variable `x` mit dem Wert oder der Variablen rechts vom Operator, in diesem Fall `y`. 

Es gibt `True` d.h. wahr zurück, wenn die beiden Operanden gleich sind. 

Also z.B. wenn wir die Zahl `1` und die Zahl `2` mit den Operator vergleichen, ergibt es `False`, weil es nicht die gleiche Zahl ist. Auf der anderen Seite, wenn wir die Zahl `1` und die Zahl `1` miteinander vergleichen, ergibt es `True`, weil es dieselbe Zahl ist.
```arduino
//Beispiel
1 == 2 //Das eribt False
1 == 1 //Das ergibt True
```
Dieser Operator wird häufig innerhalb einer if-Schleife benutzt, um z.B. zwei Bedingungen logisch zu verknüpfen.
```arduino
//Beispiel:
if(10 == 10){
    Serial.println("Anweisungen werden ausgeführt")
}

if(10 == 11){
    Serial.println("Anweisungen werden nicht ausgeführt")
}
```

---
## ! Operator
```arduino
!x = xGegenteil
```
Der Logisch-NOT-Operator wird als Ausrufezeichen im Code dargestellt und bedeutet: Macht genau das Gegenteil. Hier ist das Gegenteil von LOW, HIGH und von HIGH, LOW. 

```arduino
!LOW = HIGH //Das Gegenteil von LOW is HIGH
!HIGH = LOW // Das Gegenteil von HIGH is LOW
```

---
## Zeile des Codes
```arduino
if (digitalRead(tasterPin) == LOW){ 
    digitalWrite(ledPin,!digitalRead(ledPin)); 
    delay(180); 
}
```

Dieser Code überprüft, ob ihr die angegebene Taste auf dem Pin `tasterPin` als `INPUT_PULLUP` drückt und schaltet dann in diesem Fall die Glühbirne, die auf dem Pin `ledPin` angeschlossen und als `OUTPUT` deklariert ist, ein.

Um ein Beispiel mit den jeweiligen Zahlen zu nennen, verbinden wir wie gesagt einen Taster und eine Glühbirne mit dem Arduino und führen den Code aus.

```arduino
void setup(){
    pinMode(13, INPUT_PULLUP); // Taster als INPUT_PULLUP
    pinMode(10, OUTPUT); // Glühbirne als OUTPUT
}

void loop(){
    if (digitalRead(13) == LOW){ // Wird der Taster gedrückt?
        digitalWrite(10,!digitalRead(10)); // Den Wert der Glühbirne umkehren
        delay(180); //180 Millisekunden warten
    }
}
```

Bei `void setup(){}` werden die Pins `13`, der mit dem Taster verbunden ist, und `10`, der mit der Glühbirne in Kontakt ist, konfiguriert. Der Taster wird als `INPUT_PULLUP` und die Glühbirne als `OUTPUT` deklariert. 

Bei `void loop(){}` prüfen wir mit der Funktion `if(){}` , ob der Taster gedrückt wird oder nicht. In den Anweisungen setzen wir den Wert der Glühbirne um. Das heißt, wenn die LED vorher eingeschaltet war, lesen wir den Wert `HIGH` und setzen es auf den Gegenwert, d.h. `LOW`. Die Glühlampe ist jetzt ausgeschaltet. 

Am Ende wartet der Arduino `180` Millisekunden mit der Funktion `delay()`. Das tun wir, weil wenn man einen Taster am Arduino anschließt und diesen drückt, kann es sein, dass der Arduino den Tastendruck als mehrmaliges Drücken registriert. Dieses Phänomen nennt man "prellen". Im Normalfall kann man dieses Problem durch das Einfügen eines delays von `180` Millisekunden lösen.

---
## Zusammenfassung

Um das endgültige Projekt zu programmieren, müsst ihr eine Glühbirne, zwei Motoren und drei Taster an die digitalen Pins eurer Wahl anschließen. 

Innerhalb der Funktion `void setup(){}` soll man die Pins verbunden mit den Tastern als `INPUT_PULLUP` definieren und die mit der Glühbirne und den Motoren als `OUTPUT`. 

Bei `void loop(){}` muss die Codezeile, die wir vorher erklärt haben, mehrmals verwendet werden. Diese Zeile soll dreimal geschrieben werden und zwar für jeden Taster und Motor oder Glühbirne.

---

Das ist alles. Wir hoffen ihr habt alles verstanden!

Hier endet die Erklärung des Projekt_6, wenn ihr etwas noch nicht verstanden habt, könnt ihr uns gerne fragen. 

 > Falls ihr den Video zum endgültigen Projekts sehen wollt, könnt ihr [HIER](https://youtu.be/ne3wZrqCxOM) clicken. 


### Viel Spaß beim Programmieren!
