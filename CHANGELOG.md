## [2025-02-28]

Added a dedicated logging utility. Introduced logCall(funcName, message) to standardize console logging of function calls and provide consistent debug output.

Renamed and reorganized validation functions. Replaced isValidBlueskyOutput / isValidFediverseOutput with isValidBlueskyToFediverseFormat / isValidFediverseToBlueskyFormat, respectively. Each validation function now invokes logCall for clearer traceability.

Introduced new formatting and display-update patterns. Removed older “updateXYZ” style functions (e.g., updateFediverseDisplay) in favor of two core converters:

- convertBlueskyToFediverseFormat
- convertFediverseToBlueskyFormat

Consolidated repeated logic into a reusable utility, updateDisplayWithValidation, so that validation checks and DOM updates are performed consistently.

Streamlined “Mastodon” and “Bluesky” link updates. Enhanced updateMastoLink to clean handles and display invalid states with updateLinkState, rather than hardcoding repeated class toggles. Similarly refactored updateBlueskyLink to follow the same pattern.

Eliminated inline event handlers. Moved all input-field event bindings into the initializeInputHandlers function, to ensures each field fires only one event handler, preventing duplicate calls and making the code simpler to maintain.