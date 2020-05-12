<!-- .slide: data-background="#111111" -->

# Podstawy C++

## Typy danych

<a href="https://coders.school">
    <img width="500" data-src="../img/coders_school_logo.png" alt="Coders School" class="plain">
</a>

===

## Prosta matematyka

* <!-- .element: class="fragment fade-in" --> 1 bajt == 8 bitów
* <!-- .element: class="fragment fade-in" --> W binarnym totolotku wylosowane liczby mogą mieć `0` lub `1`
* <!-- .element: class="fragment fade-in" --> Zatem podczas losowania 8 numerków możemy otrzymać przykładowo: `1 0 1 0 1 0 1 0`
* <!-- .element: class="fragment fade-in" --> Takich kombinacji jest dokładnie `128 -> (2^8)`
* <!-- .element: class="fragment fade-in" --> Zatem na 1 bajcie (8 bitach) możemy zapisać 128 liczb, np. od 0 do 127
* <!-- .element: class="fragment fade-in" --> Jeżeli w totolotku losujemy 32 numerki, (32/8 = 4) czyli 4 bajty to takich kombinacji jest `2^32` (czyli ponad 4 miliardy)

===

## Typ pusty - `void`

Nie można tworzyć obiektów typu `void`. Służy do zaznaczenia, że funkcja nic nie zwraca.
Można tworzyć wskaźniki `void*` (zła praktyka w C++).

===

## Typ logiczny - `bool`

* Rozmiar: 1 bajt
  * `sizeof(bool) == 1`
* 2 możliwe wartości
  * `false`
  * `true`

===

## Typy znakowe

* Romiar: 1 bajt
* 256 możliwych wartości
* `char` -> od `-128` do `127`
* `unsigned char` -> od `0` do `255`

Przedrostek `unsigned` oznacza, że typ jest bez znaku (bez liczb ujemnych), czyli od 0 do jakieś dodatniej wartości.

Rozmiar typów logicznych i znakowych to zawsze 1 bajt.

Rozmiary dalszych typów zależą od platformy np. 32 bity, 64 bity.

===

## Typy całkowitoliczbowe

* `short (unsigned short)` - co najmniej 2 bajty
* `int (unsigned int)` - co najmniej 2 bajty
* `long (unsigned long)` - co najmniej 4 bajty
* `long long (unsigned long long)` - co najmniej 8 bajtów

===

## Typy zmiennoprzecinkowe

* `float` - zwykle 4 bajty
* `double` - zwykle 8 bajtów
* `long double` - zwykle 10 bajtów (rzadko stosowany)
* Nie istnieją wersje `unsigned`. Typy zmiennoprzecinkowe zawsze mogą mieć ujemne wartości
* Posiadają specjalne wartości:
  * `0`, `-0` (ujemne zero)
  * `-Inf`, `+Inf` (Infinity, nieskończoność)
  * `NaN` (Not a Number)

Uwaga! Porównanie `NaN == NaN` daje `false`

Zaawansowana lektura: [Standard IEEE754 definiujący typy zmiennoprzecinkowe](https://en.wikipedia.org/wiki/IEEE_754)
===

## Aliasy typów

Istnieją też typy, która są aliasami (inne nazewnictwo w celu lepszego zrozumienia typu).

`std::size_t` w zależności od kompilatora może być typu (`unsigned short`, `unsigned int`, `unsigned long`, `unsigned long long`). Przeważnie jest on typu `unsigned int`. Warto wykorzystywać go, gdy nasza zmienna będzie odnosić się do jakiegoś rozmiaru np. wielkość tablicy.

Własne aliasy typów możemy tworzyć używając `typedef` lub `using`

```cpp
typedef int Number;
Number a = 5;   // int a = 5;

using Fraction = double;
Fraction b = 10.2;  // double b = 10.2;
```

===

## Typ `auto`

W pewnych miejscach możemy użyć typu `auto`. Kompilator sam wydedukuje typ, np. na podstawie przypisanej wartości.

```cpp
  auto num = 5;         // int
  auto num = 5u;        // unsigned int
  auto num = 5.5;       // double
  auto num = 5.f;       // float
  auto letter = 'a';    // char
  auto num = false;     // bool
  auto sth;             // compilation error, unable to deduce type
```

===

Standard C++ definiuje taką zależność pomiędzy rozmiarami typów

```cpp
1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)
```

===

## Operacje arytmetyczne

* Podstawowe: + - * /
* Modyfikujące zmienną: += -= *= /=
* Inkrementujące (+1) zmienną: ++
* Dekrementujące (-1) zmienną: --
  
Przykłady

```cpp
int a = 5 + 7; // a = 12
```

```cpp
int a = 5;
a += 7; // a = 12
```

```cpp
int a = 5;
++a; // a = 6
a--; // a = 5
```

===

## Pytania

```cpp
int i = 5;
auto j = i++ - 1;
```

<span class="fragment fade-in">Ile wynoszą wartości `i` oraz `j`?</span>

`i = 6` <!-- .element: class="fragment fade-in" -->

`j = 4` <!-- .element: class="fragment fade-in" -->

<span class="fragment fade-in">Jakiego typu jest `j`?</span>

`int` <!-- .element: class="fragment fade-in" -->

===

## Mały suchar

Kim jest Hobbit? <!-- .element: class="fragment fade-in" -->

Jest to 1/8 Hobbajta :) <!-- .element: class="fragment fade-in" -->

===

Linki dla poszerzenia wiedzy:

* [Fundamental types on cppreference.com](https://en.cppreference.com/w/cpp/language/types)
* [Standard IEEE754 definiujący typy zmiennoprzecinkowe](https://en.wikipedia.org/wiki/IEEE_754)