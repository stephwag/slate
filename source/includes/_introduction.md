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