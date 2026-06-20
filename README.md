# Lede 2026 — Web Scraping Project (Six Scripts)

A set of six Jupyter notebooks built for the **Lede Program 2026** (summer data
journalism program at Columbia Journalism School). Each notebook scrapes a
different website, working up from a simple static page to forms, multi-page
results, and sites that block ordinary requests. Most notebooks save their
results to a CSV.

## Tools used

- **requests** — fetch pages
- **BeautifulSoup (bs4)** — parse and select HTML
- **pandas** — build tables / `read_html` / save CSVs
- **playwright** — form submission (Part 3)
- **curl_cffi** — browser-impersonating requests to get past a 403 block (Part 6)

## Notebooks, in order

Work through them in numbered order — each one adds a new scraping technique.

| # | Notebook | Site scraped | What it does | Output |
|---|----------|--------------|--------------|--------|
| 1 | [Scrape_part1_ArizonaRcok.ipynb](Scrape_part1_ArizonaRcok.ipynb) | Arizona rock & mineral clubs list — [rocktumbler.com](https://rocktumbler.com/blog/rock-and-mineral-clubs/) | First scrape: parse a nested HTML table with BeautifulSoup into a list of dictionaries | — |
| 2 | [Scrape_part2_leMonde_draft.ipynb](Scrape_part2_leMonde_draft.ipynb) | *Le Monde* — [lemonde.fr](https://www.lemonde.fr/) | Practice with `find`, `select`, and `select_one` CSS selectors on a news homepage | — |
| 3 | [Scrape_part3_water.ipynb](Scrape_part3_water.ipynb) | SC water systems — [dww.des.sc.gov](https://dww.des.sc.gov/DWW/) | Submit a search **form**, scrape results, handle failures with try/except | [water.csv](water.csv) |
| 4 | [Scrape_part4_wikipedia.ipynb](Scrape_part4_wikipedia.ipynb) | List of US Presidents — [Wikipedia](https://en.wikipedia.org/wiki/List_of_presidents_of_the_United_States) | Pull a table with `pandas.read_html` (plus request headers) | — |
| 5 | [Scrape_part5_courtcases_multiplepages.ipynb](Scrape_part5_courtcases_multiplepages.ipynb) | TN Bankruptcy Court opinions — [tnwb.uscourts.gov](https://www.tnwb.uscourts.gov/Search/Search.aspx) (search: "CAR") | Scrape **across multiple result pages**, split detail strings, download linked PDFs | [courtcases10.csv](courtcases10.csv), [courtcases_page234.csv](courtcases_page234.csv) |
| 6 | [Scrape_part6_Thirdparty.ipynb](Scrape_part6_Thirdparty.ipynb) | AZ third-party driver license locations — [travel-id-documents.az.gov](https://travel-id-documents.az.gov/authorized-third-party-driver-license-locations) | Get past a **403 block** using user-agent headers / `curl_cffi` | [third_party_locations.csv](third_party_locations.csv) |

## Sites scraped (summary)

1. rocktumbler.com — Arizona rock & mineral clubs listing
2. lemonde.fr — *Le Monde* news homepage
3. dww.des.sc.gov — South Carolina Drinking Water Watch
4. en.wikipedia.org — List of presidents of the United States
5. tnwb.uscourts.gov — U.S. Bankruptcy Court, Western District of Tennessee (opinions search)
6. travel-id-documents.az.gov — Arizona authorized third-party driver license locations

## Output files

- [water.csv](water.csv) — water system search results (Part 3)
- [courtcases10.csv](courtcases10.csv) / [courtcases_page234.csv](courtcases_page234.csv) — court case results (Part 5)
- [third_party_locations.csv](third_party_locations.csv) — license locations (Part 6)

## Running

```bash
pip install requests beautifulsoup4 pandas playwright curl_cffi
playwright install        # only needed for Part 3
jupyter lab               # open and run the notebooks in order
```

