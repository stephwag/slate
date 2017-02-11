# Authentication

### API Key

> API Key Information Retrieval

```shell
curl "http://api.ispeech.org/api/rest?apikey=**YOUR_KEY_HERE**
&action=information&output=rest"
```

> HTTP Response

```shell
[…]&voice-locale-94-1=ja&voice-locale-94-2=ja-jp&voice-gender-94=female
&voice-description-94=Japanese+Female+Voice&wordlimit=40&model=assistant%2cdate
%2cnfl%2cnba%2cusmoney%2cmlb%2cnumbersto9%2cnumbersto99%2cnumbersto999%2ctime
%2cphonenumber%2cstreets%2csportsteam%2ccitystate&credits=5672606&unlimited=enabled
&alias=enabled&asr-sms=enabled&asr-voicemail=enabled&asr-dictation=enabled
```

<aside class="info">
All calls to the API require an API Key as a parameter
</aside>

An API key is a password that is required for access. To obtain an API key please visit: http://www.ispeech.org/developers and register for a developer account.

### View/Edit Keys

Manage your API keys by using the [iSpeech developer website](http://www.ispeech.org/developers).  You can request additional features for your API keys on that website.