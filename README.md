# Webscraping

## Introduction
The following post illustrates an approach to “scraping” information from a job posting site where each page on the site contains a number of job post titles, each linking to a full job post. For more resources, considerations, and examples see here.

> [!Note] 
> For webscraping tasks, each website is different and solutions will need to be tailored.

Example objective: The code in this example scrapes job post information from “https://www.gumtree.co.za/”. The objective is to identify, extract, and aggregate job post information into a data set. We will use an approach called “screen scraping”, or HTML parsing. I use a combination of my browser’s “inspect tool” and SelectorGadget (“point and click CSS selectors”) to figure out what pattern (in the HTML) identifies the piece of information on my screen I’m interested in scraping (in this case job titles, job descriptions, location, &c.). I use the rvest R package (“rvest helps you scrape information from webpages”), and a number of tidyverse tools for data manipulation.

> [!Note]
>  An “element” refers to an HTML element: “An HTML element is defined by a start tag, some content, and an end tag.” CSS-selectors “are used to "find" (or select) the HTML elements […]”

Best practice:
1. Check if the site has a “robots.txt” file which — if a site has one — includes do’s and don’ts for scrapers/crawlers. This file can be found at the root of the website host, i.e. “https://www.gumtree.co.za/robots.txt”. In the example, I use the robotstxt package to access and check the robots.txt file.
2. Don’t go too fast, don’t send too many requests to the website per second — be polite.

