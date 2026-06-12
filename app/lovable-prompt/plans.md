This is how lovable frames my problem statement

Recipes surfaced on / (home) and /ma-semaine are sometimes condiments, sauces, or single-component items (e.g. "Classic Emulsion Dressing") rather than complete, edible meals. The underlying AI prompts don't explicitly forbid this, don't enforce a real meal shape (protein + starch/veg + flavor), and rely on weak allergen wording.
----------------------------------------------------------
Add server-side meal validator + title↔ingredient match

Goal

Make sure no recipe (weekly plan, rescue, adapted) gets surfaced unless it passes a hard "is this a real main dish" check. The reported failure case — Title: Tomato Rice / Ingredients: 1 egg, 50 g potato, 0.3 onion, 0.5 tbsp olive oil, 0.1 tsp salt, 0.1 tsp black pepper — must be rejected: no rice in the ingredients (title↔ingredient mismatch), and no real main-dish anchor.

Two layers: stricter prompt wording, plus a deterministic post-generation validator so we don't depend on the model self-policing.
----------------------------------------------------------

My Prompt: 
in /pantry page: 
(1) Add Pantry , manual: accept manual entry not part of the auto-complete list. 
# Context: 
There are x use cases we user AI/tavily generated recipe: 
  - Use it up Recipes 
    * How do user use this: from the /pantry page, user clicks one of the Use it up card
      * Goal of this feature: Cook expiring ingredients 
      * Expected Outcome: a recipe is generated(or replaces) in **/recipes page** 
  - Week Recipes (This Week or Next Week)
    * How do user use this: 
      * This week: from the /ma-semaine page - this week, user clicks replan - quick setup or customized per day.
      * Next week: from the /ma-semaine page - next week, user clicks replan - quick setup or customized per day.
    * Goal of this feature: Create a full week recipe matching user's energy
    * Expected Outcome: A **full week plan** with a recipe placed or a reheat instructions.
        - If there are any chaotic days, there must be a day where the qty is multiplied to cover the reheat days. Indicate which days when the user will over cook, and reference which meals reheat is from or be used as reheat. (give the indication why user is getting "higher" qty.
  - Suggest another dinner 
    * How do user use this: 
      * This week: from the /ma-semaine page - this week, user clicks on one of the recipe card and clicks "Suggest another dinner" 
      * Next week: from the /ma-semaine page - next week, user clicks on one of the recipe card and clicks "Suggest another dinner" 
    * Goal of this feature: Allow user to change one specific recipe
    * Expected Outcome: Change the recipe on the **specific recipe card** where it was launch
  - Regenerate full week (this or next week)
    * How do user use this: 
      * This week : from the /ma-semaine page - this week, user clicks refresh button (upper right)
      * Next week: from the /ma-semaine page - next week, user clicks refresh button (upper right)
    * Goal of this feature: Allow user to change the whole week recipes
    * Expected Outcome: Change the recipe on the **specific week** where it was launched
  - Generate Recipe
    * How do user use this: 
      * from the /recipes page - user clicks "Generate Recipe" in the Quick Generate Card
    * Goal of this feature: Allow user to generate a more "customized" recipe by adding more instrctions
    * Expected Outcome: a recipe is generated(or replaces) in **/recipes page** based on the Meal, time and fine-tune instructions defined by the user. 
  - Adapt a Recipe
    * How do user use this: 
      * Photo of a recipe / Upload a file
      * Paste a link
    * Goal of this feature: Allow user to generate a more "customized" existing recipe with some ingredients suggestions based on what the user have (optional)
    * Expected Outcome: a recipe is generated(or replaces) in **/recipes page** 

# Issues we're facing:
