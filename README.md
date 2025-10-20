Product Review Aggregator Workflow

This n8n workflow automates the collection, analysis, and blog generation of product reviews from e-commerce platforms and discussion forums. It produces a clean, ready-to-publish HTML blog post summarizing user sentiment and feature insights.

Overview

The workflow takes a product URL as input, collects reviews from multiple sources, analyzes sentiment and features, and generates a complete HTML blog post. It is designed to help content creators and reviewers quickly produce structured product reviews with minimal manual effort.

How It Works
Input

A product URL is sent to the n8n webhook via a POST request:

{
"productUrl": "<PRODUCT_URL>"
}

Workflow Steps

Product Info Extraction

Extracts key product details like name, variant, and specifications.

Review Aggregation

Searches e-commerce sites (Flipkart, Amazon, Walmart, etc.) and forums (Quora, StackExchange, Reddit) for user reviews.

Uses Firecrawl as the scraper for robust data extraction.

Review Cleaning

Removes HTML tags, duplicates, and irrelevant text to prepare for analysis.

Feature & Sentiment Analysis

Analyzes reviews for key product features (display, camera, battery, etc.) and categorizes them as positive, negative, or neutral.

Uses AI (Google Gemini / PaLM API) for high-quality analysis.

HTML Blog Generation

Generates a ready-to-publish HTML post including:

Header: Product title and summary

Pros & Cons: Highlighting top positives and negatives

Feature Analysis: Detailed insights for each feature with sentiment

User Opinions: Key quotes from actual users

Verdict: Overall rating and purchase recommendations

Output

The workflow returns a JSON object containing the HTML blog post:

{
"parts": [
{
"text": "<!DOCTYPE html> ... </html>"
}
]
}

HTML includes all structured sections ready for publishing.

How to Add a New Product

Send a POST request to the webhook URL with the product URL:

curl -X POST "https://<your-n8n-instance>/webhook/product-review"
-H "Content-Type: application/json"
-d '{"productUrl": "<PRODUCT_URL>"}'

The workflow will automatically process the URL and return a fully structured HTML review.

Required Credentials

Google Custom Search API: For review aggregation

API Key

Search Engine ID

Firecrawl Scraper API: For fetching page content

Google Gemini / PaLM API: For sentiment and feature analysis

⚠️ Make sure all credentials are configured in n8n before running the workflow.

Output Summary

HTML blog post with full review ready for publishing

Structured sections: Header, Pros & Cons, Feature Analysis, User Opinions, Verdict

Sentiment and feature insights embedded for each section

Enhancements

Use paid or more advanced scraping APIs for better forum and website data extraction.

Use a higher-tier AI model for improved feature extraction and blog generation quality.

Add more data sources or customize feature analysis as needed.
