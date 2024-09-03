# Puppeteer Web Scraping Script
This script uses Puppeteer to scrape product information from a specific website and save the data into CSV files and images into local directories. The target website for this example is `daraz.com.bd`, but it can be adapted to scrape other sites with similar structures.

## Features
- Scrapes Product Information: Collects product details such as name, prices, categories, and images.
- Saves Data in CSV Format: Exports the scraped product data into a CSV file.
- Downloads Images: Saves product images into a local directory.

## Requirements
- Node.js
- Puppeteer
- Axios
- CSV-Stringify
- Dotenv

## Setup

#### Clone the Repository:
```bash
git clone https://github.com/yourusername/puppeteer-scraper.git
cd puppeteer-scraper
```

#### Install Dependencies:
```bash
npm install
```

#### Environment Configuration:
- Create a `.env` file to set configurations such as image location if needed.

## How to Use
#### Run the Script:
- Start the script by running:
```bash
node scraper.js
```

#### Modify the URL:
- Change the target URL in the script to the desired product listing page:
```bash
await page.goto("https://www.daraz.com.bd/glamygirl/?q=All-Products&langFlag=en&from=wangpu&lang=en&pageTypeId=2", {waitUntil : "load"});
```

#### Pagination:
- The script navigates through pagination to collect data from multiple pages. You can specify a starting page number or let it run from the first page.

#### Saving Data:
- Data such as product name, sale price, regular price, categories, images, and descriptions are saved into a CSV file in the `csv-files` directory.
- Images are saved into the `images` directory with a timestamped subfolder for each scraping session.

## Key Code Sections

#### Launch Puppeteer:
```bash
const browser = await puppeteer.launch({ headless: false, defaultViewport: false });
const page = await browser.newPage();
await page.setDefaultNavigationTimeout(0);
```

#### Navigate to Product Listings:
```bash
await page.goto("YOUR_TARGET_URL", { waitUntil: "load" });
```

#### Scrape Product Data:
- The script fetches product links from the page, then opens each link in a new tab to extract detailed information including the product title, prices, categories, and descriptions.

#### Download and Save Images:
- Images are downloaded and saved to a specified local directory, which is dynamically created based on the current timestamp.

#### CSV Output:
- The scraped data is saved into a CSV file with headers, and product details are appended row by row.

#### Close Browser:
- The browser closes automatically once all pages and data have been processed:
```bash
await browser.close();
```

## Customization
- Modify the selectors to match the HTML structure of your target website.
- Adjust the pagination logic if the website has a different pagination setup.
- Enhance data extraction by adding or modifying the fields being scraped.

## Important Notes
- Make sure to handle rate limits and respect the terms of service of the websites you are scraping.
- Adjust `headless: false` to `true` if you want the browser to run without a GUI.
- Use responsibly and ensure you have permission to scrape the data.

## License
This project is open-source and available under the [MIT license](https://choosealicense.com/licenses/mit/).
