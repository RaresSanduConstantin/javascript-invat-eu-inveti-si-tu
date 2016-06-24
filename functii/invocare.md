# Invocarea funcțiilor

Este chemarea funcțiilor pentru a fi executate.

## Mantre

- A invoca înseamnă aplicarea funcției pe zero sau mai multe argumente.
- De fiecare dată când o funcție este invocată, se creează un nou „mediu” (**environment**).
- Funcțiile sunt invocate într-un loc care determină rezultatul, adică într-un anumit *context*.
- La invocarea funcțiilor pe lângă argumente sunt pasate „tacit” `this` și `arguments`.
- Când invoci funcția ca metodă a unui obiect, acel obiect devine **contextul** funcției și acesta devine disponibil în funcție prin intermediul parametrului `this`.
- `this` este un obiect-context: pentru funcții simple este `window`, pentru metode este obiectul în care se execută iar pentru noile obiecte create este chiar noul obiect generat.
- există patru cazuri în care o funcție este invocată:
  - ca funcție invocată în mod direct;
  - ca metodă, fapt care leagă invocarea de un obiect;
  - ca și constructor prin care un nou obiect este generat;
  - prin folosirea lui call() și apply().
- Contextul de execuție al unei funcții se modifică după „locul” în care a fost invocată.
- O funcție are acces și poate performa operațiuni asupra obiectului în interiorul căruia a fost invocată.


## Ce se întâmplă când o funcție este invocată?

1. se aplează funcția iar locul în care se întâmplă acest lucru se numește **call-site**
- Se stabilește **execution context** - contextul de execuție
  1. vorbim de context de execuție global (obiectul **window**) când funcția este invocată ca funcție, nu ca metodă sau callback
  2. contextul de execuție este o sumă de informații (activation record) privind
    1. **unde** a fost apelată funcția (în callstack)
    2. ce parametri au fost pasați, etc,
    3. referința `this` care va fi folosită pe durata execuției funcției.

2. Se generează un obiect căruia îi sunt pasate automat ARGUMENTELE într-o colecție aemănătoare unui array și **this**.

**arguments** este o colecție (seamănă dar NU ESTE UN ARRAY) a tuturor argumentelor pasate funcției și are proprietatea length pentru a afla numărul argumentelor pasate. Valorile pot fi obținute prin indecși arguments[i].

Invocarea funcțiilor se poate face în patru cazuri:

1. ca funcții;
2. ca metode;
3. ca și constructori cu `new`;
4. indirect prin apelarea într-un context de execuție diferit folosind call() și apply() (vezi binding explicit la `this`).

## Cazurile de invocare
### Funcție invocată

Această invocare se întâmplă atunci când este folosit operatorul `()`.

### Invocarea ca metodă

Când invoci funcția ca metodă a unui obiect, acel obiect devine **contextul** funcției și acesta devine disponibil în funcție prin intermediul parametrului `this` pasat tacit împreună cu `arguments`. Acesta este mecanismul de acces la membrii obiectului.

### Invocarea ca și constructor

#### Regulile constructorului

1. Se creează un obiect nou.
2. Se creează o legătură la obiectul prototype al funcției a cărui identificator a fost folosit cu ```new```. Se creează legătura prototipală.
3. Obiectul generat automat este pasat funcției cu rol de constructor ca fiind parametrul `this` și astfel, devine contextul de execuție a funcției constructor invocate (`this` este pasat ca parametru împreună cu `arguments`).
4. Dacă funcția nu returnează ceva, atunci înainte de a se închide blocul („}”), ```this``` va fi returnat automat.

### Invocarea funcțiilor prin call() și apply()

Cele două funcții realizează un binding explicit a funcției cu un nou context de execuție. Se face „un împrumut” al mecanismelor și proceselor interne ale funcției în contextul de lucru oferit de un anume obiect.

## Invocare condițională

Poți invoca rapid prin evaluarea Truthy sau Falsy a unei expresii

```js
var testVal = 200;
testVal >= 150 && console.log("Acest mesaj va apărea dacă evaluarea lui testVal este truthy");            // Acest mesaj va apărea dacă evaluarea lui testVal este truthy
testVal >= 150 || console.log("Acest mesaj va apărea doar dacă evaluarea din left-hand-side este true");  // true
```

În caz de valoare truthy, pentru && se va afișa mesajul, dacă false, va returna false expresia.
În caz de valoare truthy, pentru || se va returna `true`. Pentru false, se va afișa mesajul.

Un alt caz este apelarea unui callback:

```js
function tester(callback){
  callback && callback();
};
```