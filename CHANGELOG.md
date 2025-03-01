## [2025-03-01]

**Refined link updates and expanded event binding**

- **Consolidated “link valid/invalid” logic**
  Now relies on `updateLinkState` to set link attributes and classes in a single place, rather than manually toggling classes within each handle update function.

- **Unified copy button event binding**
  Removed the inline `onclick` attributes on copy buttons and now bind them through JavaScript in `initializeInputHandlers`.

- **Minor cleanup**
  Removed redundant code paths in `updateBlueskyLink` and `updateMastoLink`, making them more consistent with the rest of the code.
## [2025-02-28]

**Refactoring with Logging Utility, Validation Improvements, and Consolidated Display Logic**

- **Dedicated Logging Utility**
  Introduced `logCall(funcName, message)` to standardize console logging of function calls and provide consistent debug output.

- **Renamed and Reorganized Validation Functions**
  Replaced `isValidBlueskyOutput` and `isValidFediverseOutput` with `isValidBlueskyToFediverseFormat` and `isValidFediverseToBlueskyFormat`, respectively. Each validation function now invokes `logCall` for clearer traceability.

- **New Formatting and Display-Update Patterns**
  Removed older “updateXYZ” style functions (e.g., `updateFediverseDisplay`) in favor of two core converters, `convertBlueskyToFediverseFormat` and `convertFediverseToBlueskyFormat`. Consolidated repeated logic into a reusable utility, `updateDisplayWithValidation`, so validation checks and DOM updates happen consistently.

- **Streamlined “Mastodon” and “Bluesky” Link Updates**
  Enhanced `updateMastoLink` to clean handles and display invalid states with `updateLinkState` rather than hardcoding repeated class toggles. Similarly refactored `updateBlueskyLink` to follow the same pattern.

- **Eliminated Inline Event Handlers**
  Moved all input-field event bindings into the `initializeInputHandlers` function to ensure each field fires only one event handler, preventing duplicate calls and simplifying the code.
