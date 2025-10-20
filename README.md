# 🛠 Product Review Aggregator Workflow

Automate the collection, analysis, and blog generation of product reviews from e-commerce platforms and discussion forums using n8n. This workflow produces a clean, ready-to-publish HTML blog post summarizing user sentiment and feature insights for any product URL.

---

## 🚀 Overview

This workflow streamlines the entire product review process:
- Input a product URL.
- Aggregate reviews from multiple sources.
- Analyze feature sentiment using AI.
- Generate a fully structured HTML blog post for publishing.

Ideal for content creators, tech bloggers, and reviewers who want to quickly produce detailed product reviews with minimal manual effort.

---

## ⚙️ How It Works

### **1. Input**
Send a product URL to the n8n webhook via a POST request:
```json
{
  "productUrl": "<PRODUCT_URL>"
}
```

### **2. Workflow Steps**

#### **Product Info Extraction**
- Parses the product page to extract key details (name, variant, specifications).

#### **Review Aggregation**
- Searches e-commerce sites (Flipkart, Amazon, Walmart, etc.) and forums (Quora, StackExchange, Reddit) for user reviews.
- Uses [Firecrawl](https://firecrawl.dev/) as the main scraper for robust data extraction.

#### **Review Cleaning**
- Removes HTML tags, duplicates, and irrelevant text for cleaner analysis.

#### **Feature & Sentiment Analysis**
- Analyzes reviews for key product features (e.g., display, camera, battery).
- Categorizes sentiments: positive, negative, or neutral.
- Powered by AI (Google Gemini / PaLM API) for high-quality insights.

#### **HTML Blog Generation**
- Produces a ready-to-publish HTML post with:
  - **Header:** Product title and summary
  - **Pros & Cons:** Highlights top positives and negatives
  - **Feature Analysis:** Detailed insights per feature with sentiment
  - **User Opinions:** Key quotes from real users
  - **Verdict:** Overall rating and purchase recommendations

### **3. Output**
Returns a JSON object containing the full HTML blog post:
```json
{
  "parts": [
    {
      "text": "<!DOCTYPE html> ... </html>"
    }
  ]
}
```
HTML includes all structured sections, ready for publishing.

---

## ➕ How to Add a New Product

Send a POST request to the webhook endpoint with your product URL:
```bash
curl -X POST "https://<your-n8n-instance>/webhook/product-review" \
-H "Content-Type: application/json" \
-d '{"productUrl": "<PRODUCT_URL>"}'
```
The workflow will process the URL and return a structured HTML review.

---

## 🔑 Required Credentials

- **Google Custom Search API**
  - API Key
  - Search Engine ID
- **Firecrawl Scraper API**
- **Google Gemini / PaLM API** (for sentiment & feature analysis)

**⚠️ Ensure all credentials are configured in n8n before running the workflow.**

---

## 🛠 Enhancements

- Use paid or more advanced scraping APIs for improved data extraction.
- Upgrade to higher-tier AI models for better feature extraction and blog quality.


---

## 🙋‍♂️ Support & Contributions

Feel free to open issues or pull requests for enhancements and bug fixes!
