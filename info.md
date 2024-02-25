PrismarineJS is a Github organization that hosts many Minecraft-related projects written in JavaScript for use in Node.js apps.

The projects include the following Node.js libraries:
| Repo and npm package name | Description and Purpose |
|-|-|
| mineflayer                | Ceating Minecraft Java Edition bots
| node-minecraft-data (npm: minecraft-data) | Exposes data inside the language-agnostic PrismarineJS/minecraft-data repo
| prismarine-biome          | Exposes Biome class that can be instantiated to query biome information such as temperature
| prismarine-block          | Exposes Block class to represent a block in the world. Can be used to query information such as block break time.
| prismarine-item           | Exposes Item class to represent a Minecraft item. Can be used to query information such as item name
| prismarine-chat           | Exposes ChatMessage class to parse and serialize Minecraft chat messages
| prismarine-chunk          | Exposes ChunkColumn class to hold and query Minecraft chunk data, like when obtaining a block in world at a position. Holds methods to serialize and deserialize chunk data from and to binary for reading and writing network and disk Minecraft chunk data.
| prismarine-world          | Exposes World class to represent a Minecraft world. Can be used to raycast and query block information
| prismarine-windows        | Exposes Window class to represent a Minecraft inventory. Can be used to query information such as window title
| prismarine-entity         | Exposes Entity class to represent a Minecraft entity. Can be used to query information such as entity type
| prismarine-nbt            | Convert binary NBT data to JavaScript objects and vice versa
| prismarine-physics        | Simulate Minecraft physics
| prismarine-recipe         | Query Minecraft recipes
| prismarine-registry       | Creating an "instance" of minecraft-data for a specific version of Minecraft. This is helpful when the data needs to be mutated in some way for a specific session
| vec3                      | Vector3 class for 3D vector operations

And some non-PrismarineJS projects, but relevant to PrismarineJS:
* protodef - a Node.js library for binary protocol serialization/de-serialization that is used by nmp and bedrock-protocol. ProtoDef's compiler can take in a JSON schema for a binary protocol and use that to generate JavaScript code to serialize and deserialize the protocol packets

Key points:
* Almost all the PrismarineJS projects support multi-versioning, meaning they are support a wide range of Minecraft versions.
* mineflayer and node-minecraft-protocol currently support all Minecraft Java Edition versions beyond 1.8.
* bedrock-protocol supports all Minecraft Bedrock Edition versions after 1.16
* minecraft-data holds data for various Minecraft Java and Bedrock Edition versions, even if they're not supported by other PrismarineJS projects

Dependency information:
* mineflayer - Mineflayer depends on the `mineflayer-pathfinder, prismarine-chat, prismarine-windows, prismarine-registry, prismarine-physics, prismarine-recipe, prismarine-registry, prismarine-world, prismarine-entity, prismarine-item, prismarine-nbt, prismarine-block, prismarine-chunk, prismarine-biome, minecraft-data, node-minecraft-protocol, protodef, vec3` packages. Mineflayer's API can be extended by creating plugins that use these packages. Notably, this includes:
  * mineflayer-pathfinder - a mineflayer plugin for A* pathfinding
* node-minecraft-protocol - Node-minecraft-protocol depends primarily on the `protodef` and `minecraft-data` packages. minecraft-data mainly to access protocol schemas
* bedrock-protocol - Bedrock-protocol similarly depends on the `protodef` package and `minecraft-data`
* node-minecraft-data - github.com/prismarinejs/node-minecraft-data has a submodule that points to the language-agnostic github.com/prismarinejs/minecraft-data repo
