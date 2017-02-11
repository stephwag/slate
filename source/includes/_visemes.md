# Visemes

## Request Parameters

Parameter | Data Type | Example Value
---------- | ------- | -------
Action | String | viseme
Text | String | Hello World
Voice (optional) | String | usenglishfemale (default)
Format  (optional) | String | mp3 (default)
Speed (optional) | Integer | -10 to 10 (default: 0)
Startpadding (optional) | Integer (seconds) | 5 (default: 0)
Endpadding (optional) | Integer (seconds) | 5 (default: 0)

## Introduction

Visemes provide information regarding the mouth position and time interval of spoken audio which allows applications to visually pronounce audio.

This is accomplished by first retrieving audio from the iSpeech API (see section 2 for more details), then making a second request for an XML document which contains viseme information.

## Example Transaction for Viseme Retrieval

> HTTP GET network transaction to retrieve viseme positions

```shell
http://api.ispeech.org/api/rest?apikey=YOUR_API_KEY&action=viseme
&text=hello+world
```

> Response

```xml
<visemes>
   <text>hello world</text>
   <voice>usenglishfemale</voice>
   <length>753</length>
   <frames>9</frames>
   <viseme>
      <start>1</start>
      <end>74</end>
      <index>1</index>
      <length>74</length>
      <mouth>12</mouth>
   </viseme>
   <viseme>
      <start>75</start>
      <end>102</end>
      <index>2</index>
      <length>28</length>
      <mouth>4</mouth>
   </viseme>
   <viseme>
      <start>103</start>
      <end>182</end>
      <index>3</index>
      <length>80</length>
      <mouth>14</mouth>
   </viseme>
   <viseme>
      <start>183</start>
      <end>269</end>
      <index>4</index>
      <length>87</length>
      <mouth>8</mouth>
   </viseme>
   <viseme>
      <start>270</start>
      <end>359</end>
      <index>5</index>
      <length>90</length>
      <mouth>7</mouth>
   </viseme>
   <viseme>
      <start>360</start>
      <end>470</end>
      <index>6</index>
      <length>111</length>
      <mouth>5</mouth>
   </viseme>
   <viseme>
      <start>471</start>
      <end>660</end>
      <index>7</index>
      <length>190</length>
      <mouth>14</mouth>
   </viseme>
   <viseme>
      <start>661</start>
      <end>752</end>
      <index>8</index>
      <length>92</length>
      <mouth>19</mouth>
   </viseme>
   <viseme>
      <start>753</start>
      <end>753</end>
      <index>9</index>
      <length>1</length>
      <mouth>0</mouth>
   </viseme>
</visemes>
```

<aside class="info">
Viseme data is currently only presented in XML form.
</aside>

To obtain viseme information from the iSpeech API, you query the server in the same manner as a normal text-to-speech request. The only difference between a TTS request and a marker request is the “action” parameter, which is set to “convert” for audio, and “viseme” for viseme information.

## Viseme Chart

<table cellpadding="0" cellspacing="0" class="c0">
         <tbody>
            <tr class="c60">
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth08.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 0</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth09.jpg" width="100%"><span class="c4">&nbsp;Mouth 1</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth11.jpg" width="100%"><span class="c4">Mouth 2</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth12.jpg" width="100%"><span class="c4">Mouth 3</span></p>
               </td>
            </tr>
            <tr class="c6">
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth01.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 4</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth00.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 5</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth03.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 6</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth02.jpg" width="100%"><span class="c4">&nbsp;Mouth 7</span></p>
               </td>
            </tr>
            <tr class="c6">
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth04.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 8</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth13.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 9</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth14.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 10</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth15.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 11</span></p>
               </td>
            </tr>
            <tr class="c6">
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth16.jpg" width="100%"><span class="c4">&nbsp;Mouth 12</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth19.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 13</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth20.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 14</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth21.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 15</span></p>
               </td>
            </tr>
            <tr class="c6">
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth22.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 16</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth17.jpg" width="100%"><span class="c4">&nbsp;Mouth 17</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth18.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth18</span></p>
               </td>
               <td class="c43">
                  <p class="c3 c38"><img height="100%" src="http://www.ispeech.org/images/mouth10.jpg" width="100%"><span class="c4">&nbsp;Mouth 19</span></p>
               </td>
            </tr>
            <tr class="c6">
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth05.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 20</span></p>
               </td>
               <td class="c43">
                  <p class="c3"><img height="100%" src="http://www.ispeech.org/images/mouth07.jpg" width="100%"></p>
                  <p class="c3 c38"><span class="c4">Mouth 21</span></p>
               </td>
               <td class="c43">
                  <p class="c1"><span class="c10"></span></p>
               </td>
               <td class="c43">
                  <p class="c1"><span class="c10"></span></p>
               </td>
            </tr>
         </tbody>
      </table>

## Viseme Usage Technique

Once you have obtained an audio file and the respective viseme information XML document, you are ready to animate mouth positions to simulate speaking.

There are many methods to processing iSpeech viseme information; the following outlines the most basic of those methods. Use the following steps as a baseline implementation.

<aside class="info">
Implementations will vary greatly depending on the platform.
</aside>

### Media Player Considerations

Your media player must support “location”, “position”, or must notify you of its current progress periodically. For example, in Flash, we set a timer to poll for the audio position every 250 milliseconds. Mouth positioning will be more accurate with a low interval.

### Implementation

If your media player supports retrieval of “current position” or similar, you can follow these basic steps:

1.  Retrieve audio
2.  Retrieve viseme information xml
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
Due to the overhead of creation, we strongly recommend using short sentences instead of large blocks of text when requesting viseme information.
</aside>

The same parameters must be sent in the viseme request as the original TTS audio request. For example, if you pass a “speed” parameter during audio conversion, you must also send this parameter in your marker information request. If you fail to do so, the viseme will not line up correctly.

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
29 | Viseme not supported for the selected voice.
30 | Option not enabled for your account. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
32 | Invalid pitch
100 | This evaluation account has exceeded its trial period. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to upgrade your license.
101 | Your key has been disabled. Please contact iSpeech sales at +1 (917) 338-7723 or at sales@ispeech.org to modify your license.
997 | No api access
998 | Unsupported output type
999 | Invalid request
1000 | Invalid Request Method POST Required