## invocation name
office health

## intents

### runtime
Soll gleich vom Nutzer nach LaunchRequest aufgerufen werden. Fragt wie lange der Nutzer arbeiten möchte bzw. wie lange der Skill aktiv bleiben soll.

**slots**: Ja
* `work_time` (Type: AMAZON.DURATION): Arbeitszeit in Minuten/Stunden

**utterances**: Ja
* "Für `{work_time}`"
* "Ich arbeite heute für `{work_time}`"
* "Ich arbeite `work_time`"
* "`{work_time}`"

**intent confirmation**: Ja 
* "Für `{work_time}` also. Stimmt das?"
* "Ich habe mir {work_time} gemerkt, passt das?"

***

### intervals
Folgt auf runtime. Fragt wie häufig der Nutzer während der Arbeit für Health Breaks unterbrochen werden will.

**slots**: Ja
* `break_amount` (Type: AMAZON.NUMBER): Anzahl an Pausen
* `break_interval` (Type: AMAZON.DURATION): Intervall zwischen den Pausen in Minuten/Stunden

**utterances**: Ja
* "`{break_amount}` mal bitte"
* "Alle `{break_interval}` bitte"
* "Jede `{break_interval}` bitte"

**intent confirmation**: Ja
* "`{break_amount}` mal Pause also. Stimmt das?" oder "`Alle {break_interval}` also. Stimmt das?"

***

### session_init
Folgt auf intervals. Fragt nach letzter Bestätigung des Nutzers, bevor die Session gestartet wird. Soll auch den Timer starten.

**slots**: Nein

**utterances**: Ja
* "Ja, los."
* "Ich will beginnen."

**intent confirmation**: Nein

***

### workout_explanation
Folgt auf session_init (erster Intervall) oder workout_finish (alle folgenden Intervalle) wenn Timer vorüber ist. Erklärt Nutzer die Übung, die bevorsteht.

**slots**: Nein

**utterances**: Ja
* "Bereit."
* "Ich bin bereit."

**intent confirmation**: Nein

***

### workout_init
Folgt auf workout_explanation. Führt Nutzer durch die Übung.

**slots**: Nein

**utterances**: Ja
* "Es kann losgehen."
* "Ich habe Dich verstanden."

**intent confirmation**: Nein

***

### workout_finish
Folgt ohne utterance des Nutzers auf workout_init so bald drei Übungen durchgeführt wurden. Gibt Nutzer Zeit, bevor die Arbeitszeit weitergeht.

**slots**: Nein

**utterances**: Nein

**intent confirmation**: Nein

***

### session_finish
Folgt ohne utterance des Nutzers auf workout_init wenn alle Übungen durchgeführt wurden. Bringt die Session zu Ende.

**slots**: Nein

**utterances**: Nein

**intent confirmation**: Nein