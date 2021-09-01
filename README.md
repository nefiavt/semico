# semico
Powerful Word generation service

Demo link https://semico.azurewebsites.net/

## Tags
The template is a document (docx) created in Microsoft Word or other software.

Semico supports following features:
* Simple tags
* Loops
* Conditions
* Table rows
* Table columns
* Bullets
* Numbering
* Images
* Convert to PDF

### Simple tags

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|Hi {name}| ``` {"name": "John Doe" }```|Hi John Doe|

### Loops

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{%list} {item1} {item2} {/list}| ```{"list": [{"item1": "aculis"},{"item1": "faucibus"},{"item1": "sit"}]}```| aculis faucibus sit|

### Conditions

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{%if template == "Document"} YES {/if}| ```{"template": "Document"}```| YES|


### Table rows

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{tr%list} {item1} {tr/list}| ```{"list": [{"item1": "aculis"},{"item1": "faucibus"},{"item1": "sit"}]}```|  |


### Table columns

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{tc%list} {item1} {tc/list}| ```{"list": [{"item1": "aculis"},{"item1": "faucibus"},{"item1": "sit"}]}```|  |

### Bullets

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{bl%list} {item1} {bl/list}| ```{"list": [{"item1": "aculis"},{"item1": "faucibus"},{"item1": "sit"}]}```| <ul> <li>aculis </li>  <li>faucibus </li>  <li>sit </li> </ul>|

### Numbering

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{nl%list} {item1} {nl/list}| ```{"list": [{"item1": "aculis"},{"item1": "faucibus"},{"item1": "sit"}]}```| <ol> <li>aculis </li>  <li>faucibus </li>  <li>sit </li> </ol>|

### Images

|Template (docx)|Data (json)|Document (docx)|
|---------------|-----------|---------------|
|{smile}| ```{"smile": "image:iVBORw0KG..."```| <img src="https://semico.azurewebsites.net/img/smile.png" />  |

## Testing
You can use our API to access Semico contents.

When integrating and testing our API, please use the following URL:

https://nefiavt.azure-api.net

### Authentication

Semico uses subscription keys to enable access to the API content and perform requests.

You can register a new Semico subscription key by [contacting](https://semico.azurewebsites.net/Contact) us

Semico expects for the subscription key to be included in all API requests to the server in the header of the request that looks like the following:

`subscription-key: 23117b5e1a13494cbaf908ca9ac8d8b0`

> Make sure to replace 23117b5e1a13494cbaf908ca9ac8d8b0 with your subscription key.

### Generate Document

This endpoint is used to generate document.

### HTTP Request

`POST https://nefiavt.azure-api.net/api/v1/Semico/GenerateDocument`

#### Header Parameters

| Parameter | Mandatory | Description |
|-----------|-----------|-------------|
|subscription-key|YES|	Enables access to the API|

#### Body Parameters

| Parameter | Mandatory | Description | Example|
|-----------|-----------|-------------|--------|
|template|YES|	A base64 representation of a Word document (docx)|UEsDBBQABgAIA....|
|data|YES|	A base64 representation of a JSON document|ew0KICAgICJ0Z....|
|options| NO | Additional options| |

##### Options
```json
 "options": {
        "convertToPdf": true,
        "pdfOptions": {
            "additionalMetadata": "More metadata",
            "author": "Nefia",
            "producer": "Semico",
            "subject": "Semico client",
            "title": "PDF generation",
            "application": "Semico Web"
        }
    }

```

### Postman

Here’s a collection of sample queries in Postman that’ll help you get up to speed with our API faster.

[Postman collection](https://semico.azurewebsites.net/postman/Semico.postman_collection.json) 
