# Transaction Types

The iSpeech API supports URL Encoded, XML, and JSON formats.

<aside class="info">
Position Marker and Viseme data is currently only presented in XML form
</aside>

### Supported transaction types

Transaction Type | Input Format | URL
---------- | ------- | -------
HTTP GET/POST | URL Encoded | http://api.ispeech.org/api/rest
HTTP GET/POST | XML | http://api.ispeech.org/api/xml
HTTP GET/POST | JSON | http://api.ispeech.org/api/json

### Request Parameters

Parameter | Supported Values
---------- | -------
output (optional) | xml, json, rest (default)