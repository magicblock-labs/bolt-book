# Create a System

Systems contain the logic that processes and manipulates entities based on their components. A system will typically operate on all entities that have a specific set of components. For example, a "Movement" system might update the position of a "Position" component

Create a movement system with with

```
bolt system system-movement
```

which will add a new system to your workspace:

```rust
use bolt_lang::*;
use component_position::Position;

declare_id!("FSa6qoJXFBR3a7ThQkTAMrC15p6NkchPEjBdd4n6dXxA");

#[system]
#[program]
pub mod system_movement {

    pub fn execute(ctx: Context<Components>, args_p: Vec<u8>) -> Result<Components> {

        let position = &mut ctx.accounts.position;

        position.x += 1;
        position.y += 1;

        Ok(ctx.accounts)
    }

    // Define the input components
    #[system_input]
    pub struct Components {
        pub position: Position,
    }
}
```