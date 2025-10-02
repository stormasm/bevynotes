

### Google Question

- in bevy calls to add_systems update how do the function parameters get injected

In Bevy, when you add a system function to a schedule using add_systems(Update, my_system), the parameters of my_system are automatically "injected" by Bevy's Entity Component System (ECS) framework. This process relies on the SystemParam trait.

Here's how it works:

#### SystemParam Trait:

Bevy systems are essentially Rust functions where all parameters must implement the SystemParam trait. This trait signifies that a type can be provided by the Bevy ECS.

#### Automatic Conversion:

When you provide a function to add_systems, Bevy uses the IntoSystem trait to convert that function into a System type, specifically a FunctionSystem. This conversion process analyzes the function's signature and its parameters.

#### Dependency Injection:

Bevy's ECS acts as a dependency injection container. When a system is scheduled to run, Bevy examines the types of its parameters. For each parameter, Bevy looks into its World (which contains all ECS data, resources, events, etc.) and automatically fetches the correct data based on the parameter's type.

- Queries: If a parameter is a Query, Bevy provides a query object that can iterate over entities and components matching the query's criteria.
- Resources: If a parameter is a Res<T> or ResMut<T>, Bevy provides a read-only or mutable reference to a resource of type T stored in the World.
- Commands: The Commands parameter provides a way to queue up ECS operations (like spawning entities, adding/removing components) that will be executed at a safe point in the schedule.
- Events: EventReader<T> and EventWriter<T> allow systems to read and write events.
- Local: Local<T> stores a local, mutable state that persists across system runs.

#### Type-Driven Provision:

The key is that Bevy uses the type of the parameter to determine what to inject. You don't explicitly pass these parameters; Bevy handles the retrieval and provision based on the declared types in your system function's signature.

This allows you to write clean, declarative system functions where you simply specify the data you need, and Bevy handles the underlying mechanics of providing it from the ECS.
