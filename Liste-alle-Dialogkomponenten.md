## invocation name
office health

## intents

### runtime / runtime_corr
Fragt wie lange Nutzer arbeiten möchte bzw. wie lange der Skill aktiv bleiben soll. runtime_corr korrigiert einen falschen Input.

**slots**
* `work_time_min`: Arbeitszeit in Minuten
* `work_time_hour`: Arbeitszeit in Stunden (muss evtl. in Minuten umgerechnet werden)

**utterances**
* "Für `{work_time_min}` Minuten."
* "Für `{work_time_hour}` Stunden."
(Für runtime_corr sollte ein "Nein,..." oder "Falsch,..." Teil der utterance sein)

***

### intervals / intervals_corr
Fragt wie häufig der Nutzer während der Arbeit für Health Breaks unterbrochen werden will. intervals_corr korrigiert einen falschen Input.

**slots**
* `break_amount`: Anzahl an Pausen
* `break_interval_min`: Intervall zwischen den Pausen in Minuten
* `break_interval_hour`: Intervall zwischen den Pausen in Stunden

**utterances**
* "`{break_amount}` mal bitte."
* "Alle `{break_interval_min}` bitte."
* "Jede `{break_interval_hour}` Stunde bitte."

***

### confirmation
Bestätigt die vom Nutzer ausgewählten Einstellungen (runtime & intervals).

**utterances** 
* "Ja."
* "Ich bin bereit."

***

### workout_ready
Bestätigt, dass der Nutzer bereit ist die Health Break zu beginnen.

**utterances**
* "Ja."
* "Ich bin bereit."

***

### exercise_ready
Bestätigt, dass der Nutzer bereit ist die Übung zu beginnen. Gibt den Nutzer die Möglichkeit, die Anleitung nochmal anzuhören.

**utterances**
* "Ja."
* "Ich bin bereit."
* "Wiederhole die Anweisungen."

***

### next_exercise_ready
Bestätigt, dass der Nutzer die nächste Übung machen möchte. (Eventuell redundant?)

**utterances**
* "Ja."
* "Ich bin bereit."
