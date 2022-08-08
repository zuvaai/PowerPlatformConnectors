# Zuva DocAI connector

The Zuva DocAI connector enables developers to implement contracts AI features into their applications.

## Prerequisites

You will need a Zuva account and a DocAI token for the United States region.

See the [DocAI documentation](https://zuva.ai/documentation/) for information about creating an account and token.

## Supported Operations

### File Management

Upload your file for analysis. Note that files automatically expire 48 hours after being uploaded.

- `Submit File`: Upload a file to Zuva's servers
- `Delete File`: Remove a file from Zuva's servers

### Extraction

Extract specific information from your document, such as its Title or particular legal clauses.

- `Create Field Extraction Request`: Initiate asynchronous extraction of fields from a document
- `Get Field Extraction Request Status`: Check the status of an existing extraction request.
- `Get Field Extraction Request Text Results`: Get text results from a completed extraction request.

### Language Classification

Discover the language of your document.

- `Create Language Classification Request`: Initiate asynchronous classification of the document language
- `Get Language Classification Request Status`: Get status and results of language classification

### Document Classification

Categorize your document: is it a contract and, if so, what type of contract (real estate agreement, employment agreement etc.)?

- `Create Document Classification Request`: Initiate asynchronous classification of the document type
- `Get Document Classification Request Status`: Get status and results of document classification

### Optical Character Recognition (OCR)

Obtain the text of your documents, regardless of their original file type (pdf, docx, png ...), as well
as images of the document.

- `Create OCR Request`: Initiate synchronous OCR processing of a file
- `Get OCR Request Status`: Check whether OCR processing of a file is complete
- `Get OCR Results Text`: Retrieve the text from a processed file
- `Get OCR Results Images`: Retrieve the images from a processed file
- `Get File Layouts`: Retrieve the layouts from a processed file

## Differences between the connector and the DocAI API

This connector makes use of a C# script to modify both requests and responses. As a result, the
Power Automate connector functionality does not correspond one-to-one with the documentation for
the underlying API. In particular, the connector:
1. Exposes an extra `is_finished` boolean, which can be used to tell if the request is either complete OR failed
2. All requests operate on single files, rather than batches of multiple files. If you need to process many files,
use an "Apply to each" block in Power Automate, or by set up a trigger such that a separate flow applies to each individual file.

## Known issues and limitations

The connector does not support any of Zuva's endpoints related to training custom fields.