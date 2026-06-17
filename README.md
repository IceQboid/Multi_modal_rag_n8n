
**Purpose:** Multi-modal RAG (Retrieval Augmented Generation) system for engineering documents

**Key Features:**
- Fetches PDFs from S3 bucket (zamil-manuals, engineering documents [scanned PDFs, Digital PDFs, etc.)
- Uses Mistral OCR to extract text and images
- Applies custom engineering document annotations (AISC codes, section IDs, technical summaries)
- Uploads images to Supabase Storage
- Stores processed content in Supabase Vector Store
- Provides Q&A interface using OpenAI GPT-4.1-mini

**Flow:**
1. Manual trigger → Fetches file list from S3
2. Checks record_manager in Supabase to find unprocessed files
3. Uses Mistral OCR with JSON schema for engineering annotations
4. Separates images from text, uploads images to Supabase
5. Replaces markdown image placeholders with hosted URLs + annotations
6. Chunks text and embeds via OpenAI
7. Stores in Supabase Vector Store
8. Updates record_manager to track processed files
9. Can be triggered by another workflow for Q&A

**Stack:**
- Mistral Cloud 
- Supabase 
- OpenAI

---
