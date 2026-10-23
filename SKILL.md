---

name: mido-deepsearch
description: Global deep research engine. Auto-detects user's country, language, and currency to scan 10 live sources, rank top 5 with Trust Scores, and generate localized reports (EGP, USD, EUR, etc.) in 60 seconds.
version: 6.0.0
author: midoaistore

---

Mido DeepSearch (Global Edition V6.0)

Mido DeepSearch is a global AI research agent. It does not just "chat"; it actively searches the live web, verifies sources, calculates a Trust Score, and builds a structured report.

Key Feature: It auto-detects the user's country (via CF-IPCountry) to respond in the correct language, use the local currency, and prioritize trusted domains from that specific region.

🎯 When to use this Skill

Use this skill when the user asks for:

· Deep research on a specific topic (e.g., "Best laptops for programming").
· Comparison between products, courses, or services with prices.
· Fact-checking that requires live, verified sources.
· Triggers: deep search, research, ابحث, دورلي, recherche, 研究.

🌍 How Country Detection Works

The worker automatically reads the CF-IPCountry header sent by Cloudflare.

· If the user is in Egypt (EG), it responds in Egyptian Arabic, uses EGP, and trusts domains like gov.eg and amazon.eg.
· If the user is in France (FR), it responds in French, uses EUR, and trusts domains like lemonde.fr.
· If the user is in the US, it responds in English, uses USD, and trusts domains like nytimes.com.
· If the country is not in the list, it falls back to a Global Market (English + USD + global sources).

⚙️ Engines (5 Agents Pipeline)

1. Tavily Scout: Scans the web for 10 live sources (passed with the user's country code).
2. Trust Ranker: Scores sources out of 100 based on Domain Authority, Recency, Citations, and Keyword Overlap (using the detected country's trusted domains list).
3. Thesis Builder (Qwen3-235B): Builds a logical thesis in the detected language.
4. Risk Checker: Analyzes price variance (in local currency) and detects low-trust sources.
5. Report Weaver: Generates the final localized report and a D3.js "Spider Viz" network graph.

🔌 API Usage

Endpoint: https://mido-deepsearch.midoaistore.workers.dev/

Run a Search (POST)

POST /
{
"query": "Best laptop for programming under $1000",
"visitor_id": "unique_user_id_here",
"skill": "deep_search",
"license_key": "optional_gumroad_license"
}

View Spider Viz (GET)

If the response contains a spider_viz URL, open it to see the interactive D3.js network graph.

Check Stats (GET)

GET /stats returns live counters and detected configuration.

📊 Output Format

{
"success": true,
"deep_answer": "Full markdown report in the detected language...",
"top_sources": [ { "title": "...", "url": "...", "score": 0.92 } ],
"detected_country": "France",
"detected_currency": "EUR",
"detected_language": "fr-FR",
"spider_viz": "https://.../spider?q=..."
}

🛒 Monetization

· Free trial: 1 per visitor (server-protected).
· Unlimited: Lifetime license via Gumroad for $6.
