# Twitter Scraper

## Overview
This project is a Twitter scraper that collects tweets from Twitter (X) using Selenium and BeautifulSoup. It extracts tweet URLs, tweet content, engagement metrics (likes, replies, reposts, bookmarks, views), and timestamps. The scraped data is stored in JSON format and can be converted to CSV for further analysis.

## Features
- **Automated Web Scraping**: Uses Selenium WebDriver to navigate Twitter and collect tweets dynamically.
- **Content Extraction**: Extracts tweet text, engagement metrics (likes, retweets, replies, bookmarks, views), and timestamps.
- **Scroll Automation**: Handles scrolling and retry mechanisms for continuous data extraction.
- **Data Storage**: Saves extracted tweets in JSON format.
- **CSV Export**: Converts the JSON data to CSV for easy analysis.

## JSON Fields
The scraped data is stored in `tweets.json` with the following structure:
```json
[
  {
    "href": "Tweet URL",
    "text": "Tweet content",
    "timestamp": "Tweet timestamp",
    "replies": "Number of replies",
    "reposts": "Number of reposts",
    "likes": "Number of likes",
    "bookmarks": "Number of bookmarks",
    "views": "Number of views",
    "scrapingTimestamp": "Time when the data was scraped"
  }
]
```

## Requirements
### Python Packages
Ensure you have the following Python packages installed:
```sh
pip install selenium beautifulsoup4 webdriver-manager pandas
```

### WebDriver Setup
- The script uses `webdriver_manager` to automatically install the latest ChromeDriver.
- Ensure that Google Chrome is installed.
- The script is configured to use a specific Chrome user profile. Modify `user_data_dir` and `profile` variables in `set_up_driver()` if needed.

## Usage

### 1. Scraping Tweets
Run the script to start scraping tweets:
```sh
python twitterscraping.py
```
This will:
1. Open Twitter search results for a specified keyword.
2. Scroll and collect tweet URLs.
3. Extract tweet content and engagement metrics.
4. Save the data in `tweets.json`.

### 2. Convert JSON to CSV
To convert the scraped data to CSV:
```sh
python -c "import twitterscraping; twitterscraping.jsontocsv()"
```
This will generate `tweets.csv`.

## Configuration
- Modify `url` in `get_all_posts()` to scrape different search queries.
- Change `totalposts` in `collect_all_hrefs()` to adjust the number of tweets scraped.
- Uncomment `chrome_options.add_argument("--headless")` in `set_up_driver()` to run in headless mode.

## Limitations & Considerations
- **Twitter Rate Limits**: Frequent scraping may trigger rate limits or require login.
- **Dynamic Content**: Twitter changes its HTML structure frequently, so the script may need updates.
- **IP Blocking**: Use proxies or rotate user agents to reduce detection risk.

## License
This project is open-source and available under the MIT License.

## Author
Sagar Singh and Tiwari Vivek

