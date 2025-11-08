

- [google search: rust default trait](https://www.google.com/search?q=rust+default+trait&rlz=1C5OZZY_enUS1141US1141&oq=rust+default+trait&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIHCAEQABiABDIICAIQABgWGB4yCAgDEAAYFhgeMggIBBAAGBYYHjIICAUQABgWGB4yBggGEEUYQTIGCAcQRRhB0gEINDQyM2owajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

### Location of bevy macro definitions

- [bevy_ecs_macros](https://github.com/bevyengine/bevy/tree/main/crates/bevy_ecs/macros)

#### To find all of the macros in bevy run this command

```rust
rg 'proc-macro = true' -g Cargo.toml
```

#### Original Google Answer

Bevy's derive macros are defined in separate, dedicated procedural macro crates within the Bevy codebase.

The primary crates are:

- bevy_ecs_macros: This crate contains the implementations for core ECS derive macros like Component, Resource, Events, and Bundle.
- bevy_reflect_derive: This crate implements the macros related to Bevy's reflection system, most notably the Reflect derive macro, along with others like FromReflect and TypePath.
- bevy_derive: This crate provides other general-purpose derive implementations used by Bevy Engine.

These crates are typically located in the main Bevy repository under their respective names (e.g., crates/bevy_ecs_macros, crates/bevy_reflect_derive) and have proc-macro = true specified in their Cargo.toml file.

The actual implementation of the macros within these crates often uses libraries like syn and quote to parse and generate Rust code.
