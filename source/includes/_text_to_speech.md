# Text to Speech

The iSpeech Text-To-Speech API allows you to synthesize high-quality spoken audio in multiple formats. The iSpeech API doesn’t use callbacks because it’s fast and synchronous. You'll always receive audio data or an error message in the same HTTP transaction.

> Example HTTP GET Request (Using most variables)

```shell
curl http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=mp3
&frequency=44100&bitrate=128&speed=1&startpadding=1&endpadding=1
&pitch=110&filename=myaudiofile
```

## Transaction Types and URL Formats

Transaction Type | Input Format | URL
---------- | ------- | -------
HTTP GET/POST | URL Encoded | http://api.ispeech.org/api/rest
HTTP GET/POST | XML | http://api.ispeech.org/api/xml
HTTP GET/POST | JSON | http://api.ispeech.org/api/json

## Request Parameters

Parameter | Data Type | Example Value
---------- | ------- | -------
Apikey | 32 character hex integer | abcdef1234567890abcdef1234567890
Action | String | convert, ssml
Text | String | Hello World
Ssml (optional) | String | <?xml version=”1.0” ?><speak version= […] |
Voice (optional) | String | usenglishfemale (default)
Format (optional) | String | mp3 (default)
Frequency (optional) | Integer (hertz) | 16000 (default)
Bitrate (optional) | Integer (kbps) | 48 (default)
Speed (optional) | Integer | -10 to 10 (default: 0)
Startpadding (optional) | Integer (seconds) | 5 (default: 0)
Endpadding (optional) | Integer (seconds) | 5 (default: 0)
Pitch (optional) | Integer | 0 to 200 (default: 100)
Bitdepth (optional) | Integer (bits per sample) | 8 or 16 (default: 16)
Filename (optional) | String | myaudio or myaudio.mp3 (default: rest.*)
Library (optional) | String | libmath

## Voices - Standard

> HTTP GET Request (Setting voice to European French Female)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&format=mp3&voice=eurfrenchfemale"
```

Name | Alias
---------- | -------
US English Female (default) | usenglishfemale
US English Male | usenglishmale
UK English Female | ukenglishfemale
UK English Male | ukenglishmale
Australian English Female | auenglishfemale
US Spanish Female | usspanishfemale
US Spanish Male | usspanishmale
Chinese Female | chchinesefemale
Chinese Male | chchinesemale
Hong Kong Cantonese Female | hkchinesefemale
Taiwan Chinese Female | twchinesefemale
Japanese Female | jpjapanesefemale
Japanese Male | jpjapanesemale
Korean Female | krkoreanfemale
Korean Male | krkoreanmale
Canadian English Female | caenglishfemale
Hungarian Female | huhungarianfemale
Brazilian Portuguese Female | brportuguesefemale
European Portuguese Female | eurportuguesefemale
European Portuguese Male | eurportuguesemale
European Spanish Female | eurspanishfemale
European Spanish Male | eurspanishmale
European Catalan Female | eurcatalanfemale
European Czech Female | eurczechfemale
European Danish Female | eurdanishfemale
European Finnish Female | eurfinnishfemale
European French Female | eurfrenchfemale
European French Male | eurfrenchmale
European Norwegian Female | eurnorwegianfemale
European Dutch Female | eurdutchfemale
European Polish Female | eurpolishfemale
European Italian Female | euritalianfemale
European Italian Male | euritalianmale
European Turkish Female | eurturkishfemale
European Turkish Male | eurturkishmale
European German Female | eurgermanfemale
European German Male | eurgermanmale
Russian Female | rurussianfemale
Russian Male | rurussianmale
Swedish Female | swswedishfemale
Canadian French Female | cafrenchfemale
Canadian French Male | cafrenchmale
Arabic Male | ararabicmale

## Voices - Custom

Custom Voices may be enabled for your account.  They can be found in the developer portal -> api key properties -> custom voices.  You can use them by setting the variable voice to the custom alias.

Name | Alias
---------- | -------
President Obama | Obama (voice=obama)
Custom Voice | customvoice1 (voice=customvoice1)

## Voices - List Retrieval

> HTTP GET Network Transaction to get XML voice list.

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=information&output=(xml, rest, or json)"
```

> XML Response

```xml
<?xml version='1.0'?>
<data>
    <result>success</result>
    <voice-1>krkoreanfemale</voice-1>
    <voice-locale-1-1>ko-kr</voice-locale-1-1>
    <voice-locale-1-2>ko</voice-locale-1-2>
    <voice-gender-1>female</voice-gender-1>
    <voice-description-1>Korean Female Voice</voice-description-1>
    <voice-2>usenglishfemale</voice-2>
    <voice-locale-2-1>en-us</voice-locale-2-1>
    <voice-locale-2-2>en</voice-locale-2-2>
    <voice-gender-2>female</voice-gender-2>
    <voice-description-2>United States English Female Voice</voice-description-2>
</data>
```

> JSON Response

```json
{
  "voice-gender-48":"female",
  "voice-locale-22-1":"fr-ca",
  "voice-locale-8-1":"pt-br",
  "voice-description-2":"Finnish Female Voice",
  "voice-description-3":"Hong Kong Chinese Male Voice",
  "voice-58":"eurdanishfemale",
  "voice-description-1":"Korean Female Voice",
  "voice-description-6":"Chinese Female Voice",
  "voice-description-7":"United Kingdom English Female Voice"
}
```

> REST / URL Encoded Response

```shell
"result=success&voice-1=krkoreanfemale2&voice-locale-1-1=ko-kr&voice-gender-1=female&voice-description-1=Korean+Female+Voice&voice-2=eurfinnishfemale&voice-locale-2-1=fi-fi&voice-gender-2=female&voice-description-2=Finnish+Female+Voice&voice-3=chchinesemale1&voice-locale-3-1=zh&voice-locale-3-2=zh-hk[...more voices...]"
```

A current list of voices that are enabled for an API key can be retrieved in REST, JSON, and XML format by using the following service.  HTTP GET and POST are supported.  A web browser or a REST client can be used to make these HTTP requests.

Parameter | Supported Values
---------- | -------
output | xml, json, rest

## Speed

> HTTP GET Request (Setting speed to 5)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=mp3&speed=5"
```

Most voices support speed controls.

Speed | Value (Integer)
---------- | -------
Fastest | 10
Faster | Speed > 0
Normal (default) | 0
Slower | Speed < 0
Slowest | -10

## Bitrates

> HTTP GET Request (Setting bitrate to 16 kilobits per second)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=mp3&bitrate=16"
```

### Note: Bitrates can only be selected for MP3s.

Valid values are 16, 24, 32, 48 (default), 56, 64, 80, 96, 112, 128, 144, 160, 192, 224, 256, or 320.
Bitrates are listed in kilobits per second.

## Formats

> Example HTTP GET Request (Setting format to wav)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=wav"
```

Name | Extension
---------- | -------
Audio Interchange File Format | aiff
MPEG Layer 3 (default) | mp3
Ogg Vorbis | ogg
Windows Media Audio | wma
Free Lossless Audio Codec | flac
Wave PCM | wav
Wave (alaw) | alaw
Wave (µ-law) | ulaw
Dialogic ADPCM | vox
MPEG-4 | mp4

## Frequencies

> Example HTTP GET Request (Setting frequency to 16000 Hz)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&frequency=16000"
```

Possible values: 8000, 11025, 16000 (default), 22050, 24000, 32000, 44100, 48000 cycles per second (Hertz)

## Padding

Padding adds silence to a section of the audio file.

### Start Padding

> Example HTTP GET Request (Setting start padding to 3 seconds)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&startpadding=3"
```

Adds a period of silence to the beginning of the audio file.

### End Padding

> Example HTTP GET Request (Setting end padding to 3 seconds)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&endpadding=3"
```

Adds a period of silence to the beginning of the audio file.

## Pitch

> Example HTTP GET Request (Setting pitch to 50)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&pitch=50"
```

Possible values: 0 to 200 (integer), 0 is lowest pitch, 100 is default, 200 is highest pitch. Pitch is enabled only on some voices.

## Bit Depth

> Example HTTP GET Request (Setting bit depth to 8)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=wav
&bitdepth=8"
```

The bit depth is amount of audio detail for each audio sample.  

Possible values are 8 and 16 (default) bits/sample on AIFF, FLAC, and WAVE file formats.

## Filename

> Example HTTP GET Request (Setting filename of audio)

```shell
curl "http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=wav
&filename=myaudiofile"
```

The filename is the name of the audio file that will download.  Specifying the extension is optional.  If the extension is missing, the correct extension will be added automatically.  The default is rest.[extension], for example:  rest.mp3.

## Speech Synthesis Markup Language (SSML)

> Example HTTP GET Request (Emphasis added on the word big)

```shell
curl "http://api.ispeech.org/api/rest?apikey=YOUR_API_KEY_HERE&
action=ssml&ssml=%3C%3Fxml%20version%3D%221.0%22%3F%3E%3Cspeak
%20version%3D%221.0%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org
%2F2001%2F10%2Fsynthesis%22%20xmlns%3Axsi%3D%22http%3A%2F%2F
www.w3.org%2F2001%2FXMLSchema-instance%22
%20xsi%3AschemaLocation%3D%22http%3A%2F%2Fwww.w3.org%2F2001
%2F10%2Fsynthesis%20http%3A%2F%2Fwww.w3.org%2FTR%2Fspeech-synthesis
%2Fsynthesis.xsd%22%20xml%3Alang%3D%22en-US%22%3E
That%20is%20a%20%3Cemphasis%3E%20big%20%3C%2Femphasis%3E%20car!
%3C%2Fspeak%3E"
```

> Response

```xml
SSML used:

<?xml version="1.0"?>
<speak version="1.0" xmlns="http://www.w3.org/2001/10/synthesis"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.w3.org/2001/10/synthesis
                   http://www.w3.org/TR/speech-synthesis/synthesis.xsd"
         xml:lang="en-US">
  That is a <emphasis> big </emphasis> car!
</speak>
Audio synthesized as, “That is a BIG car!”.
```

SSML tags are used to customize the way a text-to-speech engine creates audio.  The tags can be used to add pauses, change emphasis, and change pronunciation.  This option is disabled by default but can be requested by emailing sales@ispeech.org.
The parameter “action” must set to “ssml” and the parameter “ssml” must be set to a complete SSML XML statement.

The parameter “text” is not used and the parameters voice and speed should be represented using the “voice” and “prosody” SSML tags instead of request parameters.

More information on SSML can be found at: http://www.w3.org/TR/speech-synthesis/.

## Math Markup Language (MathML)

```shell
curl "http://api.ispeech.org/api/rest?action=convert
&apikey=YOUR_API_KEY_HERE&library=libmath
&text=%3Cfmath%3E%3Cmrow%3E%3Cmtext%3E%3Csup%3E%2B%3C%2Fsup%3E%3C%2Fmtext%3E
%3Cmn%3E7%3C%2Fmn%3E%3C%2Fmrow%3E%3C%2Ffmath%3E"
```

> Response

```xml
MathML used: <mrow><mtext><sup>+</sup></mtext><mn>7</mn></mrow>

Audio synthesized as, “positive 7” instead of plus 7.
```

MathML tags are used to display and represent mathematical statements.  This option is disabled by default but can be requested by emailing sales@ispeech.org.

Remember to set “library” to “libmath” so that the MathML processor loads your text as MathML.

More information on MathML can be found at: https://developer.mozilla.org/en-US/docs/MathML

The following table lists MathML tags supported by the iSpeech API.

MathML Tag | Purpose
------- | -------
mfrac | Used to display fractions
mi | Rendered as an identifier such as function names, variables or symbolic constants.
mn | A numeric literal which is normally a sequence of digits with a possible separator (a dot or a comma). However, it is also allowed to have arbitrary text in it which is actually a numeric quantity, for example "eleven".
mo | An operator in a broad sense. Besides operators in strict mathematical meaning, this element also includes "operators" like parentheses, separators like comma and semicolon, or "absolute value" bars.
mroot | Displays roots with an explicit index. Two arguments are accepted, which leads to the syntax:`<mroot>` base index `</mroot>`.
mrow | Groups sub-expressions, which usually contain one or more operators with their respective operands (such as `<mi>` and `<mn>`). This element renders as a horizontal row containing its arguments.
msqrt | Displays square roots (no index is displayed). The square root accepts only one argument, which leads to the following syntax: `<msqrt>` base `</msqrt>`.
msup, sup | Attaches a superscript to an expression.
mtext | Renders arbitrary text with no notational meaning, such as comments or annotations.
mspan, span | Used for highlighting text or just general styling of an equation
mtable, table | Creates tables or matrices. Inside a `<mtable>`, only `<mtr>` and `<mtd>` elements may appear. These elements are similar to `<table>`, `<tr>` and `<td>` elements of HTML.

## Example Transactions

> HTTP POST URL encoded request for Text to Speech

```shell
POST /api/rest HTTP/1.1
Content-Length: 71
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive

apikey=developerdemokeydeveloperdemokey&action=convert&text=hello+world
```

> HTTP Response

```shell
HTTP/1.0 200 OK
Connection: close
Server: iSpeech Cloud/1.2
Accept-Ranges: none
X-Time-Length: 3853
X-Content-Hash: e969ef3dd0dc0e9c417f31f7ffbd10ed
Content-Length: 23760
Content-Type: audio/mpeg
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

[mp3 binary audio data]
```

> HTTP POST JSON request for Text to Speech

```shell
POST /api/json HTTP/1.1
Content-Length: 111
Content-Type: application/json; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive

{"apikey":"developerdemokeydeveloperdemokey","action":"convert","text":"hello world","voice":"usenglishfemale"}
```

> HTTP Response

```shell
Connection: close
Server: iSpeech Cloud/1.2
Accept-Ranges: none
X-Time-Length: 3853
X-Content-Hash: e969ef3dd0dc0e9c417f31f7ffbd10ed
Content-Length: 23760
Content-Type: audio/mpeg
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

[mp3 audio binary data]
```

> HTTP POST XML request for Text to Speech

```xml
POST /api/xml HTTP/1.1
Content-Length: 150
Content-Type: application/xml; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive

<data>
<apikey>developerdemokeydeveloperdemokey</apikey>
<action>convert</action>
<text>hello world</text>
<voice>usenglishfemale</voice>
</data>
```

> HTTP Response

```shell
HTTP/1.0 200 OK
Connection: close
Server: iSpeech Cloud/1.2
Accept-Ranges: none
X-Time-Length: 3853
X-Content-Hash: 4affe15913fccd851ebf08a7e2650955
Content-Length: 23760
Content-Type: audio/mpeg
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

[mp3 audio binary data]
```

> Example of a text-to-speech network transaction with an error. 
> Responses with an error message return HTTP status response code “HTTP/1.0 202 Accepted”.

```shell
GET /api/rest?apikey=developerdemokeydeveloperdemokey&action=convert&
text=something&output=rest&voice=usenglishfemal HTTP/1.1
Host: api.ispeech.org
Connection: keep-alive
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.2 (KHTML, like Gecko) Chrome/15.0.874.58 Safari/535.2
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Encoding: gzip,deflate,sdch
Accept-Language: en-US,en;q=0.8
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3
```

> Response

```shell
HTTP/1.0 202 Accepted
Server: iSpeech Cloud/1.2
Connection: close
Content-Length: 41
Content-Type: text/plain
Cache-Control: no-cache, no-store, must-revalidate, max-age=0,
proxy-revalidate, no-transform
Pragma: no-cache

result=error&code=8&message=Invalid+voice
```

The following examples are packet captures from TCP connections that used the HTTP protocol.  You can compare your network traffic to these transactions to debug code.  Wireshark can be used to analyze network connections.  A REST client can be used to make these HTTP requests.

## Example network transactions containing MathML


## Errors

Code | Summary
------- | -------
1 | Invalid API key
2 | Could not convert text
3 | Not enough credits
4 | No action specified
5 | Invalid text
6 | Too many words
7 | Invalid text entry
8 | Invalid voice
12 | Invalid file format
13 | Invalid speed
14 | Invalid dictionary
15 | Invalid bitrate
16 | Invalid frequency
30 | Option not enabled for your account. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
32 | Invalid pitch
100 | This evaluation account has exceeded its trial period. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to upgrade your license.
101 | Your key has been disabled. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
997 | No api access
998 | Unsupported output type
999 | Invalid request
1000 | Invalid Request Method POST Required
3000 | SSML error