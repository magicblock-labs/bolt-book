# Entity, Component and Systems (ECS)

The framework includes a standardized way to model the game logic, using the ECS (Entity, Components and Systems), which is commonly used in the gaming industry and also adopted in most on-chain engines.

This pattern decouples logic from state, enabling optimizations in terms of performance and scalability. Additionally, its modular nature facilitates code reusability and extensibility, which are two essential properties for fully on-chain games and autonomous worlds.

The Solana Virtual Machine makes use of a paradigm similar to an ECS. The state (the accounts) and the logic (the programs) are natively separated.

When drawing a comparison with Solana's architecture, we can see how the ECS easily implementable:

- Entity: An entity is a general-purpose object typically represented by a unique identifier.
It doesn't directly contain any data or behaviour but serves as an identifier for a collection of components. Entities can be registered in a world instance account on Solana and could themselves be accounts.
- Components: Raw data structure that represents some aspect or attribute of an entity. For instance, a PositionComponent might just contain x, y, and z coordinates. This is concept is essentially equivalent to accounts on Solana.
- Systems: Performs the game logic or behaviour by acting upon entities that have specific components. Systems are essentialy programs on Solana, which only specify the logic and the accounts they operate on.

Solana's Program Derived Addresses (PDAs) facilitate the efficient storage and retrieval of entities, components and system mimicking a hash table-like structure. 