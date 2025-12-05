# Documentation

## Corpus 
This corpus contains text (content) scraped from Literaturepage.com, specifically passages from 19th century English novels. Each row in the corpus represents a single page scraped from the website. The corpus contains 12 passages, with each passage ranging from approximately 450 to 800 tokens (words). These passages are extracted from 6 female authors and 6 male authors, which could be interesting for analysis of stylistic differences between genders. Since each passage/page is hosted on a separate url, it was not possible to scrape larger amounts of text per novel for this assignment. The corpus includes both the textual content of the passages and associated metadata, the chapter headings and page numbers were also scraped from the website.

## What was scraped
- Book passages (content): The main text of each page, located in &lt;p class="reading"&gt; tags.
- Chapter headings: Extracted from &lt;h2 class="readerhead2"&gt; tags.
- Page numbers: Extracted from &lt;div class="pagefoot"&gt; tags.
- Metadata.csv was made manually before beginning scraping the website which included the author, title, year, and url of each novel.

## Cleaning 
- Extra whitespace, line breaks, and multiple spaces were removed from chapter headings and content using regular expressions (re.sub(r'\s+', ' ', ...)).
- Word token counts were calculated for each passage using .split() and stored in a separate column Word_count.

## Robots.txt and Terms of Use 
I chose Literaturepage.com for web scraping because its robots.txt makes it clear that normal user-agents are allowed to access the main content of the site. The file blocks only a long list of high-load or potentially abusive crawlers (such as “WebZip,” “Wget,” “Offline Explorer,” and similar tools), but it does not restrict standard automated access by educational scripts. The only general rule applying to all user-agents is:
- User-agent: *
- Disallow: /zz
- Disallow: /ztrap.php
- Disallow: /zpage
- Disallow: /zzpage
- Disallow: /work

Since none of these blocked paths are related to the book pages I used, scraping small amounts of text for research purposes falls within the allowed behavior. Further, unlike sites such as Poetry Foundation, which actively restrict automated access, Literaturepage.com serves simple static HTML with minimal JavaScript, making it straightforward, stable, and ethically suitable for this assignment. All data was collected exclusively for educational use and in line with the site’s guidelines.

## Corpus.csv format 
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
