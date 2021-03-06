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

## Developer Support

### Sales

Automated purchasing system: https://www.ispeech.org/developer/purchase/
iSpeech sales can be contacted at the following phone number: +1-917-338-7723 from 10 AM to 6 PM Eastern Time, Monday to Friday.  You can also email sales@ispeech.org.

### Support / Troubleshooting

Please contact our support team at <a href="mailto:support@ispeech.org">support@ispeech.org</a>.

## Software Development Kits

iSpeech SDKs simplify the iSpeech API.  You should use iSpeech SDKs if the option is available.  Only mobile SDKs made by iSpeech allow you to use the iSpeech API for free.

### Availability

iPhone, Android, BlackBerry, .NET, Java (Server), PHP, Flash, Javascript/Flash, Ruby, Python, Perl

### API Access Pricing

Platforms | Price
---------- | -------
iPhone, Android, BlackBerry | Free with fair usage using iSpeech SDK for non-revenue generating apps.  Apps must follow the iSpeech standard usage guidelines for branding.
.NET, Java, PHP, Flash, Ruby, Python, Perl | Between $0.05 and $0.0001 per word (TTS) or transaction (ASR), depending on quantity