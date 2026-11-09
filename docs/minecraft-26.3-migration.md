# Minecraft 26.3 migration

## Starting snapshot

- Recorded: November 9, 2026.
- Source branch: `MC-Fabric-26.2`.
- Source commit: `727fbfb6134fa7ad74ad9fb15901563b79c77893`.
- Working tree was clean before creating `port/minecraft-26.3`.
- Mod version: `3.13`; Minecraft: `26.2`.
- Fabric Loader: `0.19.3`; Fabric API: `0.152.2+26.2`.
- Loom declaration: `1.17-SNAPSHOT`; Gradle wrapper: `9.5.1`.
- Loom resolved during the baseline build: `1.17.21`.
- Mod Menu: `20.0.0-beta.3`; Java compilation target: `25`.

The source commit is the baseline snapshot; this documentation does not change
dependencies or runtime behavior.

## Baseline validation

- Command: `./gradlew build`.
- Environment: macOS, Temurin OpenJDK `25.0.3+9-LTS`.
- Result: **BUILD SUCCESSFUL** in 1 minute 8 seconds; five tasks executed.
- Client sources compiled and binary and sources JARs were assembled.
- Gradle reported `test NO-SOURCE`; this is build validation, not a test-suite pass.
- No automated test source files are present under `src`.
- Client launch and in-game behavior have not been verified.

## Commit checklist

- [x] Record the 26.2 baseline and migration checklist.
- [ ] Update the build and dependencies for 26.3.
- [ ] Port settings and input handling.
- [ ] Port HUD rendering and mixins.
- [ ] Verify gameplay and prepare the release.

Keep each change focused and use Conventional Commit messages. If the dependency
update cannot compile before API adaptations, record the compiler failures in
that checkpoint. A successful build does not establish runtime compatibility.

## 26.3 acceptance checklist

Record actual results as the port progresses; unchecked items are unverified.

### Build and startup

- [ ] `./gradlew clean build` succeeds on Java 25 (or the target's required Java version).
- [ ] Client starts and loads a world without mod or mixin errors.
- [ ] Mod Menu opens the RPG-Hud settings screen.

### HUD styles and layout

Check every style at small and large GUI scales and in windowed and fullscreen
mode. Watch for clipped text, overlapping bars, incorrect colors, and duplicate
or missing vanilla HUD elements.

- [ ] Vanilla.
- [ ] Simplified.
- [ ] Default.
- [ ] Extended Widget.
- [ ] Full Texture.
- [ ] Hotbar Widget.
- [ ] Modern Style.

### Gameplay states

- [ ] Health changes, regeneration, absorption, and armor.
- [ ] Hunger, saturation display, and hunger effects.
- [ ] Underwater air depletion and recovery.
- [ ] Mount health and jump bar.
- [ ] Experience bar and level changes.
- [ ] Hotbar selection, item counts, and durability.
- [ ] Status effects, boss bars, and multiplayer locator bar.
- [ ] Compass, clock, details, and entity inspection.
- [ ] HUD visibility in survival, creative, spectator, and with F1 toggled.

### Settings

- [ ] Title-screen and pause-menu settings entry points work.
- [ ] Buttons, sliders, tooltips, and keyboard navigation work.
- [ ] Color text input supports focus changes, typing, editing, and applying values.
- [ ] Style, position, scale, visibility, and color changes render correctly.
- [ ] Settings persist after restarting the client; reset restores defaults.

### Release

- [ ] Fixes found during acceptance checks are committed separately by concern.
- [ ] Mod version, Minecraft requirement, artifact name, and release notes agree.
- [ ] Final build and `git diff --check` pass.
