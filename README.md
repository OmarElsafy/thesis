# 

> A centralized intelligence platform for crypto research - aggregating analyst content, podcasts, and research across all platforms

## Overview

THESIS is the "Spotify for Crypto Intelligence" - a discovery engine that aggregates, tags, and recommends research content from analysts, VCs, and thought leaders across the crypto ecosystem.

**The Problem:** Alpha is scattered across 47 tabs. Twitter threads, Substack posts, podcast episodes, VC blogs - all fragmented.

**The Solution:** One feed. AI-curated. Personalized recommendations based on your portfolio and reading history.

## Core Features (MVP)

### 1. Multi-Source Ingestion
- **Twitter/X:** Track top 500 analysts via curated lists
- **Substack/Medium:** RSS feeds from thought leaders
- **VC Blogs:** Paradigm, a16z, Placeholder, Mechanism Capital
- **Podcasts:** Bankless, Unchained, Empire (future phase)

### 2. AI-Powered Tagging
Every piece of content is automatically tagged with:
- **Entities:** `$SOL`, `EigenLayer`, `Coinbase`
- **Concepts:** `#Restaking`, `#Modular`, `#ZK-Rollups`
- **Sentiment:** Bullish, Bearish, Neutral
- **Format:** Deep Dive, News Update, Tutorial

### 3. Analyst Profiles
- Auto-generated profiles for top analysts
- Claimable verification system
- Track record and "Thesis Accuracy Score"
- Tier system (Verified Gods, Contributors, Community)

### 4. Discovery Feed
- Messari-style dense list view
- Filter by narrative, analyst, or asset
- "Smart Preview" on hover
- Unified content cards (Tweet next to PDF next to Podcast)

## Tech Stack

| Layer | Tool | Purpose |
|-------|------|--------|
| **Frontend** | Next.js + Shadcn UI | Fast, professional UI |
| **Backend** | Supabase | Postgres + Vector DB |
| **Scrapers** | Firecrawl + Apify | VC sites + Twitter |
| **AI** | OpenAI GPT-4o-mini | Tagging + Summarization |
| **Hosting** | Vercel + Railway | Frontend + Background jobs |

**Total Cost:** ~$135/month

## Project Structure

```
thesis/
├── apps/
│   ├── web/              # Next.js frontend
│   └── jobs/             # Python scrapers
├── packages/
│   ├── database/         # Supabase schema
│   ├── ui/               # Shared components
│   └── types/            # TypeScript types
├── docs/
│   ├── ARCHITECTURE.md   # System design
│   ├── API.md            # API documentation
│   └── ROADMAP.md        # Development roadmap
└── README.md
```

## Database Schema

```sql
-- Core Tables
analysts (
  id, name, twitter_handle, tier, 
  accuracy_score, profile_claimed, bio
)

content (
  id, title, url, source_type, 
  published_at, analyst_id, raw_text,
  summary_text, read_time_minutes
)

tags (
  id, content_id, tag_type, tag_value
)

embeddings (
  id, content_id, embedding_vector
)
```

## Development Roadmap

### Week 1: Foundation
- [x] Set up GitHub repo
- [ ] Initialize Next.js + Supabase
- [ ] Build basic Content Card component
- [ ] Create database schema

### Week 2: Ingestion Pipeline
- [ ] RSS scraper for Substack (50 feeds)
- [ ] Apify integration for Twitter (100 accounts)
- [ ] Firecrawl for VC blogs
- [ ] Cron job (runs hourly)

### Week 3: AI Layer
- [ ] GPT-4o-mini tagging script
- [ ] Auto-summary generation
- [ ] Entity extraction ($TOKENS)
- [ ] Sentiment analysis

### Week 4: UI Polish
- [ ] Main feed with filtering
- [ ] Analyst profile pages
- [ ] Search functionality
- [ ] Mobile responsive

## Getting Started

```bash
# Clone the repo
git clone https://github.com/OmarElsafy/thesis.git
cd thesis

# Install dependencies (coming soon)
npm install

# Set up environment variables
cp .env.example .env.local

# Run development server
npm run dev
```

## Launch Strategy

**Soft Launch (Week 5):**
- Share with 20 crypto friends
- Post on Twitter: "I built a tool that reads 500 newsletters for me"
- Collect early feedback

**Public Launch (Week 6):**
- r/CryptoCurrency, Farcaster, Twitter
- DM top 20 analysts to claim profiles
- Write launch post on Substack

## Value Proposition

> "There are ~8,000 professional analysts in crypto managing the intellectual capital for a $3 Trillion industry. Currently, their track record is scattered across Twitter threads and PDF attachments. We are building the ledger for their reputation."

## Contributing

This is an open-source project. Contributions welcome!

## License

MIT License - see [LICENSE](LICENSE) for details

---

**Built by [@OmarElsafy](https://github.com/OmarElsafy)**
