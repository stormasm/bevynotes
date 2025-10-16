

### Schedule

In Bevy's schedule system, the primary difference between Update and FixedUpdate lies in their execution frequency and purpose:

### Update Schedule:

`Execution`: Systems in the Update schedule run once per rendered frame. This means their execution rate is tied directly to the game's framerate, which can fluctuate depending on hardware and scene complexity.

`Purpose`: Update is generally used for logic that needs to be executed every frame and is often related to visual updates or input handling that needs to be responsive to the user. Examples include camera movement, animation updates, and general game logic that doesn't require precise, consistent timing.

### FixedUpdate Schedule:

`Execution`: Systems in the FixedUpdate schedule run at a fixed, predetermined rate, independent of the game's framerate. This fixed timestep ensures consistent execution intervals, regardless of whether the game is running fast or slow. If the framerate is lower than the fixed update rate, FixedUpdate might run multiple times per frame to catch up. If the framerate is higher, FixedUpdate might not run every frame.

`Purpose`: FixedUpdate is crucial for logic that requires consistent, reliable timing, especially physics simulations, networking, and AI. By using a fixed timestep, these systems can ensure predictable behavior and avoid issues that arise from variable frame rates, such as inconsistent physics calculations or synchronization problems in multiplayer games.

#### In summary:

Update is for per-frame, visually-oriented logic.
FixedUpdate is for time-sensitive, simulation-oriented logic.
