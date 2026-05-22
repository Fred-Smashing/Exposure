# Porting Phase 2: Core Code Refactoring (The Logic)

**Goal:** Adapt the core logic, event handling, and platform interfaces to match the v26.1.2 APIs, utilizing the Fabric Porting documentation for guidance.

**Action Items:**

1.  **API Migration Review (Documentation Guided):**
    *   Use the content in `docs/fabric/porting/porting.summary.md` and `docs/fabric/porting/fabric-api.summary.md` to identify major API shifts (e.g., changes to blocks, entities, or core game functions).
    *   Perform a targeted review of the Minecraft v26.1.2 changelogs for these specific areas.
2.  **`common/` Module Review:**
    *   Review core logic in `common/src/main/java/io/github/mortuusars/exposure/`.
    *   Refactor any logic relying on deprecated methods or classes to align with v26.1.2. This applies specifically to image effects and core data handling logic.
3.  **Platform Integration Updates:**
    *   **Event System:** Verify that event handlers (e.g., `FabricS2CPackets.java` in `fabric/`) are correctly registering listeners and handling event payloads under the new API structure.
    *   **Mixins and Mappings:**
        *   Consult `docs/fabric/porting/mappings.summary.md` for Mojang mapping changes.
        *   Update `Mixins` (`mixin/` directory) and associated data generation logic to align with the new mapping scheme and Loom version (1.16-SNAPSHOT).

**Reference Material:**
*   `docs/fabric/porting/porting.summary.md`
*   `docs/fabric/porting/fabric-api.summary.md`
*   `docs/fabric/porting/mappings.summary.md`

**Verification Step:**
*   Run all unit tests successfully, ensuring core logic is sound.