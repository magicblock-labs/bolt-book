# Mapping and State listening

The standardized **ECS** pattern allows for easy integration of game components with a rendering engine to display the game interface. Bolt can be viewed as an open and permissionless alternative to a backend intended as a multiplayer game server. 

For visualization and rendering, existing engines such as [Unity](https://unity.com/), [Unreal Engine](https://www.unrealengine.com), [Phaser](https://phaser.io/), and others can be used. 

The standardized structure of the components allows for automatic mapping of components and entity properties (abstracting serialization and deserialization. State updates can be easily performed and intercepted, providing a mechanism similar to the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern) to listen to state changes and update the rendering.

If you are building with Unity, the [Solana.Unity-SDK](https://github.com/magicblock-labs/Solana.Unity-SDK) gives you all the necessary tools to connect the gaming interface with Bolt. 