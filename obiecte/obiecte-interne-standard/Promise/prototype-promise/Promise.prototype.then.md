# Promise.prototype.then()

Această metodă returnează la rândul său un alt obiect `Promise`, care are nevoie să fie prelucrat. Metoda `then()` acceptă două argumente. Fiecare dintre aceste două argumente sunt callback-uri. Primul callback va prelucra rezultatele dacă acestea există. În caz contrar, cel de-al doilea callback va procesa eroarea. Cel de-al doilea callback este opțional.

Poți să înțelegi necesitatea callback-urilor ca niște acțiuni de răspus în cazurile posibile `fullfiled` ori `rejected`. Primul callback, cel al succesului și îndeplinirii acțiunii primește un singur argument, care este valoarea obținută în sine. Callbackul este executat cu prima ocazie când stiva se eliberează. Callback-ul în cazul `rejected` acceptă un argument acesta fiind și motivul pentru care nu s-a încheiat cu succes acțiunea.

Pentru ca o eroare să poată fi tratată, un `Promise` va trebui să paseze și cel de-al doilea callback - `reject` lui `catch`. Acest lucru este foarte util atunci când tratezi o promisiune anterioară într-o nouă promisiune.

```javascript
let oPromisiune = new Promise( (resolve, reject) => {
  altăPromisiune.then((rezultat) => {
    resolve(rezultat);
  }).catch(reject); // pasează reject-ul pentru a putea capta erorile
});
```

## Bifurcarea promisiunilor

Atunci când creezi o promisiune și folosești metoda `then`, dar nu într-o manieră înlănțuită, vei crea ramuri separate ale promisiunii.

```javascript
oPromisiune.then((rezultat) => {
  console.log(rezultat);
}).catch((error) => {
  console.error(error.message);
});

oPromisiune.then((rezultat) => {
  console.log(rezultat);
}).catch((error) => {
  console.error(error.message);
});
```

Acest lucru se întâmplă deoarece `then` returnează o promisiune.
