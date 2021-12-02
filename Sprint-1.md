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

_Isabella hier Beschreibung erklären_

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
* Fokus auf Muskelübungen: [sportübungen verbessert.docx](https://github.com/ID-Start-Winter21/start-team-10/files/7637197/sportubungen.verbessert.docx)
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

_Alex hier deine Erklärung einfügen_

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

_Alex, Eva, Melanie hier Erklärung einfügen_

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
- Einfügen von Sprechpausen mit SSML (`<break>` oder `<audio>`)
- Dialoge nochmals überarbeiten, Variationen für `workout_explanation` und `workout_init`

<br>