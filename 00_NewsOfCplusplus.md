<!--
author:   Your Name

email:    your@mail.org

version:  0.0.1

language: en

narrator: US English Female

comment:  Try to write a short comment about
          your course, multiline is also okay.

import: https://raw.githubusercontent.com/liaScript/coderunner/master/README.md

-->

# Aktuelle Entwicklung von C++

Prüfungsmodalitäten


## Geschichte von C++

Aktuelle Entwicklungen


## Die wirklich neuen Sachen ...

### Concepts

### Coroutines

### Modules

### Ranges

## Erweiterung der Kernsprache


### Space Ship operator




```c SpaceShip.cpp
#include <compare>

struct MyInt {
  int value;
  MyInt(int value): value{value} { }
  auto operator<=>(const MyInt&) const = default;
};

int main(){
  return
}
```
@LIA.eval(`["main.cpp"]`, `g++ main.cpp -o a.out`, `./a.out`)


### constexpr


https://www.modernescpp.com/index.php/c-core-guidelines-programming-at-compile-time-with-constexpr

In C++11 wurde das `constexpr`-Schlüsselwort als Zusatz zu einer regulären `const`-Deklaration eingeführt, die einen konstanten Ausdruck definiert, der zur Kompilierungszeit ausgewertet werden kann.

```c constexpr14.cpp
#include <iostream>

constexpr auto gcd(int a, int b){
  while (b != 0){
    auto t= b;
    b= a % b;
    a= t;
  }
  return a;
}

int main(){

 std::cout << std::endl;

  constexpr auto i= gcd(11,121);

  int a= 11;
  int b= 121;
  int j= gcd(a,b);

  std::cout << "gcd(11,121): " << i << std::endl;
  std::cout << "gcd(a,b): " << j << std::endl;
  std::cout << std::endl;
}
```
@LIA.eval(`["main.cpp"]`, `g++ main.cpp -o a.out`, `./a.out`)

Beachten Sie, dass `constexpr` nur definiert, dass der Code zur Kompilierungszeit ausgewertet werden KANN und daher ein gültiger konstanter Ausdruck ist, aber nicht zwingend werden muss. Das ist auch nicht garantiert!

*Auszug aus Assembler code*


```c++
constexpr int foo(int factor) {
    return 123 * factor;
}

const int const_factor = 10;
int non_const_factor = 20;

const int first = foo(const_factor);
const int second = foo(non_const_factor);
```

*consteval*


Dies eröffnet dem Compiler viele Optimierungsmöglichkeiten, ermöglicht aber auch die Deklaration, dass z.B. eine Funktion einen konstanten Wert zurück gibt.

```c constFuction.cpp
#include <iostream>

constexpr auto giveConstValue_0(){
  return 678;
}

int giveConstValue_1() {
    return 678;
}

const int first = giveConstValue_0();
const int second = giveConstValue_1();
```

Die Verwendung von `constexpr` beseitigt hier jeden Zweifel und vermeidet mögliche zufällige Nebeneffekte, was den Code auf lange Sicht stabiler macht.

C++20 erweitert diese Funktionalität nun und erlaubt virtuelle constexpr-Funktionen, Entwickler können zudem `try` / `catch` innerhalb von constexpr verwenden.


```c constexpr20.cpp
#include <iostream>

int main(){

    //Beispiel einfügen
}
```
@LIA.eval(`["main.cpp"]`, `g++ main.cpp -o a.out`, `./a.out`)


Hier wird erstens zur Kompilierungszeit ausgewertet, da alle beteiligten Ausdrücke und Werte Konstanten sind und als solche zur Kompilierungszeit bekannt sind, während zweitens zur Laufzeit ausgewertet wird, da non_const_factor selbst keine Konstante ist. Das ändert zwar nichts an der Tatsache, dass foo() immer noch einen konstanten Wert zurückgibt, der Compiler kann sich nur noch nicht sicher sein, welcher genaue Wert das sein könnte. Um sicherzustellen, dass der Compiler den Wert kennt, führt C++20 das Schlüsselwort consteval ein, um eine Funktion als Sofortfunktion zu deklarieren. Die Deklaration von foo() als consteval anstelle von constexpr führt nun tatsächlich zu einem Fehler. Tatsächlich sind Sofortfunktionen eigentlich erst zur Kompilierungszeit bekannt, und in der Konsequenz macht dies die consteval-Funktionen zu einer Alternative für Makrofunktionen.



```c constexpr20.cpp
#include <iostream>

int main(){

    //Beispiel einfügen
}
```
@LIA.eval(`["main.cpp"]`, `g++ main.cpp -o a.out`, `./a.out`)


### Neue Lambda Funktionalitäten



### Verwendung von Attributen


## Standardbibliothek

### Zeitzonen
