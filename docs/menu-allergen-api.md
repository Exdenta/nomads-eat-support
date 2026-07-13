# Restaurant Menu Allergen API — EU-14 Allergen & Nutrition Data from Google Maps

Turn any restaurant on Google Maps into structured menu data with **EU-14
allergen classification, nutrition estimates, and translated dish names** —
no API keys, no OCR pipeline to build, no manual data entry.

This is the production menu pipeline behind the Nomads Eat dietary-restrictions
travel app, available as ready-to-run APIs on the Apify platform.

## What you get per dish

| Field | Description |
|---|---|
| `name` / `originalName` | Dish name translated to your language + exactly as printed |
| `price` | With currency symbol, as shown on the menu |
| `ingredients` | Atomic base ingredients, each with **EU-14 allergens and a confidence score** |
| `allergens` | Human-readable summary of the 14 EU-regulated allergens: gluten, crustaceans, eggs, fish, peanuts, soy, milk, nuts, celery, mustard, sesame, sulfites, lupin, molluscs |
| `dietaryType` | Vegan / Vegetarian / Pescetarian / Other, with an explanation |
| `nutritionInfo` | Estimated serving size, calories, protein, fat, carbs |
| `story` | Origin story / cultural significance of the dish |

Unlike scrapers that keyword-match "dietary tags" from menu descriptions, the
allergen and dietary classification here is AI-parsed from each dish's actual
ingredients — with a confidence score per allergen, so you can decide your own
safety threshold.

## Who uses menu allergen data

- **Food & dietary apps** — allergen-safe and vegan restaurant discovery at
  the dish level, not the venue level.
- **EU 1169/2011 allergen compliance** — the EU Food Information for
  Consumers Regulation requires allergen information for non-prepacked food;
  audit how a venue's published menu maps to the EU-14 list.
- **Delivery & ordering platforms** — enrich partner restaurant catalogs
  with structured dishes, prices, and allergen labels before onboarding.
- **Market research** — compare dish pricing and menu composition across a
  city or cuisine, translated into one language.

## The APIs

- **[Google Maps Menu Scraper (no API key)](https://apify.com/nomad-agent/google-maps-menu-scraper-managed)**
  — paste a Google Maps place URL or name, get the structured menu. Photo
  fetching and AI cost included in the per-dish price. First run: up to 10
  dishes free; empty runs are never charged.
- **[Google Maps Menu Scraper (bring your own keys)](https://apify.com/nomad-agent/google-maps-menu-scraper)**
  — the same scraper at a lower per-dish price, using your own free-tier
  Google AI Studio and Outscraper keys.
- **[AI Restaurant Menu Parser](https://apify.com/nomad-agent/ai-menu-parser-managed)**
  — already have menu photos (from any source)? Parse them directly into the
  same structured dish format.

## How it works

1. You provide a Google Maps place URL, place ID, or plain place name.
2. The scraper collects the place's **Menu** photos (falling back to the
   menu published on the restaurant's own website, including PDFs).
3. An AI vision model extracts every dish and classifies its ingredients
   against the EU-14 allergen list, at temperature 0 for reproducible output.
4. You get one JSON record per dish via the Apify dataset API — ready for
   your app, spreadsheet, or data warehouse.

Questions? [Open an issue](https://github.com/exdenta/nomads-eat-support/issues)
or email [nomads.eat@gmail.com](mailto:nomads.eat@gmail.com).
