---
title: "Filimoa/open-parse: Improved file parsing for LLM’s"
source: "https://github.com/Filimoa/open-parse?tab=readme-ov-file"
author:
  - "[[GitHub]]"
published:
created: 2025-03-15
description: "Improved file parsing for LLM’s. Contribute to Filimoa/open-parse development by creating an account on GitHub."
tags:
  - "clippings"
---
[![](https://camo.githubusercontent.com/5ebde52c5211877f7dd8b8331e19f98aa3c27628c71721f845bba75101a667bc/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f6f70656e2d70617273652d776974682d746578742d74702d6c6f676f2e77656270)](https://camo.githubusercontent.com/5ebde52c5211877f7dd8b8331e19f98aa3c27628c71721f845bba75101a667bc/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f6f70656e2d70617273652d776974682d746578742d74702d6c6f676f2e77656270)

  

**Easily chunk complex documents the same way a human would.**

Chunking documents is a challenging task that underpins any RAG system. High quality results are critical to a sucessful AI application, yet most open-source libraries are limited in their ability to handle complex documents.

Open Parse is designed to fill this gap by providing a flexible, easy-to-use library capable of visually discerning document layouts and chunking them effectively.

**How is this different from other layout parsers?**

#### ✂️ Text Splitting

Text splitting converts a file to raw text and [slices it up](https://docs.llamaindex.ai/en/stable/api_reference/node_parsers/token_text_splitter/).

- You lose the ability to easily overlay the chunk on the original pdf
- You ignore the underlying semantic structure of the file - headings, sections, bullets represent valuable information.
- No support for tables, images or markdown.

#### 🤖 ML Layout Parsers

There's some of fantastic libraries like [layout-parser](https://github.com/Layout-Parser/layout-parser).

- While they can identify various elements like text blocks, images, and tables, but they are not built to group related content effectively.
- They strictly focus on layout parsing - you will need to add another model to extract markdown from the images, parse tables, group nodes, etc.
- We've found performance to be sub-optimal on many documents while also being computationally heavy.

#### 💼 Commercial Solutions

- Typically priced at ≈ $10 / 1k pages. See [here](https://cloud.google.com/document-ai), [here](https://aws.amazon.com/textract/) and [here](https://www.reducto.ai/).
- Requires sharing your data with a vendor

## Highlights

- **🔍 Visually-Driven:** Open-Parse visually analyzes documents for superior LLM input, going beyond naive text splitting.
- **✍️ Markdown Support:** Basic markdown support for parsing headings, bold and italics.
- **📊 High-Precision Table Support:** Extract tables into clean Markdown formats with accuracy that surpasses traditional tools.

*Examples* The following examples were parsed with unitable.  

  
[![](https://camo.githubusercontent.com/bda997fc8c9cb381726cd755dd984631519a3582c3aebc0c952701e47ee70be4/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f756e697461626c652d70617273696e672d73616d706c652e77656270)](https://camo.githubusercontent.com/bda997fc8c9cb381726cd755dd984631519a3582c3aebc0c952701e47ee70be4/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f756e697461626c652d70617273696e672d73616d706c652e77656270)
- **🛠️ Extensible:** Easily implement your own post-processing steps.
- **💡Intuitive:** Great editor support. Completion everywhere. Less time debugging.
- **🎯 Easy:** Designed to be easy to use and learn. Less time reading docs.

  

[![](https://camo.githubusercontent.com/c5810478cbb8cfc269ae2c25cf664c008aaa9ed86ceadc22f5ffd9957890141e/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f6d61726b65642d75702d646f632d322e77656270)](https://camo.githubusercontent.com/c5810478cbb8cfc269ae2c25cf664c008aaa9ed86ceadc22f5ffd9957890141e/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f6d61726b65642d75702d646f632d322e77656270)

## Example

#### Basic Example

```
import openparse

basic_doc_path = "./sample-docs/mobile-home-manual.pdf"
parser = openparse.DocumentParser()
parsed_basic_doc = parser.parse(basic_doc_path)

for node in parsed_basic_doc.nodes:
    print(node)
```

**📓 Try the sample notebook** [here](https://colab.research.google.com/drive/1Z5B5gsnmhFKEFL-5yYIcoox7-jQao8Ep?usp=sharing)

#### Semantic Processing Example

Chunking documents is fundamentally about grouping similar semantic nodes together. By embedding the text of each node, we can then cluster them together based on their similarity.

```
from openparse import processing, DocumentParser

semantic_pipeline = processing.SemanticIngestionPipeline(
    openai_api_key=OPEN_AI_KEY,
    model="text-embedding-3-large",
    min_tokens=64,
    max_tokens=1024,
)
parser = DocumentParser(
    processing_pipeline=semantic_pipeline,
)
parsed_content = parser.parse(basic_doc_path)
```

**📓 Sample notebook** [here](https://github.com/Filimoa/open-parse/blob/main/src/cookbooks/semantic_processing.ipynb)

#### Serializing Results

Uses pydantic under the hood so you can serialize results with

```
parsed_content.dict()

# or to convert to a valid json dict
parsed_content.json()
```

## Requirements

Python 3.8+

**Dealing with PDF's:**

- [pdfminer.six](https://github.com/pdfminer/pdfminer.six) Fully open source.

**Extracting Tables:**

- [PyMuPDF](https://github.com/pymupdf/PyMuPDF) has some table detection functionality. Please see their [license](https://mupdf.com/licensing/index.html#commercial).
- [Table Transformer](https://huggingface.co/microsoft/table-transformer-detection) is a deep learning approach.
- [unitable](https://github.com/poloclub/unitable) is another transformers based approach with **state-of-the-art** performance.

## Installation

#### 1\. Core Library

```
pip install openparse
```

**Enabling OCR Support**:

PyMuPDF will already contain all the logic to support OCR functions. But it additionally does need Tesseract’s language support data, so installation of Tesseract-OCR is still required.

The language support folder location must be communicated either via storing it in the environment variable "TESSDATA\_PREFIX", or as a parameter in the applicable functions.

So for a working OCR functionality, make sure to complete this checklist:

1. Install Tesseract.
2. Locate Tesseract’s language support folder. Typically you will find it here:

- Windows: `C:/Program Files/Tesseract-OCR/tessdata`
- Unix systems: `/usr/share/tesseract-ocr/5/tessdata`
- macOS (installed via Homebrew):

- Standard installation: `/opt/homebrew/share/tessdata`
- Version-specific installation: `/opt/homebrew/Cellar/tesseract/<version>/share/tessdata/`
3. Set the environment variable TESSDATA\_PREFIX

- Windows: `setx TESSDATA_PREFIX "C:/Program Files/Tesseract-OCR/tessdata"`
- Unix systems: `declare -x TESSDATA_PREFIX=/usr/share/tesseract-ocr/5/tessdata`
- macOS (installed via Homebrew): `export TESSDATA_PREFIX=$(brew --prefix tesseract)/share/tessdata`

**Note:** *On Windows systems, this must happen outside Python – before starting your script. Just manipulating os.environ will not work!*

#### 2\. ML Table Detection (Optional)

This repository provides an optional feature to parse content from tables using a variety of deep learning models.

```
pip install "openparse[ml]"
```

Then download the model weights with

```
openparse-download
```

You can run the parsing with the following.

```
parser = openparse.DocumentParser(
        table_args={
            "parsing_algorithm": "unitable",
            "min_table_confidence": 0.8,
        },
)
parsed_nodes = parser.parse(pdf_path)
```

Note we currently use [table-transformers](https://github.com/microsoft/table-transformer) for all table detection and we find its performance to be subpar. This negatively affects the downstream results of unitable. If you're aware of a better model please open an Issue - the unitable team mentioned they might add this soon too.

## Cookbooks

[https://github.com/Filimoa/open-parse/tree/main/src/cookbooks](https://github.com/Filimoa/open-parse/tree/main/src/cookbooks)

## Documentation

[https://filimoa.github.io/open-parse/](https://filimoa.github.io/open-parse/)

## Sponsors

[![](https://camo.githubusercontent.com/6de3874f2a0ff127a017e55b45a6cfb30162baca9dbd2cc8fba3c0908aa24c6c/68747470733a2f2f7365726765792d66696c696d6f6e6f762e6e7963332e6469676974616c6f6365616e7370616365732e636f6d2f6f70656e2d70617273652f6d61726b6574696e672f74687265652d7369676d612d776964652e706e67)](https://www.data.threesigma.ai/filings-ai "Three Sigma: AI for insurance filings.")

Does your use case need something special? Reach [out](https://www.linkedin.com/in/sergey-osu/).