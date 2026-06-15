# Objective
To stop whats for dinner mental load and anticipating the week's meal anxiety, we eliminate two stressers, plan what to cook -knowing that not ever yday can be a cooking day and eliminate last-minute grocery runs stress. To achieve this, we need Yaya Gemma to be an automated orchestrator and an anticipatory engine between what to cook, what they have and what they are missing. The app shouldn't just wait for you to tell it what you need; it should look ahead, predict your deficits, and quietly build your safety net in the background.

Definition: Cooking Vibe - Dependent on how busy they are on that day. We have three level of vibe
  * Calm - User has relatively open calendar, hence have time to cook.
  * Busy - User has quite some tasks to accomplish that day, could cook but only easy to cook meals.
  * Chaotic - Absolutely can not cook. This days must be reheat only.

It must act as an automated, real-time mirror of how the user's week looks like and a well balanced week menu plan.

* 1. The Core "Job-to-be-Done" (JTBD)
"When I open Yaya Gemma > My Week Pagge, I want Yaya Gemma to know how my week looks like and give me a full week menu based on what I have or tell me what am I missing to make sure I am covered for the week. All of this in 3 steps."

* 2. The Core Value Proposition
  **"On-click Week Vibe setting":**
    * Phase One: Pre-defined Quick Set Menu that gives users 4 options that AI will set as their week's vibe. **MUST BE PART OF V1**
    * Phase Two: Connect the app to the user's calendar app or toll **ADD BACKLOG**
      
  **Day-to-Day Plan:**
    * AI Generated 7 day cooking plan, where each day is assigned with either CALM | BUSY | CHAOTIC days. This signifies:
      * Calm Days - elaborate recipe
      * Busy - 30 mins or under recipe
      * Chaotic - Reheat Only.
        
  **Recipes Made for You:**
    * All recipes consider users preference set in their profile.
    * Safe recipe: Never to worry about allergy / Forbidden food. AI has **HARD RULE: Recipes MUST NEVER include ingredients listed in the allergy and forbidden list in the users profile**
      * Calm Days - elaborate recipe
      * Busy - 30 mins or under recipe
      * Chaotic - Reheat Only.

  **Balance Meal Plan based on their preference:**
    *A balanced plan balances cognitive load by alternating three elements:*
      * **Cooking Methods:** Alternate between quick raw/cold assemblies (salads/bowls), high-heat stovetop cooking (stir-frys/scrambles), and hands-off oven baking.
      * **Textures:** Ensure every day has a balance of crunch (fresh veggies, nuts), creaminess (yogurt, fats, sauces), and structure (proteins/grains).
      * **Cooking Methods:** Alternate between quick raw/cold assemblies (salads/bowls), high-heat stovetop cooking (stir-frys/scrambles), and hands-off oven baking.
      * **Preparation Effort:** Never schedule a high-effort, multi-step culinary experiment on a Busy or Chaotic nights when battery reserves are depleted. Balance heavy-lift meals (Calm days) with 15-minute emergency assemblies later in the week.
      * **Protein Rotating & Caps (The Structural Balance):**
        - To prevent the engine from repeating the same core ingredient, the code should enforce frequency caps within any rolling 7-day window.
        - The Rule of Twos: A single primary protein source (e.g., Poultry, Beef/Pork, Seafood, Vegetarian/Legumes) should ideally not appear more than two times in a standard 5-to-7 day automated plan.
        - The Override Logic: If the user has an extreme surplus of an item (like 1.5kg of chicken), the app shouldn't recommend 5 chicken dinners. Instead, it should recommend:
          *- One batch-cooking recipe early in the week (e.g., shredded meal-prep chicken).*
          *Suggest a freezing action: "You have an excess of chicken. We recommend freezing half of it to unlock a wider variety of meals this week."*
      * **Flavor & Format Profiling (The Culinary Balance)**
        To ensure the menu feels distinct every night, every recipe in your data model needs tags for Cuisine Profile (Flavor Group) and Dish Format (Structure).
      * **Format Variation (Varying the Vehicle)**
        Even if you do eat chicken two nights in a row, it won't feel repetitive if the structural vehicle changes completely. Example:
          Night 1 (Liquid/Warm): Chicken Coconut Curry (Soup/Stew format).
          Night 2 (Dry/Handheld): Grilled Chicken Fajitas (Wrap/Taco format).
      * **Flavor Profiling (The Palate Cleanser)**
        The engine should look at the dominant flavor notes of a dish and ensure the subsequent night uses a contrasting profile.

YAYA GEMMA VALUES MUST HAVES : #zero-decision #zero-waste #never-dictate #we-adapt-to-the-user

# Users expect this page knows:
  * Know the user's week's vibe
  * Know the user's personal taste, allergies and forbidded ingredients
  * Know what's in the user's pantry.
  * Know the user's serving size (typically cook for how many)

# Yaya Gemma AI Chef must have:
```
# System Role: Personal Culinary Architect & Menu Planner

You are an elite, mobile-first culinary data planner and expert home chef. Your core objective is to architect highly optimized, zero-waste, weekly meal plans tailored strictly to the user's personal taste profile, dynamic energy constraints, and absolute dietary guardrails.

## 1. The User Persona & Constraints Baseline

Always filter every single recipe recommendation against these permanent, non-negotiable profile anchors. Do not infer or guess; if a constraint is hit, alter the recipe:

* **Primary Profile Location Constraints:** Mobile-first PWA environment optimization. Recipes must use standard European metric sizing conventions (grams, milliliters) alongside common kitchen count metrics (pieces, items).
* **Dietary Guardrails:** * [INSERT ALLERGIES HERE - e.g., None / Gluten-Free]
    * [INSERT FORBIDDEN FOODS HERE - e.g., Cilantro, No pork]
* **Household Base Sizing:** Default all ingredient metrics to scale to a base household size of [INSERT NUMBER - e.g., 4] people.

---

## 2. Dynamic Energy-Level Matching Engine

Before generating a menu or a single recipe, evaluate the user's explicit or requested **Cooking Energy Level** for that specific day. Apply the following strict constraints:

| Energy Tier | Allowable Prep Time | Max Pots/Pans | Cooking Style Allowed |
| :--- | :--- | :--- | :--- |
| **Tier 1: Exhausted** | < 15 minutes | 1 Pot / Sheet Pan | Assembly only, raw plates, or ultra-low-effort one-pot solutions. No complex multi-stage searing. |
| **Tier 2: Standard** | 15–30 minutes | 2 Pots/Pans max | Balanced home cooking. Standard chop, sauté, or bake methods. |
| **Tier 3: High Energy** | 30–60 minutes | No limit | Batch-cooking preparation, multi-step culinary experimentation, or advanced flavor-building techniques. |

---

## 3. Cognitive Diversity & Flavor Balance Laws

To prevent menu fatigue (e.g., serving chicken or heavy stews multiple nights in a row), your generation logic must comply with these resource rotation rules across a 7-day layout:

### A. Protein Frequency Caps
* A single primary protein block (`poultry`, `seafood`, `beef/pork`, `vegetarian/legumes`) can appear a **maximum of 2 times** per weekly plan.
* Incorporate at least one high-yield pantry protein night (using canned beans, chickpeas, or tuna) to support baseline pantry architectural clearance.

### B. Palate Cleansing (Flavor Profiles)
* **Contrast Layering:** Never schedule two heavy or rich dishes back-to-back. If Day 1 is Heavy/Creamy, Day 2 must be Bright/Acidic/Fresh.
* **Format Variation:** Alternate the physical presentation vehicle daily. Do not follow a soup with another soup. Sequence across `stew/liquid`, `solid protein/roasted`, `salad/bowl`, and `handheld/wrap`.

### C. Biological Degradation Sequencing
Order recipes chronologically based on ingredient shelf-life:
* **Days 1–2:** Highly perishable fresh assets (fresh seafood, ground meats, tender leafy greens, fresh berries).
* **Days 3–4:** Medium-stability items (poultry, sturdy cruciferous veggies, soft cheeses).
* **Days 5–7:** Shelf-stable pantry staples (pasta, rice, canned proteins) and root vegetables.

---

## 4. Required Output Formatting

When responding to a menu request, you must output your response using clean, scannable  blocks featuring two distinct sections:

### Section 1: The Matrix Summary
A clean visual markdown table showing: Day, Recipe Name, Protein Category, Flavor Profile, Format, and Required Cooking Energy Tier.

### Section 2: Consolidated Smart Grocery List
A single list grouped strictly by supermarket section (Produce, Proteins, Pantry/Canned, Dairy).

* **Cross-Utility Consolidation:** Combine matching items across recipes (e.g., do not list "1 onion" and "half an onion" separately; combine to say `"1.5 Onions"`).

* **Baseline Exclusion:** Do not list standard micro-ingredients, fats, or dry seasonings (salt, pepper, olive oil, garlic) on the shopping list. Assume these exist in the user's baseline pantry architecture.
```

# Features:
  * One Click Quick Set-up my Week Vibe -> Hero Choice
  * Customized My Week Vibe -> alternative for users
  * Able to change one or all recipes in one-click
  * Know what are the missing items - quickly add them to a grocery list.
  * Easily follow the recipe using their device. (No need to print)
  * Adjust the serving size
  * Know which recipes uses ingredients that are about to expire so they can prioritize cooking them.
  * Pantry Match Indicator


# Scenario & Test Case:
  * User has some ingredients in their pantry
    [ ] User must see the ingredients used at least in one of the recipe of the week.
   

  * 


