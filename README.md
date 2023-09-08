# PySeoHtml

PySeoHtml is a Python library designed to intelligently link specific keywords within HTML text content. It enhances SEO (Search Engine Optimization) strategies by optimizing content with linked keywords, maintaining readability, and preventing over-optimization.

## How It Works

### Initialization

To get started, create an instance of the PySeoHtml class by providing the following parameters:

- `html_text` (str): The HTML text content you want to process.
- `keywords` (dict): A dictionary where keys are the keywords you want to link, and values are the URLs to which the keywords should link.
- `density` (int, optional): The maximum allowed length (in characters) for linked text snippets. Default is 500 characters.
- `random_links` (bool, optional): If set to True, the library will randomly choose keywords to link each time. If False, it will link the same keywords consistently. Default is False.

### Text Processing

#### Tokenization

The HTML text is tokenized into words and punctuation using the NLTK WordPunctTokenizer.

#### Keyword Matching

The library identifies keywords within the text, matches them to the provided keywords, and prepares them for linking.

#### Link Insertion

Keywords are linked to their respective URLs within the HTML content. The library ensures that linked keywords are surrounded by readable text snippets, maintaining the quality of the content.

#### HTML Escaping

Any HTML escaping (e.g., &lt; and &gt;) is corrected to ensure valid HTML output.

#### Punctuation Handling

Extra spaces before punctuation marks are removed to maintain proper grammar and readability.

#### Link Limitation

To prevent over-optimization and maintain content quality, the library removes excess `<a>` tags if there are more than one per 500 characters (configurable via `density`).

### Randomization (Optional)

If the `random_links` parameter is set to True, the library will randomly choose keywords to link each time it processes the HTML content. This feature can be useful to avoid over-optimization penalties from search engines.

## How It Benefits SEO

### Keyword Linking

PySeoHtml automatically identifies and links keywords to relevant URLs within your HTML content. This helps search engines understand the context and relevance of your content, potentially improving search rankings.

### Content Optimization

By strategically linking keywords, you can enhance the SEO value of your content and increase its visibility in search engine results.

### Prevents Over-Optimization

The library limits the number of linked keywords to maintain a natural keyword density. Over-optimization can lead to SEO penalties, so PySeoHtml helps you avoid this.

### Maintains Readability

PySeoHtml ensures that linked keywords are embedded within readable text snippets, improving the user experience and preventing content from appearing spammy.

## Usage

Here's an example of how to use the PySeoHtml library:

```python
from PySeoHtml import PySeoHtml

# Initialize the PySeoHtml with your HTML text and keywords
html_text = """
    <p>This is an example HTML text containing keywords like Python and SEO.</p>
    <p>Python is a versatile programming language for SEO professionals.</p>
"""
keywords = {"python": "https://python.org", "seo": "https://seo-example.com"}
linker = PySeoHtml(html_text, keywords, density=500, random_links=False)

# Process the HTML text to add links to keywords
processed_html = linker.process_text()

# Use the processed_html in your web content
print(processed_html)
