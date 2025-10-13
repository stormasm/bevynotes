
https://docs.rs/bevy/latest/bevy/prelude/index.html

The bevy prelude is defined in the crate [bevy_internal/src/lib.rs](https://github.com/bevyengine/bevy/blob/main/crates/bevy_internal/src/lib.rs)

```rust
use bevy::prelude::*; to import common components, bundles, and plugins.
```

To search for the location of all of the different preludes across all of the bevy crates

```rust
rg pub mod prelude
```
