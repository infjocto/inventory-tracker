## Monitor Your Amazon Competitors' Inventory

### Objective

This script will create a spreadsheet of the competiting products that are currently "Out Of Stock" or low in stock, like shown below.

![](low.JPG)

### Why is this useful? 

1. This could be an opportunity to push out competitors. When a product goes out of stock, Amazon drops their search ranking. 
2. Knowing when your competitors are/will be out of stock can help you make better informed restocking and pricing decisions. 

### Requirements

For this script to work, you must add your competitors' products to your Amazon wishlist. It can be any wishlist, just make sure you set it to "public". This script is unable to web-scrape private wishlists and Amazon searches. 

----------------------------------

### **UPDATE 10/26/2018** -------

Amazon has changed the wishlist formatting, so that the inventory data does not show. As a result, this script can no longer return inventory data.

It is possible to adapt the script to return other pieces of information available through the wishlist page. 

---------------------------------
### The Action Plan

#### Section 1. Observe HTML of wishlist for clues on pattern extraction
#### Section 2. Extracting HTML data
#### Section 3. Organize data using vectors, polish the data (& if possible, systematize the process of data cleaning for reproducible results)
#### Section 4. Store data in spreadsheet

# Section 1. Observe HTML for Patterns

For the purposes of this project, we will be using [this](https://www.amazon.com/hz/wishlist/ls/18UQZ34U5ANT0?&sort=default) public wishlist. See below. 

![](wishlist.JPG)

### We Need To:

1. Decide what information to extract
2. Determine how to extract desired information from HTML data

### 1. Deciding What Information To Extract

We observe the webpage, taking note of the information types, such as price, product name, stock status. 

- 14 items, after full loading.
- Stock/availability information shows as "In Stock", "Only X left in stock--order soon", "Out Of Stock", "Usually ships in X days"

It would be useful to extract:

- the website link
- product id
- product name
- inventory information

### 2. Determine How To Extract

Look at the HTML data to look for patterns. You can find the HTML data by right clicking the page & view page source.

To find patterns in the HTML data, try "finding" specific information you saw on the webpage. For example, if you saw a product with inventory information "Usually ships in 5 to 7 days", find that in the HTML data. Try to find when each products' HTML data starts and ends. This is useful because we can then extract these lines in a organized manner for further polishing. 

#### Observations of each product's HTML data

- Product ID consistently shows up 71 times for each item. 
(From observing individual listings, we can determine that the product ID comes after "coliid" in the web address.)
- The data-itemId tag shows up 3 times per item.

Below are screenshots of the highlighted code we would like to extract:

HTML code containing the product id
![](prodid.JPG)

HTML code containing availbility info
![](avail.JPG)

HTML code containing web address and product name
![](webaddy.JPG)

## Section 2. Extracting HTML Data Using Product ID

### Setting Up Libraries

```python
# setup libraries
# pip is a package management system
import pip
pip.main(["install", "bs4"])
# beautifulsoup parses HTML
from bs4 import BeautifulSoup
pip.main(["install", "requests"])
# requests, in this case, helps us get HTML from URL
import requests
```











## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/infj-octo/Amazon-Competitor-Inventory-Tracker/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/infj-octo/Amazon-Competitor-Inventory-Tracker/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
