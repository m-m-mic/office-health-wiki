## invocation name
office health

## intents

### runtime
Fragt wie lange Nutzer arbeiten möchte bzw. wie lange der Skill aktiv bleiben soll.

**slots**
* `work_time` (Type: AMAZON.DURATION): Arbeitszeit in Minuten/Stunden

**utterances**
* "Für `{work_time}`"
* "Ich arbeite heute für `{work_time}`"
* "Ich arbeite `work_time`"
* "`{work_time}`"

Intent confirmation: "Für `{work_time}` also. Stimmt das?"

***

### intervals
Fragt wie häufig der Nutzer während der Arbeit für Health Breaks unterbrochen werden will. intervals_corr korrigiert einen falschen Input.

**slots**
* `break_amount` (Type: AMAZON.NUMBER): Anzahl an Pausen
* `break_interval` (Type: AMAZON.DURATION): Intervall zwischen den Pausen in Minuten/Stunden

**utterances**
* "`{break_amount}` mal bitte"
* "Alle `{break_interval}` bitte"
* "Jede `{break_interval}` bitte"

Intent confirmation: "`{break_amount}` mal Pause also. Stimmt das?" oder "`Alle {break_interval}` also. Stimmt das?"

***

### final_confirmation
Fragt, ob der Benutzer bereit ist die Arbeitszeit zu beginnen.

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
**nicht notwendig, zu redundant**

Bestätigt, dass der Nutzer die nächste Übung machen möchte.

**utterances**
* "Ja."
* "Ich bin bereit."
