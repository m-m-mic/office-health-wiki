_Letzter commit vor Abgabe: [insert last commit here]()_

# Hi!A Festival
<br>

![Hi!A Logo](https://github.com/ID-Start-Winter21/start-team-10/blob/main/img-folder/hia_banner.png)

Am 10. Dezember 2021 haben wir im Rahmen des Hi!A Festivals unseren "Office Health" Skill vorgestellt. Für die Präsentation haben wir sowohl Folien als auch einen Durchlauf unseres Skills geplant.

<br>

## Planung
<br>

_Hier Planung erklären_

<br>

## Ablauf
<br>

_Hier Ablauf erklären_

<br>

# Interaction Model v3.0
<br>

Um unser Interaction Model in diesem Sprint zu verbessern haben wir mit mehreren Leuten Usability Testing durchgeführt. Die Ergebnisse und Verbesserungen sind im Folgenden aufgelistet.

<br>

## Usability Testing
<br>

_Unsere Ergebnisse hier einfügen_

<details class="note-details">
<summary class="arrow-summary"><b>Hier klicken, um alle Notizen zu sehen</b></summary>
    <img class="note-img" src="test_details.jpg" alt="Usability Testing Notizen">
</details>

<br>

## Iterativ verbesserte Dialoge
<br>

_Verbesserungen zu speak_output und utterances einfügen_

<br>

# Implementierung
<br>

In diesen Sprint haben wir...

<br>

## Melli Übungsablauf
<br>

_Melli, hier Erklärung einfügen_

<br>

## Verbesserte Sprechpausen mit `audio`
<br>

_Hier Erklärung einfügen_

<br>

# Sprint Review Planung
<br>

_Hier Planung für Sprint Review einbauen_

<br>

<style>
.note-details{
    background-color: #252626;
    padding: 5px 5px 7px 5px;
    /*top right bottom left*/
    border-radius: 8px;
}
.note-img{
    text-align: center;
    margin: 10px 0 -5px 0;
    border-radius: 5px;
}
/*details animation on open*/
@keyframes details-show {
    from {
        opacity:0;
        transform: var(--details-translate, translateY(-0.5em));
    }
}
/* changes to arrow for animation */
summary.arrow-summary{
    padding: 3px 0 0 21px;
    display: block;
    position: relative;
    cursor: pointer;
}
summary.arrow-summary:before {
    content: '';
    border-width: .4rem;
    border-style: solid;
    border-color: transparent transparent transparent white;
    position: absolute;
    top: 9px;
    left: 5px;
    transform: rotate(0);
    transform-origin: .2rem 50%;
    transition: .25s transform ease;
    margin-left: 2px;
}
details[open] > summary.arrow-summary:before {
    transform: rotate(90deg);
    transition: 0.45s transform ease;
}
details > summary.arrow-summary {
    list-style-type: none;
}
details > summary.arrow-summary::-webkit-details-marker {
    display: none;
}
details[open] > *:not(summary) {
animation: details-show 150ms ease-in-out;
}
</style>
