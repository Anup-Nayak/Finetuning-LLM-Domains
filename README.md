# Corpus Q&A Tool

## Project Overview

This project involves the development of a Corpus Q&A tool designed to query large corpora and extract relevant information using advanced data structures and algorithms. The tool is particularly aimed at finding answers within large text corpora, such as "The Collected Works of Mahatma Gandhi" and selected works of Maharishi Ramana, by leveraging search and ranking techniques.

## Features

1. **Search Results Ranking**: Implemented a scoring algorithm to rank paragraphs based on their relevance to the input query.
2. **Paragraph Scoring**: Calculated paragraph scores by considering the frequency and importance of query words within the corpus.
3. **Querying Large Language Models (LLMs)**: Utilized LLMs like ChatGPT to process and answer queries using the top-ranked paragraphs.

## Getting Started

### Prerequisites

- Python 3.x
- Necessary Python libraries (`requests`, `json`, etc.)
- ChatGPT API key (if using the provided `query_llm` function)

### Files

- `qna_tool.h`: Header file containing the declaration of the `QNA_tool` class.
- `qna_tool.cpp`: Implementation file where the functions of the `QNA_tool` class are defined.
- `main.cpp`: Entry point of the program where the Q&A tool is utilized.
- `Makefile`: Script to compile and run the program.

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo/corpus-qa-tool.git
    cd corpus-qa-tool
    ```

2. Compile the program using the provided Makefile:
    ```bash
    make
    ```

3. Run the program:
    ```bash
    ./corpus_qa_tool
    ```

## Usage

1. **Loading the Corpus**: Ensure the text files of the corpora are placed in the correct directory. The tool will load these files for processing.
   
2. **Running Queries**: Input queries into the tool, which will search the corpus, rank the paragraphs, and use the LLM to provide answers.

3. **Customizing Search and Scoring**: Modify the search and scoring algorithms in `qna_tool.cpp` as needed to improve the accuracy and relevance of the results.


## Run

﻿to run the code:
open terminal
navigate to the directory in which qna_tool.cpp is located
type make and press enter
type ./qna_tool and press enter
the tool will take some time to initialize

type a number from 0-14 if you want to ask a question from the following list 
{
    "What were the views of Mahatma Gandhi on the 9 of India?",
    "Who was Mahatma Gandhi?",
    "What were Gandhi's views on the manner of how one should eat?",
    "What is the purpose of life?",
    "What was the effect of tea and coffee according to Mahatma?",
    "What role did Mahatma Gandhi play in the Indian independence movement?",
    "What were the key principles of non-violence advocated by Mahatma Gandhi?",
    "How did Mahatma Gandhi lead and inspire people during various protests and movements?",
    "What impact did Mahatma Gandhi have on social reforms, including caste discrimination and untouchability?",
    "How did Mahatma Gandhi contribute to international diplomacy and relations during India's struggle for independence?",
    "How did Mahatma Gandhi's religious and spiritual beliefs influence his actions and decisions?",
    "What is Mahatma Gandhi's legacy, and how is he remembered in contemporary times?",
    "Can you elaborate on the concept of civil disobedience as advocated by Mahatma Gandhi?",
    "What were the circumstances surrounding Mahatma Gandhi's assassination, and how did it impact the nation?",
    "Who was Mahatma Gandhi's wife?"
}
to stop type a negative number
you can edit testcases by going to tester.cpp

the last query with answer will be stored in answer.txt


## Function Documentation

### QNA_tool

- **Constructor**: Initializes the QNA tool and loads the corpus.
    ```cpp
    QNA_tool();
    ```

- **search_query**: Searches the corpus for relevant paragraphs and ranks them.
    ```cpp
    std::vector<Paragraph> search_query(std::string query);
    ```

- **score_paragraph**: Calculates the score of a paragraph based on the presence and frequency of query words.
    ```cpp
    double score_paragraph(Paragraph p, std::vector<std::string> query_words);
    ```

- **query_llm**: Sends the top-ranked paragraphs to the LLM and returns the response.
    ```cpp
    std::string query_llm(std::string query, std::vector<Paragraph> top_paragraphs);
    ```

## Example

```cpp
#include "qna_tool.h"

int main() {
    QNA_tool qna_tool;
    std::string query = "What were Gandhi's views on the Partition of India?";
    std::vector<Paragraph> top_paragraphs = qna_tool.search_query(query);
    std::string answer = qna_tool.query_llm(query, top_paragraphs);
    std::cout << "Answer: " << answer << std::endl;
    return 0;
}

