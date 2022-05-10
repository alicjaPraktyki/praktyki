# Dokumentacja program kolory

**Autor: Alicja Janeczko 3G**

## Budowa i funkcjonalości programu:
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