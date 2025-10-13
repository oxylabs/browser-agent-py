# Browser Agent

[![AI-Scraper Header]()]()

[![](https://dcbadge.limes.pink/api/server/Pds3gBmKMH?style=for-the-badge&theme=discord)](https://discord.gg/Pds3gBmKMH) [![YouTube](https://img.shields.io/badge/YouTube-Oxylabs-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@oxylabs)

**[Browser Agent](https://aistudio.oxylabs.io/apps/browser_agent)** is an AI browser automation tool from **[Oxylabs AI Studio](https://aistudio.oxylabs.io/)**. It simulates real user browsing by executing multi-step actions like clicking links, filling forms, scrolling, capturing screenshots, and then extracting structured data – all controlled through natural language prompts.

Unlike traditional automation frameworks (e.g., Puppeteer or Selenium), Browser Agent requires no static scraping rules or manual scripting. Users can describe tasks in plain English or provide a sequence of steps, and the AI will carry them out just like a human would.

## Key features

- **Full control through browser AI** – execute clicks, inputs, navigation, and scrolling.  
- **Multi-step task execution** – define browsing flows in natural language.  
- **Multiple outputs** – get results in JSON, Markdown, HTML, or PNG screenshots.  
- **Dynamic content support** – interact with JavaScript-rendered pages.  
- **Schema-based extraction** – request structured JSON after the browsing sequence completes.

## How it works

To run tasks with browser AI agent, follow these steps:

1. **Enter the target URL.**  
2. **Describe the browsing process as:**  
   - **Natural language prompt** (e.g. “Open the pricing page, accept cookies, and extract all product names with prices.)  
   - **Structured step list** – provide an array of AI browser actions (`click`, `type`, `navigate`, `wait`, `extract`).  
3. **Select output format:** JSON, Markdown, HTML, or PNG screenshot.  
4. **(Optional) If JSON is selected**, define or auto-generate a schema to structure the gathered data.

### Installation

To begin, be sure you have access to an API key (or get a [free trial](https://aistudio.oxylabs.io/register) with 1000 credits) and `Python ver. 3.10` or above installed. You can install the `oxylabs-ai-studio` package using pip:

```bash
pip install oxylabs-ai-studio
```
### Code examples (Python)

The following examples show how to use the browser AI agent to perform browsing and data extraction.

```python
from oxylabs_ai_studio.apps.browser_agent import BrowserAgent

browser_agent = BrowserAgent(api_key="<API_KEY>")

schema = browser_agent.generate_schema(
    prompt="game name, platform, review stars and price"
)
print("schema: ", schema)

prompt = "Find if there is game 'super mario odyssey' in the store. If there is, find the price. Use search bar to find the game."
url = "https://sandbox.oxylabs.io/"
result = browser_agent.run(
    url=url,
    user_prompt=prompt,
    output_format="json",
    schema=schema,
)
print(result.data)
```

To capture screenshots, use the following Browser Agent workflow:

```python
from oxylabs_ai_studio.apps.browser_agent import BrowserAgent

browser_agent = BrowserAgent(api_key="<API_KEY>")

result = browser_agent.run(
    url="https://example.com",
    user_prompt="Take a screenshot of this page",
    output_format="screenshot"
)

with open("screenshot.png", "wb") as f:
    f.write(result.data)
```
Learn more about Browser Agent and Oxylabs AI Studio Python SDK in our [PyPI repository](https://pypi.org/project/oxylabs-ai-studio/).  
You can also check out our [AI Studio JavaScript SDK](https://github.com/oxylabs/oxylabs-ai-studio-js?tab=readme-ov-file#oxylabs-ai-studio-javascript-sdk) guide for JS users.

### Request parameters

| Parameter        | Description                                                  | Default Value |
|-------------------|--------------------------------------------------------------|---------------|
| `url`*           | Starting URL to browse                                       | –             |
| `user_prompt`*   | Natural language prompt for extraction                        | –             |
| `output_format`  | Output format (`json`, `markdown`, `html`, `screenshot`)      | `markdown`    |
| `schema`         | OpenAPI schema for structured extraction (mandatory for JSON) | –             |
| `geo_location`   | Proxy location in ISO2 format                                 | –             |

\* – mandatory parameters

### Output samples

Browser Agent can return parsed results or screenshots that are easy to integrate into your applications. This is a direct output example of our request code:

```json
{
  "type": "json",
  "content": {
    "games": [
      {
        "game_name": "Super Mario Odyssey",
        "platform": null,
        "review_stars": null,
        "price": 89.99
      }
    ]
  }
}
```
Browser Agent supports multiple output formats (`"output": "YOUR_FORMAT"`):

- `json` – structured data using schema-based parsing.  
- `markdown` – easy-to-read data, perfect for AI and automation workflows.  
- `html` – raw HTML data of the webpage.  
- `screenshot` – PNG image of the browser content.

## Practical use cases

You can use AI Browser Agent in various ways, including:

1. **E-commerce checkout simulation** – add items to cart, apply coupon, confirm checkout flow.  
2. **Travel search automation** – enter destinations, apply filters, and extract flight or hotel prices.  
3. **Job search scraping** – search for a role, click through postings, extract job details.  
4. **Event & ticket discovery** – navigate event sites, retrieve titles, dates, and prices.  
5. **And many more…**

## FAQ

### How is Browser Agent different from Puppeteer or Selenium?
Traditional tools rely on writing selectors and scripts for every action. AI browser agents replace that with natural language instructions and add organic browsing, making automation much faster, easier, and less fragile.

### Can Browser Agent log in to websites or fill forms?
Yes, you can instruct the agent to enter text, submit forms, or click buttons. Keep in mind that sites with advanced bot detection may require advanced setup.

### Can I use Browser Agent on any website?
Browser Agent works on most public websites, including ones that rely on JavaScript or interactive flows. However, you should always make sure your use case complies with the target website’s Terms of Service and applicable laws.

### Is Browser Agent free to use?
Oxylabs AI Studio Browser Agent is free to try by signing up for a free trial that includes 1,000 credits. After the trial, the [monthly plans](https://aistudio.oxylabs.io/pricing) start at just $12/month with 3000 credits and 1 request/s, with higher plans offering more credits and higher request rates.

## Learn more

For a deeper dive into available parameters, advanced integrations, and additional examples, check out the [AI Studio documentation](https://aistudio.oxylabs.io/apps/browser_agent).

## Contact us

If you have questions or need support, reach out to us at [hello@oxylabs.io](mailto:hello@oxylabs.io), through [live chat](https://oxylabs.drift.click/oxybot), or join our [Discord community](https://discord.gg/Pds3gBmKMH).
