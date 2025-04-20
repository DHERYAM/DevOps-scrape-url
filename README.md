# DevOps-scrape-url
Uses Node.js with Puppeteer and Chromium to scrape a user-specified URL
const puppeteer = require('puppeteer');

async function scrapeWebsite(url) {
  try {
    const browser = await puppeteer.launch({
      executablePath: '/usr/bin/chromium-browser', // Adjust path if needed
      headless: 'new', 
    const page = await browser.newPage();
    await page.goto(url, { waitUntil: 'domcontentloaded' });

    // Puppeteer methods to extract data
    
    console.log('Links:', links.slice(0, 10)); 

    await browser.close();
    return { title, bodyText, links }; // Return the scraped data
  } catch (error) {
    console.error('Error during scraping:', error);
    return null;
  }
}


const targetUrl = process.argv[2];

if (!targetUrl) {
  console.log('https://books.toscrape.com/');
  
} else {
  console.log(`Scraping URL: ${targetUrl}`);
  scrapeWebsite(targetUrl)
    .then((data) => {
      if (data) {
        console.log('\nScraping successful!');
        
      }
    })
    .catch((err) => {
      console.error('Scraping failed:', err);
    });
}
