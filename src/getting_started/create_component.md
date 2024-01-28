# Create a Component

Components are plain data structures (classes or structs) that contain data relevant to a specific aspect of an entity. They don't have any logic or methods. Examples of components could be a "Position" component containing x, y, z coordinates.

Create a Position component with

```
bolt component position
```

which will add a new component to your workspace:

```rust
use bolt_lang::*;

declare_id!("Fn1JzzEdyb55fsyduWS94mYHizGhJZuhvjX6DVvrmGbQ");

#[component(Position)]
#[program]
pub mod component_position {
    use super::*;
}

#[account]
#[bolt_account(component_id = "component-position")]
#[derive(Copy)]
pub struct Position {
    pub x: i64,
    pub y: i64,
    pub z: i64,
}
```