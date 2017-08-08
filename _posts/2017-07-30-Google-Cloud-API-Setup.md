---
layout: post
title: Google Cloud API Setup
author: Author Heming
---

Continued from the last post. This note intends to give a small demonstration of the API usage of Google cloud.


## First you need to enable it
Here we use the translation API as the example. Search "Google translation API" in control console, and then choose "enable".

Once you've done that, create a new directory say called 'translationAPI'

## Read the Documentation and get started
https://cloud.google.com/translate/docs/getting-started?csw=1
Here is the link for the translation API.
Using python will simplify the task. Install the whole set of api by
~~~
pip install google-cloud
~~~

or just install the translation api

~~~
pip install google-cloud-translate
~~~

## Setup Google cridentials
Choose create credentials > choose "service account key" > choose new service account > make a name > select a role. This will give you a a json file of identity info. Open up this .json file then copy it to the working directory.

Then set the path

~~~
export GOOGLE_APPLICATION_CREDENTIALS=~/gcloud/apikey.json
~~~ 
If you want to make it permanent, add this time in the .profile file.


## Run the test

With the setups, it is time for coding.

~~~
from google.cloud import translate

def translate_text(text, target='en'):
    translate_client = translate.Client()
    result = translate_client.translate(text, target_language=target)

    print('Text: ', result['input'])
    print('Translation', result)

if __name__ == "__main__":
    test_text = 'Comment vous appelez-vous?'
    translate_text(test_text)~~~

translation_client = translate.Client()

~~~

The result is 
~~~
('Text: ', 'Comment vous appelez-vous?')
('Translation', {u'translatedText': u'What is your name?', 'input': 'Comment vous appelez
-vous?', u'detectedSourceLanguage': u'fr'})
~~~