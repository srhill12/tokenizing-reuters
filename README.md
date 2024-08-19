# Reuters Corpus Text Analysis

This project focuses on extracting, processing, and analyzing textual data from the Reuters corpus using the Natural Language Toolkit (NLTK). The project specifically targets the 'income' category of the Reuters dataset, providing methods to retrieve, tokenize, and store text data for further analysis.

## Project Structure

- **Main Script**: The script imports the necessary libraries, retrieves stories from the 'income' category in the Reuters corpus, and processes them by tokenizing the text into sentences and words.
- **Text Processing Techniques**:
  - **Sentence Tokenization**: Splitting raw text into individual sentences.
  - **Word Tokenization**: Breaking down sentences into individual words.
  - **Data Storage**: Storing raw stories and their tokenized forms in a pandas DataFrame for easy manipulation and analysis.

## Requirements

- **Python 3.x**
- **NLTK**: The Natural Language Toolkit is required for text processing. Install it using pip:
  ```bash
  pip install nltk
  ```
- **Pandas**: A data analysis library to store and manipulate the text data. Install it using pip:
  ```bash
  pip install pandas
  ```

## Setup

Before running the script, ensure that you have the required NLTK data packages. The script will download them if they are not already installed:

```python
import nltk
nltk.download('reuters')
nltk.download('punkt')
```

## Usage

1. **Search Through Categories**:
   - The script begins by printing all available categories in the Reuters corpus.
   - Example:
     ```python
     print(reuters.categories())
     ```

2. **Retrieve and Process Stories**:
   - **Retrieve Stories**: Extract all file IDs associated with the 'income' category and retrieve the corresponding raw text articles.
   - **Sentence Tokenization**: Break down each article into sentences.
   - **Word Tokenization**: Tokenize each sentence into individual words.
   - Example:
     ```python
     income_ids = reuters.fileids(categories='income')
     raw_stories = [reuters.raw(id) for id in income_ids]
     sentence_tokenized = [sent_tokenize(i) for i in raw_stories]
     word_tokenized = []
     for story in sentence_tokenized:
         words = []
         for sentence in story:
             words = words + word_tokenize(sentence)
         word_tokenized.append(words)
     ```

3. **Store Data in a DataFrame**:
   - The processed data, including raw stories, sentence-tokenized stories, and word-tokenized stories, are stored in a pandas DataFrame for easy access and further analysis.
   - Example:
     ```python
     reuters_income = pd.DataFrame({'raw_stories': raw_stories,
                                    'sentence_tokenized': sentence_tokenized,
                                    'word_tokenized': word_tokenized})
     reuters_income.index = ids  # Use story IDs as index
     reuters_income.head()
     ```

## Example Output

The resulting DataFrame will contain columns for the raw stories, tokenized sentences, and tokenized words, indexed by the story IDs. Here's an example of what the DataFrame might look like:

| raw_stories                                           | sentence_tokenized                                      | word_tokenized                                      |
|-------------------------------------------------------|---------------------------------------------------------|-----------------------------------------------------|
| YUGOSLAV ECONOMY WORSENED IN 1986, BANK DATA S...      | [YUGOSLAV ECONOMY WORSENED IN 1986, BANK DATA ...       | [YUGOSLAV, ECONOMY, WORSENED, IN, 1986, ,, BAN...   |
| UK AVERAGE EARNINGS ROSE 6.5 PCT IN YEAR TO AP...     | [UK AVERAGE EARNINGS ROSE 6.5 PCT IN YEAR TO A...       | [UK, AVERAGE, EARNINGS, ROSE, 6.5, PCT, IN, YE...   |
| U.K. EARNINGS UP UNDERLYING 7.75 PCT IN APRIL...      | [U.K. EARNINGS UP UNDERLYING 7.75 PCT IN APRIL...       | [U.K., EARNINGS, UP, UNDERLYING, 7.75, PCT, IN...   |
| U.S. PERSONAL INCOME ROSE 0.2 PCT IN MAY, SPEN...     | [U.S., PERSONAL INCOME ROSE 0.2 PCT IN MAY, SP...       | [U.S, ., PERSONAL, INCOME, ROSE, 0.2, PCT, IN...   |
| U.S. PERSONAL INCOME ROSE 0.2 PCT IN MAY\n U....      | [U.S., PERSONAL INCOME ROSE 0.2 PCT IN MAY\n ...        | [U.S, ., PERSONAL, INCOME, ROSE, 0.2, PCT, IN...   |

## Conclusion

This project demonstrates how to work with the Reuters corpus using NLTK in Python, focusing on text tokenization and data preparation. The resulting DataFrame is well-structured and ready for further analysis, such as text mining, sentiment analysis, or machine learning tasks.
