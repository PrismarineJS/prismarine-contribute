# prismarine-contribute
What is PrismarineJS and how to contribute ?

# What is prismarinejs ?

PrismarineJS is a collection of libraries around minecraft to build servers, bots, proxies, and everything else around minecraft.

* minecraft-data provide the data for the various version of minecraft, it is extracted from wikis, the minecraft jars, and manually written
* node-minecraft-protocol supports multiple protocol of minecraft to provide for clients, servers and proxies
* mineflayer uses node-minecraft-protocol to provide a high level api to build bots
* flying-squid uses node-minecraft-protocol to provider an api to builds servers
* prismarine-* libraries are used in mineflayer and flying-squid to implement parts of minecraft (entities, recipes, windows, ...)
* extractors are used to provide data in minecraft-data

# How to contribute ?

## Decide on what you want to contribute

Options :

* look at mineflayer, minecraft-data, flying-squid and node-minecraft-protocol issues and find something you're interested in
* updating to a new minecraft versions
* writing new bots : look at example of bots in the mineflayer readme, such as rbot, you might find inspiration
* writing servers and proxies : look at usage in the node-minecraft-protocol readme

## Updating to new minecraft versions

During the whole process you can ask for help on our gitters, our discords or #mcdevs@irc.freenode.net

1. update minecraft data
  * copy the minecraft-protocol from the previous version
  * add new changes using wiki.vg/Protocol
  * use wiki extractors, burger extractors, ... whatever is needed to extract the new blocks.json, ...
  * release a new version of minecraft-data and node-minecraft-data : ask the maintainers to do that
2. make sure it works in node-minecraft-protocol
  * update minecraft-data dependencies
  * add your version in the supported versions
  * run the tests
  * try the examples and make sure it works
3. update mineflayer
  * update node-minecraft-protocol and minecraft-data dependencies
  * check wiki.vg for new things to support
  * check the changes in the protocol
  * adapt mineflayer for changes in the packet names, fields, ... 
  * try compatible with old version : put your changes under `ifs` or other conditional mecanism
  * you might need to update prismarine-* packets if things changed a lot
4. update flying-squid
  * the process is similar to mineflayer


## History of PrismarineJS

In 2012, mineflayer was built by @andrewrk written in c++ to make bots. It had plugin written in js.
In 2013, @andrewrk decided to rewrite it in node.js. First node-minecraft-protocol was written to separate concern and handle only the minecraft protocol : the lower level.

Mineflayer was then rewritten in pure js using node-minecraft-protocol to make bots.
Some bots were created, including rbot written by @rom1504.
Since 2013, mineflayer and node-minecraft-protocol have been maintained by @roblabla, @rom1504 and a few others.

Not long after, PrismarineJS was created to try a build a minecraft server using node-minecraft-protocol.
It soon became the place regrouping all our js project for minecraft.

@rom1504 created minecraft-data to have a single place regrouping all the data used by these packages.
@mhsjlw created flying-squid using node-minecraft-protocol and minecraft-data to build a minecraft server in js.

node-minecraft-protocol has been refactored a lot since its beginnings. Including a big refactor to extract its protocol in a json file and make a protodef lib to handle it (initiated by @roblabla).

People used the protodef definition and minecraft-data to build minecraft stuff in other languages, in particular @hansihe which built protodefc which is a rust compiler for protodef targetting various languages.

minecraft-data is updated using extractors. Initially it used burger written by people at #mcdevs@irc.freenode.net. These days it also uses the minecraft wiki using automatic extractors.
