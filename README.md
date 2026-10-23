# 🌍 Mido DeepSearch Agent (V6.0 Global Edition)

**Deep Research in 60 Seconds.** 
Mido DeepSearch is an advanced AI agent that scans 10 live sources, ranks them with a Trust Score, and generates a localized, structured report. It auto-detects your country, language, and currency to give you the exact market context you need.

[![Live Demo](https://img.shields.io/badge/Live_Demo-Try_it_Free-success?style=for-the-badge&logo=github)](https://midoaistore.github.io/mido-landing/)
[![Buy on Gumroad](https://img.shields.io/badge/Buy_on_Gumroad-$6-blue?style=for-the-badge&logo=gumroad)](https://midoaistore.gumroad.com/l/dtqpvka)

---

## 🚀 Why Mido DeepSearch?

Traditional search engines give you a list of links. Mido DeepSearch gives you **verified knowledge**. 

*   **🌐 Global by Design:** It detects the user's country (via `CF-IPCountry`) and adapts automatically.
    *   *Egypt (EG):* Egyptian Arabic + EGP + `gov.eg` sources.
    *   *France (FR):* French + EUR + `lemonde.fr` sources.
    *   *USA (US):* English + USD + `nytimes.com` sources.
    *   *And 20+ other countries...*
*   **⚡ Lightning Fast:** Saves 96% of research time (60 seconds vs. 25 minutes of manual search).
*   **🛡️ Trust Score:** Ranks sources based on Domain Authority (40%), Recency (30%), Citations (20%), and Keyword Overlap (10%).
*   **🕸️ Spider Viz:** Generates an interactive D3.js network graph to visualize how sources connect.
*   **🔒 Server-Side Protection:** Includes Rate Limiting, IP caps, and Trial management via Cloudflare KV.

---

## ⚙️ How It Works (5-Agent Pipeline)

1.  **Tavily Scout:** Scans the web for 10 live sources (using the detected country code).
2.  **Trust Ranker:** Scores sources out of 100 based on the detected country's trusted domains.
3.  **Thesis Builder (Qwen3-235B):** Builds a logical thesis in the detected language.
4.  **Risk Checker:** Analyzes price variance (in local currency) and flags low-trust sources.
5.  **Report Weaver:** Generates the final report and the Spider Viz network graph.

---

## 🛠️ Tech Stack

*   **Backend:** Cloudflare Workers (Serverless)
*   **Search Engine:** Tavily API (Advanced Search)
*   **LLM:** Qwen3-235B via Nebius AI Studio
*   **Database:** Cloudflare KV (for stats, trials, and caching)
*   **Frontend:** HTML5, Tailwind CSS, Vanilla JS
*   **Viz:** D3.js (Force-directed graph)
*   **Payments:** Gumroad (License verification)

---

## 💻 Try the API (Direct Call)

You can test the engine directly via `curl`:

```bash
curl -X POST https://mido-deepsearch.midoaistore.workers.dev/ \
-H "Content-Type: application/json" \
-d '{
  "query": "Best laptop for programming under $1500",
  "visitor_id": "test_user_123",
  "skill": "deep_search"
}'**Note:** The first call is free. Subsequent calls require a valid Gumroad license key. 

---

## 📦 What's Inside the Package?

When you purchase the lifetime license for **$6**, you get:
*   The complete `worker.js` source code.
*   The `index.html` landing page.
*   The `mido-search.py` CLI script.
*   The `SKILL.md` configuration for AI Agents.
*   Detailed setup guide for Cloudflare and GitHub.

👉 **[Get Lifetime Access Here](https://midoaistore.gumroad.com/l/dtqpvka)**

---

## 🤝 Contributing

We welcome contributions! If you find a bug or want to add a new country to the `COUNTRY_CONFIG`, feel free to open a Pull Request.

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---
*Built with ❤️ in Cairo, Egypt.*
