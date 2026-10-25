# Lucid-blocks-COOP-mod
A Godot 4.6 co-op mod for Lucid Blocks featuring Steam/local multiplayer, persistent player progression, custom 3D character imports (.glb, .gltf, .usdz), and reliable world synchronization. Focused on shared gameplay, independent saves, and seamless multiplayer.
Lucid Blocks Co-op — Multiplayer Expansion Mod

Project Overview

Lucid Blocks Co-op is a multiplayer expansion mod for Lucid Blocks, built to transform the original single-player experience into a fully functional cooperative gameplay experience. The project extends the game's existing systems to support multiplayer sessions, persistent player progression, shared world exploration, and custom character imports.

The mod already includes Steam and local multiplayer invitations, cooperative session management, player state synchronization, and an experimental custom character loading system.

Core Features and Development Goals

1. Fully Persistent Multiplayer Progression

Implement reliable save and load functionality for every player, including clients who join another player's world. Each player's progress must persist independently across disconnections and subsequent sessions.

Persistent data must include:

Inventory and collected items.

Qualia and other character-specific resources.

Attributes, stats, and progression.

Equipment, accessories, upgrades, and enhancements.

Custom character data and other relevant player-specific state.

Players must be able to leave a session and return later without losing their progress. The host's world and each client's personal progression must remain consistent and independent.

2. Custom Character Import System

Add a Load Character button to the cooperative multiplayer interface. Players should be able to browse their local computer, select a supported 3D model, and load it into the game.

Supported formats:

.glb

.gltf

.usdz

The system should support importing models with textures, materials, skeletons, and animations whenever these are available in the source asset. USDZ files may require conversion to a Godot-compatible format.

Imported characters must appear correctly in the game and be synchronized across all connected players. Other players must see the same character model, appearance, and animations. The system should handle large assets reliably, with a target maximum file size of 100 MiB per character.

3. Reliable World Synchronization

Fix the multiplayer world synchronization system so that clients can consistently join the host's world without missing world chunks.

Previous issues include errors such as:

Missing world chunk 0

Missing world chunk 1

Missing chunks later in the snapshot transfer.

Incomplete world snapshots, including progress indicators such as 4/9.

The networking implementation should provide reliable chunk delivery, transfer validation, acknowledgements, retries, and proper completion checks. A client must not enter the world until the required world data has been received and validated.

Large snapshots should be transferred efficiently without overwhelming the connection or causing incomplete world states.

4. Multiplayer Networking and Compatibility

Preserve and improve the existing Steam and local multiplayer invitation systems. Ensure that player state, world data, custom characters, and relevant gameplay events are synchronized correctly between the host and all connected clients.

The system should handle connection failures, disconnections, reconnections, duplicate packets, incomplete transfers, and late-joining players gracefully.

5. Technical Requirements

Game engine: Godot 4.6.

Mod format: Compiled .pck package.

Networking: Extend the existing cooperative networking architecture rather than rebuilding it unnecessarily.

Persistence: Use the game's existing serialization and save systems wherever possible.

Asset loading: Implement runtime 3D model loading and multiplayer asset distribution.

File transfer: Support chunked transfers, integrity validation, and recovery from missing data.

Compatibility: Preserve the original game's functionality and existing mod integrations.

Current Status

The mod has undergone several experimental updates:

A multiplayer player-state persistence fix was implemented.

A custom character loading interface was added.

The character file-size limit was increased to 100 MiB.

Large character files and world snapshots were modified to use smaller, paced chunks.

Snapshot retry logic was added to address missing world chunks.

However, these changes have not been fully verified in live multiplayer sessions. Character loading still requires debugging, and world synchronization remains unreliable.

Immediate Priorities

Inspect the current mod source and the installed .pck package before making further changes.

Identify and fix the root cause of custom character loading failures.

Resolve missing world chunks and implement reliable snapshot synchronization.

Verify independent save and load behavior for both host and guest players.

Test imported models with textures, materials, skeletons, and animations.

Perform real multiplayer testing using two separate game instances and, where possible, separate computers.

Produce a validated, installable .pck package while preserving backups of previous working versions.

Development Principles

Do not rebuild existing systems unnecessarily, fabricate game APIs, or assume that compilation alone proves a feature works. Inspect the actual game and mod implementation, preserve existing functionality, make targeted changes, and validate each fix through reproducible tests.

Ultimate Goal: Deliver a stable, genuinely cooperative Lucid Blocks experience where multiple players can share a world, retain their individual progression, import custom 3D characters, and play together without synchronization errors or lost data.
