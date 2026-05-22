# Porting Plan: Minecraft v26.1.2

**Goal:** Update the Exposure mod from its current supported versions (up to 1.21.1) to fully support Minecraft v26.1.2.

**Current State Analysis:**
The project utilizes **Architectury**, which provides a unified codebase (`common/`) while managing platform-specific implementations for **NeoForge** and **Fabric**. The build is managed by **Gradle**. The current version appears to target Minecraft 1.21.1.

**Key Porting Challenges:**
1.  **API Changes:** Minecraft and its associated Forge/Fabric APIs change significantly between major versions.
2.  **Dependency Compatibility:** All external libraries (JEI, Jade, ParchmentMC, etc.) must have corresponding v26.1.2 compatibility.
3.  **Gradle Configuration:** The `build.gradle` must be updated to reflect the new versioning scheme.

---

## ⚙️ Phase 1: Infrastructure & Build System Updates (The Foundation)

**Goal:** Establish the build environment to recognize v26.1.2.

1.  **Update `build.gradle`:**
    *   Locate and update `rootProject.minecraft_version` (or equivalent properties) in `build.gradle` to `26.1.2`.
    *   Review the `architectury` block and ensure all version variables (`minecraft_version`, `neoforge_version`, etc.) are correctly configured for the new version.
2.  **Update Loom/Architectury Plugins:**
    *   Check the latest compatible versions of `dev.architectury.loom` and `architectury-plugin` for Minecraft v26.1.2. The current snapshot versions (`1.7-SNAPSHOT`, `3.4-SNAPSHOT`) will likely need upgrading.
3.  **Dependency Versioning:**
    *   Update all version identifiers for external dependencies in the `dependencies` block of `build.gradle` (e.g., `jei_version`, `jade_neoforge_id`, etc.) to their v26.1.2 compatible versions.

## 💻 Phase 2: Core Code Refactoring (The Logic)

**Goal:** Adapt the core logic and platform interfaces to match the v26.1.2 APIs.

1.  **Analyze Breaking Changes:**
    *   Perform a targeted review of Minecraft v26.1.2 changelogs for any changes to the APIs used by Exposure (e.g., Block registration, Entity components, Event handling, Data Generation).
2.  **`common/` Module Review:**
    *   Review the core logic in `common/src/main/java/io/github/mortuusars/exposure/` files.
    *   Any logic relying on deprecated methods or classes must be refactored. This is crucial for the image effects and core data handling.
3.  **Platform Integration Updates:**
    *   **`fabric/` and `neoforge/` Modules:** Update platform-specific integration code.
        *   Verify that event handlers (e.g., `FabricS2CPackets.java`, `NeoForgeClientEvents.java`) are correctly registering listeners for the new event system in v26.1.2.
        *   Check the `Mixins` (`mixin/` directory) for any Mojang mapping changes that require updates.

## 🎨 Phase 3: Resource and Data Updates (The Assets)

**Goal:** Ensure all assets and data files are correctly formatted for v26.1.2.

1.  **Resource Pack Updates:**
    *   Review `common/src/main/resources/data/minecraft` and `fabric/src/main/resources/data/exposure` for any changes in data pack structure or required metadata (e.g., advancements, recipes).
    *   Ensure JSON schema compliance for v26.1.2.
2.  **Asset Exports:**
    *   Verify that the image export logic (which depends on the Minecraft rendering pipeline) remains functional with the new client rendering API. This may require adjustments in `ExportLook.java` and `ExportSize.java`.

## ✅ Phase 4: Quality Assurance & Testing

**Goal:** Verify that all features work as intended in the new environment.

1.  **Unit and Integration Tests:**
    *   Run all existing unit tests (`common/src/test/java/`). Fix any tests that fail due to API changes.
    *   Write or update integration tests to ensure the cross-platform logic works correctly for v26.1.2.
2.  **Manual QA:**
    *   Deploy to a v26.1.2 development environment.
    *   Perform full feature testing: Camera controls, effect application, data persistence (photo frames, recipes), and compatibility with other major mods (JEI, Jade).

---
**Estimated Effort:** High. Due to the breadth of API changes in a major Minecraft update, this will be an extensive refactoring effort.