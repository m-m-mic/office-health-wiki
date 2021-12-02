_Letzter commit vor Abgabe: [77fffec](https://github.com/ID-Start-Winter21/start-team-10/commit/77fffec928a554f9f10fd99d970964c0df25ff11)_

# Gestaltung
<br>

Wir haben unser finales Logo gestaltet und eine Beschreibung für unseren Skill unter Distribution geschrieben.

<br>

## Icon und Design
<br>

<p align="center">
<img src="https://user-images.githubusercontent.com/85286401/142627388-d76c79d9-93f4-431c-9c8d-f65dab0b2c36.png" alt="Finales Icon" height="220"/>
</p>
<br>

Unser finales Icon Design, welches unseren Office Health Skill repräsentiert. Wir haben mit dem Adobe Contrast Checker den Kontrast überprüft, damit das Logo auch für Personen mit Sehbehinderungen gut erkennbar ist.
<br>

<p align="center">
<img src="https://user-images.githubusercontent.com/85286401/142628260-00c2fc6d-3061-4fbf-b434-f72e75617ad7.png" alt="Finales Icon" height="250"/>
</p>

Der für das Logo verwendete Farbverlauf ist festgelegt (`#43f3e4` - `#457efd` - `#972bea`) und soll für sämtliches Designmaterial verwendet werden.

<br>

## Beschreibung
<br>

Für ein besseres Verständnis von "Office Health" wurde in der Alexa Developer Console eine Beschreibung des Skills erstellt.

Mit der One Sentence Description
"Bleib fit bei der Arbeit! "Office Health" hilft dir auf deine Gesundheit zu achten, indem es mit dir regelmäßig Übungen macht."
werden dem Nutzer schnell und pregnant die Vorteile des Skills und seine Funktion dargelegt.

Die Detailed Description hingegen bietet mehr Auskunft. Sie zeigt dem Nutzer verschiedene Probleme bei der Büroarbeit auf, die mit diesm Skill behoben werden können und erklärt verschieden Funktionen von "Office Health" genauer. Des Weiteren macht sie die Einzigartigkeit und die Notwendigkeit des Skills deutlich.

So erhält der Nutzer alle wichtigen Informationen auf einem Blick.

<br>

# Interaction Model v2.0
<br>

Das Interaction Model wurde grundsätzlich überarbeitet. Sowohl Intents als auch Dialoge wurden verbessert.

<br> 

## Intents
<br>

Um den Ablauf unseres Skills in der Developer Console verständlicher zu machen haben wir die Intent-Namen und deren Beschreibungen überarbeitet.

|**intent name** | **slots** | **confirmation** | **explanation** |
|------------|-------|--------------|-------------|
| **runtime** | {work_time} | yes | Soll gleich vom Nutzer nach LaunchRequest aufgerufen werden. Fragt Nutzer nach Arbeitszeit. |
| **intervals** | {break_amount}, {break_intervals} | yes | Folgt auf runtime. Fragt Nutzer wie viele Pausen er machen möchte. |
| **session_init** | no | no | Folgt auf intervals. Fragt nach letzter Bestätigung des Nutzers, bevor die Session gestartet wird. Soll auch den Timer starten. |
| **workout_explanation** | no | no | Folgt auf session_init (erste Intervall) oder workout_finish (alle folgenden Intervalle) wenn Timer vorüber ist. Erklärt Nutzer die Übung, die bevorsteht. |
| **workout_init** | no | no | Folgt auf workout_explanation. Führt Nutzer durch die Übung. |
| **workout_finish** | no | no | Folgt ohne utterance des Nutzers auf workout_init so bald drei Übungen durchgeführt wurden. Gibt Nutzer Zeit, bevor die Arbeitszeit weitergeht. |
| **session_finish** | no | no | Folgt ohne utterance des Nutzers auf workout_init wenn alle Übungen durchgeführt wurden. Bringt die Session zu Ende. |

Die verschiedenen Intents sind auch in der [Liste aller Dialogkomponenten](https://github.com/ID-Start-Winter21/start-team-10/wiki/Liste-aller-Dialogkomponenten) dokumentiert.

<br>

## Dialoge
<br> 

* [Dialog v2.0](https://github.com/ID-Start-Winter21/start-team-10/files/7571033/Dialoge.docx): Unterteilung in Blöcke
* [Dialog v2.1](https://github.com/ID-Start-Winter21/start-team-10/files/7607673/Dialoge_ver2_1.docx): Überarbeitung der Dialoge, Intent-Namen hinzugefügt

<br>

## Liste an Sportübungen
<br>


* Fokus auf Dehnübungen: [Dehnübungen_Alexa](https://github.com/ID-Start-Winter21/start-team-10/files/7619621/Sportubungen_Alexa.docx)
* Fokus auf Muskelübungen: [sportübungen verbessert](https://github.com/ID-Start-Winter21/start-team-10/files/7637197/sportubungen.verbessert.docx)
<br>

Beide Dokumente sind so aufgebaut:
* Kurzbefehl/Einleitung (falls der User schon mit dem Skill bekannt ist)
* zwei Beschreibungen (eine kürzere und eine ausführlichere)
* Aussagen die Alexa während der Übung sagen kann



<br>

# Implementierung
<br>

Wir haben in diesem Sprint verschiedene Funktionen erarbeitet und diese in unseren Skill implementiert.

<br>

## Dreimalige Wiederholung des `workout_init` Intents
<br>

Innerhalb einer workout-Session sollen indgesamt 3 übungen gemacht werden, also brauchen wir eine Möglichkeit, dass Alexas Aussagen nach einer Übung sich abhängig von der Anzahl verbleibender Übungen verändern.
Nach den Ersten zwei Übungen sollte der User utterances nutzen, durch die eine weitere Übung begonnen wird und nach der letzten solche sodass der `session_init` Intent aufgerufen wird und die nächste arbeits-Session beginnt.
Dazu habe ich ein persistent attribute genuzt, welches be jeder Übung hochzählt und nach der dritten Übung wieder auf 0 gesetzt wird.

```python
attr = handler_input.attributes_manager.persistent_attributes
if not attr:
    attr['exercisenum'] = 0
attr['exercisenum'] += 1

...#Ausgabe der Übung selbst

if attr['exercisenum'] < 3:
        if attr['exercisenum'] == 1:
                ...#Ausgabe nach Erster Übung
        else:
                ...#Ausgabe nach Drittter Übung
else:
    ...#Ausgabe nach letzter Übung
    attr['exercisenum'] = 0

#Speichern des Attributes
handler_input.attributes_manager.save_persistent_attributes()
```

<br>

## Intent Confirmation
<br>

Für die Intents `runtime` und `intervals` soll Alexa nach der Eingabe nachfragen, ob die Eingabe richtig verstanden wurde. Dafür haben wir "Intent Confirmation" im Interaction Model aktiviert. Nach Aktivierung fragt Alexa nun ob die Eingabe stimmt, jedoch muss in der `lambda-function.py` erst per if-Schleife definiert werden, was passieren soll, wenn der Nutzer "Nein" sagt. Die Abfrage dafür sieht so aus:

```python
import ask_sdk_model

...

    def handle(self, handler_input): 
        logger.info(handler_input.request_envelope.request.intent.confirmation_status)
        if handler_input.request_envelope.request.intent.confirmation_status == ask_sdk_model.intent_confirmation_status.IntentConfirmationStatus.CONFIRMED:
            speak_output = "Wie häufig möchten Sie währenddessen Health Breaks nehmen?"
        else:
            speak_output = "Okay, wie lange willst du heute arbeiten?"
```

Wenn der Nutzer "Ja" antwortet, fährt Alexa zu der nächsten Frage fort. Bei "Nein" wird die Frage wiederholt.

[➔ Genauere Dokumentation](https://github.com/ID-Start-Winter21/start-team-10/wiki/Python-Dokumentation-f%C3%BCr-Alexa-Skills#intent-confirmation)

<br>

## Zufälliger speak_output
<br>

Damit Alexas Dialog natürlicher klingt haben wir mehrere Variationen für ihre Sprachausgabe geschrieben. Um diese einzubauen haben die verschiedenen Variationen als Listen gespeichert und dann durch Anwendung von Pythons `random.randrange` Funktion zufällig in `speak_output` aufgerufen. Die Listen befinden sich dabei in einer separaten Python-Datei, um die Lesbarkeit der `lambda_function.py` nicht zu beeinträchtigen.

```python
import random
import speak_input as si

...

        spo_1 = si.lr_spo_1
        spo_2 = si.lr_spo_2
        
        speak_output = spo_1[random.randrange(0, len(spo_1)-1)] + " " + spo_2[random.randrange(0, len(spo_2)-1)]len(spo_3)-1)]
```

```python
lr_spo_1 = [
        "...", 
        "..."
        ]

lr_spo_2 = [
        "...", 
        "..."
        ]
```

Indem wir die verschiedenen Ausgaben von Alexa in einzelne Teile aufgeteilt haben ergibt sich daraus eine sehr große Menge an verschiedenen Kombinationen. Alexas Ausgabe wirkt dadurch natürlicher.

[➔ Genauere Dokumentation](https://github.com/ID-Start-Winter21/start-team-10/wiki/Python-Dokumentation-f%C3%BCr-Alexa-Skills#zufälliger-speak_output)

<br>

## Zufällige Auswahl von Sportübungen
<br>

Um Abwechslung zu garantieren haben wir entschieden, dass die Übungen während den workouts zufällig aus einer großen Liste Möglicher Übungen gewählt werden. Dazu haben wir erst eine JSON datei mit allen Übungen und ihren Daten erstellt und diese in Dehn- und Sportübungen aufgeteilt.

```python
#json Datei wird in python als dict geladen
exercisesDict = json.load(open('exercise.json', 'r'))
#liste aller dehnübungen
stretches = exercisesDict['stretch']
#liste aller sportübungen
sports = exercisesDict['sport']
```

Zuerst war wichtig, dass vor jedem Workout drei zufällige Übungen ausgewählt, was in dem `session_initHandler` geregelt wird.
Ein Workout sollte mit einer Dehnübung anfangen, gefolgt von einer Sportübung und wieder einer Dehnübung. Somit werden drei zufällige Zahlen gespeichert wobei die erste und dritte sich unterscheiden sollten um gleiche Übungen in einem Workout zu verhindern.

```python
stl = len(stretches)
spl = len(sports)

r1 = random.randrange(0, stl)
r2 = random.randrange(0, spl)
r3 = r1
while r3 == r1:
    r3 = random.randrange(0, stl)
```

Die Übungen und ihre Details werden in persistent attributes gespeichert damit auf sie auch in anderen Intents zugegriffen werden kann. 
Diese sind eine Liste die Namen, Wiederholungen, ob ein Seitenwechsel nötig ist, sowie eine Erklärung zur Ausführung der Übung enthalten sind.

```python
#Beispiel für die Attribute
attr['stretch_one'] = ['name', 0, False, 'beschreibung']
attr['sport'] = ['name', 0, False, 'beschreibung']
attr['stretch_two'] = ['name', 0, False, 'beschreibung']
```

Wir brauchen eine Funktion die eine Übung aus einer der Übungslisten in einem attribut speichert.

```pyhton
def listifyExercise(attrName, exList, rn):
    attr[attrName][0] = exList[rn]['name']
    attr[attrName][1] = int(exList[rn]['dauer'])
    attr[attrName][2] = exList[rn]['seitenwechsel'] == 'TRUE'
    attr[attrName][3] = exList[rn]['beschreibung']
    handler_input.attributes_manager.save_persistent_attributes()
```

Nun wird die Funktion drei mal mit dem richtigen attribut namen, der dazugehörigen Übungsliste und dem Zufälligen Wert aufgerufen.

```python
listifyExercise('stretch_one', stretches, r1)
listifyExercise('sport', sports, r2)
listifyExercise('stretch_two', stretches, r3)
```

Beispiel für den ```speak_output``` bei der Beschreibung der ersten Übung:

```
if attr['exercisenum'] == 0:
            speak_output = "<speak>Deine nächste Übung heißt " + attr['stretch_one'][0] + '. ' + attr['stretch_one'][3] + "<break time=\"2s\"/> Soll ich die Anleitung wiederholen oder kann es los gehen? </speak>" 
```

<br>

## Übungsintervall runterzählen
<br>

Damit der Nutzer auch ein Gefühl dafür bekommt, wie lange er die Übung ausführen muss und wie viel Zeit noch vor ihm liegt. 
Da wir noch Probleme haben die eigentlich gedachte Definition als Output auszugeben, wurde vorerst die Funktion in den starren Ablauf eingefügt. 
Die Logik dahinter besteht darin, das geplante Zeitintervall der Übung abzurufen und dann in einer `while-Schleife` zu verringern. 
Damit die Texte für den Anfang nicht eintönig werden, gibt es mehrere `if-Abfragen`. Diese werden in der Zukunft durch bessere Möglichkeiten (z.B. zufällige abfrage des index einer liste; wie bei der Ausahl der Sportübungen) ersetzt.
Wenn wir die Implementierung als `def` haben, kann man mit einer `if-Abfrage` auch ganz einfach Wiederholungen bei Seitenwechsel mitreinbauen.

Jetziger Code: <br>

```python
        time = attr["stretch_one"][1] # Countdown der die Zeitintervalle der Übungen runterzählt.
        while time != 0:
            if time >= 30: 
                outp += ("Diese Übung wird wohl etwas länger. Also beweg deinen Arsch mal so richtig!<break time =\"10s\"/> Kommst du schon ins Schwitzen? <break time =\"10s\"/>")
                time -= 25
            if time == 30:
                outp += ("30 sekunden hast du vor dir! Leg dich ins Zeug. <break time =\"10s\"/> Nur noch die hälfte, gib also mal richtig Gas!<break time =\"10s\"/> ")
                time -= 25
            if time > 10: 
                outp += ("Die Zeit läuft, streng dich also mal an! <break time=\"9s\"/> ")
                time -= 10
            if time == 10:
                outp += ("Die zehn Sekunden schaffst du bestimmt nicht. <break time =\"3s\"/> ")
                time -= 5
            if time == 5:
                outp +=  ("Noch fünf Sekunden. Fünf <break time =\"1s\"/> vier <break time =\"1s\"/> drei <break time =\"1s\"/> zwei <break time =\"1s\"/> eins <break time =\"1s\"/> Na endlich! ")
                time -= 5
```

<br>

# Sprint Review Planung
<br>

**Demo des Skills:**
- Wir stellen beim Review einen Prototypen unseres Skills vor
- Der Skill soll in der Alexa Mobile App laufen

<br>

**Planung für das Hi!A Festival:**
- Teamvorstellung
- Online-Präsentation mit Designelementen
- Skill-Demo mit Ausblick auf die Zukunft
- Einblick in die Entwicklung

<br>

**Was wollen wir in Sprint 2 (bzw. bis zum Festival) schaffen:**
- "Intent Chaining": Manche Intents sollen automatisch auf andere folgen
- Einfügen von weiteren Sprechpausen mit SSML (`<break>` oder `<audio>`)
- Dialoge nochmals überarbeiten, Variationen für `workout_explanation` und `workout_init`

<br>