# Objective
This page aims to tackle mental load, double-buying, and food waste for a busy parent.  
Parents don't want a second job as a data entry clerk. The app needs to do 90% of the thinking, tracking, and predicting for them.
The pantry page promises a frictionless pantry inventory management.

Here are the non-negotiable features and functionalities required to deliver on that promise:

**1. Zero-Friction Ingestion (No Manual Typing)**
*The biggest reason inventory apps fail is that manual entry feels like a chore. To relieve the mental load, getting food into the app must take seconds.* 

  * **Smart Receipt Scanning (OCR):** The user takes a quick photo of their shelves/fridge or their grocery receipt (from Carrefour, Leclerc, etc.), and the app instantly extracts the items, quantities, and prices.

  * **Barcode Scanner + Voice Log:** A lightning-fast barcode scanner for stocking shelves, or a quick voice-command feature ("Hey app, I just added three cartons of oat milk").

  * **Direct Store Integration:** Syncing directly with grocery loyalty programs or online shopping accounts so purchase histories import automatically.

**2. Anti-Double-Buying Safeguards**
*This feature turns the app into a real-time copilot while the user is away from home or planning the week.*

  * **The "Do We Have This?" Quick-Search:** A prominent, global search bar right at the top of the home screen. In two taps, a user standing in an aisle can verify: "Yes, we have an unopened jar of mayo in the back left of the bottom shelf."

  * **Geofenced Shopping Mode:** When the phone detects they’ve walked into a grocery store, it sends a push notification or opens a specific "At the Store" view showing a live snapshot of what is currently low or out of stock.

  * Collaborative Real-Time Sync: If a partner or teenager uses the last of the milk and logs it, it updates instantly across all devices so the primary shopper doesn't buy a duplicate.

**3. Passive Waste Prevention (Predictive Analytics)**
*Instead of forcing the user to look at lists of dates, the app should bubble up urgency automatically.*

  * **The "Eat Me First" Smart Zone:** A dedicated, visual section on the home screen that ranks items by expiration urgency (e.g., dynamic color coding: Red = Eat within 48h, Orange = Eat this week).

  * **Predictive Shelf-Life (AI Estimates):** Fresh produce often doesn't have a barcode or an expiration date. The app should apply standard shelf-life logic based on the purchase date (e.g., "Strawberries bought 4 days ago — likely need using today").

  * **Smart Waste Reminders:** Subtle, proactive push notifications that double as dinner inspiration: "Your spinach and chicken breasts are expiring in 2 days. Tap to see a 15-minute recipe that uses both."

**4. The "Inverse" Recipe Engine**
*Traditional recipe apps ask what you want to make, then give you a shopping list of things you don't have. This feature reverses that dynamic.*

  * **Pantry-First Match Cooking:** A search engine that filters recipes based strictly on what is already in the kitchen, prioritized by items closest to spoiling.

  * **The "Missing Ingredient" Factor:** Recipes labeled clearly by how many ingredients are missing (e.g., "You have 4 of 5 ingredients for this Curry — you just need lime"), allowing the user to make smart substitutions or minimal purchases.

**5. Automated "Safety Stock" Replenishment**
*Moms shouldn't have to check if they are running low on household staples; the app should track the baseline.*

  * **Dynamic Low-Stock Thresholds:** Users can set a minimum safety level for core items (e.g., "Always keep 2 boxes of pasta").

# The 3-Step Mobile User Journey
* 1.Fast Capture & Background Processing:Takes ~5 seconds.
  The user taps a hero button labeled "Photo Pantry" directly from the screen.
  A camera overlay appears with an auto-capture frame (like a banking app document scanner).Once the photo is taken, the app displays a success animation and immediately hands control back to the user. The heavy lifting of text extraction and item matching happens asynchronously in the background so the user can keep unpacking their bags.
* 2.Smart Merging & Batch Grouping:Background automation.
  In the background, the AI parses the raw receipt lines (e.g., "CHIPOLATA X6 BIO 4.50€"), matches it to a known grocery database category (e.g., Meats > Pork), and references standard food safety data to assign a predicted shelf life (e.g., Fresh pork: 3 days in fridge).
  Items are automatically batched into location zones: Fridge, Freezer, or Pantry.

* 3.The:Takes ~30 seconds, user-facing.A subtle push notification appears: "Receipt parsed! 12 items added. Tap to verify 2 uncertainties."Instead of showing a giant, intimidating spreadsheet of data, the review screen only highlights items where the AI confidence score fell below a certain threshold or where a price/quantity looks irregular.
  
* 4.One-Tap Approval & Log:Takes ~2 seconds.The user scans the beautifully organized summary grouped by storage zone. They tap a single, large "Confirm & Log to Pantry" button. The items instantly populate their active inventory, and the expiring items are pushed straight to the top of their homepage "Eat First" feed.

# Designing the UX for OCR Correction
To prevent typing fatigue, you must treat every correction as a selection game rather than a data entry task.

* 1. The "Inline Split" Review Screen
When a user opens the review card, they see a clean list. Unclear items are flagged with a soft color indicator. Tapping a flagged item opens an inline expansion showing a high-contrast cropped snippet of the original physical receipt photo directly above the interpreted text. This saves the user from having to fish the paper receipt out of the trash to check what it actually said.

* 2. Auto-Suggest Instead of Text Inputs
If the scanner reads "L4IT D'4VOIN" instead of "Lait d'avoine", don't open an empty text box. Present 3 smart, pill-shaped buttons based on fuzzy matching:

[ Lait d'avoine ]

[ Lait d'amande ]

[ Lait demi-écrémé ]

The user simply taps the correct pill, and the error is resolved in one touch.

* 3. Quick-Swipe Quantity & Trash Actions
If an item was double-scanned or shouldn't be tracked (like a reusable shopping bag or a magazine), a simple swipe-to-delete removes it. Quantities should use giant [-] and [+] hit targets so they can be adjusted rapidly with a thumb.

# How Smart Shelf-Life Assignment Works Behind the Scenes

Assigning expiry dates automatically requires merging different layers of logic so parents don't have to think about complex food safety guidelines while unpacking their groceries.

The backend classification engine routes every scanned line item through one of three automated processing strategies based on its product profile:

| Item Type | Extraction Logic | Shelf-Life Assignment Strategy |
| :--- | :--- | :--- |
| **Fresh Produce / Loose Items** | Lacks standard packaging, barcodes, or expiration dates on printed retail receipts. | The application applies a **standardized freshness countdown** starting from the exact timestamp of purchase. These are calculated from standard regional food safety guidelines (e.g., *Strawberries = 4 days*, *Avocado = 5 days*). |
| **Barcoded Packaged Items** | Receipt text strings or scanned EAN codes map directly to a known global product identifier database. | The engine extracts the **average manufacturer shelf-life window** (e.g., *Danone yogurt generally carries a 21-day buffer from production*). The user interface highlights this as an estimate, allowing a parent to quickly adjust it if a physical date printed on the lid differs. |
| **Ambient Staples** | Item strings map to non-perishable categories such as flour, pasta, canned goods, or rice. | Automatically flagged as **Long Life** or assigned a baseline 180-day buffer. To heavily reduce mental friction and visual dashboard clutter, these items are completely omitted from daily "Urgent Expiry" lists, only surfacing if they remain stagnant in the inventory for months. |

---

# Maximizing App Retention: The "Aha!" Moment
The moment a mom finishes verifying a receipt, the app should immediately close the loop on value.

Instead of just showing a static confirmation screen saying "Items Saved", the success screen should immediately display a dynamic breakdown of the value generated by that single scan:
```
Receipt Processed! 🎉

8 Fresh items protected with auto-expiration alerts.

2 Double-buys successfully prevented at checkout.

3 New dinner recipes unlocked using what you just bought.
```

This transforms a routine data-logging task into an immediate feeling of relief and control over the household budget.

To reliably transform chaotic, fragmented OCR text into a structured, production-ready JSON payload, your LLM system prompt needs to act as a rigorous Deterministic Data Pipeline. Because LLMs can be prone to hallucination or structural formatting errors, the prompt must enforce strict schema constraints, provide clear formatting heuristics, and mandate semantic mapping logic.

Here is the optimal system prompt structure, designed to minimize processing failures and maximize categorization accuracy.

# The Master LLM System Prompt Structure
```
### ROLE & OBJECTIVE
You are a highly precise, deterministic Data Extraction and Normalization Engine. Your sole purpose is to ingest messy, raw OCR text from supermarket receipts (primarily French/European retailers like Carrefour, E.Leclerc, Auchan, Monoprix) and convert it into a clean, structured JSON array of inventory items.

### SYSTEM CONSTRAINTS & OUTPUT FORMAT
- Output **ONLY** a valid JSON object. 
- Do **NOT** wrap the JSON in markdown blocks (e.g., do not use ```json ... ```).
- Do **NOT** include any conversational intro, outro, or explanatory prose.
- If a field cannot be confidently extracted or inferred, return `null` for that field.

### INPUT DATA DEFINITION
You will receive a string of raw text lines extracted via OCR. This text contains spelling errors, missing letters, truncated words, prices, quantities, and operational store codes.

### STRUCTURAL JSON SCHEMA
The output object must strictly follow this shape:
{
  "receipt_metadata": {
    "merchant_name": string or null,
    "purchase_date": "YYYY-MM-DD" or null,
    "total_amount_eur": float or null
  },
  "items": [
    {
      "raw_line": string,       // The original line text from the OCR input
      "clean_name": string,     // Normalized, human-readable product name in title case
      "quantity": integer,      // Default to 1 if not explicitly stated
      "unit_price_eur": float or null,
      "category": string,       // Must be one of the ALLOWED CATEGORIES listed below
      "storage_zone": string,   // Must be one of: "Fridge", "Freezer", "Pantry", "Non-Food"
      "estimated_shelf_life_days": integer or null // Expected days until expiry from purchase_date
    }
  ]
}

### DATA PROCESSING & INFERENCE RULES

1. **Text Cleansing & Fuzzy Matching:**
   - Strip out internal inventory prefixes, store numbers, VAT rates (e.g., "A", "B", "10%"), and promotional markers (e.g., "PROMO", "DRE").
   - Fix obvious OCR typos using culinary context (e.g., "L4IT D'4VOIN" -> "Lait d'avoine", "AV0CAT" -> "Avocat").
   - Expand abbreviations common to grocery receipts (e.g., "BIO" stays as "Bio", "X6" maps to quantity: 6, "CHOC" -> "Chocolat").

2. **Categorization Taxonomy (STRICT):**
   You must map the item to exactly one of these allowed categories: 
   `[Fruits & Vegetables, Meat & Seafood, Dairy & Eggs, Bakery & Pastry, Pantry Staples, Snacks & Sweets, Beverages, Frozen Foods, Household & Personal Care, Baby, Pet, Miscellaneous]`.

3. **Storage Zone Routing:**
   - "Fridge": Fresh meats, dairy, eggs, opened or fresh juices, specific delicate produce.
   - "Freezer": Anything explicitly marked as frozen ("surgelé").
   - "Pantry": Ambient staples, canned goods, rice, pasta, oil, UHT milk, snacks, intact root vegetables.
   - "Non-Food": Household cleanings, pet food, baby diapers, clothing.

4. **Predictive Shelf-Life Heuristics:**
   Calculate `estimated_shelf_life_days` starting from the `purchase_date`. Use standard food science baselines if the exact expiration date isn't on the receipt:
   - Fresh Red Meat / Poultry / Fresh Fish: 3 days.
   - Ground Meat / Chopped Steak: 2 days.
   - Berries, Strawberries, Soft Fruits: 4 days.
   - Hard Vegetables (Carrots, Potatoes, Onions): 30 days.
   - Pasteurized Milk / Yogurt: 14 days.
   - Eggs: 21 days.
   - Hard Cheese: 30 days.
   - Ambient Pantry Staples (Pasta, Rice, Canned goods): 180 days.
   - Non-Food Items: null.

### EXCLUSION CRITERIA
Do **NOT** include line items that are transactional adjustments, such as:
- Total lines, tax summaries, discount subtractions, loyalty points gained, or change returned.
- Reusable bag charges (e.g., "SAC CABAS") should be categorized as "Miscellaneous" with a "Non-Food" storage zone.

### CRITICAL ERROR HANDLING
- If the OCR input is entirely illegible or contains no food/retail items, return an empty array for "items": `{"receipt_metadata": null, "items": []}`.
```

Testing the model:
1. The Input: 
Imagine a receipt that got slightly crinkled in the grocery bag, causing typos, missing letters, and random character insertions during the text extraction phase:
```
E.LECLERC TALENCE
ST: 33400 MERCH: 482910
06/16/2026 11:42 CHK: 049
--------------------------
1  PACK LAIT DEMI UHT X6    4.95 A
2  FILET AV0CAT 1KG         2.99 A
1  CHIPOLATAS X6 BIO        5.40 A
3  YAOURT NAT.DANONE X4     3.15 A
-0.50e PROMO JALOUSIE       -0.50 A
1  STEAK HACHE VBF X2       4.20 A
1  ESPINARD FRAIS 500G      1.99 A
1  SAC CABAS R_UTIL         0.40 B
--------------------------
TOTAL A PAYER               22.58
TVA A 5.5%                  1.16
TVA B 20%                   0.08
```
2. The Output: Normalized, Categorized JSON Object
Following the strict deterministic rules, constraints, and shelf-life heuristics set out in the system prompt, the LLM converts that unstructured payload into this exact format:
```
{
  "receipt_metadata": {
    "merchant_name": "E.Leclerc",
    "purchase_date": "2026-06-16",
    "total_amount_eur": 22.58
  },
  "items": [
    {
      "raw_line": "1  PACK LAIT DEMI UHT X6    4.95 A",
      "clean_name": "Lait Demi-Écrémé UHT (Pack x6)",
      "quantity": 1,
      "unit_price_eur": 4.95,
      "category": "Dairy & Eggs",
      "storage_zone": "Pantry",
      "estimated_shelf_life_days": 180
    },
    {
      "raw_line": "2  FILET AV0CAT 1KG         2.99 A",
      "clean_name": "Filet D'avocats 1kg",
      "quantity": 2,
      "unit_price_eur": 2.99,
      "category": "Fruits & Vegetables",
      "storage_zone": "Pantry",
      "estimated_shelf_life_days": 5
    },
    {
      "raw_line": "1  CHIPOLATAS X6 BIO        5.40 A",
      "clean_name": "Chipolatas x6 Bio",
      "quantity": 1,
      "unit_price_eur": 5.40,
      "category": "Meat & Seafood",
      "storage_zone": "Fridge",
      "estimated_shelf_life_days": 3
    },
    {
      "raw_line": "3  YAOURT NAT.DANONE X4     3.15 A",
      "clean_name": "Yaourt Nature Danone (Pack x4)",
      "quantity": 3,
      "unit_price_eur": 3.15,
      "category": "Dairy & Eggs",
      "storage_zone": "Fridge",
      "estimated_shelf_life_days": 14
    },
    {
      "raw_line": "1  STEAK HACHE VBF X2       4.20 A",
      "clean_name": "Steak Haché VBF x2",
      "quantity": 1,
      "unit_price_eur": 4.20,
      "category": "Meat & Seafood",
      "storage_zone": "Fridge",
      "estimated_shelf_life_days": 2
    },
    {
      "raw_line": "1  ESPINARD FRAIS 500G      1.99 A",
      "clean_name": "Épinards Frais 500g",
      "quantity": 1,
      "unit_price_eur": 1.99,
      "category": "Fruits & Vegetables",
      "storage_zone": "Fridge",
      "estimated_shelf_life_days": 4
    },
    {
      "raw_line": "1  SAC CABAS R_UTIL         0.40 B",
      "clean_name": "Sac Cabas Réutilisable",
      "quantity": 1,
      "unit_price_eur": 0.40,
      "category": "Miscellaneous",
      "storage_zone": "Non-Food",
      "estimated_shelf_life_days": null
    }
  ]
}
```
* Key Transformations to Notice in this Execution:
Dynamic Routing to Zones: Even though the milk and the yogurts are both under Dairy & Eggs, the milk is recognized as UHT (ambient) and routed to the Pantry with a 180-day shelf life, while the fresh yogurt is sent to the Fridge with 14 days.

Typo Correction (Fuzzy Matching): The OCR typo "AV0CAT" (with a zero) was corrected to "D'avocats", and "ESPINARD" was normalized to the correct French spelling "Épinards Frais".

Exclusion & Deduction Handling: The line "-0.50e PROMO JALOUSIE" was entirely skipped by the parser because it represented a transactional promotional discount rather than an inventory asset item. Tax totals and shop metadata were neatly parsed directly into the receipt_metadata block.

# Architecture for the 4 Core Features 
## 1. Recipe Matcher & "Missing Ingredient" Engine
To calculate what a user can cook without running a massive SQL overhead loop, use a three-tier matching logic:
* Perfect Match (100%): A SQL query returns recipes where 100% of the required product_ids or categories exist in pantry_items where status = 'in_stock'.
* The "Missing Item" Indicator (+1 or +2): The query cross-references the recipe requirements against active pantry rows. If a recipe requires 5 items and the user has 4, it flags the recipe with a status badge: Missing 1 item: [Lime].
* One-Tap Addition: If the user clicks that recipe, a button appears: "Add missing items to grocery list", inserting the missing product_id straight into the grocery_lists table with source = 'missing_recipe_ingredient'.
  
## 2. Expiration-Prioritized Recipe Routing
To actively prevent food waste, the recipe sorting algorithm shouldn't just look at alphabetical order or ratings; it should use an Urgency Weighting Score.
  * Step 1: Query pantry_items filtering for items where estimated_expiry_date is less than or equal to current_date + INTERVAL '3 days'.
  * Step 2: Boost recipes that utilize these specific high-priority product_ids.
  * The Formula Logic:$$\text{Recipe Score} = (\text{Available Ingredients \%}) \times 10 + (\text{Number of Expiring Ingredients Used} \times 5)$$
    *This guarantees that a recipe using a carton of cream and spinach expiring tomorrow bubbles up straight to the top of the home screen feed.*

## 3. The Grocery List Recommender
This serves as a predictive system to capture items before a parent realizes they are gone.
  * Velocity Tracking: The app monitors the time delta between an item being added (status = 'in_stock') and marked empty (status = 'consumed'). If a household buys milk every 7 days, on day 6, the system moves the item to a "Recommended for you" tray at the bottom of the shopping list view.
  * Auto-Replenish Logic: Any row in pantry_items where is_staple = true and status changes to 'consumed' or 'wasted' triggers a database webhook that instantly duplicates that item into the active grocery_lists table.

## 4. Staple Builder & "Safety Stock" Tracker
  * The Core Loop: Inside the app, users can toggle a star icon on any product to mark it as a "Household Staple". This sets a threshold constraint (e.g., Always maintain 2 units of Milk).
  * The Passive Reminder: If the count drops below the threshold, a background cron job flags it as low_stock and surfaces a home screen card: "You're out of your staple: Milk. Tap to add to list."

# PWA Event Tracking & Analytics Strategy
Because our application runs as a Progressive Web App, we have to handle offline moments (e.g., a user updating their list while standing in a concrete supermarket basement with zero cellular reception) while maintaining precise event visibility.
## 1. The Local-First Analytics Schema (audit_logs)
Instead of sending a live API request for every button tap, write logs locally to IndexedDB using a lightweight library (like Dexie.js) and sync them to this database table whenever a stable internet network connection is detected:
```
SQLCREATE TABLE inventory_audit_logs (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    household_id UUID REFERENCES households(id),
    user_id UUID REFERENCES profiles(id),
    action_type VARCHAR NOT NULL, -- 'item_added', 'item_consumed', 'item_wasted', 'page_viewed'
    entry_method VARCHAR,         -- 'manual_typing', 'barcode_scan', 'ocr_receipt_upload'
    product_details JSONB,        -- Tracks metadata about the action taken
    client_timestamp TIMESTAMP,   -- When the action physically occurred offline
    synced_at TIMESTAMP DEFAULT now()
);
```
## 2. Event Tracking Matrix (Who did what?)

To build accurate user telemetry, behavioral analytics, and engagement dashboards, the system must explicitly capture the `entry_method` at the client UI layout level. This allows the product team to track feature adoption (e.g., OCR success vs. manual entry friction) and household user interaction.

### UI Event Mapping Matrix

The frontend PWA application must trigger the following telemetry payloads based on explicit user interactions:

| User Action | UI Component Context | Trigger Data Collected | Analytics Log Output Example |
| :--- | :--- | :--- | :--- |
| **Manual Input** | `AddCustomItemForm.tsx` | `action: "item_added"`<br>`entry_method: "manual_typing"`<br>`user_id: "user_123"` | *"Dad added 1kg Flour manually"* |
| **Camera Scan** | `BarcodeScanner.tsx` | `action: "item_added"`<br>`entry_method: "barcode_scan"`<br>`user_id: "user_456"` | *"Mom added Milk via barcode"* |
| **Receipt Upload** | `ReceiptOcrProcessor.tsx` | `action: "batch_items_added"`<br>`entry_method: "ocr_receipt_upload"`<br>`user_id: "user_456"` | *"Mom added 14 items via Carrefour receipt"* |
| **Pantry Depletion** | `PantryItemCard.tsx` *(Swipe Left)* | `action: "item_consumed"`<br>`item_id: "pantry_uuid"`<br>`user_id: "user_123"` | *Clears inventory, triggers logic to update household product velocity metrics.* |

---

## Core Telemetry Objectives
1. **Friction Analysis:** Compare the ratio of `manual_typing` vs. `ocr_receipt_upload` events to identify if users are running into parsing errors and abandoning automation.
2. **Velocity Tracking:** Use the time delta between an item's `item_added` event and its subsequent `item_consumed` swipe to dynamically build the predictive grocery list engine.
3. **Multi-User Collaboration:** Segment data by `user_id` inside the same household to ensure shared family dashboards correctly attribute updates to the respective parent or family member.

# Essential PWA Optimizations for No-Code/Low-Code Scale
* **Service Worker Sync:** Use the browser's native Background Sync API. If a parent checks off three items on their grocery list inside a retail store with poor reception, the service worker catches the network failure, queues the updates, and fires them to your database backend the second they step out into the parking lot.

* **Optimistic UI Updates:** Do not make the user wait for a loading spinner when they mark an item as eaten or change a quantity. Modify the local frontend state instantly, then let the database mutation resolve quietly in the background. This makes the PWA feel like a fast, responsive native app.
