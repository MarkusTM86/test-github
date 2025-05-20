# BitBot: Enkla rörelser och avstånd

# package
bitbot=github:4tronix/BitBot

## Steg 1: Kör framåt

Vi börjar med att få BitBot att köra rakt fram.

```blocks
bitbot.motor(BBMotor.All, 100)
```

Denna kod kör båda motorerna framåt med full fart.

## Steg 2: Vänta lite

Vi vill att BitBot ska köra i 1 sekund, sedan stanna.

```blocks
bitbot.motor(BBMotor.All, 100)
basic.pause(1000)
bitbot.stop(BBMotor.All)
```

Blocket `pause` väntar 1000 millisekunder = 1 sekund.

## Steg 3: Avståndssensor

BitBot har en ultraljudssensor framtill. Den mäter avstånd till t.ex. väggar.

Lägg till följande block för att **visa avståndet i cm** på micro:bitens display:

```blocks
basic.showNumber(bitbot.sonar(BBPingUnit.Centimeters))
```

Prova att hålla handen framför BitBot – siffran ändras!

## Steg 4: Stanna om något är i vägen

Nu ska vi kombinera sensorn med motorerna.

BitBot ska köra **så länge det är fritt framför**, och stanna om något är närmare än 10 cm.

```blocks
basic.forever(function () {
    if (bitbot.sonar(BBPingUnit.Centimeters) < 10) {
        bitbot.stop(BBMotor.All)
    } else {
        bitbot.motor(BBMotor.All, 100)
    }
})
```

## Steg 5: Testa!

Sätt BitBot på golvet.

1. Kör programmet.
2. Håll upp handen eller ett föremål framför roboten.
3. Vad händer när du kommer nära?

## Bonus: Lägg till ljud

Vill du att BitBot ska pipa när den måste stanna?

Lägg till detta inuti `if`-blocket:

```blocks
music.playTone(Note.C, music.beat(BeatFraction.Quarter))
```

---

## Klar!

Nu har du skapat en BitBot som:
- Kör framåt
- Reagerar på hinder
- Kan användas i t.ex. hinderbanor

Vad mer kan du styra med sensorer? Vändning? Ljusstyrka? Tryck?
