Here is a Python script using Beautiful Soup, Selenium, and Json libraries. Please do ensure that you install these libraries using pip install if you have not done so.

Also, it is important to note Automated Extraction of data from Oddsportal may violate their terms of service. So please ensure you have the necessary permissions to scrape data. Violation of the website’s TOS can lead to legal issues.


```bash
pip3 install bs4
pip3 install requests
pip3 install json
pip3 install selenium
pip3 install webdriver_manager 
```

```python

from bs import BeautifulSoup

import requests

import json

import time

from selenium import webdriver


# Set up the driver and navigate to the page

from webdriver_manager.chrome import ChromeDriverManager

driver = webdriver.Chrome(ChromeDriverManager().install())

url = "https://www.oddsportal.com/american-football/usa/nfl/results/#/page/1"

driver.get(url)


# Allow the page to load

time.sleep(5)


# Parse HTML content

soup = BeautifulSoup(driver.page_source, 'html.parser')


# Close the driver

driver.quit()


# Extract JSON Data

script_tag = soup.find('script', text=lambda x: x and 'window.xhrUrls' in x)

json_text = re.search('window.xhrUrls = ({.*})', script_tag.string, re.DOTALL | re.MULTILINE).group(1)

json_data = json.loads(json_text)


print(json_data)

```

This code deals primarily with obtaining the JSON from the initial page load.

You would need a separate block of code to navigate to subsequent pages, perhaps through interaction with the "Next" button and repeating these steps. Alternatively, you could extract the "Next" button's href attribute and navigate directly to that URL.

This module uses Selenium, which gives it the capacity to interact with the Javascript on the page and scrape dynamic content contrary to Request module which only scrapes static or rather a snapshot of the page.

Also, ensure you check if the specific web page allows data scraping or not in their ‘robots.txt’ file, you can view it by appending '/robots.txt' to the base URL.

E.g https://www.oddsportal.com/robots.txt

To dynamically install a chrome driver that has support for both macOS and Linux in Python, you could use a library called `webdriver_manager`. This library handles the installation and configuration of the Chrome driver for you.

In this example, `webdriver_manager` will check the latest version of the Chrome driver, download it and create a path, so you don't need to deal with these details manually.
This solution is good because it's cross-compatibility (Windows, MacOS, Linux). It's also able to determine the version of Chrome currently installed and download the corresponding ChromeDriver.
