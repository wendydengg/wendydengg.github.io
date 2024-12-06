---
layout: post
title: Web-Scraping Workshop
date: 2024-09-024 00:32:13
description: Summary of an Introduction to Web Scraping Workshop at the Research Data & Digital Scholarship (RDDS) Exchange at Van Pelt 
tags: Digital Humanities
categories:
tabs: true
---

Web scraping is a common tool used to quickly and efficiently extract large amounts of data from websites. I attended the Introduction to Web Scraping Workshop by Stephen Hall, a Computer Science librarian at the Research Data & Digital Scholarship (RDDS) Exchange at Van Pelt, introduced us to the Python package BeautifulSoup and some precautions to keep in mind before doing any web-scraping on the website.

## Before Web-Scraping

He started off the presentation by reminding us of the dangers and precautions to keep in mind when doing web-scraping. Specifically, we need to check the terms and services file to see if the owner of the site permits web-scraping. If that is not available, we can inspect the site’s robots.txt file (which is meant to be machine-readable but can also be checked by humans) that tells web crawlers what their permissions are. For example, the New York Times does not allow web-scraping of any of their articles. Web-scraping in itself is not an illegal task, but if done so without the permission of the site owners, it is possible to get into a lot of legal troubles. This is especially an issue when web-scraping is done illegally and dangerously for users with bad intentions as they can introduce a lot of problems to the site owners. For instance, university resources are not allowed to be scrapped because vendors of the universities monitor their sites and will ban the university’s IP address if suspicious activities are found. The bottom line is that if you are unsure about the permissions of a site, don’t perform web-scraping. Below is a list of other key considerations when performing web-scraping:

- Had the owner made it publicly and freely available? (if it is behind a paywall, then no)
- An account is not required to access the data
- The website should not block scrapers
- Issues of copyright infringement and plagiarism
- How are we using the data?
- Does it have an API? Cuz we should use that instead
- Most of the sites we wanna scrape… we can’t
- Penn has an intellectual property manager to handle these types of issues

## Technical Details

As for the technical details, web-scraping is simply a form of regular expression matching. Regular expressions are a sequence of characters that specifies a pattern to search for in text. It is the backbone of most “find and replace” algorithms, including Ctrl-F. We then performed some simple regex queries over a toy website called https://books.toscrape.com. Below are some examples of regex matching syntax:

- '*' looks for preceding character 0 or more times
  ab*c (a and c with any number of b in b/t)
- '+' looks for preceding character 1 or more times
  ab\*c (a and c with at least one b in b/t)
- '.' wildcard character
  a.c (a and c with any single character in b/t)
- '?' preceding character may or may not be present in string
  docx (doc and docx)
- '\d' matches any digit character
- '\s' matches any whitespace character
- '[...]{#}' matches any character in a range, with # number of characters back-to-back
- '[A-Za-z0-9]' any character between A to Z, any b/t a to z, any b/t 0 to 9
- '()' sub-catch returns only stuff in that parenthesis, but need to specify which group # in group(#)

## Digital Humanities Application

I can see this skill being extremely useful for digital humanities projects, where the historical data is scattered around the web and requires manual checking of the text to ensure validity. For example, if we want to find more data regarding inmates in the Eastern State Penitentiary (ESP), which is sparsely available, we can perform web-scraping over websites that contain all possible information about inmates in Philadelphia and narrow down to those who lived in the ESP.
Thank you to the RDDS team at Van Pelt!
