---
title: API Reference

language_tabs:
  - curl

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Developer Guide

iSpeech Inc. (“iSpeech”) has made efforts to ensure the accuracy and
completeness of the information in this document. However, iSpeech Inc. disclaims all
representations, warranties and conditions, whether express or implied, arising by
statute, operation of law, usage of trade, course of dealing or otherwise, with respect to
the information contained herein. iSpeech Inc. assumes no liability to any party for any
loss or damage, whether direct, indirect, incidental, consequential, special or exemplary,
with respect to (a) the information; and/or (b) the evaluation, application or use of any
product or service described herein.

iSpeech Inc. disclaims any and all representation that its products or services infringe
upon any existing or future intellectual property rights. iSpeech Inc. owns and retains all
right, title and interest in and to the iSpeech Inc. intellectual property, including without
limitation, its patents, marks, copyrights and technology associated with the
iSpeech Inc. services. No title or ownership of any of the foregoing is granted or
otherwise transferred hereunder. iSpeech Inc. reserves the right to make changes to
any information herein without further notice.

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

### Information

### Text to Speech

### Automated Speech Recognition

### Position Markers

### Visemes

