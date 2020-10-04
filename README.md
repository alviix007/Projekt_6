# Projekt_6 Taster - Lorena & Álvaro 10c

Hallo, wir sind Álvaro und Lorena aus der 10c und heute werden wir euch den Projekt namens Taster vorstellen. 

Die Aufgabe bei diesem Projekt ist es, ein Programm zu schreiben, mit dem man mit drei Tastern jeweils eine Glühlampe und zwei Motoren ein und ausschalten kann.

Als erstes, erklären wir euch die unterschiedlichen Strukturen und Funktionen, die für dieses Projekt spezifisch innerhalb der Funktion void setup wissenswert sind und was ihr bei der Funktion void loop können muss.

> Wir haben ein Video über das Thema gemacht, wo wir die verschiedene Funktionen des Codes erklären. Wenn ihr das Video sehen möchetet, clicke [HIER](buenastardes.com)
---
Wir werden die Funnktionen in diese Reihenfolge erklären:
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

Die Funktion `pinMode()` erlaubt zwei Argumente, eine Pinnummer, die wir definieren wollen, und den Modus, in dem sich der Pin befindet.


```arduino
//Beispiel:
pinMode(13, OUTPUT);
```

Im obigen Beispiel deklarieren wir den Pin `13` als `OUTPUT`. Das heißt, auf Pin `13` befindet sich eine Komponente, die Signale vom Arduino empfängt.

Wir weisen darauf hin, dass der Modus, der die Funktion `pinMode()` akzeptiert, viele Dinge sein kann. Wenn wir einen Pin als `OUTPUT` deklarieren, sagen wir der Arduino-Platte, dass die Komponente auf Pin `13` Signale vom Arduino empfängt. 

Was für euch neu sein kann, ist der `INPUT` Modus. Wenn wir einen Pin als `INPUT` deklarieren, sagen wir dem Arduino, dass die Komponente, die mit Pin `13` verbunden ist, Signale an den Arduino sendet.
```arduino
//Beispiel:
pinMode(13, INPUT);
```

>Denkt daran:                                             
> OUTPUT: Die Komponente empfangen Signale der Arduino.               
> INPUT: Die Komponente senden Signale an der Arduino.

In diesem Projekt musst ihr zusätzlich zum neuen `INPUT_PULLUP` Modus verwenden. Was genau ist `INPUT_PULLUP`? Dieser Modus, wie `INPUT`, sagt dem Arduino, dass der Komponent, der mit dem betreffenden Pin verbunden ist, Signale an den Arduino sendet.
```arduino
//Beispiel:
pinMode(13, INPUT_PULLUP);
```
 Der einzige Unterschied zum `INPUT` Modus ist, dass die empfangenen Werte umgekehrt werden. Sagen wir, wir haben einen Sensor, der `HIGH`- oder `LOW`-Signale an den Arduino sendet.
 
  Wenn der Sensor aktiviert ist, sendet er `HIGH`-Signale. Dies geschieht, wenn der Pin als `INPUT` deklariert wird. Wenn wir den Pin als `INPUT_PULLUP` deklarieren, geschieht das Gegenteil. Wenn der Sensor eingeschaltet ist, wird er `LOW`-Signale an den Arduino senden.

> Denkt daran:                           
> Wenn eine als `INPUT` deklarierte Komponente `LOW`-Signale an den Arduino sendet, sendet eine als `INPUT_PULLUP` deklarierte Komponente `HIGH`-Signale, d. h. das Gegenteil.

---
## if(){}

```arduino
if(Bedingung){Anweisungen;}

//oder

if(Bedingung){
    Anweisungen;
}
```
Die `if(){}` Funktion testet ob eine bestimmte Bedingung wahr ist oder nicht. Das Format für eine `if`-Abfrage wird in obigen Beispiel vorgestellt.

Wenn die Bedingungen in den runden`()` Klammern erfüllt sind, wird der Code in den geschweiften`{}` Klammern ausgeführt. Wenn die Bedingung nicht erfüllt ist, wird der Code in den geschweiften`{}` Klammern einfach übersprungen. 

```arduino
//Beispiel:
if(1 == 1){
    //Anweisungen
    Serial.println("Anweisungen werden ausgeführt")
}
```
Die Anweisung bei diesem Beispiel ist es, dass ein Satz gedruckt wird. In diesem Fall wird die Anweisung ausgeführt, weil die Bedingungen in den runden`()` Klammern erfüllt sind. Also jeder weiss das 1 gleich 1 ist. 
```arduino
//Beispiel:
if(1 == 2){
    //Anweisungen
    Serial.println("Anweisungen werden nicht ausgeführt")
}
```

Im Gegenteil dazu wird die Bedingung in diesem zweiten Beispiel nicht erfüllt, weil 1 ist nicht gleich 2, deshalb wird den Code innerhalb der geschweiften`{}` Klammern übersprungen. 
 
 ---
 ## digitalRead()
 ```arduino
digitalRead(pin);
```
Die Funktion digitalRead() liest nur einen Wert von einem vorgegebenen Digitalpin ein, der als `INPUT` oder `INPUT_PULLUP` konfiguriert wurde. Als Parameter wird daher nur die Nummer des Arduino-Digitalpins benötigt.

Angenommen, auf Pin `10` ist ein Taster verbunden. Die Funktion würde wie folgt geschrieben:
```arduino
//Beispiel
pinMode(10, INPUT);
digitalRead(10);
```
Wenn der Taster gedrückt wird, liest `digitalRead()` den `HIGH`-Wert, und wenn er nicht gedrückt ist, liest er den `LOW`-Wert. Einfach, oder?

Die Dinge werden etwas komplizierter, wenn wir den Pin-Modus ändern. Wir haben vorhin darüber gesprochen, dass man den Pin in `INPUT` oder `INPUT_PULLUP` setzen kann. Im folgenden Beispiel deklarieren wir den Pin als `INPUT_PULLUP`:
```arduino
//Beispiel
pinMode(10, INPUT_PULLUP);
digitalRead(10);
```
Wenn ein Pin als `INPUT_PULLUP` deklariert ist, werden seine Werte umgekehrt. Das heißt, wenn der Taster früher `HIGH`-Signale gab, als er fest war, sendet er jetzt `LOW`-Signale.

> Also merkt ihr euch:  
> Wenn ein Pin als `INPUT_PULLUP` deklariert wird, entsprechen seine Werte den Werten eines als INPUT deklarierten Pin.

 ---
 ## == Operator
  ```arduino
x == y
```
Der Vergleichsoperator mit den beiden Gleichheitszeichen vergleicht hier die linke Variable `x` mit dem Wert oder der Variablen rechts vom Operator in diesem Fall `y`. 

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
Der Logisch-NOT-Operator wird als Ausrufezeichen im Code dargestellt und bedeutet: macht genau das Gegenteil. Hier ist das Gegenteil von LOW, HIGH und von HIGH, LOW. 

```arduino
!LOW = HIGH //Das Gegenteil von LOW is HIGH
!HIGH = LOW // Das Gegenteil von HIGH is LOW
```

---
## Zeile des Codes
```arduino
if (digitalRead(tasterPin) == LOW){ 
    digitalWrite(komponentPin,!digitalRead(komponentPin)); 
    delay(180); 
}
```

Dieser Code überprüft, ob ihr die angegebene Taste auf dem Pin `tasterPin` als `INPUT_PULLUP` drücken und schaltet dann die Motoren oder Glühbirnen, die auf dem Pin `komponentPin` angeschlossen und als `OUTPUT` deklariert sind, ein.

Um ein Beispiel zu nennen, verbinden wir einen Taster und eine Glühbirne mit dem Arduino und führen den Code aus.

```arduino
void setup(){
    pinMode(13, INPUT_PULLUP); //Taster als INPUT_PULLUP
    pinMode(10, OUTPUT); //Glühbirne als OUTPUT
}

void loop(){
    if (digitalRead(13) == LOW){ //Wird der Taster gedrückt?
        digitalWrite(10,!digitalRead(10)); // Den Wert der Glühbirne umkehren
        delay(180); //180 Milisekunden warten
    }
}
```

Im `void setup(){}` ist der Taster mit Pin `13` und die Glühbirne mit Pin `10` verbunden. Der Taster wird als `INPUT_PULLUP` und die Glühbirne als `OUTPUT` deklariert. 

Im `void loop(){}` prüfen wir, ob der Taster mit der Funktion `if(){}` gedrückt wird, in den Anweisungen setzen wir den Wert der Glühbirne um. Das heißt, wenn es vorher eingeschaltet war, lesen wir den Wert `HIGH` und setzen es auf den Gegenwert, d. h. `LOW`. 

Am Ende warten wir `180` Millisekunden mit der Funktion `delay()`. Das tun wir, weil wenn man einen Taster am Arduino anschliesst und diesen drückt, kann es sein, dass der Arduino den Tastendruck als mehrmaliges Drücken registriert. Dieses Phänomen nennt man "prellen". Im Normalfall kann man dieses Problem durch das Einfügen eines delays von `180` Millisekunden lösen.

---
## Zussamenfassung

Um das endgültige Projekt zu programmieren, müsst ihr eine Glühbirne, zwei Motoren und drei Taster an die digitalen Pins eurer Wahl anschließen. 

Innerhalb des `void setup(){}` müsst ihr die Pins verbunden mit den Tastern als `INPUT_PULLUP` definieren und die mit der Glühbirne und den Motoren als `OUTPUT`. 

Im `void loop(){}` soll man die Codezeile benutzen, die wir vorher erklärt haben. Diese Zeile muss 3 Mal geschrieben werden, eine für jeden Taster und Motor oder Glühbirne.

---

Das ist alles. Wir hoffen ihr habt alles verstanden!

 Hier endet die Erklärung des Projekt_6, wenn ihr etwas noch nicht verstanden habt, zögert ihr nicht, Lorena oder Álvaro zu kontaktieren, um ihre Zweifel zu lösen. Wir werden ihnen gerne helfen, so gut wir können.

 > Falls ihr den Video zum endgültigen Projekts sehen wollt, konnt ihr [HIER](todavianotenemoslinkestosecambiadespues.com) clicken


### Viel Spaß beim Programmieren!
