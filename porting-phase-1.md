# Porting Phase 1: Infrastructure & Build System Updates (The Foundation)

**Goal:** Establish the build environment for v26.1.2 and update all versioning variables in the project configuration.

**Target Versions:**
*   Minecraft Version: 26.1.2
*   Loom Version: 1.16-SNAPSHOT
*   Loader Version: 0.19.2
*   Fabric API Version: 0.149.1+26.1.2

**Action Items:**

1.  **Update `build.gradle`:**
    *   Locate and update `rootProject.minecraft_version` to `26.1.2`.
    *   Update `dev.architectury.loom` version in `build.gradle` to `1.16-SNAPSHOT`.
    *   Review the `architectury` block to ensure all version variables (`minecraft_version`, `neoforge_version`, etc.) are correctly configured using the new target versions.
2.  **Dependency Versioning:**
    *   **Fabric API:** Update the dependency for the Fabric API to `0.149.1+26.1.2` or its nearest stable counterpart compatible with v26.1.2.
    *   **General Dependencies:** Review and update all other dependency version identifiers in the `dependencies` block of `build.gradle` (e.g., `jei_version`, `jade_neoforge_id`, `parchment_version`).
3.  **Tooling/Plugin Check:**
    *   Verify that `com.github.johnrengelman.shadow` and `me.modmuss50.mod-publish-plugin` versions are compatible with the new Minecraft environment and Gradle setup.

**Reference Material:**
*   `docs/fabric/porting/porting.summary.md` (General porting advice)
*   `docs/fabric/porting/fabric-api.summary.md` (API specific changes)

**Verification Step:**
*   Successfully compile the entire project using the new configuration.