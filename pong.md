
### References

- [pong tutorial](https://taintedcoders.com/bevy/tutorials/pong-tutorial)
- [pong repo](https://github.com/nolantait/pong-tutorial)

---

### Api Notes

- [Bevy Observer](https://docs.rs/bevy/latest/bevy/ecs/observer/struct.Observer.html)

---

### Focusing on the Score for starters

There are two `add_observer` calls

```rust
.add_observer(reset_ball)
.add_observer(update_score)
```

---

In this game there are three things that can be derived

- Components
- Resource
- EntityEvent

---

The `Resource` and the `EntityEvent` are both associated with the score

```rust
#[derive(Resource)]
struct Score {
  player: u32,
  ai: u32,
}

#[derive(EntityEvent)]
struct Scored {
  #[event_target]
  scorer: Entity,
}
```
