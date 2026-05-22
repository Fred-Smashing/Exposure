# Porting Phase 4: Quality Assurance & Testing

**Goal:** Verify that all features work as intended in the v26.1.2 environment and finalize the port.

**Action Items:**

1.  **Testing Execution:**
    *   Run all existing unit tests (`common/src/test/java/`) to catch immediate API breakage.
    *   Write or update integration tests specifically targeting v26.1.2 features and cross-platform logic.
2.  **Manual Quality Assurance (QA):**
    *   Deploy the mod to a v26.1.2 development environment.
    *   Perform comprehensive end-to-end feature testing, including:
        *   Camera controls (FOV, rotation, exposure settings).
        *   Image effect application (testing `HSBEffect.java`, `LevelsEffect.java`, etc.).
        *   Data persistence (Photo frames, recipes).
        *   Compatibility with major mods (JEI, Jade).

**Success Criteria:**
*   All tests pass.
*   All core mod functionality works correctly in the v26.1.2 client.
*   The build process is stable and reproducible.