# JS

## Einfache Datentypen

### Nichts

```js {cmd=node}
console.log(null)
console.log(undefined)
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
vorname = 'Jasmin'
nachname = 'Herti'
alter = 41
now = new Date()
jahrgang = now.getFullYear() - alter

console.log(`Frau ${nachname} ist im Jahr ${jahrgang} geboren.`)
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


