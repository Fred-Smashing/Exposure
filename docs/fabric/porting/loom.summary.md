# Summary: Loom Mappings Porting Guide

## Key Porting Steps

*   **Loom Version:** Upgrade `dev.architectury.loom` to a version specifically designed for Minecraft v26.1.2.
*   **Loot Table & Data Generation:** Review how data generators and loot tables are structured in the new version, as Loom handles these extensively.
*   **Mixin Compatibility:** Ensure that mixins are compatible with the new Minecraft class structures and mapping names provided by Loom.
*   **Build Script Adjustments:** Update `build.gradle` to correctly invoke Loom tasks for the new Minecraft version.

---

*(Note: This summary is based on the general focus of Loom migration documentation.)*