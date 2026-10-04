# Securing the Northeast: Magazine Automation Pipeline 🇮🇳

## Overview
This project is an end-to-end automated pipeline that scrapes, cleans, summarizes, and formats defense and strategic affairs news into a professional 45-page digital magazine titled **"Securing the Northeast: Indian Army’s Role in Stability, Peace & National Security"**. 

It transitions raw web data into a Canva-ready dataset, utilizing Offline NLP (LexRank) to fit specific high-end magazine layouts.

## Key Features
* **Geofenced Scraping:** Uses SerpApi with boolean operators to lock news queries exclusively to the 8 Northeast Indian states.
* **Offline NLP Summarization:** Uses the `sumy` library to extract exact text lengths for specific Canva layout blocks (`In Brief`, `The Story`, and `Key Fact`).
* **Deep Data Cleaning:** Automatically scrubs HTML entities, hidden web formatting, and broken unicode (Mojibake) from scraped text.
* **Canva Bulk Create Integration:** Formats data specifically for Canva's Bulk Create tool, including automatic column-splitting for text and `@Image URL` formatting for automated photo placement.
* **Automated Appendices:** Generates a formatted Source Directory from the dataset.

## Prerequisites & Installation
Ensure you have Python 3.8+ installed. Install the required libraries:
```bash
pip install pandas numpy nltk sumy
