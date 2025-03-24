---
title: "Obsidian Reader - LlamaIndex"
source: "https://docs.llamaindex.ai/en/stable/examples/data_connectors/ObsidianReaderDemo/"
author:
published:
created: 2025-03-15
description:
tags:
  - "clippings"
---
## Obsidian Reader¶

If you're opening this Notebook on colab, you will probably need to install LlamaIndex 🦙.

In \[ \]:

```ipynb
%pip install llama-index-readers-obsidian
```

%pip install llama-index-readers-obsidian

In \[ \]:

```ipynb
!pip install llama-index
```

!pip install llama-index

In \[ \]:

```ipynb
%env OPENAI_API_KEY=sk-************
```

%env OPENAI\_API\_KEY=sk-\*\*\*\*\*\*\*\*\*\*\*\*

In \[ \]:

```ipynb
import logging
import sys

logging.basicConfig(stream=sys.stdout, level=logging.INFO)
logging.getLogger().addHandler(logging.StreamHandler(stream=sys.stdout))
```

import logging import sys logging.basicConfig(stream=sys.stdout, level=logging.INFO) logging.getLogger().addHandler(logging.StreamHandler(stream=sys.stdout))

In \[ \]:

```ipynb
from llama_index.readers.obsidian import ObsidianReader
from llama_index.core import VectorStoreIndex
```

from llama\_index.readers.obsidian import ObsidianReader from llama\_index.core import VectorStoreIndex

In \[ \]:

```ipynb
documents = ObsidianReader(
    "/Users/hursh/vault"
).load_data()  # Returns list of documents
```

documents = ObsidianReader( "/Users/hursh/vault" ).load\_data() # Returns list of documents

In \[ \]:

```ipynb
index = VectorStoreIndex.from_documents(
    documents
)  # Initialize index with documents
```

index = VectorStoreIndex.from\_documents( documents ) # Initialize index with documents

In \[ \]:

```ipynb
# set Logging to DEBUG for more detailed outputs
query_engine = index.as_query_engine()
res = query_engine.query("What is the meaning of life?")
```

\# set Logging to DEBUG for more detailed outputs query\_engine = index.as\_query\_engine() res = query\_engine.query("What is the meaning of life?")

```ipynb
> [query] Total LLM token usage: 920 tokens
> [query] Total embedding token usage: 7 tokens
```

In \[ \]:

```ipynb
res.response
```

res.response

Out\[ \]:

```ipynb
'\nThe meaning of life is subjective and can vary from person to person. It is ultimately up to each individual to decide what they believe is the purpose and value of life. Some may find meaning in their faith, while others may find it in their relationships, work, or hobbies. Ultimately, it is up to each individual to decide what brings them joy and fulfillment and to pursue that path.'
```