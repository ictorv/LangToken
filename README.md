# LangToken            

## Overview

**LangToken** is a Python library designed for text preprocessing and tokenization. It converts text into token IDs and provides functionality to encode and decode text, ensuring consistent mapping between words and their token representations.

This project includes a robust implementation, detailed documentation, and unit tests to validate its functionality.

## Features

- **Vocabulary Creation**: Automatically generates a token-to-ID mapping and its inverse from text.
- **Encoding**: Converts text into a list of token IDs.
- **Decoding**: Converts a list of token IDs back into readable text.
- **File Integration**: Reads text files and processes them for tokenization.
- **Handling Unknown Tokens**: Maps unknown words to a special `<|unk|>` token.
- **Special Tokens**: Includes `<|unk|>` for unknown words and `<|endoftext|>` for file-ending markers.

### Methods

| **Method**           | **Description**                                                                                                                                      | **Parameters**                                                                                                                                                                                                                     | **Returns**                          |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| `__init__()`          | Initializes the `Tokenizer` instance. Sets up the vocabulary dictionaries (`str_to_int`, `int_to_str`) and text container (`text`).                  | None                                                                                                                                                                                        | None                                 |
| `pass_file()`         | Reads a text file into the `text` attribute.                                                                                                        | `file_path` (str): Path to the text file.<br>`enc` (str): File encoding (e.g., "utf-8").                                                                                                    | None                                 |
| `fit()`               | Creates a vocabulary from the `text` attribute by preprocessing it and assigning a unique integer to each word or symbol. Adds special tokens.      | None                                                                                                                                                                                        | None                                 |
| `get_token()`         | Retrieves the vocabulary as a dictionary mapping tokens to integers.                                                                                | None                                                                                                                                                                                        | `dict`: The vocabulary dictionary.  |
| `get_token_decoder()` | Retrieves the inverse vocabulary dictionary (mapping integers to tokens).                                                                           | None                                                                                                                                                                                        | `dict`: The inverse vocabulary.     |
| `encode()`            | Converts a given text into a list of integers based on the created vocabulary. Unknown words are replaced by <\|unk\|>.                             | `text` (str): The input text to encode.                                                                                                                                                      | `list`: List of integer tokens.      |
| `decode()`            | Converts a list of integers back into the original text.                                                                                           | `ids` (list): List of integer tokens.                                                                                                                                                        | `str`: Decoded text.                 |

---
## 🚀 Quick Start

Install the library using pip:
```python
pip install LangToken
```

## Use
```python
from LangToken.tokenizer import Tokenizer

# Initialize the tokenizer
tokenizer = Tokenizer()

# Pass a file to read text (example: 'sample.txt')
tokenizer.pass_file("sample.txt", "utf-8")

# Fit the tokenizer to create a vocabulary
tokenizer.fit()

# Get the vocabulary as a dictionary
vocabulary = tokenizer.get_token()
print("Vocabulary:", vocabulary)

# Encode a new text using the vocabulary
text_to_encode = "Hello, how are you?"
encoded_text = tokenizer.encode(text_to_encode)
print("Encoded Text:", encoded_text)

# Decode the encoded text back to its original form
decoded_text = tokenizer.decode(encoded_text)
print("Decoded Text:", decoded_text)

```
#### `sample.txt`
```text
Hello, world! How are you?
```
#### Output
```example
Vocabulary: {'!': 0, ',': 1, 'Hello': 2, 'How': 3, 'are': 4, 'world': 5, 'you': 6, '<|unk|>': 7, '<|endoftext|>': 8}
Encoded Text: [2, 1, 3, 4, 6, 0]
Decoded Text: Hello, how are you?
```
## Class Diagram
<img src="image/diagram.png" alt="Diagram" width="500" />
