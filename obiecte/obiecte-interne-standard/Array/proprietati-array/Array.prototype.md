# Array.prototype

Această proprietate este obiectul prototip la care, în caz de nevoie, se pot adăuga proprietăți și metode, care să fie disponibile tuturor obiectelor array prin efectul moștenirii.

O chestie interesantă este că aplicând metoda `isArray()` asupra acestei proprietăți, este returnat *true*. Dacă interoghezi asupra tipului, vei afla că este un obiect.

```javascript
Array.isArray(Array.prototype); // true
typeof Array.prototype; // "object"
```
