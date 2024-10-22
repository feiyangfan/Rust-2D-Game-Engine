# Rust 2D Game Engine

## Table of Contents

- [Entity Component System](#ecs-entity-component-system)
- [Render Engine](#render-engine)
- [Physics Engine](#physics-engine)
- [Input Handler](#input-handling)
- [Audio Engine](#audio-engine)
- [Script Interpreter](#script_interpreter)
- [Game Project File Management](#file_system)
- [Engine GUI](#gui)

## [Render Engine](/src/render_engine.rs)

Using [wgpu](https://github.com/gfx-rs/wgpu) for the game rendering engine.

- [x] initial implementation

## [Physics Engine](/src/physics_engine.rs)

Using [rapier2d](https://github.com/dimforge/rapier) for the game physics engine.

- [x] initial implementation

## [ECS Entity Component System](/src/ecs.rs)

Functions that can modify the atrribute of entity on the fly.
To be implemented...

## [Script Interpreter](/src/script_interpreter.rs)

For the game logic language, `lua` is a simple and popular choice in the game industry.
Using [rlua](https://github.com/Kampfkarren/rlua) for the game script interpreter.

- [x] initial implementation

## [Audio Engine](/src/audio_engine.rs)

The Audio Engine is a crucial component of our 2D game engine, responsible for handling sound playback. It utilizes [rodio](https://github.com/RustAudio/rodio), a pure Rust audio playback library, to manage audio streams and control sound output.

### Features

- Simple audio playback from file
- Pause and resume functionality
- Ability to check if audio is currently playing

### Implementation Details

The `AudioEngine` struct is the core of our audio system. It contains:

- An `OutputStream` for audio output
- An `OutputStreamHandle` for creating new sounds
- A `Sink` for controlling audio playback

Key methods include:

- `new()`: Initializes the audio engine with default output stream and sink.
- `play_sound(file_path: &str)`: Loads and plays an audio file from the given path.
- `is_playing()`: Checks if audio is currently playing.
- `pause()`: Pauses the current audio playback.
- `resume()`: Resumes paused audio playback.

The engine uses `BufReader` and `Decoder` from the `rodio` crate to efficiently read and decode audio files.

### Error Handling

The `play_sound` method returns a `Result`, allowing for graceful error handling if the file is not found or cannot be decoded.

### Unit Tests

The unit tests ([`audio_engine_test.rs`](tests/audio_engine_test.rs)) thoroughly verify the functionality of the `AudioEngine`:

1. **Initialization Test**:

   - Ensures the audio engine initializes correctly with an empty sink.

2. **Play Sound Test**:

   - Verifies that a sound file can be successfully loaded and played.
   - Checks that the engine correctly reports when audio is playing.
   - Confirms that the audio stops playing when explicitly stopped.

3. **Is Playing Test**:
   - Checks the initial state (not playing).
   - Verifies correct state after playing a sound.
   - Tests pause functionality and ensures the engine reports correct state.
   - Checks resume functionality.
   - Verifies correct state after stopping the audio.

These tests use a constant `TEST_AUDIO_FILE` path, which should point to a valid audio file in the test environment.

### Usage

To use the `AudioEngine` for game audio:

1. Create an instance of `AudioEngine` using `AudioEngine::new()`.
2. Use `play_sound(file_path)` to play audio files.
3. Control playback with `pause()` and `resume()`.
4. Check playback status with `is_playing()`.

## [Input Handling](/src/input_handler.rs)

Using [winit](https://github.com/rust-windowing/winit) for the game input handling.

- [x] initial implementation

> [!NOTE]
> Will add more script languages in the future if have time, such as C# and python.

## [Game Project File Management](/src/project_manager.rs)

A game engine should be able to display and manage the game project files.

- [x] create a new project
- [x] open a project
- [ ] save a project
- [ ] build a project

> [!NOTE]
> Not sure if project files need to be saved manually for now, since the project is directly modified in the engine.

## [Engine GUI](/src/engine_gui.rs)

Using [egui](https://github.com/emilk/egui) for the engine GUI.

- [x] initial implementation
