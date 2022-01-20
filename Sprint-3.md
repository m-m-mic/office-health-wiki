_Letzter commit vor Abgabe: [d7fe3b7](https://github.com/ID-Start-Winter21/start-team-10/commit/d7fe3b76760bb0a2a4c5f125615f42ea31fb0833)_

# Finales Interaction Model
<br>

Für das letzte Interaction Model unseres Skills haben wir die Ergebnisse der Usability Tests zusammengefasst und die Dialoge dementsprechend verbessert.

<br>

## Usability Testing
<br>

Das Usability Testing ergab, dass der Aufbau des Skills gut verständlich ist und die Relevanz von Office Health deutlich ist. Nur an manchen Stellen bleiben Nutzer noch hängen, wenn sie ausgefallene Utterances benutzen. Auch ein Teil der Übungen kann bei einzelnen Personen missverstanden werden und muss noch verbessert werden.

<br>

## Dialoge
<br>

Damit der Skill noch besser läuft wurden basierend auf das Usability Testing noch weitere Utterances eingefügt.

<br>

# Implementierung
<br>

In diesem Sprint haben wir unseren Code erneut angepasst, um die Benutzerfreundlichkeit von Office Health zu optimieren.

<br>

## Verbesserte Sprechpausen mit `audio`
<br>

Nachdem im letzten Sprint das Einfügen von selbst erstellten Audiodateien nicht funktioniert hat, haben wir uns entschieden die Audio-Bibliothek von Amazon zu verwenden. Um diese Audio-Dateien in den ```speak_output``` einzufügen mussten wir nicht zuerst einen AWS-Account erstellen, wir konnten sie einfach wie folgt einbauen:

```python
speak_output = "<speak>" + spo_1[random.randrange(0, len(spo_1)-1)] + "<audio src=\"soundbank://soundlibrary/foley/amzn_sfx_clock_ticking_long_01\"/><audio src=\"soundbank://soundlibrary/foley/amzn_sfx_clock_ticking_long_01\"/><audio src=\"soundbank://soundlibrary/foley/amzn_sfx_clock_ticking_long_01\"/>" + spo_2[random.randrange(0, len(spo_2)-1)] + " " + spo_3[random.randrange(0, len(spo_3)-1)] + " " + spo_4[random.randrange(0, len(spo_4)-1)] + " " + spo_5[random.randrange(0, len(spo_5)-1)] + "</speak>"

```

Die Audio-Datei von Amazon ist 4,09 Sekunden lang, weshalb wir sie mehrmals hintereinander einfügen mussten, damit die Pause über zehn Sekunden lang ist.

<br>


# Finale Präsentation
<br>

__Erklärung einfügen__

<br>

## Demonstration des Skills
<br>

__Erklärung einfügen__

<br>

## Entwicklungsprozess
<br>

### Ideation: 

Zu beginn hat jedes Teammitglied seine Ideen vorgestellt. Mit Hilfe von Strawpoll haben wir uns dann für eine Idee entschieden. <br>
<br>
Danach haben wir das Grundkonzept aufgestellt, wobei die wichtigsten Fähigkeiten des Skills hervorgehoben werden sollen: 
<br>

"Das Grundkonzept des Alexa Skills **Office Health** liegt darin, den User während seiner Arbeit durch regelmäßige Pausen mit Übungen fit und gesund zu halten. 
Dabei muss der User zu Beginn aktiv mit Alexa kommunizieren und ihre Frage beantworten. <br> 
So wird herausgefiltert:
1. Wie lange der User an dem Tag arbeiten will.
2. Wie lange und oft die Pausen (_Health Break_) sein sollen.
3. Nach welchem Schwierigkeitsgrad (_Sweat Mode_) die Übungen ausgeführt werden sollen.
4. Welcher Coach den Nutzer unterstützen und motivieren soll.
5. Ob der User Anweisungen für die Übungen braucht.

Danach läuft der Alexa Skill ohne weitere Eingaben des Users selbstständig weiter. Das erste Arbeitsintervall beginnt und **Office Health** plant die möglichen Übungen und deren Länge. Kurz nach Ablauf des ersten Arbeitsintervalls erinnert der Voice Assistens den User an die bevorstehende Pause. Bei Beginn der Pausen spielt der Coach dann das Sportprogramm ab, hierbei hat der User dann wieder die Möglichkeit, mit Alexa zu interagieren und den Coach zu wechseln. Sind alle Übungen beendet, beginnt für den Nutzer das nächste Arbeitsintervall. 
Dieser Ablauf wird so oft wiederholt, bis alle _Health Breaks_ ausgeführt wurden.

Mit diesem Voice Assistenten wollen wir somit die Gesundheit am Arbeitsplatz fördern und auf das Thema aufmerksam machen. Zudem trägt **Office Health** direkt dazu bei, dass der User ein gesünderes und zufriedeneres Leben führt. <br>
Außerdem wird mögliche Eintönigkeit durch die Wahl verschiedener Coaches verhindert, dabei unterscheiden sie sich nicht nur im Ton, sondern auch in deren Persönlichkeit. So kann jeder Nutzer den perfekten Coach für sich finden und sein optimales Nutzererlebnis mitgestalten." 
<br>
Anhand des Grundkonzepts haben wir dann unser Storyboard erstellt. <br>

![grafik](https://user-images.githubusercontent.com/91656704/141814253-a17764b5-cdca-4bcb-b2a0-650c0d3d7524.png) <br>

Danach haben wir zusammen ein Logo gestaltet, wobei unsere einzelnen Entwürfe als Inspiration dienten. <br>

<img src="https://user-images.githubusercontent.com/85286401/142627388-d76c79d9-93f4-431c-9c8d-f65dab0b2c36.png" alt="Finales Icon" height="150"/>

<br>

### Erste Release:

Der erste Prototyp wurde am Tag des Hi!A Festivals vorgestellt. <br>
Unser Skill umfasste dabei bereits verschiedene Dialogoptionen und Befehle, Abfrage von Arbeitszeitdauer und Pausenanzahl, eine zufällige Ausgabe von Sportübungen und einen Counter, der die Sportübungen runter zählt.
<br>



### Usability Testing:

Das Usability Testing hat uns gezeigt, dass der Skill die wichtigsten Befehle abrufen kann. Zudem konnten wir auch unbemerkte Programmfehler finden und diese im kommenden Sprint verbessern.
<br>

<details>
<summary ><b>Unsere durchgeführten Tests</b></summary>
    <br>
    <p align="center">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us1.png" width="350" alt="Folie 1">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us2.png" width="350" alt="Folie 2">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us3.png" width="350" alt="Folie 3">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us4.png" width="350" alt="Folie 4">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us5.png" width="350" alt="Folie 5">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us6.png" width="350" alt="Folie 6">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us7.png" width="350" alt="Folie 7">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us8.png" width="350" alt="Folie 8">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us9.png" width="350" alt="Folie 9">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us10.png" width="350" alt="Folie 10">
    <img src="https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/usability-slides/us11.png" width="700" alt="Folie 11">
    </p>
</details>



### Verbesserungen und Weiterentwicklung: 

Weiterhin müssen wir Programmfehler finden und lösen, sowie Dialoge verbessern.
<br>
<br> 
Nach dem Projektmodul steht die Weiterentwicklung des Skills für jedes Teammitglied frei zur Verfügung. <br>
Mögliche Erweiterungen sind: 
* weitere Coaches
* Sweat Levels umsetzten
* Option für räumliche Einschränkungen 
* Musik während der Übungen und dem Arbeiten
* Blocker im online Kalender
* User auf die Vorteile der Übungen aufmerksam machen

<br>

## Reflexion

### Was haben wir gelernt?
* blabla
