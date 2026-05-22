## Project Structure Diagram
```
├── build.gradle
├── CHANGELOG.md
├── common/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── io/
│   │   │   │       └── github/
│   │   │   │           └── mortuusars/
│   │   │   │               └── exposure/
│   │   │   │                   ├── integration/
│   │   │   │                   │   ├── jei/
│   │   │   │                   │   │   └── neoforge/
│   │   │   │                   │   └── kubejs/
│   │   │   │                   ├── neoforge/
│   │   │   │                   │   ├── api/
│   │   │   │                   │   ├── block/
│   │   │   │                   │   ├── event/
│   │   │   │                   │   ├── loot/
│   │   │   │                   │   ├── mixin/
│   │   │   │                   │   └── network/
│   │   │   ├── resources/
│   │   │   │   ├── data/
│   │   │   │   │   ├── create/
│   │   │   │   │   │   └── recipe/
│   │   │   │   │   ├── exposure/
│   │   │   │   │   └── neoforge/
│   │   │   │   └── META-INF/
│   │   │   └── pack.mcmeta
│   │   └── test/
│   └── resources/
├── docs/
├── fabric/
├── neoforge/
│   ├── build/
│   │   ├── classes/
│   │   ├── generated/
│   │   ├── libs/
│   │   ├── processIncludeJars/
│   │   ├── resources/
│   │   └── tmp/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── io/
│   │   │   │       └── github/
│   │   │   │           └── mortuusars/
│   │   │   │               └── exposure/
│   │   │   │                   ├── integration/
│   │   │   │                   │   ├── jei/
│   │   │   │                   │   │   └── neoforge/
│   │   │   │                   │   └── kubejs/
│   │   │   │                   ├── neoforge/
│   │   │   │                   │   ├── api/
│   │   │   │                   │   ├── block/
│   │   │   │                   │   ├── event/
│   │   │   │                   │   ├── loot/
│   │   │   │                   │   ├── mixin/
│   │   │   │                   │   └── network/
│   │   │   ├── resources/
│   │   │   │   ├── data/
│   │   │   │   │   ├── create/
│   │   │   │   │   │   └── recipe/
│   │   │   │   │   ├── exposure/
│   │   │   │   │   └── neoforge/
│   │   │   │   └── META-INF/
│   │   └── test/
│   └── tmp/
├── README.md
├── LICENSE.md
└── gradlew
```

## Directory Summaries

### `build.gradle`
- Main build configuration for the mod using Gradle.
- Manages dependencies, plugins, and build tasks.

### `CHANGELOG.md`
- Tracks release notes and version history.

### `common/`
- Shared code across mod platforms (Fabric, NeoForge, etc.).
- Contains Java source files, resource configurations, and mixins.

### `docs/`
- Project documentation and guides.

### `fabric/`
- Fabric-specific mod files and configurations.

### `neoforge/`
- NeoForge-specific mod files, build outputs, and resources.
- Includes compiled classes, resources, and build artifacts.

### `README.md`
- Project overview, features, and links to documentation.

### `LICENSE.md`
- MIT License for open-source distribution.

### `gradlew`
- Gradle wrapper scripts for building the project.

## File Summaries

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/ImageEffect.java
This interface defines the `ImageEffect` contract, which is the core mechanism for applying various visual filters and modifications to an image. It provides a static registry of common effects like `CENSORED`, `BLACK_AND_WHITE`, and utility methods for creating complex composite effects.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/AgedHSBEffect.java
This pixel effect modifies colors by simulating the appearance of aged film. It adjusts the color based on black and white points (Levels adjustment) and blends the resulting color with a specified tint using HSB manipulation.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/AgedHSLUVEffect.java
This pixel effect simulates aged film using the HSLUV color space for color manipulation. It applies a tint and adjusts color ranges based on defined black and white points for a more complex visual effect than the HSB version.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/BlackAndWhiteEffect.java
This pixel effect converts a color image to grayscale or black and white using a weighted average formula, applying different coefficients (rWeight, gWeight, bWeight) to the red, green, and blue channels.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/ColorBalanceEffect.java
This pixel effect adjusts the color balance of an image by applying weighted scaling factors (r, g, b) to the original red, green, and blue color channels. These factors allow for shifting the color tone of the image.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/ContrastEffect.java
This pixel effect modifies the contrast of an image. It uses a contrast factor to increase or decrease the difference between light and dark tones in the image.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/ExposureEffect.java
This pixel effect applies exposure simulation by adjusting brightness and color saturation. It calculates a bias factor based on the image's lightness and then modifies the red, green, and blue channels, redistributing excess light to prevent clipping.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/HSBEffect.java
This pixel effect modifies the Hue, Saturation, and Brightness (HSB) of a color. By adjusting these parameters, it allows for targeted color shifts, saturation changes, and brightness adjustments.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/LevelsEffect.java
This pixel effect performs a levels adjustment on the image. It allows the user to manually define shadow, midtone, and highlight points, along with black and white levels, to control the contrast and tonal range of the image.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/MultiplyEffect.java
This pixel effect multiplies the color of a pixel by a tint color. It darkens the image by blending the original pixel with the multiply color, resulting in a color overlay effect.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/NegativeEffect.java
This simple pixel effect inverts the colors of an image by subtracting each color component from 255, creating a photographic negative effect.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/NegativeFilmEffect.java
This pixel effect simulates negative film properties by inverting colors and reducing opacity based on lightness. This gives the image a more realistic film negative look.

### common/src/main/java/io/github/mortuusars/exposure/client/image/modifier/pixel/NoiseEffect.java
This pixel effect applies random Gaussian noise to the image. The intensity of the noise is dynamically adjusted based on the brightness of the pixel, resulting in more pronounced noise in darker areas.

### common/src/main/java/io/github/mortuusars/exposure/client/image/renderable/RenderableImage.java
This interface represents an image that is ready for rendering. It provides methods to access the underlying `Image`, retrieve a unique `RenderableImageIdentifier`, and allows for modifications using a function or an `ImageEffect`.

### common/src/main/java/io/github/mortuusars/exposure/client/image/renderable/RenderableImageIdentifier.java
This record uniquely identifies a rendered image. It stores a base identifier and an optional variant, and provides a utility method to convert it into a Minecraft `ResourceLocation`.

### common/src/main/java/io/github/mortuusars/exposure/client/input/Key.java
This functional interface defines a flexible system for key bindings, allowing keys to be matched based on a combination of key code, scan code, action state (press/release), and modifier keys. It provides convenience methods for creating complex key combinations.

### common/src/main/java/io/github/mortuusars/exposure/client/input/KeyBinding.java
This record links a `Key` matcher (defining the required inputs) to a `Supplier<Boolean>` handler (defining the action to take). It provides methods to check if the key press or release event matches and if the associated action handler returns true.

### common/src/main/java/io/github/mortuusars/exposure/client/input/KeyBindings.java
This class manages a collection of `KeyBinding` instances. It provides methods to add, remove, and iterate through bindings, allowing the client to check if any bound action is triggered by a specific key press or release event.

### common/src/main/java/io/github/mortuusars/exposure/client/input/KeyboardHandler.java
This class manages keyboard input handling for the mod. It provides a centralized way to register and access the key mapping for opening camera controls, and includes a method to process key presses when the viewfinder is active.

### common/src/main/java/io/github/mortuusars/exposure/client/input/Modifier.java
This interface defines standard input modifiers (Shift, Control, Alt, Super) used by the key handling system to check for specific key combinations.

### common/src/main/java/io/github/mortuusars/exposure/client/input/MouseHandler.java
This class centralizes mouse input handling for the mod. It provides methods to check for button presses, handle scrolling, and manages mouse sensitivity modifications, especially when the viewfinder is active, enabling camera control functions.

### common/src/main/java/io/github/mortuusars/exposure/client/render/CameraStandEntityRenderer.java
This custom `EntityRenderer` is responsible for rendering the `CameraStandEntity` and its attached camera components. It handles the proper positioning and rotation of the camera model relative to the camera stand block and mount.

### common/src/main/java/io/github/mortuusars/exposure/client/render/FovModifier.java
This class manages Field of View (FOV) modifications, allowing the mod to temporarily override the FOV when the viewfinder is active. It includes an animation system to smoothly transition back to the original FOV when the viewfinder is closed.

### common/src/main/java/io/github/mortuusars/exposure/client/render/GammaModifier.java
This class provides a static mechanism to temporarily modify the game's gamma settings. It allows for applying a gamma offset before a capture and ensuring that the original gamma is restored afterward.

### common/src/main/java/io/github/mortuusars/exposure/client/render/GlassPhotographFrameEntityRenderer.java
This custom `EntityRenderer` is used to correctly render the `GlassPhotographFrameEntity`. It handles model selection based on the frame's size and overrides the rendering type to use a cutout sheet.

### common/src/main/java/io/github/mortuusars/exposure/client/render/ItemFramePhotographRenderer.java
This utility class provides a static method to render a `PhotographItem` within a Minecraft `ItemFrame`. It applies specific rotations and scaling transformations to correctly position the photograph within the frame's bounds.

### common/src/main/java/io/github/mortuusars/exposure/client/render/PhotographFrameEntityRenderer.java
This entity renderer is responsible for drawing the `PhotographFrameEntity`. It handles rendering the frame itself, as well as rendering the photograph contained within, applying various scaling and rotation adjustments based on the frame's size and rotation.

### common/src/main/java/io/github/mortuusars/exposure/client/render/photograph/PhotographStyle.java
This record defines a specific photographic style by associating an `ImageEffect` modifier with specific textures for the paper and overlay. It provides static methods to retrieve the appropriate style based on the `PhotographItem`.

### common/src/main/java/io/github/mortuusars/exposure/client/render/photograph/PhotographStyles.java
This class acts as a registry for `PhotographStyle` objects, mapping each `PhotographType` to a specific style. It ensures that a unique style is registered for every photograph type used in the mod.