# Introduction

Welcome to the iSpeech Inc. Application Programming Interface (API) Developer Guide.  This guide describes the available variables, commands, and interfaces that make up the iSpeech API.

The iSpeech API allows developers to implement Text-To-Speech (TTS) and Automated Voice Recognition (ASR) in any Internet-enabled application.

The API's are platform agnostic which means any device that can record or play audio that is connected to the Internet can use the iSpeech API.

## Minimum Requirements

Below are the minimum requirements needed to use the iSpeech API.  The API can be use with and without a software development kit (SDK).

### Internet Connection

iSpeech services require an Internet connection.

### HTTP Protocol

The iSpeech API follows the HTTP standard by using GET and POST.  Some web browsers limit the length of GET requests to a few thousand characters.

### Request/Responses

Requests can be in URL-encoded, JSON, or XML data formats.  You can specify the output data format of responses.  For TTS, binary data is usually returned if the request is successful.  For speech recognition, URL-encoded text, JSON, or XML can be returned by setting the output variable.

### API Key

An API key is a password that is required for access.  To obtain an API key please visit: http://www.ispeech.org/developers and register for a developer account.

## Managing API Key Settings

### View/Edit Keys

Manage your API keys by using the [iSpeech developer website](http://www.ispeech.org/developers).  You can request additional features for your API keys on that website.

## API Features

You can retrieve the properties of your API keys.  Key information includes a voice list, amount of credits, locales, and many other parameters.

### Text to Speech

You can synthesize spoken audio through iSpeech TTS in a variety of voices, formats, bitrates, frequencies, and playback speeds.  Math markup language (MathML) and Speech synthesis markup language (SSML) are also supported.

### Automated Speech Recognition

You can convert spoken audio to text using a variety of languages and recognition models.  We can create custom recognition models to improve recognition quality.

### Position Markers

You can get the position in time when words are spoken in TTS audio.

### Visemes

You can get the position in time of mouth positions when words are spoken in TTS audio.

## API Key Information Retrieval

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

## Developer Support

### Sales

Automated purchasing system: https://www.ispeech.org/developer/purchase/
iSpeech sales can be contacted at the following phone number: +1-917-338-7723 from 10 AM to 6 PM Eastern Time, Monday to Friday.  You can also email sales@ispeech.org.

### Support / Troubleshooting

Please look for the answer to your problem in the iSpeech Developer Forum: http://www.ispeech.org/forums/

## Software Development Kits

iSpeech SDKs simplify the iSpeech API.  You should use iSpeech SDKs if the option is available.  Only mobile SDKs made by iSpeech allow you to use the iSpeech API for free.

### Availability

iPhone, Android, BlackBerry, .NET, Java (Server), PHP, Flash, Javascript/Flash, Ruby, Python, Perl

### API Access Pricing

Platforms | Price
---------- | -------
iPhone, Android, BlackBerry | Free with fair usage using iSpeech SDK for non-revenue generating apps.  Apps must follow the iSpeech standard usage guidelines for branding.
.NET, Java, PHP, Flash, Ruby, Python, Perl | Between $0.05 and $0.0001 per word (TTS) or transaction (ASR), depending on quantity