# CKD Meal Planner - Specification Document

## 1. Project Overview

- **Project Name:** CKD Stage 3 Meal Planner
- **Type:** Single-page web application
- **Core Functionality:** Meal planning tool for Stage 3 CKD patients with real-time nutritional tracking, food database, and meal plan persistence
- **Target Users:** Stage 3 Chronic Kidney Disease patients and their caregivers

---

## 2. UI/UX Specification

### Layout Structure

```
┌─────────────────────────────────────────────────────────┐
│  HEADER (gradient, title, theme toggle, print button)   │
├─────────────────────────────────────────────────────────┤
│  PATIENT INFO BAR (weight input, daily targets toggle) │
├──────────────────────┬──────────────────────────────────┤
│                      │                                  │
│   FOOD DATABASE     │       MEAL PLANNER               │
│   (Left Panel)      │       (Right Panel)              │
│                      │                                  │
│   - Search bar       │   - Breakfast section             │
│   - Category filters │   - Lunch section                │
│   - Food cards grid  │   - Dinner section               │
│                      │   - Snacks section               │
│                      │   - Daily totals display         │
│                      │                                  │
├──────────────────────┴──────────────────────────────────┤
│  SAVED PLANS BAR (load/save/delete meal plans)         │
└─────────────────────────────────────────────────────────┘
```

### Responsive Breakpoints
- **Desktop:** > 1024px - Two-column layout
- **Tablet:** 768px - 1024px - Stacked with collapsible panels
- **Mobile:** < 768px - Single column, tabbed navigation

### Visual Design

#### Color Palette
- **Primary (Dark Teal):** `#0d9488`
- **Primary Light:** `#14b8a6`
- **Secondary (Warm Sand):** `#f5e6d3`
- **Accent (Coral):** `#f97316`
- **Background Light:** `#fafaf9`
- **Background Dark:** `#1c1917`
- **Surface Light:** `#ffffff`
- **Surface Dark:** `#292524`
- **Text Primary Light:** `#1c1917`
- **Text Primary Dark:** `#fafaf9`
- **Text Secondary:** `#78716c`

#### Nutrient Warning Colors
- **Green (Safe):** `#22c55e`
- **Yellow (Caution):** `#eab308`
- **Red (Danger):** `#ef4444`

#### Typography
- **Font Family:** `'Outfit', sans-serif` (headings), `'DM Sans', sans-serif` (body)
- **Heading 1:** 32px, 700 weight
- **Heading 2:** 24px, 600 weight
- **Heading 3:** 18px, 600 weight
- **Body:** 15px, 400 weight
- **Small:** 13px, 400 weight

#### Spacing System
- **Base unit:** 4px
- **xs:** 4px
- **sm:** 8px
- **md:** 16px
- **lg:** 24px
- **xl:** 32px
- **2xl:** 48px

#### Visual Effects
- **Card shadows (light):** `0 1px 3px rgba(0,0,0,0.08), 0 4px 12px rgba(0,0,0,0.05)`
- **Card shadows (dark):** `0 1px 3px rgba(0,0,0,0.3), 0 4px 12px rgba(0,0,0,0.2)`
- **Border radius (cards):** 12px
- **Border radius (buttons):** 8px
- **Transitions:** 200ms ease-out

### Components

#### Header
- Gradient background: `linear-gradient(135deg, #0d9488 0%, #0f766e 50%, #115e59 100%)`
- App title with kidney icon
- Dark/light theme toggle (sun/moon icons)
- Print button with printer icon

#### Patient Info Bar
- Weight input field (kg) with slider
- Calculated protein target based on weight
- Toggle to show/hide daily targets panel

#### Food Database Panel (Left)
- Search input with magnifying glass icon
- Category filter buttons (All, Proteins, Vegetables, Fruits, Grains, Fats)
- Scrollable grid of food cards
- Each food card shows: name, portion size, key nutrient badges

#### Food Card
- White/dark surface background
- Food name (bold)
- Portion size in subtle text
- Nutrient badges: sodium (mg), potassium (mg), phosphorus (mg), protein (g), calories
- Click to add to selected meal
- Hover: slight lift effect

#### Meal Planner Panel (Right)
- Four meal sections: Breakfast, Lunch, Dinner, Snacks
- Each section has a header with meal name and calorie subtotal
- List of added foods with remove button
- Empty state: dashed border with "Drop foods here" text

#### Daily Totals Display
- Fixed at bottom of meal planner
- Horizontal bar showing progress for each nutrient
- Color-coded based on target thresholds
- Numerical values with target ranges

#### Saved Plans Bar
- Input for plan name
- Save button
- Dropdown or list of saved plans
- Load and delete buttons for each

#### Print View
- Clean black & white layout
- Patient weight and date
- Each meal section with foods
- Daily totals table
- Hide all interactive elements

---

## 3. Functionality Specification

### Core Features

#### Food Database (50+ items)
Categories with sample foods:

**Proteins (15)**
- Chicken breast (3oz): 70mg Na, 280mg K, 200mg P, 26g protein, 140 cal
- Egg whites (2): 110mg Na, 110mg K, 110mg P, 14g protein, 60 cal
- Salmon (3oz): 50mg Na, 300mg K, 250mg P, 22g protein, 175 cal
- Tofu (½ cup): 8mg Na, 120mg K, 120mg P, 10g protein, 76 cal
- Turkey breast (3oz): 45mg Na, 220mg K, 180mg P, 25g protein, 125 cal
- Cod (3oz): 60mg Na, 200mg K, 180mg P, 19g protein, 70 cal
- Shrimp (3oz): 190mg Na, 180mg K, 175mg P, 18g protein, 85 cal
- Beef sirloin (3oz): 55mg Na, 280mg K, 190mg P, 23g protein, 170 cal
- Pork tenderloin (3oz): 45mg Na, 320mg K, 200mg P, 22g protein, 140 cal
- Lamb (3oz): 60mg Na, 270mg K, 185mg P, 22g protein, 175 cal
- Duck (3oz): 65mg Na, 240mg K, 190g P, 21g protein, 180 cal
- Cottage cheese (½ cup): 350mg Na, 90mg K, 110mg P, 12g protein, 90 cal
- Greek yogurt (½ cup): 55mg Na, 150mg K, 100mg P, 10g protein, 65 cal
- Tempeh (½ cup): 14mg Na, 150mg K, 140mg P, 15g protein, 90 cal
- White fish (3oz): 55mg Na, 190mg K, 170mg P, 18g protein, 75 cal

**Vegetables (15)**
- Cabbage (1 cup): 20mg Na, 180mg K, 25mg P, 1g protein, 25 cal
- Cauliflower (1 cup): 30mg Na, 320mg K, 40mg P, 2g protein, 25 cal
- Bell peppers (1 cup): 5mg Na, 250mg K, 30mg P, 1g protein, 30 cal
- Cucumber (1 cup): 3mg Na, 175mg K, 25mg P, 1g protein, 16 cal
- Green beans (1 cup): 6mg Na, 190mg K, 35mg P, 2g protein, 30 cal
- Lettuce (1 cup): 20mg Na, 140mg K, 15mg P, 1g protein, 10 cal
- Onion (½ cup): 4mg Na, 115mg K, 20mg P, 1g protein, 30 cal
- Zucchini (1 cup): 12mg Na, 325mg K, 45mg P, 2g protein, 20 cal
- Asparagus (6 spears): 3mg Na, 200mg K, 50mg P, 2g protein, 20 cal
- Broccoli (1 cup): 30mg Na, 290mg K, 55mg P, 3g protein, 30 cal
- Carrots (1 cup): 85mg Na, 390mg K, 45mg P, 1g protein, 50 cal
- Celery (1 cup): 100mg Na, 260mg K, 25mg P, 1g protein, 15 cal
- Kale (1 cup): 25mg Na, 180mg K, 25mg P, 2g protein, 15 cal
- Spinach (1 cup): 25mg Na, 55mg K, 15mg P, 1g protein, 7 cal
- Snow peas (1 cup): 4mg Na, 190mg K, 35mg P, 2g protein, 25 cal

**Fruits (10)**
- Apple (medium): 2mg Na, 195mg K, 15mg P, 0g protein, 95 cal
- Blueberries (½ cup): 1mg Na, 60mg K, 10mg P, 0g protein, 40 cal
- Grapes (½ cup): 3mg Na, 90mg K, 15mg P, 0g protein, 55 cal
- Pineapple (½ cup): 1mg Na, 100mg K, 10mg P, 0g protein, 40 cal
- Cranberries (½ cup): 2mg Na, 45mg K, 8mg P, 0g protein, 20 cal
- Raspberries (½ cup): 1mg Na, 95mg K, 15mg P, 1g protein, 30 cal
- Strawberries (½ cup): 1mg Na, 115mg K, 20mg P, 0g protein, 25 cal
- Watermelon (1 cup): 3mg Na, 175mg K, 15mg P, 1g protein, 50 cal
- Pear (medium): 2mg Na, 200mg K, 15mg P, 0g protein, 100 cal
- Peach (medium): 0mg Na, 190mg K, 20mg P, 1g protein, 60 cal

**Grains (10)**
- White rice (½ cup cooked): 1mg Na, 30mg K, 20mg P, 2g protein, 70 cal
- Brown rice (½ cup cooked): 10mg Na, 55mg K, 80mg P, 2g protein, 55 cal
- Pasta (½ cup cooked): 1mg Na, 25mg K, 20mg P, 4g protein, 110 cal
- White bread (1 slice): 130mg Na, 25mg K, 25mg P, 2g protein, 70 cal
- Oatmeal (½ cup cooked): 5mg Na, 60mg K, 70mg P, 3g protein, 75 cal
- Couscous (½ cup cooked): 5mg Na, 40mg K, 20mg P, 3g protein, 90 cal
- Quinoa (½ cup cooked): 5mg Na, 90mg K, 80mg P, 4g protein, 110 cal
- Pancakes (2 small): 350mg Na, 90mg K, 80mg P, 4g protein, 150 cal
- Bagel (plain): 450mg Na, 55mg K, 50mg P, 5g protein, 245 cal
- Corn flakes (1 cup): 200mg Na, 25mg K, 10mg P, 2g protein, 100 cal

**Fats & Others (10)**
- Olive oil (1 tbsp): 0mg Na, 0mg K, 0mg P, 0g protein, 120 cal
- Butter (1 tbsp): 90mg Na, 3mg K, 3mg P, 0g protein, 100 cal
- Cream cheese (2 tbsp): 140mg Na, 30mg K, 25mg P, 2g protein, 100 cal
- Almonds (10 nuts): 0mg Na, 70mg K, 45mg P, 2g protein, 70 cal
- Peanut butter (1 tbsp): 70mg Na, 60mg K, 55mg P, 2g protein, 95 cal
- Avocado (¼): 5mg Na, 230mg K, 30mg P, 1g protein, 80 cal
- Margarine (1 tbsp): 90mg Na, 5mg K, 5mg P, 0g protein, 100 cal
- Honey (1 tbsp): 1mg Na, 6mg K, 1mg P, 0g protein, 60 cal
- Maple syrup (1 tbsp): 2mg Na, 10mg K, 2mg P, 0g protein, 50 cal
- Jam (1 tbsp): 10mg Na, 15mg K, 2mg P, 0g protein, 55 cal

#### Meal Planning
- Click on a food card to open meal selector modal
- Select which meal to add to (Breakfast, Lunch, Dinner, Snacks)
- Foods can be added multiple times
- Click X on added food to remove from meal
- Drag and drop between meal sections

#### Real-time Calculations
- Update totals immediately when foods are added/removed
- Show running totals for each nutrient
- Calculate based on patient's weight for protein target

#### Color Coding Logic
**Sodium:**
- Green: < 1500mg (50-75% of limit)
- Yellow: 1500-1999mg (75-99% of limit)
- Red: >= 2000mg (at or above limit)

**Potassium:**
- Green: < 2000mg (< 67% of lower limit)
- Yellow: 2000-2999mg (within range)
- Red: >= 3000mg (above range)

**Phosphorus:**
- Green: < 600mg (< 75% of lower limit)
- Yellow: 600-999mg (within range)
- Red: >= 1000mg (at or above limit)

**Protein:**
- Green: < 80% of target
- Yellow: 80-100% of target
- Red: > 100% of target

#### localStorage Persistence
- Auto-save current meal plan on every change
- Named plans: Save with custom name, load by name
- Data structure:
```json
{
  "currentPlan": {
    "breakfast": [...],
    "lunch": [...],
    "dinner": [...],
    "snacks": [...]
  },
  "savedPlans": {
    "Plan Name": {
      "breakfast": [...],
      "lunch": [...],
      "dinner": [...],
      "snacks": [...]
    }
  },
  "patientWeight": 70
}
```

#### Print Functionality
- Trigger browser print dialog
- Print-specific CSS hides: search, filters, buttons, interactive elements
- Shows: header, patient info, all meals, totals
- Optimized for letter/A4 paper

### User Interactions

1. **Adding food:** Click food card → Modal appears → Select meal → Add
2. **Removing food:** Click X button on food in meal section
3. **Searching:** Type in search box → Filter updates in real-time
4. **Filtering:** Click category button → Show only that category
5. **Saving plan:** Type name → Click Save → Confirm with toast
6. **Loading plan:** Select from dropdown → Click Load → Replace current
7. **Deleting plan:** Select from dropdown → Click Delete → Confirm
8. **Theme toggle:** Click sun/moon icon → Instant theme switch
9. **Print:** Click print icon → Browser print dialog

### Edge Cases
- Empty meal plan: Show helpful empty states
- Exceeding limits: Show clear red warnings, don't block
- No saved plans: Show "No saved plans" message
- localStorage full: Show error message
- Invalid weight input: Default to 70kg

---

## 4. Acceptance Criteria

### Visual Checkpoints
- [ ] Header displays with gradient background
- [ ] Theme toggle switches between light/dark instantly
- [ ] Food cards display in responsive grid
- [ ] Category filters highlight when active
- [ ] Meal sections show empty states when empty
- [ ] Daily totals bar shows all 5 nutrients with color coding
- [ ] Print view is clean and readable

### Functional Checkpoints
- [ ] Can search foods by name
- [ ] Can filter by category
- [ ] Can add food to any meal via modal
- [ ] Can remove food from meal
- [ ] Totals update in real-time
- [ ] Color coding reflects nutrient status
- [ ] Can save named plan to localStorage
- [ ] Can load saved plan from localStorage
- [ ] Can delete saved plan
- [ ] Print button triggers print dialog
- [ ] Works on mobile (responsive)
- [ ] Theme preference persists after reload
- [ ] Weight input calculates protein target
