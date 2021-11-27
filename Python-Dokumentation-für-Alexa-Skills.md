## Python Dokumentation als PDF

[ASK SDK for Python](https://readthedocs.org/projects/alexa-skills-kit-python-sdk/downloads/pdf/latest/)

<br>

## Intent Confirmation

### Code

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

### Erklärung

Damit Alexa nochmal die Eingabe des Nutzers abfragt muss für den spezifischen Intent im Interaction Model unter Build die "Intent Confirmation" aktiviert werden. Der Nutzer kann die Eingabe dann nochmal bestätigen bzw. ablehnen, was dann als `confirmation_status` (entweder `CONFIRMED` oder `DENIED`) gespeichert wird.

Um diesen `confirmation_status` in der lambda_function.py abzurufen muss erstmal das ask_sdk_model importiert werden. Dann kann überprüft werden, ob der `confirmation_status` des intents (auslesbar als `handler_input.request_envelope.request.intent.confirmation_status`) bestätigt oder abgelehnt wurde (abgefragt als `ask_sdk_model.intent_confirmation_status.IntentConfirmationStatus.CONFIRMED`).

<br>

## Zufälliger speak_output

### Code

**lambda_function.py**

```python
import random
import speak_input as si

...

        spo_1 = si.lr_spo_1
        spo_2 = si.lr_spo_2
        spo_3 = si.lr_spo_3
        rpo = si.lr_rpo
        
        speak_output = spo_1[random.randrange(0, len(spo_1)-1)] + " " + spo_2[random.randrange(0, len(spo_2)-1)] + " " + spo_3[random.randrange(0, len(spo_3)-1)]
        reprompt_output = rpo[random.randrange(0, len(rpo)-1)]
```

**speak_input.py**

```python
lr_spo_1 = [
        "...", 
        "..."
        ]

lr_spo_2 = [
        "...", 
        "..."
        ]

lr_spo_3 = [
        "...", 
        "..."
        ]

lr_rpo = [
        "...", 
        "..."
        ]

```

### Erklärung

Damit Alexa für den `speak_output` zufällig verschiedene Varianten verwendet müssen wir erstmal die `random` Library importieren. Die verschiedenen Varianten sind in Listen abgespeichert, aus welchen Alexa dann zufällig eine Variante auswählt.

Um die Lesbarkeit der `lambda_function.py` nicht zu beeinträchtigen haben wir die Listen in eine weitere Pythondatei getan, welche per `import speak_input as si` in die `lambda_function.py` eingefügt wird.

<br>