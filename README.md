# inbraakAlarm
Een project voor de bibliotheek Heerenveen waar we een inbraak alarm bouwen. 

Wat heb je nodig
- een micro.bit
- een grove inventorkit
- een laptop met internet (https://makecode.microbit.org/)

Onderstaande stappen laten je kennis maken met alle onderdelen. Probeer eerst zelf de oplossing te maken. Bij iedere stap zit een uitwerking, deze kun je bekijken als je zelf er even niet uitkomt.

## Welkom (stap1)
**doel:** micro.bit leren kennen  
**wat moet je done?** Zorg voor een melding, bijvoorbeeld je naam, op het scherm.

<details>
<summary>uitwerking: Welkom (stap1)</summary>

![micro.bit setup: stap1.](images/microbitStap1.jpg)
![makecode stap1.](images/codeStap1.png)

```javascript
input.onGesture(Gesture.Shake, function () {
    basic.showString("Hello!")
})
basic.showIcon(IconNames.Happy)
```
</details>

## Alarm! (stap2)
**doel:** grove leren kennen  
**wat moet je doen?** Ansluiten grove led. Als je op de knop A drukt moet de micro.bit één keer geluid maken het de led driekeer laten knipperen 

> [!TIP]
> In het boekje van de grove inventorkit staat beschreven hoe je de led aansluit.

<details>
<summary>uitwerking: Alarm! (stap2)</summary>

![micro.bit setup](images/microbitStap2.jpg)
![makecode](images/codeStap2.png)

```javascript
input.onButtonPressed(Button.A, function () {
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    for (let index = 0; index < 3; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.pause(100)
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.pause(100)
    }})
```
</details>


## Boef gedetecteerd (stap3)
**doel:** inbraakalarm bouwen, basis versie  
**wat moet je doen?** aansluiten bewegingssensor en zorgen dat het alarm afgaat als iemand in de buurt komt.

<details>
<summary>uitwerking: Boef gedetecteerd (stap3)</summary>

![micro.bit setup](images/microbitStap3.jpg)
![makecode](images/codeStap3.png)

```javascript
basic.forever(function () {
    if (grove.measureInInches(DigitalPin.P1) < 10) {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }})
```
</details>



## hoe wil je het inbraakalarm uitbreiden? (extra stap)
**surgesties:**  
* led strip gebruiken ipv led [moeilijkheidsgraad: MIDDEN]
* tellen hoe vaak het alarm is afgegaan en op het schermpje tonen [moeilijkheidsgraad: MIDDEN]
* radio sigaal doorsturen naar de tweede micro.bit [moeilijkheidsgraad: MOEILIJK]
