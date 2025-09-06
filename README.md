# Restaurant Review Scraper

A Python web scraper that extracts comprehensive restaurant information and reviews from TripAdvisor. This tool is designed to gather detailed data including ratings, reviews, contact information, and more. I followed a tutorial and added a comprehensive logging configuration that saves all program messages to both the console (for real-time monitoring) and a scraper.log file (for persistent record-keeping) with timestamps and proper formatting.

## Features

- 🍽️ **Comprehensive Data Extraction**: Restaurant details, ratings, reviews, and contact information
- 🔄 **Multi-page Scraping**: Automatically scrapes all available review pages
- 🌐 **Proxy Support**: Built-in proxy rotation to avoid rate limiting
- 📊 **Detailed Ratings**: Food, service, value, and atmosphere ratings
- 📝 **CSV Export**: Clean, structured data output
- 🛡️ **Error Handling**: Robust retry logic and exception handling
- 📋 **Logging**: Comprehensive logging for monitoring and debugging

## Data Extracted

### Restaurant Information
- Name, price level, cuisine type
- Overall rating and total review count
- Detailed ratings (food, service, value, atmosphere)
- Ranking and city information
- Address and phone number

### Review Data
- Individual review ratings
- Review titles and full text
- Review dates
- All reviews from all available pages

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/restaurant-review-app.git
   cd restaurant-review-app
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up proxies (optional but recommended)**
   ```bash
   cp proxies.txt.example proxies.txt
   # Edit proxies.txt and add your proxy servers
   ```

## Usage

### Basic Usage

```python
python app.py
```

The script will scrape the default restaurant (Gallagher's Steakhouse in NYC) and save results to `tripadvisor_ny_restaurant_reviews.csv`.

### Customizing the Target Restaurant

Edit the `base_url` variable in the `main()` function:

```python
base_url = 'https://www.tripadvisor.com/Restaurant_Review-g60763-d478965-Reviews-Gallaghers_Steakhouse-New_York_City_New_York.html'
```

Replace with your target restaurant's TripAdvisor URL.

### Proxy Configuration

1. Create a `proxies.txt` file with one proxy per line:
   ```
   192.168.1.1:8080
   10.0.0.1:3128
   203.0.113.1:8080
   ```

2. The scraper will automatically rotate through available proxies.

## Output

The scraper generates a CSV file with the following columns:

| Column | Description |
|--------|-------------|
| RESTAURANT_NAME | Name of the restaurant |
| PRICE_LEVEL | Price range (e.g., $$$) |
| CUISINE_TYPE | Type of cuisine |
| TOTAL_RATING | Overall rating out of 5 |
| TOTAL_REVIEWS | Total number of reviews |
| FOOD_RATING | Food rating out of 5 |
| SERVICE_RATING | Service rating out of 5 |
| VALUE_RATING | Value rating out of 5 |
| ATMOSPHERE_RATING | Atmosphere rating out of 5 |
| RANKING | Restaurant ranking in city |
| CITY | City name |
| ADDRESS | Restaurant address |
| PHONE_NO | Phone number |
| RATING | Individual review rating |
| REVIEW_TITLE | Review title |
| REVIEW_DETAILS | Full review text |
| REVIEW_DATE | Date of review |

## Configuration

### Rate Limiting
The scraper includes built-in delays to be respectful to TripAdvisor:
- 3 seconds between individual reviews
- 8-12 seconds between pages (randomized)

### Retry Logic
- 3 retry attempts for failed requests
- Automatic proxy rotation on failures
- 5-second delay between retries

## Legal and Ethical Considerations

⚠️ **Important**: This tool is for educational and research purposes only. Please ensure you:

- Respect TripAdvisor's Terms of Service
- Use reasonable delays between requests
- Don't overload their servers
- Consider using official APIs when available
- Be mindful of copyright and data usage policies

## Troubleshooting

### Common Issues

1. **No proxies loaded**
   - Ensure `proxies.txt` exists and contains valid proxies
   - Check proxy format (ip:port)

2. **Request failures**
   - Verify internet connection
   - Check if proxies are working
   - Try with different proxy servers

3. **Empty results**
   - Verify the TripAdvisor URL is correct
   - Check if the restaurant has reviews
   - Ensure the page structure hasn't changed

### Logs

Check `scraper.log` for detailed information about the scraping process.

## Dependencies

- `requests` - HTTP library for making requests
- `beautifulsoup4` - HTML parsing library
- `lxml` - XML/HTML parser (faster than default)

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This tool is provided for educational purposes only. Users are responsible for ensuring their use complies with applicable laws and website terms of service. The authors are not responsible for any misuse of this tool.
