# Documentation

## Corpus 
This corpus contains text (content) scraped from Literaturepage.com, specifically passages from 19th century English novels. Each row in the corpus represents a single page scraped from the website. The corpus contains 12 passages, with each passage ranging from approximately 450 to 800 tokens (words). These passages are extracted from 6 female authors and 6 male authors, which could be interesting for analysis of stylistic differences between genders. Since each passage/page is hosted on a separate URL, it was not possible to scrape larger amounts of text per novel for this assignment. The corpus includes both the textual content of the passages and associated metadata, the chapter headings and page numbers were also scraped from the website.

## What was scraped
- Book passages (content): The main text of each page, located in &lt;p class="reading"&gt; tags.
- Chapter headings: Extracted from &lt;h2 class="readerhead2"&gt; tags.
- Page numbers: Extracted from &lt;div class="pagefoot"&gt; tags.
- Metadata.csv was made manually before beginning scraping the website which included the author, title, year, and url of each novel.

## Cleaning 
- Extra whitespace, line breaks, and multiple spaces were removed from chapter headings and content using regular expressions (re.sub(r'\s+', ' ', ...)).
- Word token counts were calculated for each passage using .split() and stored in a separate column Word_count.

## Robots.txt and Terms of Use 
I chose Literaturepage.com for web scraping because its robots.txt lets standard user-agents access most of the site and only blocks high-load or potentially harmful crawlers. Unlike sites such as Poetry Foundation, which restricts automated access, Literaturepage.com has stable HTML pages with little to no dynamics. This makes it an ethical approach and easy to scrape for a small project. All the data was collected just for educational purposes, following the site’s usage guidelines.

## CSV format 
| Column | Description|
|----------|----------|
| Author    | Name of the author of the novel  |
| Title    | Title of the novel  |
| Year    | Publication year  |
| Url    | Url of scraped page  |
| Content    | Scraped text of the page  |
| Chapter    | Scraped chapter heading  |
| Page_num    | Scraped page number  |
| Word_count    | Number of tokens (words)  |
