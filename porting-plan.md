# Porting Plan: Minecraft v26.1.2 (Revised)

**Goal:** Update the Exposure mod from its current supported versions (up to 1.21.1) to fully support Minecraft v26.1.2.

**Target Versions (As per Fabric Documentation):**
*   Minecraft Version: 26.1.2
*   Loom Version: 1.16-SNAPSHOT
*   Loader Version: 0.19.2
*   Fabric API Version: 0.149.1+26.1.2

**Current State Analysis:**
The project utilizes **Architectury**, which provides a unified codebase (`common/`) while managing platform-specific implementations for **NeoForge** and **Fabric**. The build is managed by **Gradle**. The current version appears to target Minecraft 1.21.1.

**Key Porting Challenges:**
1.  **API Changes:** Minecraft and its associated Forge/Fabric APIs change significantly between major versions.
2.  **Dependency Compatibility:** All external libraries (JEI, Jade, ParchmentMC, etc.) must be updated to v26.1.2 compatible versions (e.g., Fabric API 0.149.1+26.1.2).
3.  **Build System Configuration:** The `build.gradle` must be rigorously updated to reflect the new target version and dependencies.

---

## ⚙️ Phase 1: Infrastructure & Build System Updates (The Foundation)

**Goal:** Establish the build environment for v26.1.2.

1.  **Update `build.gradle`:**
    *   Locate and update `rootProject.minecraft_version` to `26.1.2`.
    *   Update `dev.architectury.loom` version to `1.16-SNAPSHOT`.
    *   Ensure all version variables (`minecraft_version`, `neoforge_version`, etc.) are correctly configured using the new target versions.
2.  **Dependency Versioning:**
    *   Update Fabric-specific dependencies (Fabric API, etc.) to `0.149.1+26.1.2` or their nearest stable counterparts for v26.1.2.
    *   Review dependencies listed in `common/src/main/java/io/github/mortuusars/exposure/` to ensure they have v26.1.2 compatibility.

## 💻 Phase 2: Core Code Refactoring (The Logic)

**Goal:** Adapt the core logic and platform interfaces to match the v26.1.2 APIs, guided by the Fabric Porting documentation.

1.  **API Migration Review (Fabric Docs Reference):**
    *   Use the content in `docs/fabric/porting/porting.summary.md` and `docs/fabric/porting/fabric-api.summary.md` to identify major API shifts.
    *   Targeted review of Fabric API changes in the new version.
2.  **Event System Updates:**
    *   Verify that event handlers (`FabricS2CPackets.java`) are correctly registering listeners and handling event payloads under the new API structure.
3.  **Mixins and Mappings:**
    *   Check the `docs/fabric/porting/mappings.summary.md` for Mojang mapping changes.
    *   Update `Mixins` (`mixin/` directory) and any associated data generation logic to align with the new mapping scheme and Loom version (1.16-SNAPSHOT).

## 🎨 Phase 3: Resource and Data Updates (The Assets)

**Goal:** Ensure all assets and data files are correctly formatted for v26.1.2.

1.  **Data Pack Validation:**
    *   Review `common/src/main/resources/data/minecraft` and `fabric/src/main/resources/data/exposure` for JSON schema compliance for v26.1.2.
2.  **Rendering Pipeline Check:**
    *   Verify that the image export logic remains functional with the new client rendering API, referencing the general porting guide.

## ✅ Phase 4: Quality Assurance & Testing

**Goal:** Verify functionality in the v26.1.2 environment.

1.  **Testing:** Run all unit and integration tests (`common/src/test/java/`).
2.  **QA:** Manual feature testing across all major camera functions.

---
**Estimated Effort:** High.