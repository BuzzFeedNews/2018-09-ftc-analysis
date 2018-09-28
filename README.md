# FTC complaints about 'immigration services'-related complaints — 2006 to 2018

This repository contains data, analytic code, and findings that support portions of the BuzzFeed News article, “[She Paid A Lawyer Thousands Of Dollars To Apply For A Green Card. Then she Got A Deportation Order Instead.](https://www.buzzfeednews.com/article/lamvo/undocumented-immigrants-10-year-green-card),” published September 28, 2018. Please read that article, which contains important context and details, before proceeding.

## Data

This analysis uses three spreadsheets containing complaints filed to the Federal Trade Commission (FTC) in relation to 'immigration services'. The spreadsheets come from two sources:

- The FTC provided redacted records from July of 2015 through May of 2018 in response to a BuzzFeed News FOIA request. The two files provided are the following:
  - `consumer_compls_redacted_2018.xlsx`: Raw data of the complaints filed between Jan. 1, 2018 through May 7, 2018
  - `consumer_compls_redacted_2015_2017.xls`: Raw data of the complaints filed between July 1, 2015 through Dec. 31 7, 2017

- Matthew Blaisdell of the [American Immigration Lawyers Association](https://www.aila.org/) (AILA)  provided a spreadsheet of FTC complaints beginning in 2006 through 2015 (the spreadsheet contained one entry from the year of 2000)
  - `consumer_compls_redacted_2006_2015.xlsx`: Raw data of the complaints filed between 2006 through July 15, 2015 (as well as two pivot tables, one tallying up complaints by month and another by geolocation)

Each of the spreadsheets contain, among others, the following columns relevant to the analysis:

- `  Created Date` — The date the complaint was received.
- ` Reference Number` — A unique reference number affiliated with each complaint.
- `Complaint Info Comments` — Prose affiliated with the complaint (redacted, however, in `consumer_compls_redacted_2015_2017.xls`)

## Methodology

The notebook [`2018-09-ftc-analysis.ipynb`](notebooks/2018-09-ftc-analysis.ipynb) performs two analyses:

##### Part 1: Find a yearly average of complaints

- Merge the three spreadsheets received from FTC and AILA
- Calculate monthly count of complaints for each spreadsheet
- Calculate a yearly tally of complaints based on these counts

##### Part 2: Find words commonly used in the complaints

- Filter data down to rows that contain prose in the `Complaint Info Comments` column. (Some are redacted.)
- Create a dataframe containing one row per word in each complaint. Each row contains a complaint ID, the word, and the word's [lemmatization](https://en.wikipedia.org/wiki/Lemmatisation).
- For each lemmatized word, count the total number of times it appeared, how many distinct complaints it appeared in, and the lemma's different variations in the complaints.


## Outputs

The results of "Part 2" above are saved as [`output/word_counts.csv`](output/word_counts.csv).

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

- Python 3
- The Python libraries libraries specified in [`requirements.txt`](requirements.txt)

Additionally, before running the analysis, you'll need to install `spaCy`'s English language model. You can do so by running the following command in your terminal: `python -m spacy download en`. (The analysis uses [`spaCy`](https://spacy.io/), a natural language processing library for Python, to tokenize and lemmatize the text of the complaints.)

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact Lam Thuy Vo at lam.vo@buzzfeed.com. Looking for more from BuzzFeed News? [Click here for a list of our open-sourced projects, data, and code.](https://github.com/BuzzFeedNews/everything).
