# World Program Overview

The World Program is the entrypoint for creating world instances, entities, attaching components, and executing systems within a unified framework.

## Client Development

Ongoing development efforts are focused on delivering multiple client SDKs and integrations. The [World Program](https://explorer.solana.com/address/WorLD15A7CrDwLcLy4fRqtaTb9fbd8o8iqiEMUDse2n/anchor-program?cluster=devnet), a standard Anchor program, expose its Interface Definition Language (IDL) published on-chain for seamless interaction.

## TypeScript SDK Installation

To install the Bolt SDK, execute the following command:

```bash
npm install @magicblock-labs/bolt-sdk
```

- Initiating a project with bolt init automatically generates a simple usage example of the bolt-sdk.

### Creating a New World Instance

Create a new world instance as demonstrated below:

```ts
const registry = await Registry.fromAccountAddress(provider.connection, registryPda);
worldId = new anchor.BN(registry.worlds);
worldPda = FindWorldPda(new anchor.BN(worldId))
const initializeWorldIx = createInitializeNewWorldInstruction(
    {
        world: worldPda,
        registry: registryPda,
        payer: provider.wallet.publicKey,
    });

const tx = new anchor.web3.Transaction().add(initializeWorldIx);
const txSign = await provider.sendAndConfirm(tx);
```
### Adding a New Entity

To add a new entity:

```ts
const world = await World.fromAccountAddress(provider.connection, worldPda);
const entityId = new anchor.BN(world.entities);
entityPda = FindEntityPda(worldId, entityId);

let createEntityIx = createAddEntityInstruction({
    world: worldPda,
    payer: provider.wallet.publicKey,
    entity: entityPda,
});
const tx = new anchor.web3.Transaction().add(createEntityIx);
await provider.sendAndConfirm(tx);
```

### Attaching Components to an Entity
For attaching components:

```ts
const positionComponentPda = FindComponentPda(positionComponent.programId, entityPda, "");
let initComponentIx = createInitializeComponentInstruction({
    payer: provider.wallet.publicKey,
    entity: entityPda,
    data: positionComponentPda,
    componentProgram: positionComponent.programId,
});
const tx = new anchor.web3.Transaction().add(initComponentIx);
await provider.sendAndConfirm(tx);
```

### Applying Systems

To apply a system:

```ts
let applySystemIx = createApplyInstruction({
    componentProgram: positionComponent.programId,
    boltSystem: systemMovement.programId,
    boltComponent: positionComponentPda,
});
const tx = new anchor.web3.Transaction().add(applySystemIx);
await provider.sendAndConfirm(tx);
```