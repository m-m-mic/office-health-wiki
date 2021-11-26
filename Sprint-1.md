# Icon und Design
<br>

<p align="center">
<img src="https://user-images.githubusercontent.com/85286401/142627388-d76c79d9-93f4-431c-9c8d-f65dab0b2c36.png" alt="Finales Icon" height="250"/>
</p>
<br>

Unser finales Icon Design, welches unseren Office Health Skill repräsentiert. Wir haben mit dem Adobe Contrast Checker den Kontrast überprüft, damit das Logo auch für Personen mit Sehbehinderungen gut erkennbar ist.
<br>

<p align="center">
<img src="https://user-images.githubusercontent.com/85286401/142628260-00c2fc6d-3061-4fbf-b434-f72e75617ad7.png" alt="Finales Icon" height="250"/>
</p>

Der für das Logo verwendete Farbverlauf ist festgelegt (`#43f3e4` - `#457efd` - `#972bea`) und soll für sämtliches Designmaterial verwendet werden.

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


