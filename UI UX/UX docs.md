# Verus Marketplace App - UI/UX and Functionality Guidelines (Tauri + Svelte)

## 1. Overall Architecture

- Tauri for the core application framework
- Svelte for the frontend UI
- Direct communication with local Verus node via RPC

## 2. Main Components and Functionality

### 2.1 Home/Dashboard
- Svelte component: `Dashboard.svelte`
- Features:
  - Navigation links to all other pages/components/functions
  - Display of current block height
- RPC used:
  - `getmininginfo` (to display "blocks" result)

### 2.2 My Identities
- Svelte component: `MyIdentities.svelte`
- Features:
  - List of user's identities
  - display in a table:  name, parent (use getcurrency i-address and display its "name"), primaryaddresses
  = user can click on ID and then "makeoffer"
- RPC used:
  - `listidentities`

### 2.3 My Currencies
- Svelte component: `MyCurrencies.svelte`
- Features:
  - Display of "reserve balance" for each currency (name & amount)
  - Search function for address balance
  - user can click a currency balance and then "makeoffer"
- RPCs used:
  - `getwalletinfo` (to show "reserve balance")
  - `getcurrencybalance` (for searching balance of ID@, R-address, or z-address)

### 2.4 ID Lookup
- Svelte component: `IDLookup.svelte`
- Features:
  - Search and display identity details
  - use ui to hide and show the details in relevant sections/categories
- RPC used:
  - `getidentity`

### 2.5 Currency Lookup
- Svelte component: `CurrencyLookup.svelte`
- Features:
  - Search and display currency details
  - use ui to hide and show the details in relevant sections/categories
- RPC used:
  - `getcurrency`

### 2.6 Currency Listing
- Svelte component: `CurrencyListing.svelte`
- Features:
  - List all available currencies
  - display relevant details in a table
  - user clicks currency and that uses the "getcurrency" RPC to display the info about the selected currency
- RPC used:
  - `listcurrencies`

### 2.7 My Offers
- Svelte component: `MyOffers.svelte`
- Features:
  - List user's open offers
  - display friendly names instead of i-addresses, display by categories
  - Option to close offers (check boxes and use those txids to populate the closeoffers command)
- RPCs used:
  - `listopenoffers`
  - `closeoffer`

### 2.8 Offers Search
- Svelte component: `OffersSearch.svelte`
- Features:
  - Search offers by ID@ or currency
  - use getidentity "i-address" or getcurrency "i-address" to get and display the friendly names instead of i=addresses in the offers search ui
  - users can click the offer and it will populate the takeoffer page, including the "txid" and other relevant details
- RPC used:
  - `getoffers` (with option for ID@ or currency true)

### 2.9 Make Offer
- Svelte component: `MakeOffer.svelte`
- Features:
  - Interface for creating 4 types of offers:
    1. ID for ID
    2. ID for Currency
    3. Currency for ID
    4. Currency for Currency
    In the form:  when ID is in the "for" side, the identity json should include the required parameters "name", "parent", "primaryaddresses", "minimumsignatures"... and include the optional parameters "revocationauthority", "recoveryauthority", "privateaddress"
- RPC used:
  - `makeoffer`

### 2.10 Take Offer
- Svelte component: `TakeOffer.svelte`
- Features:
  - Interface for accepting 4 types of offers:
    1. ID for ID
    2. ID for Currency
    3. Currency for ID
    4. Currency for Currency
    In the form:  when ID is in the "accept" side, the identity json should include the required parameters "name", "parent", "primaryaddresses", "minimumsignatures"... and include the optional parameters "revocationauthority", "recoveryauthority", "privateaddress"
- RPC used:
  - `takeoffer`

### 2.11 Create ID
- Svelte component: `CreateID.svelte`
- Features:
  - Two-step process for creating a new identity
- RPCs used:
  - `registernamecommitment`
  - `registeridentity`

### 2.12 Create Currency
- Svelte component: `CreateCurrency.svelte`
- Features:
  - Interface for defining and submitting a new currency
- RPCs used:
  - `definecurrency`
  - `sendrawtransaction` (to submit the "hex" result from definecurrency)

## 3. User Experience Considerations

### 3.1 Navigation
- Implement a sidebar or top navigation bar for easy access to all components
- Use Svelte's routing (e.g., svelte-routing) for smooth navigation between components

### 3.2 Real-time Updates
- Implement polling or WebSocket connection for live updates of block height on the dashboard

### 3.3 Form Handling
- Use Svelte's built-in form binding for efficient form handling in offer creation and ID/currency creation

### 3.4 Error Handling
- Create a global error store to manage and display errors from RPC calls
- Use try-catch blocks in async functions that make RPC calls

### 3.5 Loading States
- Implement loading indicators for operations that may take time (e.g., RPC calls, offer creation)

## 4. Security Considerations

### 4.1 Input Validation
- Implement client-side validation for all input fields
- Ensure server-side validation is also in place for all RPC calls

### 4.2 Sensitive Data Handling
- Use Tauri's secure storage for saving any sensitive information
- Ensure that private keys or sensitive wallet information are never exposed in the UI

## 5. Performance Optimizations

### 5.1 Caching
- Implement caching for frequently accessed data (e.g., user's identities, currencies)
- Use Svelte stores to manage application state efficiently

### 5.2 Lazy Loading
- Implement lazy loading of components that are not immediately needed on initial app load

## 6. Testing Strategy

### 6.1 Unit Testing
- Write unit tests for each Svelte component using a testing framework like Jest

### 6.2 Integration Testing
- Test the integration between the Svelte frontend and the Tauri backend

### 6.3 E2E Testing
- Implement end-to-end tests to ensure all components work together as expected

## 7. Accessibility

- Ensure all components are keyboard navigable
- Use ARIA attributes where necessary to improve screen reader compatibility
- Maintain sufficient color contrast for all text and important UI elements

## 8. Responsive Design

- Ensure the application is usable on various screen sizes
- Implement a responsive design that adapts to desktop, tablet, and mobile views

This structure provides a clear roadmap for developing each component of your Verus Marketplace app, with a focus on the specific RPCs and functionalities you've outlined. Each section can be developed as a separate Svelte component, making the development process modular and manageable.
