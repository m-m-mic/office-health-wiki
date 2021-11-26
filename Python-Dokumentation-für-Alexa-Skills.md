## Python Dokumentation als PDF
<br>

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

