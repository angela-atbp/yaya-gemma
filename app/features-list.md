# AI Genereated Recipes
## Use it up Recipes
  * **How do user use this:** from the /pantry page, user clicks one of the Use it up card
  * ***Goal of this feature:** Cook expiring ingredients
  * **Expected Outcome:** a recipe is generated(or replaces) in /recipes page

## Week Recipes (This Week or Next Week)
  * **How do user use this:**
      * This week: from the /ma-semaine page - this week, user clicks replan - quick setup or customized per day.
      * Next week: from the /ma-semaine page - next week, user clicks replan - quick setup or customized per day.
  * **Goal of this feature:** Create a full week recipe matching user's energy
  * **Expected Outcome:** A full week plan with a recipe placed or a reheat instructions.
    - If there are any chaotic days, there must be a day where the qty is multiplied to cover the reheat days. Indicate which days when the user will over cook, and reference which meals reheat is from or be used as reheat. (give the indication why user is getting "higher" qty.

## Suggest another dinner
  * **How do user use this:**
    * This week: from the /ma-semaine page - this week, user clicks on one of the recipe card and clicks "Suggest another dinner"
    * Next week: from the /ma-semaine page - next week, user clicks on one of the recipe card and clicks "Suggest another dinner"
  * **Goal of this feature:** Allow user to change one specific recipe
  * **Expected Outcome:** Change the recipe on the specific recipe card where it was launch

## Regenerate full week (this or next week)
  * **How do user use this:**
    * This week : from the /ma-semaine page - this week, user clicks refresh button (upper right)
    * Next week: from the /ma-semaine page - next week, user clicks refresh button (upper right)
  * **Goal of this feature:** Allow user to change the whole week recipes
  * **Expected Outcome:** Change the recipe on the specific week where it was launched

## Generate Recipe
  * **How do user use this:**
    * from the /recipes page - user clicks "Generate Recipe" in the Quick Generate Card
  * **Goal of this feature:** Allow user to generate a more "customized" recipe by adding more instrctions
  * **Expected Outcome:** a recipe is generated(or replaces) in /recipes page based on the Meal, time and fine-tune instructions defined by the user.

## Adapt a Recipe
  * **How do user use this:**
    * Photo of a recipe / Upload a file
    * Paste a link
  * Goal of this feature:** Allow user to generate a more "customized" existing recipe with some ingredients suggestions based on what the user have (optional)
  * **Expected Outcome:** a recipe is generated(or replaces) in /recipes page

--------------------------------------

# Smart Pantry
## Auto Detection of Use it up Ingredients
  * **How do user use this:** from the /pantry page, user clicks one of the Use it up card
  * ***Goal of this feature:** Auto-detect perishable ingredients, flag to the user so that user never waste ingredients. there are two states:
     * expiring date is defined by the user(user inputs expiring date) -> IS and MUST BE RESPECTED 
     * missing expiring date for perishable ingredients: make an estimate of expiring date based on the date the user added the item.
  * **Consideration**
     * Canned goods may have a longer shelf life than fresh ones. 
  * **Expected Outcome:** Expiring soon items are flagged, marked and is included in the Use it up ingredients.

## Easy Entry via Autocompletion and image Recognition
  * **How do user use this:** from the /pantry page, Users have 3 ways to build a pantry list
     * Manual - user types the item (we offer auto complete) and we accept hard entered items. **Why?* User might use brand name or spelling may differ from language. We recieved feedback that user's entry are getting rejected and is causing disruption. We'd rather have a "messy" list but defined by the user now, rather than a strict blocking system. We accept this issue for now and will revisit once we have enough data.
     * Photo scan - user takes picture of their pantry or fridge and detect those items and add them in the list
     * Upload image - user uploads their grocery receipt and  detect those items and add them in the list
       
  * ***Goal of this feature:** We know, its very hard to keep their pantry updated, that's not what we expect user to do. Instead, we want this feature to be used as a "reminder" / "alert" mechanism. The Value proposition of this feature: waste nothing. 
  * **Expected Outcome:** User gets alerted via in-app notification of expiring items, and interface clearly highlights items to expire. 
  * **Nice to have** In the future, we should provide user analytics of ingredients they frequently waste + nutrional value.

## Auto Categorization & Scoring
  * **How do user use this:** from the /pantry page, Users have 3 ways to build a pantry list
     * Manual - user types the item (we offer auto complete) and we accept hard entered items. **Why?* User might use brand name or spelling may differ from language. We recieved feedback that user's entry are getting rejected and is causing disruption. We'd rather have a "messy" list but defined by the user now, rather than a strict blocking system. We accept this issue for now and will revisit once we have enough data.
     * Photo scan - user takes picture of their pantry or fridge and detect those items and add them in the list
     * Upload image - user uploads their grocery receipt and  detect those items and add them in the list
       
  * ***Goal of this feature:** We know, its very hard to keep their pantry updated, that's not what we expect user to do. Instead, we want this feature to be used as a "reminder" / "alert" mechanism. The Value proposition of this feature: waste nothing. 
  * **Expected Outcome:** User gets alerted via in-app notification of expiring items, and interface clearly highlights items to expire.
  * Sample test case:
    Action : Step 1. User uses Manual Entry for a new item: Milk (first time)
    Expected Result :
      * Autocomplete is prompted to the user while adding the item to the   list
      * Added items get added and properly categorized
      * Result > 🧀 Dairy & Eggs (Category) > Milk > QTY x 1
    Action: Step 2. User uses Manual Entry for another item: Milk (intentional, 2nd time)
    Expected Result :
     * Autocomplete is prompted to the user while adding the item to the list
     * Similar items are incremented in QTY rather than creating multiple lines. (Deduplication applied)
     * Result > 🧀 Dairy & Eggs (Category) > Milk > QTY x 2
    Action : Step 3. User uses Photo for another item: photo of Milk (intentional, 3rd time)
    Expected Result :
     * Autocomplete is prompted to the user while adding the item to the list
     * Similar items are incremented in QTY rather than creating multiple lines. (matching is applied)
     * Result > 🧀 Dairy & Eggs (Category) > Milk > QTY x 3

 
  * **Nice to have** In the future, we should provide user analytics of ingredients they frequently waste + nutrional value.

--------------------------------------

# Smart Grocery Builder
##  Add missing items (and bulk) list from a recipe to grocery list
  * **How do user use this:**
     * from any recipe card (from /ma-semaine page, users clicks add to basket one, multiple or all (bulk) missing items
     * from any items in /pantry page, users clicks add to basket one, multiple or all (bulk) missing items 
  * ***Goal of this feature:** Users can quickly build a grocery list from the recipes they intend to cook while making sure they dont buy items that already exists in their pantry. User is assured they have the complete ingredients to cook the weeks plan, no emergency last minute run to the grocery.

  * **Expected Outcome:**
    - All missing ingredients are accurately identified from the week plan.
    - When user clicks any 'add to grocery' button they see those items in the grocery list in the /grocery-list page
    - Added items are deduplicated
    - No multi-adding by mistake
    - Grocery list is properly categorizing (help user optimize their physical shopping route)
    - Correct quantity based on planned meals
    - Know if they've bought it or not
    - Quickly update pantry list so recipe generation is always up to date to what they have (full loop system)
  * **Consideration**
    * Ingredients in Recipes may sometimes include adjectives or other discreptive words on it (for example minced garlic, boiled eggs) that might affect the lookup of existing pantry list versus what is needed.
    * Recipes uses different units, aggregating total quanity for the same ingredients could be a challenge

--------------------------------------

# Pantry Inventory Loop System
##  Full Loop of Pantry > Recipe > Grocery > Pantry > Recipe
  * **How do user use this:**
     * this is an engine, not a user facing feature
  * ***Goal of this feature:** The goal is to relieve users from mentally and manually updating anything yet enabled them to have all ingredients necessary to cook/prepare food for entire week with as minimal waste as possible.

  * **Expected Outcome:** **This is more our ideal loop*
    - What we know? User expressed that they find it a challenge to constantly update their pantry.
    - Our modus then is to assume that we have 'the best possible info' in terms of pantry and that user can upload or adhoc (meaning, user can add, delete ingredients.
    - **The loop*
    - Yaya Gemma is using what is in the pantry in generating recipe > Generate recipe > missing items added to grocery > user do the grocery > added to the pantry > user cooks > ingredients are deducted from pantry > user generate recipe > missing items added to grocery.....
   
**THIS FEATURE IS STILL NOT IMPLEMENTED AND WE ARE EXPLORING THE FEASIBILITY AND ADDED VALUE FOR NOW*
    - 
  * **Consideration**
    * Ingredients in Recipes may sometimes include adjectives or other discreptive words on it (for example minced garlic, boiled eggs) that might affect the lookup of existing pantry list versus what is needed.
    * Recipes uses different units, aggregating total quanity for the same ingredients could be a challenge
