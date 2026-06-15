# Objective
To deliver instant value the absolute millisecond a user lands on the homepage—without them having to click, scroll, or type a single thing—the homepage cannot be a generic search bar or a list of random trending recipes.

It must act as an automated, real-time mirror of what the user can cook right now.

Here is the strategic breakdown for a zero-friction homepage designed exactly for this "instant-value" experience.


* 1. The Core "Job-to-be-Done" (JTBD)
"When I open the app, I want to see exactly I can cook right now considering my cooking vibe, food taste preferences, restriction and what I have in my pantry"

* 2. The Core Value Proposition
"Zero-Click Decision Making": The app eliminates choice paralysis. You don't browse; you are dynamically shown your exact evening menu based purely on your cooking vibe and the physical reality of your kitchen.
YAYA GEMMA VALUES MUST HAVES : #zero-decision #zero-waste #never-dictate #we-adapt-to-the-user

"Financial Rescue Engine": It acts as an automated budget protector by prioritizing recipes that rescue your most expensive, expiring ingredients (like proteins and dairy) before they spoil.

# UI Layout & Visual Architecture
Because the user shouldn't have to touch anything to get value, the mobile-first UI layout must be radically simple, structured from top to bottom in a clean vertical stack.

## First immediate thing message we want the user to recieve when they land on this page
  * What would this recipe look like when cooked. (Image)
  * What am I cooking (Title)
    
* The Hero Widget: "Recipe made for you tonight"
The Visual: A large, clean dynamic card at the absolute top of the screen with Big Title Centered below it.

* Primary call-to-action metric: "Cook Now" (see Cook Now Page)

* Tier 1 Content:
  * What's in this recipe?
    * Max 2 Hero Ingredients. Example: Chicken Carrot + 11 more
    * Time to cook
    * Total number of servings
  * The Visual: Unclickable, static tex
* Tier 2 Content: 
  * "Fresh in your pantry" (6 of 13)
  * X number of ingredients missing that was part of thier current shopping list
  * The Visual: A completion bar showing the % between the ingredients required versus what the user have in their pantry

* Tier 3 Content: Offer user to change their mind
  * "Not feeling this tonight?" - This allows the user to change the recipe tonight, two option:
    * Regenerate the recipe based on what is currently listed in the app's Pantry Page (invetory)
    * Regenerate the recipe based on a different from whats in the app's Pantry Page (invetory)

# Feature List (Automated & Passive)
To make this zero-touch experience work, the homepage runs these components automatically in the background the moment the app mounts. 

# Scenario
 * **(1) User has a week plan**
    **Expected outcome from this page:**
    [ ] The recipe today == the recipe shown in the equivalent date in Week's plan.
      Example: Today is Jun 16
      This Week's Plan
      Jun 15 -> Recipe A
      Jun 16 -> Recipe B
      Jun 17 -> Recipe C
      Jun 18 -> Recipe D
      Jun 19 -> Recipe E
      Jun 20 -> Recipe F
      Jun 21 -> Recipe G
      This Page Hero Recipe -> Recipe B
    [ ] Dynamic Hero Image consistent with the Recipe Title
    
* **(2) User has NO week plan** 
    **Expected outcome from this page:**
    [ ] Fallback # 1: Suggest a Dinner Recipe based on users pantry. Use Best possible match. No cooking vibe to consider but the recipe complies with Hard Rules
    [ ] Fallback # 2: Suggest a Dinner Recipe based on users pantry. Use Best possible match. No cooking vibe to consider but the recipe complies with Hard Rules
    [ ] Dynamic Hero Image consistent with the Recipe Title

# Tracking & Analytics.
Events in this page is tracked in home_page_events, tracking
- user_id
- timestamp (user's locale timestamp)
- event_name
  - opened_app. each time the user landed in the page (record only if the app or the user is active, because we are PWA, we risk tracking users where Yaya Gemma is just running in the background, to mitigate this, we need to check if Yaya Gemma screen is visible and the window is in focus and not blurry). Implement some safe time gap
  - cook_now. when user clicks "Cook Now" CTA
  - changed_recipe. when user clicks "Not feeling this tonight" CTA
    

