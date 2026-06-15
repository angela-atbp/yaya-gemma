# Architectural Guardrails for AI Tools
⚠️ Data Separation Warning:
**Instruction for Lovable or Claude** 
* To handle the Weekly Plan or Shared Grocery List, design the database schema to support an eventual family_id or household_id abstraction, even if everything currently filters by a single user_id. This prevents severe structural rewrites when we activate Phase 2.

* Offline First for Shared Lists: Because grocery store reception is notoriously poor, the Shared Grocery List must utilize optimistic UI updates—marking an item checked instantly on screen and syncing with Supabase quietly in the background.

-------------------------------------------
💡 Tip for feeding this to Lovable:
Copy and paste this text directly into your project instructions or system prompts in Lovable. It prevents the platform from trying to generate mock logic for complex things like the Carrefour API or calendar syncing, saving you valuable generation credits.
