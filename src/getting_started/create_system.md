# Create a System

Systems contain the logic that processes and manipulates entities based on their components. A system will typically operate on all entities that have a specific set of components. For example, a "Movement" system might update the position of a "Position" component

Create a movement system with with

```
bolt system -n system-movement
```

which will add a new system to your workspace:

```rust
use bolt_lang::*;

declare_id!("FSa6qoJXFBR3a7ThQkTAMrC15p6NkchPEjBdd4n6dXxA");

#[system]
#[program]
pub mod system_movement {
    use super::*;

    pub fn execute(ctx: Context<Component>, args_p: Vec<u8>) -> Result<Position> {

        let mut position = Position::from_account_info(&ctx.accounts.position)?;

        position.x += 1;
        position.y += 1;

        Ok(position)
    }
}

// Define the Account to parse from the component
#[derive(Accounts)]
pub struct Component<'info> {
    /// CHECK: check that the component is the expected account
    pub position: AccountInfo<'info>,
}

#[component_deserialize]
pub struct Position {
    pub x: i64,
    pub y: i64,
    pub z: i64,
}
```