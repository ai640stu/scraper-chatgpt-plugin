# Scraper API Plugin for OpenAI

This plugin allows OpenAI to fetch proxy data from the Scraper API, powered by AI and built specifically for developers. It allows you to easily fetch content from websites in order to train your AI models, without having to deal with common web scraping challenges such as IP blocking, CAPTCHAs, and more.

## Getting Started

To use this plugin with OpenAI, you will first need to obtain an API key from Scraper API:

1. Sign up for a free account at [https://dashboard.scraperapi.com/signup](https://dashboard.scraperapi.com/signup).
2. Log in to your account.
3. Click on the 'Dashboard' tab.
4. Click the `Show` button next to the 'API Key' field to reveal your API key. 

## Using the Plugin

Once you have your API key, you can begin using the plugin. Simply follow these steps:

1. Create a new instance of the OpenAI API using your API key:

```python
import openai_secret_manager

assert "scraper" in openai_secret_manager.get_services()
secrets = openai_secret_manager.get_secret("scraper")

import openai
openai.api_key = secrets["api_key"]
```

2. Use the `requests` module to make HTTP requests to the Scraper API endpoint:

```python
import requests

url = "https://api.scraperapi.com/v1/scrape"
params = {
    "api_key": secrets["api_key"],
    "url": "https://example.com"
}

response = requests.get(url, params=params)
html_content = response.text
```

3. Process the HTML content as needed to extract the data you require.

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html_content, "html.parser")
# Extract data from webpage here
```

## Limitations

This plugin supports only one endpoint (`/scrape`) in order to minimize the length of the text and prevent overload on the ChatGPT context limit. However, the Scraper API offers additional features that can be explored further at their website.

## Questions or Issues

If you have any questions or issues with the Scraper API plugin for OpenAI, please feel free to reach out to Scraper API's support team at [https://www.scraperapi.com/support](https://www.scraperapi.com/support).
