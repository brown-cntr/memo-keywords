# Keyword extraction to compare state bills with OMB memo 2024

This repository extracts certain keywords from state bills related regulation of artificial intelligence or automated decision making. 

The keyword categories are relevant to certain sections of the OMB's memo released on March 28, 2024.

The aim is to have some preliminary comparison of certain sections / criteria from the OMB memo and the current legislation landscape at the state level.

## Requirements

This requires `python>=3.10` and `pandoc`.

To install the required packages, do `pip install -r requirments.txt`.

Also, an OpenAI API key is needed, and can be defined in by creating a `.env` file, then inputting in `OPENAI_API_KEY` (see the example `.env.example`). 

Lastly, `pandoc` was used to create a report of both method and results.

## Methods & Preliminary results

Please see `docs/bill_details.pdf` for details on methods of extraction and keyword category definistions, as well we the preliminary detailed results.
