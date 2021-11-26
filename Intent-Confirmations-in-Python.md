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

[Dokumentation in Python](https://readthedocs.org/projects/alexa-skills-kit-python-sdk/downloads/pdf/latest/)

