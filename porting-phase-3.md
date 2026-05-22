# Porting Phase 3: Resource and Data Updates (The Assets)

**Goal:** Ensure all assets and data files are correctly formatted for v26.1.2, ensuring data compatibility with the new Minecraft version.

**Action Items:**

1.  **Data Pack Validation:**
    *   Review the structure of data packs located in `common/src/main/resources/data/minecraft` and `fabric/src/main/resources/data/exposure`.
    *   Ensure all JSON schema elements (advancements, recipes, etc.) are compliant with v26.1.2 data format specifications.
2.  **Rendering Pipeline Check:**
    *   Verify the image export logic (relying on the Minecraft client rendering API) remains functional with the new client rendering API. This may require adjustments in `common/src/main/java/io/github/mortuusars/exposure/data/export/ExportLook.java` and `ExportSize.java`.
3.  **Resource Files:**
    *   Check all JSON configuration files (like `filters.json`, `photo_papers.json`) to ensure they correctly reference new asset IDs or data types introduced in v26.1.2.

**Reference Material:**
*   `docs/fabric/porting/porting.summary.md` (General resource guidelines)

**Verification Step:**
*   Load the game using the modified data packs without errors.
*   Successfully render and export an image using the mod functionality.