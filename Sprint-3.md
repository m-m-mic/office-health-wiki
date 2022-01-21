_Letzter commit vor Abgabe: [696fb6c](https://github.com/ID-Start-Winter21/start-team-10/commit/696fb6c250d9907d729d0e51d8bab88a6e94dbc5)_

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

Am 21.01.2022 stellen wir unseren Skill **Office Health** vor. Diese Präsentation umfängt eine Demonstration des Skills, ein Rückblick auf unsere Arbeit während des Projektmoduls und eine Reflexion.

<br>

## Demonstration des Skills
<br>

Wir präsentieren in Rahmen der finalen Präsentation unseren Skill. 

<br>

<details>
<summary ><b>PowerPoint Folien</b></summary>
    <br>
    <p align="center">
    <img src="https://user-images.githubusercontent.com/85286401/150493336-1ee71f86-dad3-47fa-82a3-f3b6da8f4354.JPG" width="350" alt="Folie 1">
    <img src="https://user-images.githubusercontent.com/85286401/150493389-d6b7cfc4-1964-4319-8a22-1fc73ac55859.JPG" width="350" alt="Folie 2">
    <img src="https://user-images.githubusercontent.com/85286401/150493430-e6fa7de7-9689-4e28-aab1-268aed92b8f8.JPG" width="350" alt="Folie 3">
    <img src="https://user-images.githubusercontent.com/85286401/150493455-b070350e-5c59-4572-a9ff-7c61ccd6d272.JPG" width="350" alt="Folie 4">
    <img src="https://user-images.githubusercontent.com/85286401/150493491-2d042399-c592-472c-a318-617927c345c2.JPG" width="350" alt="Folie 5">
    <img src="https://user-images.githubusercontent.com/85286401/150493532-3f4cc581-59c0-4e85-8dec-6a4bd002bf06.JPG" width="350" alt="Folie 6">
    </p>
</details>

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
* Neue Tools kennengelernt
* einen sicken Skill erstellen
* einfach anfangen, auch wenn man überfordert ist
* vor dem Machen erstmal schauen, was möglich ist

### Welche Kompetenzen haben wir im Bereich Implementierung erworben?
* Trial & Error gehört dazu und kann sehr helfen
* Umgang mir Python in einem komplexeren Projekt
* Dialoge im Alexa Skill implementieren
* Sprechpausen einbauen
* erste Programmiererfahrung, Anwendung von dem was wir in den Vorlesungen gelernt haben
* Troubleshooting --> Lesen von Dokumentation und wie man am besten googlet

### Welche Kompetenzen im Bereich Design haben wir erworben?
* Dialoge können auch designed werden 
* Persönlichkeit kreieren 
* natürliche, verständliche Dialoge gestalten und mit Usability Testings verbessern
* Worauf muss bei der Gestaltung eines Icons geachtet werden

### Wie können wir darauf aufbauen?
* mehr Sicherheit bei Projekten
* Gelerntes in anderen Projekten umsetzten (nicht nur Alexa Skills)
* bei neuen Aufgaben nicht zurückschrecken und einfach anfangen
* stets offen für neue Ideen sein
* erste Programmiererfahrung ist auch für die künftigen Semester und für das Arbeitsleben wichtig
* Dialoge gestalten kann auch für Textinhalte in Apps hilfreich sein

### Was nehmen wir aus der Teamarbeit für zukünftige Projekte mit? 
* Gute Planung und Treffen in regelmäßigen Abständen sind wichtig für ein effektives Projektmanagement
* Wichtig, alle Mitglieder einzubinden, damit Aufgaben gleichmäßig verteilt sind
* Jeder kann durch seine Ideen das Projekt zu etwas ganz besonderen machen
* Offene Kommunikation hilft nicht nur bei der Teamarbeit, sondern stärkt diese auch :)
* Wenn man während dem Meeting vom Thema abschweift ist es vollkommen okay (Jeder braucht mal Pausen)

 
