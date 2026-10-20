# Amazon Product Reviews | Sentiment Analysis

A natural language processing (NLP) project using Python, spaCy, and spaCyTextBlob to analyse customer sentiment in Amazon product reviews.

The project focuses on text preprocessing, sentiment classification, semantic similarity, and evaluating how well predicted sentiments align with customer ratings.

## Project Overview

The objective of this project was to develop a sentiment analysis system capable of identifying whether Amazon product reviews express positive, negative, or neutral opinions.

Using a dataset of over 28,000 customer reviews, the project explores how NLP techniques can extract meaningful insights from unstructured customer feedback.

The analysis addresses several questions:

- Can customer reviews be automatically classified as positive, negative, or neutral?
- How closely do sentiment predictions align with customer star ratings?
- What challenges arise when analysing short or context-dependent reviews?
- Can two reviews be semantically similar while expressing different opinions?

## Technologies Used

- **Python** – Data processing and analysis
- **Pandas** – Data cleaning, sampling, and manipulation
- **spaCy** – Natural language processing and text preprocessing
- **spaCyTextBlob** – Sentiment polarity and subjectivity analysis
- **TextBlob** – Lexicon-based sentiment analysis
- **Jupyter Notebook** – Development, experimentation, and documentation

## Dataset

The project uses the **Datafiniti Amazon Consumer Reviews of Amazon Products (May 2019)** dataset, sourced from Kaggle.

The dataset contains:

- **28,332 customer reviews**
- **24 features**
- Product names and brands
- Customer review text and titles
- Customer star ratings
- Additional product and review information

The `reviews.text` column was selected as the primary input for sentiment analysis, while `reviews.rating` was used to compare sentiment predictions against customer ratings.

## Data Preprocessing

Before performing sentiment analysis, the review text was cleaned and standardised using spaCy.

The preprocessing steps included:

1. Selecting the relevant review text column.
2. Checking for and removing missing review values.
3. Converting review text to lowercase.
4. Removing unnecessary whitespace.
5. Tokenising the text using spaCy.
6. Removing stop words and punctuation.
7. Applying lemmatisation to reduce words to their base forms.

No missing values were identified in the review text column, so all 28,332 reviews were retained.

## Sentiment Analysis

A sentiment analysis function was developed using spaCy and spaCyTextBlob.

The function processes customer reviews and returns three values:

- **Sentiment:** Positive, Negative, or Neutral
- **Polarity:** A numerical score indicating sentiment, ranging from -1 to +1
- **Subjectivity:** A score indicating how subjective or opinion-based the text is

The sentiment categories were determined using polarity thresholds:

| Polarity Score | Classification |
|---|---|
| Greater than 0.05 | Positive |
| Less than -0.05 | Negative |
| Between -0.05 and 0.05, inclusive | Neutral |

The function was tested using manually written examples and reviews selected from the dataset.

## Model Evaluation

To evaluate the approach, a reproducible random sample of **1,000 reviews** was selected from the dataset.

### Sentiment Distribution

| Predicted Sentiment | Number of Reviews |
|---|---:|
| Positive | 814 |
| Neutral | 138 |
| Negative | 48 |
| **Total** | **1,000** |

### Comparison with Customer Ratings

Customer ratings were converted into sentiment categories:

- 4–5 stars: Positive
- 3 stars: Neutral
- 1–2 stars: Negative

The predicted sentiments were then compared against these rating-based categories.

**Result: 77.3% agreement between predicted sentiment and rating-based sentiment.**

This is an approximate agreement measure rather than a definitive accuracy score, as star ratings do not always perfectly represent the sentiment expressed in written reviews.

## Semantic Similarity Analysis

The project also explored semantic similarity using spaCy's medium-sized English language model (`en_core_web_md`).

Two customer reviews were compared using the `.similarity()` method.

**Similarity score: 0.9519**

Although the reviews expressed different opinions, they received a high similarity score.

This demonstrated that semantic similarity and sentiment classification measure different aspects of language: reviews may share similar topics or vocabulary while expressing different customer experiences.

## Key Findings

**1. Positive sentiment was the most frequently predicted category.**

Of the 1,000 reviews analysed, 814 were classified as positive, indicating that positive language was dominant in the sample.

**2. Sentiment predictions generally aligned with customer ratings.**

The analysis achieved 77.3% agreement between predicted sentiment categories and categories derived from customer star ratings.

**3. Context and negation affected sentiment classification.**

Certain reviews were incorrectly classified because the model struggled with context-dependent language, short reviews, and expressions involving negation.

**4. Text preprocessing can influence sentiment interpretation.**

Removing stop words may also remove important words such as "not", potentially changing the meaning of a review.

**5. Semantic similarity does not necessarily indicate similar sentiment.**

Two reviews can discuss similar products or topics while expressing different opinions.

## Strengths and Limitations

### Strengths

- Straightforward implementation using established NLP libraries
- No custom model training required
- Interpretable sentiment polarity and subjectivity scores
- Ability to process unstructured customer feedback
- Support for semantic similarity comparisons

### Limitations

- Difficulty interpreting sarcasm and complex expressions
- Potential loss of important context during stop-word removal
- Limited ability to interpret mixed sentiments
- Short reviews may not contain sufficient information for reliable classification
- Customer ratings are only an approximate reference for evaluating text sentiment
- Evaluation was performed on a sample of 1,000 reviews rather than the entire dataset

## How to Run the Project

1. Clone or download this repository.
2. Ensure Python 3 and Jupyter Notebook are installed.
3. Install the required libraries:

   ```bash
   python3 -m pip install pandas spacy spacytextblob jupyter
   ```

4. Download the medium-sized English spaCy model:

   ```bash
   python3 -m spacy download en_core_web_md
   ```

5. Place the dataset CSV file in the same directory as the notebook.
6. Open `sentiment_analysis.ipynb` in Jupyter Notebook.
7. Run the cells in sequence to reproduce the analysis.

## Project Report

A detailed PDF report is included in this repository, documenting the preprocessing steps, sentiment analysis implementation, evaluation results, semantic similarity analysis, and final conclusions.

## Skills Demonstrated

- Natural Language Processing (NLP)
- Text cleaning and preprocessing
- Tokenisation and lemmatisation
- Sentiment classification
- Polarity and subjectivity analysis
- Semantic similarity
- Data manipulation using Pandas
- Model evaluation and interpretation
- Analytical problem-solving
- Technical reporting

## Future Improvements

Potential improvements include:

- Preserving negation words during preprocessing to improve sentiment interpretation.
- Evaluating sentiment predictions using manually labelled review data.
- Calculating precision, recall, and F1-scores for each sentiment category.
- Testing transformer-based sentiment classification models.
- Comparing lexicon-based and machine learning approaches.
- Creating visualisations to explore sentiment distribution and product ratings.

## Author

Ally Remas
