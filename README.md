#  WordPiece Tokenization

##  Project Description

This project implements the WordPiece Tokenization algorithm from scratch using Python.

WordPiece is a subword tokenization algorithm commonly used with BERT-family models.

##  Features

- Reads words from a raw text file
- Calculates word frequencies
- Performs initial character-level splitting
- Creates the initial vocabulary
- Calculates token frequencies
- Calculates pair frequencies
- Calculates WordPiece scores
- Selects the highest-scoring pair
- Merges tokens
- Repeats the training process
- Performs longest-match tokenization
- Handles unknown words using `[UNK]`
- Converts tokens into Token IDs

## Technologies Used

- Python
- Collections Counter

##  Project Structure

```text
WordPiece_Tokenization/
│
├── wordpiece.py
├── rawdata.txt
└── README.md
```

##  How It Works

The WordPiece tokenization process follows these steps:

```text
Raw Data
   ↓
Word Frequencies
   ↓
Initial WordPiece Splits
   ↓
Initial Vocabulary
   ↓
Token Frequency
   ↓
Pair Frequency
   ↓
WordPiece Score
   ↓
Best Pair Selection
   ↓
Merge Tokens
   ↓
Final Vocabulary
   ↓
Longest Match Tokenization
   ↓
Token IDs
```
##  Initial WordPiece Splitting

Each word is initially split into individual characters.

The first character remains unchanged, while the following characters are prefixed with `##`.

Example:

```text
hug → ['h', '##u', '##g']
hugs → ['h', '##u', '##g', '##s']
pug → ['p', '##u', '##g']
mugs → ['m', '##u', '##g', '##s']
```

The `##` indicates that the token is a continuation of the word.

##  WordPiece Score

WordPiece selects the best pair of tokens to merge using a score.

The score is calculated using:

```text
Score = Pair Frequency / (Frequency of First Token × Frequency of Second Token)
```

The pair with the highest score is selected for merging.

Example:

```text
Best Pair → ('h', '##u')
New Token → hu
```

This merging process is repeated for multiple steps to build the final vocabulary.

##  Training & Merging

The WordPiece training process selects the best token pair based on the highest score.

The selected pair is merged to create a new token.

Example:

```text
Merge 1:
Best Pair → ('h', '##u')
New Token → hu

Merge 2:
Best Pair → ('p', '##u')
New Token → pu

Merge 3:
Best Pair → ('m', '##u')
New Token → mu
```

This process is repeated for multiple merges to build the final vocabulary.

##  Final Tokenization & Token IDs

After training, the final vocabulary is used to tokenize a new word using the longest-match method.

Example:

```text
Input Word:
mugs

Tokens:
['mu', '##g', '##s']

Token IDs:
[8, 0, 1]
```

The token IDs represent the numerical IDs assigned to each token in the vocabulary.

## How to Run

### 1. Clone or download the project

### 2. Open the project folder in VS Code

### 3. Install the required library

```bash
pip install transformers
```

### 4. Run the program

```bash
python wordpiece.py
```

### 5. Enter the required input in `rawdata.txt` and run the program.

##  Objective

The main objective of this project is to understand and implement the WordPiece tokenization algorithm from scratch.

It demonstrates:

- Initial word splitting
- Token and pair frequency calculation
- WordPiece score calculation
- Token merging
- Vocabulary creation
- Longest-match tokenization
- Token ID generation
