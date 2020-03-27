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
# Funktionen


```js {cmd=node}
function sayHello() {
  console.log('Hallo')
}

console.log(sayHello)
let sayHi = sayHello

console.log(sayHi)

sayHello()
```

Funktionen können Parameter entgegen nehmen:
```js {cmd=node}
function sayHello(name) {
  console.log(`Hallo ${name}`)
}

sayHello('Jasmin')
sayHello('Neda')
```

Parameter sind in JS optional:
```js {cmd=node}
function sayHello(name) {
  if (name === undefined) {
    console.log(`Hallo unbekannt`)
  } else {
    console.log(`Hallo ${name}`)
  }
}

sayHello()
sayHello('Urs')
sayHello('Urs', 'Müller')
```

Wir können mit Funktionen Berechnungen anstellen, und das Resultat zurück geben.

```js {cmd=node}
let a = 5
let b = 7
let c = 8

function add(a, b) {
  let resultat = a + b
  console.log(a, b, resultat)
  return resultat
}

let resultat = add(b - 1, add(a, -1))
console.log('Resultat:', resultat)
console.log('Resultat:', add(c - 3, add(a, c - b)))
```

```js {cmd=node}
let haustiere = [
  {art: 'Hund', alter:7, name: 'Hasso'},
  {art: 'Katze', alter:2, name: 'Fleckli'},
  {art: 'Schildkröte', alter:40, name: 'Wilma'},
  {art: 'Meerschweinchen', alter:2, name: 'Ida'},
  {art: 'Meerschweinchen', alter:3, name: 'Jakob'},
]

function findWilma(haustier) {
  // console.log(haustier)
  if (haustier.name.toLowerCase() === 'wilma') {
    return true
  } else {
    return false
  }
}

let wilma = haustiere.find(findWilma)
console.log('Resultat:', wilma)
```


#### Kurznotation für Funktionen (Fat-Arrow-Notation)

```js {cmd=node}

let haustiere = [
  {art: 'Hund', alter:7, name: 'Hasso'},
  {art: 'Katze', alter:2, name: 'Fleckli'},
  {art: 'Schildkröte', alter:40, name: 'Wilma'},
  {art: 'Meerschweinchen', alter:2, name: 'Ida'},
  {art: 'Meerschweinchen', alter:3, name: 'Jakob'},
]

let findWilma = haustier => haustier.name.toLowerCase() === 'wilma'

let wilma = haustiere.find(haustier => haustier.name.toLowerCase() === 'wilma')
console.log('Resultat:', wilma)

console.log('Alle Meerschweinchen:', haustiere.filter(
  haustier => haustier.art.toLowerCase() === 'meerschweinchen'
))

console.log('Junge Tiere:', haustiere.filter(x => x.alter <= 3))

haustiere.sort((a, b) => a.alter - b.alter)
console.log(haustiere)
```

### Methoden

Methoden sind Funktionen von Objekten.
```js {cmd=node}
let name = 'Marco'

console.log(name.length)
console.log(name.toLowerCase())

let obj = {
  length: 5,
  irgend: function() {  // Konventionelle Schreibweise
    return this.length * 2
  },
  etwas() {    // Kurzschreibweise
    return this.irgend() * 3
  }
}
console.log(obj.length)
console.log(obj.irgend())
obj.length = 2
console.log(obj.irgend())
console.log(obj.etwas())
```

## Abschliessendes Beispiel

RPN-Rechner Volume 2

```js {cmd=node}
let input = '5 3 - 0 cos + 2 %'
  .split(' ')                // An den Leerzeichen auseinander schneiden
  .filter((x) => x !== '')   // Leere Strings rausfiltern
  .map(x => {                // Versuchen so viel wie möglich in eine Zahl verwandeln
    let num = parseInt(x, 10)
    if (isNaN(num)) {
      return x
    } else {
      return num
    }
  })
console.log('Input:', input)

let stack = []

let ops = {
  '+': (a, b) => a + b,       '-': (a, b) => a - b,
  '*': (a, b) => a * b,       '/': (a, b) => a / b,
  '%': (a, b) => a % b,
  '--': a => a - 1,           '++': a => a + 1,
  'sin': Math.sin,            'cos': Math.cos,
}


for (let x of input) {
  if (typeof x === 'number') {
    stack.push(x)
  } else {
    let op = ops[x]
    if (op === undefined) {
      console.log('Operation unbekannt:', x)
      break
    } else {
      let args = []
      for (let i of Array(op.length)) {
        args.push(stack.pop())
      }
      args.reverse()
      stack.push(op(...args))
    }
  }
}
console.log('Resultat:', stack[0])
```
