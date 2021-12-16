# Issue Formulierung
<br>
Für eine transparente und reibungslose Teamarbeit ist die richtige Issue Formulierung wichtig. <br>
Damit ein Issue für wirklich jeden verständlich ist und erfolgreich und ohne Missverständnisse abgearbeitet werden kann, sollten folgende Grundsätze eingehalten werden: <br> <br>

*  Klare und ausführliche Problembeschreibung, warum das Issue erstellt wurde
*  Angaben von Akzeptanzkriterien (was MUSS erfüllt werden)
*  Wie wollen wir das Issue in dem Voice Assistenten einbauen?
*  Genaue Zielsetzung und Definition 
*  Frist, bis wann das Issue fertig sein muss<br>

Nachdem die Informationen im Issue formuliert wurden, müssen _Assignees_ festgelegt werden. Ein Issue muss *mindestens* eine Person als _Assignees_ geben, wenn keine konkrete Person für das Issue festgelegt werden kann, werden alle Teammitglieder eingeteilt und daraufhin besprochen, wer die Aufgabe übernimmt. <br> <br>
Mindestens ein _Label_ oder _Milestone_ muss angegeben werden, damit man die Issues später besser filtern und abarbeiten kann.
<br> <br>
Wenn mehreren Personen dem Issue zugeteilt wurden, muss **mindestens** eine weitere Person dem fertigen Issue zustimmen; Vier-Augen-Prinzip. Ist das Issue einwandfrei abgeschlossen worden, reicht es aus, wenn der Prüfer auf das Issue mit z. B. „ :+1: “ reagiert.  <br>
Issues, die zur Erinnerung dienen und einem selbst zugeteilt wurden, könne vom Ersteller nach abarbeiten des Issues ohne Zustimmung abgeschlossen werden. Trotzdem sollte man dem Team mitteilen, dass die Aufgabe erledigt wurde.
<br> <br>

<br> <br>
# Git push

Hierbei geht es hauptsächlich um die Alexa `JSON` Datein, sowie die Python `lambda_function`. <br>
Der _Masterbranch_ sollte so linear wie möglich sein, d.h. hier wird nur fertiger und geprüfter Code hochgeladen, der nicht mehr verändert werden muss. <br>
Wird an dem Code noch gearbeitet und/oder eine Review benötigt, so wird er in den _Developbranch_ geladen. <br>
Wurde anhand eines Issues der Code verändert, so sollte beim Pushen die Issuenummer und was genau codiert wurde mit angegeben werden , z. B.: _" feature/10_ButtonFunktioniertKorrekt"_ <br>
**Es dürfen keine Zip Datein hochgeladen werden. Befinden sich doch welche in einem Branch, werden sie gelöscht.** <br>
Zudem müssen in jedem Branch `.gitignore` Datei vorhanden sein. In ihr wird geregelt, welche Daten Github ignorieren kann. Dies hilft uns enorm, da es sonst zu unbekannten Programmstörungen kommen kann, wenn ein weiteres Teammitglied an dem Code arbeitet. <br>

Eine genauere Erklärung könnt ihr hier finden:  [Gitflow](https://www.atlassian.com/de/git/tutorials/comparing-workflows/gitflow-workflow) 
<br> <br>

Zudem sollte nicht vergessen werden, den Code in regelmäßigen Abständen in das Repository zu laden.

<br> <br>
# Sprinteinteilung

|          |  Melanie  |  Michael  | Isabella |    Eva    | Alexander |
| -------- | --------- | --------- | ---------| --------- | --------- |
| Sprint 0 |Konzept / Issues|Interaction Model | Storyboard | Dialoge | Interaction Model |
| Sprint 1 | Recherche, Intents, Wiki| Struktur, Intents | Struktur, Intents | Recherche, Intents, Wiki | Struktur, Intents|
| Sprint 2 | Usability Testing, Festivalplanung | Usability Testing, Dialogverbesserung | Usability Testing, Dialogverbesserung | Usability Testing, Dialogverbesserung | Usability Testing, Festivalplanung |