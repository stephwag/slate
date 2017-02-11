# Automated Speech Recognition

## Transaction Types and URL Formats

Transaction Type | Input Format | URL
---------- | ------- | -------
HTTP GET/POST | URL Encoded | http://api.ispeech.org/api/rest
HTTP GET/POST | XML | http://api.ispeech.org/api/xml
HTTP GET/POST | JSON | http://api.ispeech.org/api/json

There are currently three transaction types available for use with the iSpeech API.  All transactions must use the appropriate URL.

## Request Parameters

Parameter | Data Type | Example Value
---------- | ------- | -------
Apikey | 32 character hex integer | abcdef1234567890abcdef1234567890
Locale | String | en-US
Action | String | recognize
Content-Type | String | audio/x-wav, audio/amr, audio/speex
Audio | String (base64, remove \r\n) | UklGRgAKAQBsl/j2+sa0dR [...]
Output (optional) | String | xml, json, rest (default: rest)
Freeform (optional) | Integer (0 to 7) | 3
Model (optional) | String | assistant
Speexmode (optional) | Integer (1 to 3) | 1 (speex codec only)

## Locales

### Standard Locales

Name | Alias | Support
---------- | ------- | -------
English (United States) | locale=en-US (default) | freeform & command list
English (Canada) | locale=en-CA | freeform & command list
English (United Kingdom) | locale=en-GB | freeform & command list
English (Australia) | locale=en-AU | freeform & command list
Spanish (Spain) | locale=es-ES | freeform & command list
Spanish (Mexico) | locale=es-MX | freeform & command list
Italian (Italy) | locale=it-IT | freeform & command list
French (France) | locale=fr-FR | freeform & command list
French (Canada) | locale=fr-CA | freeform & command list
Polish (Poland) | locale=pl-PL | freeform & command list
Portuguese (Portugal) | locale=pt-PT | freeform & command list
Catalan (Catalan) | locale=ca-ES | command list
Chinese (Taiwan) | locale=zh-TW | command list
Danish (Denmark) | locale=da-DK | command list
German (Germany) | locale=fr-FR | command list
Finnish (Finland) | locale=it-IT | command list
Japanese (Japan) | locale=ja-JP | command list
Korean (Korea) | locale=ko-KR | command list
Dutch (Netherlands) | locale=nl-NL | command list
Norwegian (Norway) | locale=nb-NO | command list
Portuguese (Brazil) | locale=pt-BR | command list
Russian (Russia) | locale=ru-RU | command list
Swedish (Sweden) | locale=sv-SE | command list
Chinese (People's Republic of China) | locale=zh-CN | command list
Chinese (Hong Kong S.A.R.) | locale=zh-HK | command list

### Custom Locales

Contact sales@ispeech.org for details.

## Speech Recognition Models

Statistical speech recognition models are used to increase the probability of a correct result.  Models with fewer word choices are faster and more accurate than the freeform models.  For example, in the food model the words, “7 up” would be recognized as, “7up”.  Another example is with a food model would recognize the audio from “ice cream”  as “ice cream” instead of “i scream”.

### Standard Freeform Models

Name | Value | Use Case
---------- | ------- | -------
SMS / General Messages | freeform=1 | Text Messages
Voice mail | freeform=2 | Voice Mail
Dictation | freeform=3 | Normal speech
Message (coming soon) | freeform=4 | Email
Instant Message (coming soon) | freeform=5 | Instant Message
Transcript (coming soon) | freeform=6 | 
Memo (coming soon) | freeform=7 | Memorandum
Web (coming soon) | freeform=8 | Web search

### Standard Non-Freeform Models

Name | Value | Use Case
---------- | ------- | -------
Assistant | model=assistant | Personal Assistant
Date | model=date | Date
NFL | model=nfl | Football teams
NBA | model=nba | Basketball teams
US Money | model=usmoney | US Money
Numbers to 9 | model=numbersto9 | Numbers, 0 to 9
Numbers to 99 | model=numbersto99 | Numbers, 0 to 99
Numbers to 999 | model=numbersto999 | Numbers, 0 to 999
Time | model=time | Time
Phone number | model=phonenumber | Phone number
Streets | model=streets | Streets
Sports Team | model=sportsteam | Sports Teams
City/State | model=citystate | US City/States

### Custom Models

Contact sales@ispeech.org for details.

## Speex Modes

Name | Value
---------- | -------
Narrowband (8khz) | speexmode=1
Wideband (16khz) - Recommended | speexmode=2
Ultra Wideband (32kz) | speexmode=3

The speexmode variable tells the server which format your Speex data is encoded in for improved speech recognition quality. It is highly recommended you include this parameter when using Speex encoding.

## Example Transactions for Freeform Speech

### Format of Examples

> HTTP REST Request for Speech Recognition

```shell
POST /api/rest HTTP/1.1
Content-Length: 34875
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive

apikey=developerdemokeydeveloperdemokey&action=recognize&freeform=1&content-type=audio/x-wav&output=rest&locale=en-us&audio=[base64 encoded something.wav without \r\n characters]
```

> HTTP Response

```shell
HTTP/1.0 200 OK
Connection: close
Content-Length: 59
Content-Type: text/plain
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

text=something&confidence=0.0216270890086889&result=success
```

> HTTP JSON Request for Speech Recognition

```json
POST /api/json HTTP/1.1
Content-Length: 34897
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive

{"apikey":"developerdemokeydeveloperdemokey","action":"recognize",
"freeform":"1", "locale":"en-us", "content-type":"audio/x-wav", "output":"rest", "audio":"[base64 encoded something.wav without \r\n characters]”}
```

> Response

```shell
HTTP/1.0 200 OK
Connection: close
Content-Length: 59
Content-Type: application/json
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

text=something&confidence=0.0134419081732631&result=success
```

> HTTP XML network request for Speech Recognition

```xml

POST /api/xml HTTP/1.1
Content-Length: 34953
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive
User-Agent: Apache-HttpClient/4.0.1 (java 1.5)
Expect: 100-Continue

<data>
<apikey>developerdemokeydeveloperdemokey</apikey>
<action>recognize</action>
<freeform>1</freeform>
<locale>en-us</locale>
<content-type>audio/x-wav</content-type>
<output>xml</output>
<audio>[base64 encoded something.wav without \r\n characters]</audio>
</data>
```

> XML Response

```xml
HTTP/1.0 200 OK
Connection: close
Content-Length: 140
Content-Type: text/xml
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

<?xml version="1.0" encoding="UTF-8"?>
<data>
<text>something</text>
<confidence>0.0216270890086889</confidence>
<result>success</result>
</data>
```

The following examples are packet captures from TCP connections that used the HTTP protocol.  You can compare your network traffic to these transactions to debug code.  Wireshark can be used to analyze network connections.

## Command Lists

Command lists are used to limit the possible values returned during speech recognition.  For example, if the command list contains only “yes” and “no”, the result will be either “yes” or “no”.

## Example Transactions for Command Lists

### Formatting of Examples

> HTTP XML network request to detect commands from a list

```xml
POST /api/xml HTTP/1.1
Content-Length: 80941
Content-Type: text/xml; charset=UTF-8
Host: api.ispeech.org
Expect: 100-Continue

<data>
<apikey>developerdemokeydeveloperdemokey</apikey>
<action>recognize</action>
<locale>en-US</locale>
<output>xml</output>
<alias>command1|YESNOMAYBE</alias>
<YESNOMAYBE>yes|no|maybe</YESNOMAYBE>
<command1>say %YESNOMAYBE%</command1>
<content-type>audio/x-wav</content-type>
<audio>[base64 encoded say_yes.wav without \r\n characters]</audio>
</data>
```

> XML Response

```xml
HTTP/1.0 200 OK
Connection: close
Content-Length: 137
Content-Type: text/xml
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

<?xml version="1.0" encoding="UTF-8"?>
<data>
<text>say yes</text>
<confidence>0.726751327514648</confidence>
<result>success</result>
</data>
```

> HTTP REST network request to detect commands from a list

```shell
POST /api/rest/ HTTP/1.1
Content-Length: 72682
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Expect: 100-Continue

apikey=developerdemokeydeveloperdemokey&action=recognize&locale=en-us&content-type=audio%2Fwav&output=rest&alias=command1|NAMES
&NAMES=john|mary|anna&command1=call%20%25NAMES%25&audio=[base64 encoded wav without \r\n characters]
```

> HTTP Response

```shell
HTTP/1.0 200 OK
Connection: close
Content-Length: 58
Content-Type: text/plain
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

text=call+mary&confidence=0.672464966773987&result=success
```

> HTTP POST JSON request to detect commands from a list

```json
POST /api/json/ HTTP/1.1
Content-Length: 22788
Content-Type: text/plain; charset=UTF-8
Host: api.ispeech.org
Expect: 100-Continue

{"apikey":"developerdemokeydeveloperdemokey","action":"recognize","locale":"en-US","alias":"command1|YESNOMAYBE","YESNOMAYBE":"yes|no|maybe","command1":"say %YESNOMAYBE%","content-type":"audio/x-wav","output":"rest","audio":"[base64 encoded say_yes.wav without \r\n characters]"}
```

> Response

```shell
HTTP/1.0 200 OK
Connection: close
Content-Length: 56
Content-Type: application/json
Cache-Control: no-cache, no-store, must-revalidate, max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

text=say+yes&confidence=0.726751327514648&result=success
```

> Advanced Example, HTTP POST XML request to detect multiple audio commands from multiple lists

```xml
POST /api/xml HTTP/1.1
Content-Length: 91393
Content-Type: text/xml; charset=UTF-8
Host: api.ispeech.org
Connection: Keep-Alive
Expect: 100-Continue

<data>
<apikey>developerdemokeydeveloperdemokey</apikey>
<action>recognize</action>
<locale>en-us</locale>
<content-type>audio/x-wav</content-type>
<output>xml</output>
<alias>command1|command2|MONITORACTIONS|COLORLIST|
DYNAMITEACTIONS|OBJECTLIST</alias>
<MONITORACTIONS>on|off|reset</MONITORACTIONS>
<COLORLIST>blue|green|red|yellow|purple|orange|black|white|cyan</COLORLIST>
<DYNAMITEACTIONS>explode|fizzle out</DYNAMITEACTIONS>
<OBJECTLIST>monitor %MONITORACTIONS%|color %COLORLIST%|dynamite  %DYNAMITEACTIONS%</OBJECTLIST>
<command1>set %OBJECTLIST%</command1>
<command2>quit menu</command2>
<audio>[base64 encoded set_dynamite_explode.wav
without \r\n characters]</audio>
</data>
```

> XML Response

```xml
HTTP/1.0 200 OK
Connection: close
Content-Length: 150
Content-Type: text/xml
Cache-Control: no-cache, no-store, must-revalidate,
max-age=0, proxy-revalidate, no-transform
Pragma: no-cache

<?xml version="1.0" encoding="UTF-8"?><data><text>set dynamite explode</text><confidence>0.589247465133667</confidence>
<result>success</result></data>
```

<aside class="success">
If a user speaks "say yes", ”say maybe”, or “say no” it will be successfully recognized.
</aside>

<aside class="success">
If a user speaks "call john", "call anna", or "call mary" it will be successfully recognized.
</aside>

<aside class="success">
If a user speaks "set monitor on", ”set monitor off”, or “set dynamite explode”, etc. it will be successfully recognized.
</aside>

The following examples are packet captures of TCP connections that use the HTTP protocol.  You can compare your network traffic with these transactions to debug code.  Wireshark can be used to analyze network connections.  A REST client can be used to make these HTTP requests.

## Errors

Code | Summary
------- | -------
1 | Invalid API key
3 | Not enough credits
4 | No action specified
12 | Invalid file format
14 | Invalid dictionary
17 | Invalid alias list
18 | Alias missing
19 | Invalid content type
20 | Alias list too complex
21 | Could not recognize
23 | Invalid locale
24 | Bad audio data
25 | Model not supported or disabled
26 | Selected model does not support desired locale
28 | Locale not supported
30 | Option not enabled for your account. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
100 | This evaluation account has exceeded its trial period. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to upgrade your license.
101 | Your key has been disabled. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
997 | No api access
998 | Unsupported output type
999 | Invalid request
1000 | Invalid Request Method POST Required