# n8n Workflows Portfolio

**Author: Rayan DJEBAR**

A curated collection of nine production-grade n8n workflows covering AI agents, e-commerce automation, RAG pipelines, multi-channel content generation, and operational tooling. Every workflow ships as a self-contained folder with a translated `workflow.json` ready to import into n8n, a focused README, and an architecture diagram.

## Workflows

| # | Workflow | What it does |
| - | -------- | ------------ |
| 1 | [ecommerce-ad-creation-agent](ecommerce-ad-creation-agent/) | Turns a product photo and a marketing intent into a finished ad creative — static image (Nano Banana Pro) or 8-second UGC video (Veo 3.1 Fast). |
| 2 | [customer-support-rag-agent](customer-support-rag-agent/) | Inbound-email RAG agent: answers product questions from a Supabase vector store and order questions from a Google Sheets order book, then drafts a Gmail reply. |
| 3 | [hotel-voice-agent](hotel-voice-agent/) | Backend for an ElevenLabs voice assistant that answers hotel queries, checks Google Calendar availability, books rooms, and emails confirmations. |
| 4 | [ai-newsletter-automation](ai-newsletter-automation/) | Daily AI-news digest: aggregates six RSS feeds, summarises with GPT-4.1-mini, formats a styled HTML email, and ships it via Gmail at 22:00. |
| 5 | [dropshipping-product-researcher](dropshipping-product-researcher/) | Amazon → TikTok product research pipeline: scrapes candidates, ranks the top 5, validates each against TikTok engagement metrics, logs winners to Google Sheets. |
| 6 | [retail-catalog-analyzer](retail-catalog-analyzer/) | Promotional-catalog PDF analyser: GPT-4o Vision extracts non-food products, computes discount %, and writes the Top 5 resale opportunities to Google Sheets. |
| 7 | [telegram-invoice-generator](telegram-invoice-generator/) | Telegram bot that turns a text or voice instruction into a branded PDF invoice through APITemplate.io and replies with the download link. |
| 8 | [linkedin-job-scraper](linkedin-job-scraper/) | Form-driven LinkedIn job hunter: logs the search to Google Sheets, fires an Apify scraper, filters by location, and emails the candidate a styled HTML digest. |
| 9 | [whatsapp-ai-assistant](whatsapp-ai-assistant/) | WhatsApp bot that answers text directly and replies to voice notes with a transcribed → AI-answered → text-to-speech audio response. |

## Importing a workflow

1. Open n8n and choose **Import from File**.
2. Upload the `workflow.json` from the workflow's folder.
3. Configure the required credentials listed in that workflow's README.
4. Replace any sample identifiers (Google Drive folder IDs, Sheets `documentId` / `sheetName`, Telegram `phoneNumberId`, etc.) with your own.
5. Activate.

## Repository layout

```
n8n-workflows/
├── README.md                              ← you are here
├── CLAUDE.md                              ← guidance for AI coding assistants
├── ecommerce-ad-creation-agent/
│   ├── workflow.json
│   ├── README.md
│   └── architecture.png                   ← (add your own diagram)
├── customer-support-rag-agent/
├── hotel-voice-agent/
├── ai-newsletter-automation/
├── dropshipping-product-researcher/
├── retail-catalog-analyzer/
├── telegram-invoice-generator/
├── linkedin-job-scraper/
└── whatsapp-ai-assistant/
```
