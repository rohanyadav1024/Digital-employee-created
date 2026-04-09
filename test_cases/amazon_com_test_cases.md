## Test Suite: Amazon.com Core Functionality

### Scope:
This test suite covers the core functionalities of user authentication (login/logout), product search, cart management, and the initial steps of the checkout process on amazon.com.

### Test Design Layers Covered:
*   **Data:** Validating data consistency (e.g., product details, cart totals).
*   **Business Logic:** Verifying core workflows (e.g., login flow, adding to cart, checkout steps).
*   **UI:** Checking interaction and visual feedback (e.g., search results display, cart updates).
*   **Negative/Edge Cases:** Handling invalid inputs and unexpected scenarios.

---

### Test Cases

#### A. User Authentication

**TC-AUTH-001: Verify successful user login with valid credentials**
*   **Title:** Verify successful user login with valid credentials
*   **Pre-conditions:** User has a registered Amazon account.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Click on "Hello, Sign in Account & Lists".
    3.  Click on "Sign in" button.
    4.  Enter valid email/phone number in the "Email or mobile phone number" field.
    5.  Click "Continue".
    6.  Enter valid password in the "Password" field.
    7.  Click "Sign in".
*   **Test Data:**
    *   Email: `valid_user@example.com`
    *   Password: `ValidPassword123`
*   **Expected Result:** User is successfully logged in, and the "Hello, Sign in Account & Lists" text changes to "Hello, [User's Name]".
*   **Priority:** Critical
*   **Type:** Functional

**TC-AUTH-002: Validate user login with invalid password**
*   **Title:** Validate user login with invalid password
*   **Pre-conditions:** User has a registered Amazon account.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Click on "Hello, Sign in Account & Lists".
    3.  Click on "Sign in" button.
    4.  Enter valid email/phone number in the "Email or mobile phone number" field.
    5.  Click "Continue".
    6.  Enter an invalid password in the "Password" field.
    7.  Click "Sign in".
*   **Test Data:**
    *   Email: `valid_user@example.com`
    *   Password: `InvalidPassword123`
*   **Expected Result:** An error message "Incorrect password" or similar is displayed, and the user remains on the login page.
*   **Priority:** High
*   **Type:** Negative

**TC-AUTH-003: Validate user login with unregistered email/phone number**
*   **Title:** Validate user login with unregistered email/phone number
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Click on "Hello, Sign in Account & Lists".
    3.  Click on "Sign in" button.
    4.  Enter an unregistered email/phone number in the "Email or mobile phone number" field.
    5.  Click "Continue".
*   **Test Data:**
    *   Email: `unregistered_user@example.com`
*   **Expected Result:** An error message "We cannot find an account with that email address" or similar is displayed.
*   **Priority:** High
*   **Type:** Negative

**TC-AUTH-004: Check user logout functionality**
*   **Title:** Check user logout functionality
*   **Pre-conditions:** User is successfully logged in.
*   **Steps:**
    1.  Hover over "Hello, [User's Name] Account & Lists".
    2.  Click on "Sign Out" from the dropdown menu.
*   **Test Data:** N/A
*   **Expected Result:** User is logged out, and the "Hello, [User's Name] Account & Lists" text reverts to "Hello, Sign in Account & Lists".
*   **Priority:** Critical
*   **Type:** Functional

#### B. Product Search

**TC-SEARCH-001: Verify product search with a valid keyword**
*   **Title:** Verify product search with a valid keyword
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Enter "laptop" in the search bar.
    3.  Click the search icon/button.
*   **Test Data:**
    *   Search Term: `laptop`
*   **Expected Result:** Search results page is displayed with a list of laptops, and the search term "laptop" is visible in the search bar.
*   **Priority:** Critical
*   **Type:** Functional

**TC-SEARCH-002: Validate product search with a keyword yielding no results**
*   **Title:** Validate product search with a keyword yielding no results
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Enter "asdfghjklqwerty" in the search bar.
    3.  Click the search icon/button.
*   **Test Data:**
    *   Search Term: `asdfghjklqwerty`
*   **Expected Result:** A "No results found" message or similar is displayed, suggesting alternative searches.
*   **Priority:** High
*   **Type:** Negative

**TC-SEARCH-003: Check product search with empty input**
*   **Title:** Check product search with empty input
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Leave the search bar empty.
    3.  Click the search icon/button.
*   **Test Data:**
    *   Search Term: `(empty)`
*   **Expected Result:** The page remains on the homepage or navigates to a general browse page, without displaying an error or search results.
*   **Priority:** Medium
*   **Type:** Edge Case

**TC-SEARCH-004: Verify search results display relevant product information**
*   **Title:** Verify search results display relevant product information
*   **Pre-conditions:** Perform a successful product search (e.g., "laptop").
*   **Steps:**
    1.  Observe the displayed search results.
*   **Test Data:** N/A
*   **Expected Result:** Each search result item displays at least product image, title, price, and customer rating (if available).
*   **Priority:** High
*   **Type:** UI / Data Validation

#### C. Cart Management

**TC-CART-001: Verify adding a single item to the cart**
*   **Title:** Verify adding a single item to the cart
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Navigate to amazon.com.
    2.  Search for a product (e.g., "USB drive").
    3.  Click on a product from the search results to go to its detail page.
    4.  Click the "Add to Cart" button.
*   **Test Data:**
    *   Product: `USB drive`
*   **Expected Result:** The item is added to the cart, the cart icon updates to show "1" item, and a confirmation message (e.g., "Added to Cart") is displayed.
*   **Priority:** Critical
*   **Type:** Functional

**TC-CART-002: Validate updating item quantity in the cart**
*   **Title:** Validate updating item quantity in the cart
*   **Pre-conditions:** One item is already in the cart.
*   **Steps:**
    1.  Navigate to the Cart page.
    2.  Locate the quantity dropdown for the added item.
    3.  Change the quantity from "1" to "2".
*   **Test Data:**
    *   Initial Quantity: `1`
    *   New Quantity: `2`
*   **Expected Result:** The item quantity updates to "2", and the subtotal in the cart reflects the new quantity.
*   **Priority:** High
*   **Type:** Functional / Data Validation

**TC-CART-003: Check removing an item from the cart**
*   **Title:** Check removing an item from the cart
*   **Pre-conditions:** At least one item is in the cart.
*   **Steps:**
    1.  Navigate to the Cart page.
    2.  Click the "Delete" or "Remove" button next to an item.
*   **Test Data:** N/A
*   **Expected Result:** The item is removed from the cart, and the cart total updates accordingly. If it was the last item, the cart displays an "empty cart" message.
*   **Priority:** High
*   **Type:** Functional

**TC-CART-004: Verify adding multiple distinct items to the cart**
*   **Title:** Verify adding multiple distinct items to the cart
*   **Pre-conditions:** None.
*   **Steps:**
    1.  Add "USB drive" to cart (TC-CART-001).
    2.  Search for "HDMI cable".
    3.  Click on an HDMI cable product.
    4.  Click the "Add to Cart" button.
*   **Test Data:**
    *   Product 1: `USB drive`
    *   Product 2: `HDMI cable`
*   **Expected Result:** Both items are present in the cart, and the cart icon shows "2" items.
*   **Priority:** Medium
*   **Type:** Functional

**TC-CART-005: Validate cart persistence for logged-in users**
*   **Title:** Validate cart persistence for logged-in users
*   **Pre-conditions:** User is logged in.
*   **Steps:**
    1.  Add an item to the cart.
    2.  Log out (TC-AUTH-004).
    3.  Log back in with the same user (TC-AUTH-001).
    4.  Navigate to the Cart page.
*   **Test Data:** N/A
*   **Expected Result:** The item previously added to the cart is still present in the cart after logging back in.
*   **Priority:** High
*   **Type:** Business Logic

#### D. Checkout Process

**TC-CHECKOUT-001: Verify proceeding to checkout from the cart page**
*   **Title:** Verify proceeding to checkout from the cart page
*   **Pre-conditions:** At least one item is in the cart.
*   **Steps:**
    1.  Navigate to the Cart page.
    2.  Click the "Proceed to checkout" button.
*   **Test Data:** N/A
*   **Expected Result:** The user is redirected to the "Select a shipping address" or "Sign in to checkout" page.
*   **Priority:** Critical
*   **Type:** Functional

**TC-CHECKOUT-002: Validate selecting an existing shipping address**
*   **Title:** Validate selecting an existing shipping address
*   **Pre-conditions:** User is logged in and has at least one saved shipping address.
*   **Steps:**
    1.  Proceed to checkout (TC-CHECKOUT-001).
    2.  On the "Select a shipping address" page, select an existing address.
    3.  Click "Use this address" or "Continue".
*   **Test Data:**
    *   Saved Address: `123 Main St, Anytown, USA`
*   **Expected Result:** The user is redirected to the "Select a payment method" page.
*   **Priority:** High
*   **Type:** Functional

**TC-CHECKOUT-003: Check adding a new shipping address during checkout**
*   **Title:** Check adding a new shipping address during checkout
*   **Pre-conditions:** User is logged in.
*   **Steps:**
    1.  Proceed to checkout (TC-CHECKOUT-001).
    2.  On the "Select a shipping address" page, click "Add a new address".
    3.  Fill in all required fields for a new address.
    4.  Click "Add address" or "Use this address".
*   **Test Data:**
    *   Full Name: `John Doe`
    *   Address Line 1: `456 Oak Ave`
    *   City: `Otherville`
    *   State: `CA`
    *   Zip Code: `90210`
    *   Phone Number: `555-123-4567`
*   **Expected Result:** The new address is saved and selected, and the user is redirected to the "Select a payment method" page.
*   **Priority:** Medium
*   **Type:** Functional / Data Validation

**TC-CHECKOUT-004: Verify selecting an existing payment method**
*   **Title:** Verify selecting an existing payment method
*   **Pre-conditions:** User is logged in and has at least one saved payment method.
*   **Steps:**
    1.  Proceed to checkout and select a shipping address (TC-CHECKOUT-002).
    2.  On the "Select a payment method" page, select an existing payment method (e.g., credit card).
    3.  Click "Continue" or "Use this payment method".
*   **Test Data:**
    *   Saved Payment Method: `Visa ending in ****1234`
*   **Expected Result:** The user is redirected to the "Review your order" page.
*   **Priority:** High
*   **Type:** Functional

**TC-CHECKOUT-005: Validate order summary details on the review page**
***Title:** Validate order summary details on the review page
*   **Pre-conditions:** User has proceeded to the "Review your order" page.
*   **Steps:**
    1.  Observe the order summary section.
*   **Test Data:** N/A
*   **Expected Result:** The order summary accurately displays the selected items, quantities, shipping address, payment method, subtotal, shipping cost, and estimated total.
*   **Priority:** High
*   **Type:** Data Validation / UI

**TC-CHECKOUT-006: Check "Place your order" button functionality (pre-payment)**
*   **Title:** Check "Place your order" button functionality (pre-payment)
*   **Pre-conditions:** User is on the "Review your order" page.
*   **Steps:**
    1.  Click the "Place your order" button.
*   **Test Data:** N/A
*   **Expected Result:** The system attempts to process the order. Depending on the environment, this might lead to a confirmation page, a payment processing page, or a simulated success/failure message without actual transaction. (Note: Actual payment processing is out of scope for this test case).
*   **Priority:** Critical
*   **Type:** Functional

---

### Appendix

#### 1. Coverage Summary by Layer:

*   **Functional:** 15 (TC-AUTH-001, TC-AUTH-004, TC-SEARCH-001, TC-CART-001, TC-CART-002, TC-CART-003, TC-CART-004, TC-CHECKOUT-001, TC-CHECKOUT-002, TC-CHECKOUT-003, TC-CHECKOUT-004, TC-CHECKOUT-006)
*   **Data Validation:** 4 (TC-SEARCH-004, TC-CART-002, TC-CHECKOUT-003, TC-CHECKOUT-005)
*   **Negative/Edge Case:** 4 (TC-AUTH-002, TC-AUTH-003, TC-SEARCH-002, TC-SEARCH-003)
*   **Business Logic:** 1 (TC-CART-005)
*   **UI:** 2 (TC-SEARCH-004, TC-CHECKOUT-005)

#### 2. Assumptions:

*   A standard Amazon.com website structure and behavior are assumed.
*   Test data for valid users, products, and addresses are assumed to exist in the test environment.
*   The scope of "checkout process" ends at the point of clicking "Place your order" without actual financial transaction processing.
*   Basic UI elements (buttons, text fields, links) are functional and visible.

#### 3. Out-of-Scope Recommendations:

*   **User Registration & Account Management:** Creating new accounts, managing profile details, password recovery.
*   **Advanced Search & Filtering:** Detailed filtering by brand, price range, customer reviews, sorting options beyond basic relevance.
*   **Product Details Page:** In-depth validation of product specifications, images, videos, customer reviews, Q&A, "Buy Now" functionality.
*   **Payment Processing:** Actual financial transactions, various payment gateway integrations, error handling for specific payment failures.
*   **Order History & Tracking:** Viewing past orders, tracking shipments, managing returns.
*   **Non-Functional Testing:** Performance, security (beyond basic negative login), accessibility, localization.
*   **Specific Promotions/Coupons:** Applying discount codes, gift cards.

#### 4. Documents that would improve coverage:

*   **Low-Level Design (LLD) / API Specifications (Swagger/OpenAPI):** To generate comprehensive API/Integration tests for user authentication, cart updates, and checkout steps, including specific request/response payloads, error codes, and data constraints.
*   **UI/UX Wireframes / Component Specifications:** To validate exact visual states, responsive behavior, and specific interaction patterns for all UI elements, especially during dynamic updates (e.g., cart count, error messages).
*   **Non-Functional Requirements (NFRs):** To design performance tests (load, stress, concurrency) for critical paths like login, search, and checkout, and to define specific security test cases.
*   **Detailed Acceptance Criteria:** For each specific feature, to ensure all nuances and edge cases are explicitly covered.