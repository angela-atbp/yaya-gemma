# 1. Product Vision & Phase Strategy
Our app is a high-utility, low-friction Recipe PWA engineered for busy families who want to plan meals, manage grocery budgets, and reduce food waste.

* **The "Mobile-First" Mandate**
  * **The Goal:** We are launching as a PWA (Progressive Web App) to rapidly test and validate Product-Market Fit (PMF). Once validated, we will migrate to a native app.

  * **The Guardrail:** The UI/UX must be strictly optimized for mobile device screen widths (maximum 430px). Every view, card, and interaction must look, feel, and perform like a native iOS/Android application. Do not spend time optimizing for wide desktop interfaces.

* **Development Stage: Lovable Era**
We are building exclusively through Lovable during this validation phase to maximize speed-to-market.

* **Code Quality Philosophy:**
Prioritize rapid UI component assembly and clean integrations. Do not over-engineer scalable backends until we officially enter the "Scale Stage."

## Monetization & Tier Constraints
The app follows a dual Freemium / Full Access pricing model.

* **Freemium Tier ($0/month):**
  Gives users access to base features. In the future, this tier will be monetized via a "Convenience Fee" fee (€0.50 per order - Subject to change) when users check out directly via local supermarket integrations (e.g., Carrefour).

**IMPORTANT** Current Implementation Status: **DEFERRED**. Do not implement checkout fees or cart processing logic until API integrations are complete.

* **Full Access Tier**
  €1.99/month - Subject to change: Removes all transactional friction and unlocks advanced premium features (Family accounts, predictive waste tracking).

# Feature Status Matrix (The Build Roadmap)
To maintain absolute clarity on what should be actively coded versus what is simply text/UI placeholders, use this matrix:

## Phase 1: Currently Implemented (Protect & Optimize)
  * **Weekly Meal Planner:** Calendar layout allowing users to map recipes to days of the week.
  * **Shared Grocery List:** Real-time collaborative checklist for shopping trips.
  * **Pantry Scanner:** Optical/camera tracking to scan receipts or items to automatically populate the user's digital pantry inventory.
  * **Food Preference & Waste**
    * Standard static filters (e.g., Veg, Vegan).

## Phase 2: Planned / Not Yet Implemented (UI Placeholders Only)
*If building these features in Lovable right now, only create the UI buttons, settings toggles, or premium "Coming Soon" screens. Do not build backend infrastructure for them yet.*
  * **Family Shared Account**
    * Profile switcher UI / "Invite Family" button.
    * Unified `household_id` sharing with multi-device background sync. 
  * **Budget Setting**
    * Maximum weekly spend caps input field.
    * Real-time automated pricing engine pulling item costs.
  * **Food Preference & Waste**
    * Predictive machine learning to calculate item spoilage vectors.
  * **Calendar Sync Tool**
    * View-only internal interactive app grid.
    * Bi-directional API syncing with Apple Calendar, Google Calendar, etc.
  * **Supermarket API Bridge**
    * Manual inventory adjustment fields.
    * **Carrefour/Grocery Store API**: Automatic receipt retrieval and automated checkout cart generation.

  ## 4. Architectural Guardrails for AI & Lovable

## The "Household" Relational Abstraction
* **Critical Database Rule:** When prompting Claude or Lovable to manipulate schemas for the `Weekly Plan` or `Shared Grocery List`, always design the tables to inherit or map cleanly to a potential `household_id` or `family_id` grouping mechanism, even if the query filters by an individual `user_id` today. This prevents major structural rewrites when Phase 2 goes active.

## Network Resiliency & Optimistic UI
* **IMPORTANT:** Grocery stores and home kitchens are notorious dead-zones for mobile data.*
  * The **Shared Grocery List** must operate with an *Optimistic UI architecture*. Items marked as checked must update instantly on screen locally, queueing the synchronization payloads to Supabase to run quietly in the background upon connection recovery. 
