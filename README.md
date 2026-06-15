# 🍳 Recipe PWA (Validation Engine)
A mobile-first, high-utility Progressive Web App (PWA) designed for busy families to map out weekly meal plans, collaborate on shared grocery lists, and track pantry inventory seamlessly.Built using Vite + React + Tailwind CSS on the frontend, orchestrated via Lovable, and backed by Supabase (PostgreSQL).

# 🏗️ Repository Architecture
This repository uses a structured documentation layout alongside the codebase to ensure our development process, AI knowledge base, and product guardrails remain entirely synchronized.Plaintextyour-project-repo/

```text
your-project-repo/
│
├── .github/------------------ # GitHub Actions, workflows, and issue templates
│
├── src/---------------------- # THE CODEBASE (Mobile-First UI Layout)
│   ├── components/----------- # Shared UI elements (Cards, Inputs, Modals)
│   ├── hooks/---------------- # React hooks (pantry matching, optimistic sync)
│   └── supabase/------------- # DB migrations, schemas, and RLS policies
│
├── docs/--------------------- # THE KNOWLEDGE BASE (Project Source of Truth)
│   ├── context/-------------- # High-level product alignment & constraints
│   │   ├── ai-guardrails/---- # Executive strategy, roadmap, and design guardrails
│   │   ├── product-dna.md---- # Executive strategy, roadmap, and design guardrails
│   │   └── why-we-exists.md-- # Executive strategy, roadmap, and design guardrails
│   │
│   ├── data-model/----------- # Database architecture & type definitions
│   │   └── data-model.md----- # Tables, constraints, and optimization indexes
│   │
│   ├── ai-chats/------------- # Preserved Claude/LLM raw outputs and prompts
│   │   └── 2026-06-matching-logic.md
│   │
│   └── marketing/------------ # Copywriting, pricing strategy, launch notes
│       └── tier-pricing.md
│
└── README.md----------------- # This file (Project overview & developer map)
```

# 🚦 Feature Roadmap & Current Status
To maximize velocity during our validation stage, features are strictly bifurcated. Do not write backend scaling logic for Phase 2 items.

## 🟢 Phase 1: Fully Implemented (Active Production)
* Weekly Meal Planner: Full interactive calendar view letting users seamlessly distribute recipes across specific days of the week.
* Shared Grocery List: Real-time, collaborative, synchronized checklist allowing multiple users to cross off items during shopping trips.  * Pantry Receipt Scanner: Optical/camera-driven intake flow allowing users to snap pictures of physical receipts or items to automatically parse and populate their digital pantry inventory.

## 🟡 Phase 2: Deferred Pipeline (UI Placeholders Only)
Implement these exclusively as visual entry points, disabled buttons, settings toggles, or premium "Upgrade to Unlock" prompts:  Family Shared Accounts: Base UI profile switchers (deferred unified household_id sharing).  Budget Settings: Maximum weekly spend caps input fields (deferred real-time automated pricing engine).  Food Preference & Waste: Static filter elements (deferred predictive machine learning spoilage vectors).  External Integrations: Calendar Sync Tool UI placeholders and Supermarket API (Carrefour) cart checkout buttons.  🪙 Monetization FrameworkThe platform operates on a structural Freemium / Full Access bifurcated tier system:  Freemium Tier (€0/Month): Core features active. Will eventually charge a €0.50 transaction-driven convenience fee per order checkout once grocery API integrations are complete. (Status: DEFERRED).  Full Access Tier (€1.99/Month): Flat-rate subscription unlocking total utility, advanced family syncing, and removing all transaction processing fees. (Status: ACTIVE).  🛠️ Critical Guardrails for Developers & AI ToolsWhen feeding tasks or generating components using Claude or Lovable, you must adhere to these architectural laws:The Mobile-First Mandate: The user interface must be designed exclusively for mobile screen widths (maximum 430px breakpoint). Do not spend engineering cycles optimizing for wide-screen desktop viewports.  The Household Abstraction: When writing schemas for the Weekly Plan or Shared Grocery List, always design tables to map cleanly to a future household_id or family_id grouping mechanism, even if filtering by a single user_id today.  Network Resiliency & Optimistic UI: Grocery stores are dead zones. The Shared Grocery List must update instantly on screen locally and queue background synchronization payloads to Supabase quietly upon connection recovery.  
# 🚀 Local Development SetupPrerequisitesNode.js (v18 or higher)Supabase CLI (for database schema management)Step 1: Clone and InstallBashgit clone https://github.com/your-username/your-project-repo.git
cd your-project-repo
npm install
Step 2: Environment VariablesCreate a .env.local file in the root directory:PlaintextVITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_public_key
Step 3: Run the Local EngineBashnpm run dev
Open http://localhost:5173 with your browser's inspect tool toggled to a mobile viewport layout.💡 AI Prompting Tip:Before starting a new feature build with Claude or Lovable, upload docs/context/product-dna.md and docs/data-model/data-model.md as context files. This guarantees the AI respects our database structures and roadmap bounds without generating out-of-scope code.

# Product DNA & Core Constraints
This document establishes the foundational rules, architectural philosophies, and design guardrails for the Recipe PWA. Every feature implementation and AI prompt must respect these rules.
