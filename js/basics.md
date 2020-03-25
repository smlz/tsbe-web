# JS

## Einfache Datentypen

### Nichts

`undefined` und `null` werden gebraucht, um die Absenz von einem Resultat zu markieren. `undefined` ist der Default.

```js {cmd=node}
console.log(undefined)
console.log(null)

let l = [1]
console.log(l.pop())
console.log(l.pop())

let o = {a: 42}
console.log(o.a)
console.log(o.b)

console.log('Marco'.match(/r/))
console.log('Marco'.match(/R/))
```

### Wahr oder Falsch (boolean)

```js {cmd=node}
let wahr = true
if (wahr) {
  console.log('Es ist wahr')
}
```

### Zahlen

Es gibt nur einen Datentyp für Zahlen: `double`.

```js {cmd=node}
console.log(1 + 2)
console.log(1 + 2.0)
console.log(1.1 + 2.1)
console.log(1 / 3)
console.log(Math.PI * 2)
console.log(Math.log2(1024))
```

### Text (string)

Einfache oder doppelte Anführungszeichen markieren Text.

Empfehlung: In JS Code einfache Anführungszeichen, im HTML doppelte verwenden.

```js {cmd=node}
console.log('Hallo')
console.log("Hallo")
console.log("Joe's Diner")
console.log('Er sagte: "Guten Tag"')
console.log('She says, "let\'s go to Joe\'s Diner"')
console.log('A\nB\nC')
```

Multiline Strings und String-Interpolationen mit einfache Back-Ticks:

```js {cmd=node}
console.log(`Hallo`)
console.log(`Warum?
Wieso?
Weshalb?`)

name = 'Kurt'
console.log(`Hallo ${name}`)
```
## Variablen

```js {cmd=node}
let vorname = 'Jasmin'
let nachname = 'Herti'
let alter = 41
let now = new Date()
let jahrgang = now.getFullYear() - alter

console.log(`Frau ${nachname} ist im Jahr ${jahrgang} geboren.`)
```

Konstanten
```js {cmd=node}
const vorname = 'Jasmin'
vorname = 'Kurt'
```

Die alte Version von `let` hiess `var`.

## Verschachtelte Datentypen

### Array

Arrays in JS können gemischte Datentypen enthalten.

```js {cmd=node}
let zahlen = [2, 3, 5, 7, 11, 13]

console.log(zahlen[2]) // Dritte Primzahl

let auchZahlen = ['Eins', 'Zwei', 'Drei']
console.log(auchZahlen[0])
console.log(`Anzahl Zahlen: ${auchZahlen.length}`)

let gemischt = [1, 'Zwei', 3.1, 'Vier']
console.log(gemischt[gemischt.length - 1])

let komplexeZahlen = [[1, 3], [2, -1]]
let resultat = [
  komplexeZahlen[0][0] + komplexeZahlen[1][0],
  komplexeZahlen[0][1] + komplexeZahlen[1][1],
]
console.log(`${resultat[0]} + ${resultat[1]}i`)
```

Arrays können erweitert und gekürzt werden:

```js {cmd=node}
let teilnehmer = ['Tina', 'Franz']
console.log(teilnehmer)

teilnehmer.push('Emre')
console.log(teilnehmer)

teilnehmer.pop()
console.log(teilnehmer)

ausfall = teilnehmer.pop()
console.log(teilnehmer)
console.log(`${ausfall} kann nicht teilnehmen`)
```

### Objekt

Objekte sind komplexe Datentypen, in welchen Werte (values) unter Stichworten oder Schlüsselwörtern (keys) abgespeichert werden.

Leere Objekte:
```js {cmd=node}
let o = {}
```

Gefüllte Objekte (Die Anführungszeichen bei den Keys sind optional).
```js {cmd=node}
let person = {
  'vorname': 'Julia',
  'nachname': 'Heinzen',
  alter: 29,
  beruf: 'Schreinerin',
  hobbies: ['Velofahren', 'Musik', 'Brettspiele'],
  haustiere: [
    {art: 'Hund', alter: 5, name: 'Hasso'},
    {art: 'Hamster', alter: 1, name: 'Mimmi'},
  ],
}

console.log(person)
console.log(person.alter)    // Default: Punktnotation
console.log(person['vorname'])

nameKey = 'nachname'

console.log(`key: ${nameKey}, value: ${person[nameKey]}`)
```

Die Keys sind _immer_ Strings
```js {cmd=node}
let o = { 1: 'Eins', '.zwei': 'Zwei'}
console.log(o)

// console.log(o.1)
console.log(o['1'])

//console.log(o..zwei)
console.log(o['.zwei'])
```

Iterieren über den Inhalt von Objekten:
```js {cmd=node}
let person = {vorname: 'Julia', nachname: 'Heinzen', alter: 29}

console.log('Inhalt (values):')
for (let val of Object.values(person)) {
  console.log(' -', val)
}

console.log('Schlüsselwörter (keys):')
for (let key of Object.keys(person)) {
  console.log(' -', key)
}

console.log('Einträge (entries):')
for (let [key, val] of Object.entries(person)) {
  console.log(' -', key, ':' , val)
}
```

**Bemerkung**: Die Ordnung der Einträge in Objekten bleibt erhalten.

##### Hinzufügen und Löschen von Einträgen

```js {cmd=node}
let o = {}
console.log(o)

// Hinzufügen
o.a = 'Eins'
console.log(o)

o.a = 'zwei'
console.log(o)

// Löschen
delete o.a
console.log(o)
console.log(o.a === undefined)
```

## Kontrollstrukturen

### if (Verzweigung)

```js {cmd=node}
alter = 18

if (alter >= 18) {
  console.log('OK')
} else if (alter >= 16) {
  console.log('Vielleicht')
} else {
  console.log('Nein')
}
```

_Achtung_ bei Vergleichsoperatoren:
`==` und `!=` nicht verwenden, sondern `===` und `!==`.

```js {cmd=node}
if (0 == '') {
  console.log('Wiesooo?!?')
}

if (0 === '') {
  // wird nicht ausgeführt
} else {
  console.log('Alles in Ordnung')
}
```

## for-loop

For mit `of`: Iteriert über den Inhalt.

```js {cmd=node}
let schule = 'TSBE'

for (let buchstabe of schule) {
  console.log(buchstabe)
}
```

Mit `in` iterieren wir über die Indizes.

**Praxistipp**: Immer `of` benutzen.

Ein komplizierteres Beispiel (HP-Rechner lässt grüssen):

```js {cmd=node}
let stack = []
let input = [1, 2, 3, '*', '+']  // 1 + (2 * 3)

for (let x of input) {
  if (typeof x === 'number') {
    stack.push(x)
  } else {
    let a = stack.pop()
    let b = stack.pop()

    if (x === '*') {
      stack.push(a * b)
    } else if (x === '+') {
      stack.push(a + b)
    } else {
      console.log('Unknown operation')
    }
  }
}
console.log('Resultat:', stack[0])
```

## while-loop

Ein ganz okayer while-Loop:

```js {cmd=node}
let done = false

let sum = 0
let zahlen = [1, 3, 5, 7]

while (!done) {
  if (zahlen.length === 0) {
    done = true
  } else {
    sum += zahlen.pop()
  }
}
console.log('Summe:', sum)
```

While-loops eignen sich, wenn die Menge der Arbeit nicht bekannt ist.

Colatz-Zahlen:
```js {cmd=node}
let zahl = Math.round(Math.random() * 100)
let done = false

while (!done) {
  if (zahl % 2 === 0) {  // gerade Zahl
    zahl = zahl / 2
  } else {               // ungerade Zahl
    zahl = zahl * 3 + 1
  }
  console.log(zahl)
  
  if (zahl === 1) {
    done = true
  }
}
```
