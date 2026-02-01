# Search Functionality Test Cases

## 1. Basic Search Functionality

### TC-01: Valid search by product name
**Precondition:** Products exist (e.g., Gaming Laptop, Laptop Charger)

**Steps:**
1. Enter `Laptop` in the search box
2. Click Search

**Expected Result:**
- Products with “Laptop” in the name or description are displayed
- Results are case-insensitive and partial matches

---

### TC-02: Valid search by product description
**Steps:**
1. Search for a keyword that exists only in product descriptions (e.g., `RGB`)

**Expected Result:**
- Products whose description contains the keyword are displayed

---

### TC-03: Case-insensitive search
**Steps:**
1. Search for `laptop`
2. Search for `LAPTOP`

**Expected Result:**
- Both searches return identical results

---

### TC-04: Partial match search
**Steps:**
1. Search for `shoe`

**Expected Result:**
- Products like Running Shoe, Sports Shoes are displayed

---

## 2. Empty & No-Result Scenarios

### TC-05: Empty search query
**Steps:**
1. Leave search field empty
2. Click Search

**Expected Result:**
- All products are displayed (default behavior)

---

### TC-06: No matching results
**Steps:**
1. Search for `NonExistentProduct`

**Expected Result:**
- No product list shown
- Message displayed: “No results found”

---

## 3. Search Result Display

### TC-07: Verify result format
**Steps:**
1. Perform any valid search

**Expected Result:**
Each product shows:
- Product name
- Price
- Thumbnail image

---

### TC-08: Results per page limit
**Steps:**
1. Perform a search that returns more than 10 products

**Expected Result:**
- Only 10 products shown per page

---

## 4. Pagination

### TC-09: Pagination controls visibility
**Steps:**
1. Search returning more than 10 products

**Expected Result:**
- Pagination controls (Next / Previous) are visible

---

### TC-10: Pagination navigation
**Steps:**
1. Click Next
2. Click Previous

**Expected Result:**
- Correct products load for each page
- No duplicate or missing items

---

## 5. Sorting Functionality

### TC-11: Sort by price – low to high
**Steps:**
1. Search for `Shirt`
2. Sort by Price (Ascending)

**Expected Result:**
- Results sorted from lowest price to highest

---

### TC-12: Sort by price – high to low
**Steps:**
1. Sort by Price (Descending)

**Expected Result:**
- Results sorted from highest price to lowest

---

### TC-13: Sort by name (alphabetical)
**Steps:**
1. Sort by Name

**Expected Result:**
- Products ordered alphabetically (A–Z)

---

## 6. Filtering Functionality

### TC-14: Filter by category
**Steps:**
1. Search for `Shirt`
2. Apply category filter: `Clothing`

**Expected Result:**
- Only clothing items are displayed

---

### TC-15: Filter by price range
**Steps:**
1. Apply price range filter (e.g., `500–1000`)

**Expected Result:**
- Only products within the selected range are shown

---

### TC-16: Combined search, filter, and sort
**Steps:**
1. Search for `Shirt`
2. Filter by category `Clothing`
3. Sort by price (Low to High)

**Expected Result:**
- Filtered results sorted correctly

---

## 7. Special Characters & Input Validation

### TC-17: Search with special characters
**Steps:**
1. Search for `Shoe@#$`

**Expected Result:**
- Special characters are ignored
- Search executes without error

---

### TC-18: Search with numeric values
**Steps:**
1. Search for `12345` (SKU or numeric product name)

**Expected Result:**
- Products containing the number are returned

---

### TC-19: Long search query (>100 characters)
**Steps:**
1. Enter a 150-character query

**Expected Result:**
- Query is truncated to 100 characters
- Search executes successfully

---

## 8. Negative & Edge Cases

### TC-20: SQL/script injection attempt
**Steps:**
1. Search for `' OR 1=1 --`

**Expected Result:**
- No system error
- Input safely handled (no crash, no data leak)

---

### TC-21: Performance check (basic)
**Steps:**
1. Perform a common search

**Expected Result:**
- Results load within acceptable response time (e.g., < 2 seconds)