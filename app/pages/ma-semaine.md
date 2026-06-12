# About My Week Page
**Value Proposition** Users can plan their entire week's cooking plan based on their schedule -> energy, taste and restrictions.
**About our Users**
  Users have three types of day
  - calm day - they can cook any
  - busy day - they can cook but something really fast and easy
  - chaotic - they can not cook anything at all, reheat and microwave food becomes their go to

**Features**
  - Quick Week Planning - AI assigns each day calm | busy | chaotic based on 4 different type of weeks. This should be default option.
  - Assign energy level for each day of the week - optional path
  - Regenerate or (all) recipe in one click
  - Plan for next week
  - Add to grocery missing items in one click.

**Hard Rules**
- Core :
  - AI Recipe generation Rule
    - Recipe **MUST NOT** contain any of ingredients in the restriction or allergy in their profile.
      - apply fuzzy matching to ensure we catch all ingredients, we rather over match than miss
    - Expiring ingredients first. Otherwise, always use the current ingredients.
    - Always consider Taste and preferrence.
    - Real Recipes: must be at least 3 ingredients (not including staples) and has 4 or more actual cooking steps.
      
**Logic and Definition**
- Your week : current day truncate to week
- Next week : current day+6 days truncate to week
   
**Backlog**
- Batch Cooking Feature
- Start of the Day
- Grocery Day
