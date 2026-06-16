# 🍳 Recipe PWA (Validation Engine)
A mobile-first, high-utility Progressive Web App (PWA) designed for busy families to map out weekly meal plans, collaborate on shared grocery lists, and track pantry inventory seamlessly.Built using Vite + React + Tailwind CSS on the frontend, orchestrated via Lovable, and backed by Supabase (PostgreSQL).

# 🏗️ Repository Architecture
This repository uses a structured documentation layout alongside the codebase to ensure our development process, AI knowledge base, and product guardrails remain entirely synchronized.Plaintextyour-project-repo/

```text
your-project-repo/
│
├── .github/------------------------- # GitHub Actions, workflows, and issue templates
│
├── src/----------------------------- # THE CODEBASE (Mobile-First UI Layout)
│   ├── components/------------------ # Shared UI elements (Cards, Inputs, Modals)
│   ├── hooks/----------------------- # React hooks (pantry matching, optimistic sync)
│   └── supabase/-------------------- # DB migrations, schemas, and RLS policies
|
├── docs/---------------------------- # THE KNOWLEDGE BASE (Project Source of Truth)
│   ├── knowledge-base/-------------- # High-level product alignment & constraints
│   │   ├── ai-guardrails.md--------- # Best practices for prompting, context loading, and interacting with AI tools
│   │   ├── product-dna.md----------- # Operational constraints, feature matrix, and phased launch roadmap
│   │   └── why-we-exists.md--------- # Core value proposition, user problem statement, and long-term product vision
|   |
│   └── glossary.md ----------------- # list of terms and definition
|
├── app/----------------------------- # Yaya Gemma's App Feature UI/UX esign and Value Proposition
│   ├── pages/----------------------- # Client-Side (The Frontend / UI)
│   │   ├── home.md
│   │   ├── my-week.md
│   │   ├── recipes.md
│   │   ├── grocery-list.md
│   │   ├── favorites.md
│   │   └── profile.md
│   │
│   └── data-model/------------------ # Database architecture & type definitions
│       └── data-model.md------------ # Tables, constraints, and optimization indexes
|
├── function/------------------------ # Yaya Gemma's App Feature UI/UX esign and Value Proposition
│   ├── features/-------------------- # Client-Side (The Frontend / UI)
│   │   ├── week-planner.md
│   │   ├── generate-recipe.md
│   │   ├── scan-to-recipe.md
│   │   ├── photo-to-recipe.md
│   │   ├── week-recipe.md
│   │   ├── add-to-grocery.md
│   │   ├── smart-substitute.md
│   │   └── share-grocery.md
│   │
│   └── data-model/------------------ # Database architecture & type definitions
│       └── data-model.md------------ # Tables, constraints, and optimization indexes
|
├── data-layer/---------------------- # Database architecture & type definitions
│   
├── ai-chats/------------------------ # Preserved Loavble/Claude/LLM raw outputs and prompts
│   └── 2026-06-matching-logic.md
│   
├── marketing/----------------------- # Copywriting, pricing strategy, launch notes
│   ├── micro-influencers/----------- # Conversation logs with instagram microinfluencers
│   └── tier-pricing.md
│
└── README.md------------------------ # This file (Project overview & developer map)

```


# 🚀 Local Development Setup 
Prerequisites Node.js (v18 or higher)Supabase CLI (for database schema management)

Step 1: Clone and Install
Bashgit clone https://github.com/your-username/your-project-repo.git
cd your-project-repo
npm install

Step 2: Environment VariablesCreate a .env.local file in the root directory:PlaintextVITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_public_key
Step 3: Run the Local EngineBashnpm run dev
Open http://localhost:5173 with your browser's inspect tool toggled to a mobile viewport layout.💡 AI Prompting Tip:Before starting a new feature build with Claude or Lovable, upload docs/context/product-dna.md and docs/data-model/data-model.md as context files. This guarantees the AI respects our database structures and roadmap bounds without generating out-of-scope code.

# Product DNA & Core Constraints
This document establishes the foundational rules, architectural philosophies, and design guardrails for the Recipe PWA. Every feature implementation and AI prompt must respect these rules.
