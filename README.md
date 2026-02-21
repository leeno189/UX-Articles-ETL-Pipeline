# Automated ETL Pipeline & Web Scraper for UX Research

## Overview
This project features a complete Extract, Transform, Load (ETL) data pipeline built in Python. The system is designed to programmatically navigate the Nielsen Norman Group (NN/g) publication directory, scrape detailed article metadata across multiple pages, clean the unstructured text, and load it into a relational database for querying and analysis.

## Pipeline Architecture

### 1. Extraction (Web Scraping)
* **Library:** `BeautifulSoup4` & `requests`
* **Process:** Engineered a robust scraping script with built-in timeouts and request delays (`time.sleep()`) to respect server load. The scraper handles pagination and dynamically navigates to individual article URLs to extract deep metadata, including:
  * Title & Description
  * Publication Date & Author
  * Full Article Outline
  * Related Courses & Topics

### 2. Transformation (Data Cleaning)
* **Library:** `Pandas`
* **Process:** Converted the nested JSON/Dictionary responses into structured DataFrames. Conducted rigorous data cleaning, which included:
  * Dropping duplicate records and handling `NaN` values.
  * Normalizing text structures by stripping errant HTML artifacts (e.g., `\xa0` non-breaking spaces).
  * Formatting string representations of arrays to ensure clean database insertion.

### 3. Loading (Database Storage)
* **Library:** `SQLite3`
* **Process:** Connected a local SQLite database instance and automatically mapped the cleaned Pandas DataFrame into a persistent SQL table (`articles.db`), enabling fast querying and future analytical scalability.

## Tech Stack
* **Language:** Python
* **Libraries:** BeautifulSoup, Requests, Pandas, SQLite3
* **Concepts:** ETL, Web Scraping, DOM Parsing, Data Normalization
