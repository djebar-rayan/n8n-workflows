# Customer Support RAG Agent

## Use Case
An AI customer-support assistant for the fictional Aquapure water-purification company. Every minute the workflow polls Gmail for new messages, extracts the sender's email, and decides whether the question is about an order (looked up in the Orders Sheet by email) or about products / services (looked up in the Supabase vector store, populated from PDFs in Google Drive). The Agent generates a fully-formatted Gmail draft reply with strict status-consistency rules between financial status and shipping status.

## Tools & Integrations
- Gmail Trigger (poll every minute) + Gmail (create draft)
- Set node (`Prepare Data`) for session ID and email extraction
- LangChain Agent on OpenAI `gpt-4.1-mini`
- Postgres Chat Memory (per-session conversation memory)
- Supabase Vector Store (`documents` table) with OpenAI Embeddings — knowledge base retrieval
- Google Sheets Tool (`Orders Sheet`) — order lookup by email
- Google Drive + Default Data Loader (PDF) + Supabase Vector Store (insert) — for ingesting source documents into the vector DB
- Structured Output Parser (`subject` / `message` JSON)

## Setup Instructions
1. In n8n, choose **Import from File** and upload `workflow.json` from this folder.
2. Configure credentials: **Gmail OAuth2**, **OpenAI API**, **Supabase**, **Postgres**, **Google Drive OAuth2**, **Google Sheets OAuth2**.
3. Replace the example identifiers:
   - The Google Drive `fileId` on `Download file` (currently a sample `pdf entreprise test.pdf`).
   - The spreadsheet `documentId` and `sheetName` on `Orders Sheet` so they point at your own orders sheet (the lookup uses the `Email` column; preserve the existing column headers — `ID de commande`, `Statut financier`, `Statut d'expedition`, etc. — or update both the sheet and the keyword-mapping section of the AI system message together).
4. Run the **Drive → Vector Database Ingestion** branch manually once to seed the Supabase `documents` table from your reference PDF.
5. Activate the main workflow.

## Architecture
![Workflow Architecture](architecture.png)

## Author
Rayan DJEBAR
