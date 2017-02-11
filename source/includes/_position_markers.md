# Position Markers

## Request Parameters

> Example HTTP GET Request (Using most variables)

```shell
http://api.ispeech.org/api/rest?apikey=developerdemokeydeveloperdemokey
&action=convert&text=something&voice=usenglishfemale&format=mp3
&frequency=44100&bitrate=128&speed=1&startpadding=1&endpadding=1
&pitch=110&filename=myaudiofile
```

Parameter | Data Type | Example Value
---------- | ------- | -------
Action | String | markers
Text | String | Hello World
Voice (optional) | String | usenglishfemale (default)
Format (optional) | String | mp3 (default)
Speed (optional) | Integer | -10 to 10 (default: 0)
Startpadding (optional) | Integer (seconds) | 5 (default: 0)
Endpadding (optional) | Integer (seconds) | 5 (default: 0)

## Introduction

Position markers provide information regarding word boundaries to allow applications to visually display the current location in spoken audio.  It is similar to how a karaoke system would display lyrics.

This is accomplished by first retrieving audio from the iSpeech API (see section 2 for more details), then making a second request for an XML document which contains word boundary information.

## Example Transactions for Position Markers

### Note: Marker data is currently only presented in XML form.

To obtain marker information from the iSpeech API, you query the server in the same manner as a normal text-to-speech request. The only difference between a TTS request and a marker request is the “action” parameter, which is set to “convert” for audio, and “markers” for marker information.

> HTTP GET network transaction to retrieve position markers

```shell
http://api.ispeech.org/api/rest?apikey=YOUR_API_KEY&action=markers
&text=hello+world
```

> Response

```xml
<?xml version="1.0" encoding="UTF-8"?>
<markers>
    <text>hello world</text>
    <voice>usenglishfemale</voice>
    <length>894</length>
    <words>2</words>
    <word>
        <start>70</start>
        <end>339</end>
        <index>1</index>
        <length>270</length>
        <text>hello</text>
    </word>
    <word>
        <start>340</start>
        <end>894</end>
        <index>2</index>
        <length>555</length>
        <text>world</text>
    </word>
</markers>
```

## Marker Information Usage Technique

Once you have obtained an audio file and the respective marker information XML document, you are ready to highlight text.

There are many methods to processing iSpeech marker information; the following outlines the most basic of those methods. Use the following steps as a baseline implementation.

<aside class="info">
Implementations will vary greatly depending on the platform.
</aside>

### Media Player Considerations

Your media player must support “location”, “position”, or must notify you of its current progress periodically. For example, in Flash, we set a timer to poll for the audio position every 250 milliseconds. Highlighting will be more accurate with a low interval.

### Implementation

If your media player supports retrieval of “current position” or similar, you can follow these basic steps:

1.  Retrieve audio
2.  Retrieve marker information xml
3.  Parse xml into enumerable container/object
4.  Load audio into media player and start playing
5.  Create a timer and set it’s interval to 250 milliseconds
6.  Inside of the newly created timer, at every interval query the media player’s current position
7.  Convert the position to milliseconds (if you have number such as 1.343, simply multiply by 1000)
8.  Move to first (or next) “word” node inside of marker information xml document
9.  Check to see if current position is greater than or equal to the value of ”start” AND ALSO current position is less than or equal to the value of “end”, highlight the specified “text”
10.  If current position is greater than “word” “end” value go to step 8

You can follow the above steps until the audio file is exhausted.

## Notes

<aside class="info">
Due to the overhead of creation, we strongly recommend using short sentences instead of large blocks of text when requesting marker information.
</aside>

The same parameters must be sent in the markers request as the original TTS audio request. For example, if you pass a “speed” parameter during audio conversion, you must also send this parameter in your marker information request. If you fail to do so, the marker information will not line up correctly.

File type affects audio length. A MP3 file is always longer than a WAV file due to compression padding. The API will modify the file length accordingly.

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
33 | Invalid text or markers not supported for the selected voice
34 | Markers do not support audio padding or other option.
100 | This evaluation account has exceeded its trial period. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to upgrade your license.
101 | Your key has been disabled. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
997 | No api access
998 | Unsupported output type
999 | Invalid request
1000 | Invalid Request Method POST Required