# Dokumentacja program kolory 
Autor: Alicja Janeczko 3G

___

## Budowa i funkcjonalości programu:

___

* App.java
* KolorRGB.java
    * przechowuje wartości kolorów RGB
* KolorCMYK.java
    * przechowuje wartości kolorów CMYK
* PorownanieJasnosci.java
    * zawiera metody porównujące dwa kolory i wypisujące informację o tym, który jest jaśniejszy i o ile:
        * porownajJasnosc()
        * toRGB()
        * lumin()
    * zawiera metody porównujące dwa kolory i wypisujące informacje jaka barwa jest dominująca w danym kolorze:
        * dominant()
        * rgbToHSV()
* KolorPrzeciwny.java
    *  zawiera metody wypisujące wartości do koloru kontrastowego (przeciwnego):
       *  kolorPrzeciwny()
       *  kpRGB()
       *  kpCMYK()

___

## Opisy funkcji

___

### porownajJasnosc()
To funcja typu void. Odpowiada za:
* Rozpoznawanie przestrzeni barwy koloru poprzez sprawdzienie wielkości tablicy przechowującej wartości kolorów w przestrzeniach barw 
* Wywołanie funkcji odpowiadających za obliczenie względnej luminancji (jasności) koloru oraz dominującej barwy koloru
* Wypisanie na ekran informacje o tym, który kolor jest jaśniejszy (ma większą względną luminację-> w skali 0 - 100) i o ile

![porownajJasnosc](images/porownajJasnosc.PNG)

___

### toRGB()
Funkcja typu double, przyjmuje jako argumenty wartości c, m, y i k w zakresie 0 - 100 (przestrzeń barw CMYK). Zwraca funkcję lumin(). Odpowiada za:

* Zmianę przestrzeni barw z CMYK na RGB używając formuły:
> The R, G, B values are given in the range of 0 - 255. The red (R) color is calculated from the cyan (C) and black (K) colors:

    R = 255 × (1-C) × (1-K)   
> The green color (G) is calculated from the magenta (M) and black (K) colors:
    
    G = 255 × (1-M) × (1-K)  
> The blue color (B) is calculated from the yellow (Y) and black (K) colors:
    
    B = 255 × (1-Y) × (1-K)  
* Umożliwienie obliczenia względnej luminacji dla danego koloru z przestrzeni barw CMYK za pomocą przekonwertowania go do przestrzeni barw RGB, ponieważ nie ma żadnych rzetelnych źródeł w których został określony wzór na określenie postrzeganej jasności koloru CMYK
* Wywołanie funkcji **dominant()**

![toRGB](images/toRGB.PNG)

___

### lumin()
Funkcja typu double, przyjmuje jako argumenty wartości r, g, b w zakresie 0 - 255 (przestrzeń barw RGB). Zwraca obliczoną wartość względnej luminacji w zakresie 0 - 1. Odpowiada za:

* Obliczenie wartości względnej luminacji używając formuły zdefiniowanej przez *Web Content Accessibility Guidelines (WCAG)*:

>  Relative luminance is the relative brightness of any point in a colorspace, normalized to 0 for darkest black and 1 for lightest white. For the sRGB colorspace, the relative luminance of a color is defined as L = 0.2126 * R + 0.7152 * G + 0.0722 * B where R, G and B are defined as:

    if RsRGB <= 0.03928 then R = RsRGB/12.92 else R = ((RsRGB+0.055)/1.055) ^ 2.4
    if GsRGB <= 0.03928 then G = GsRGB/12.92 else G = ((GsRGB+0.055)/1.055) ^ 2.4
    if BsRGB <= 0.03928 then B = BsRGB/12.92 else B = ((BsRGB+0.055)/1.055) ^ 2.4

> and RsRGB, GsRGB, and BsRGB are defined as:

    RsRGB = R8bit/255
    GsRGB = G8bit/255
    BsRGB = B8bit/255

![lumin](images/luminance.PNG)
___

### dominant()
Funkcja typu String, 