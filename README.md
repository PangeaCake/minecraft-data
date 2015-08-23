# minecraft-data 
[![Build Status](https://circleci.com/gh/PrismarineJS/minecraft-data/tree/1.9.svg?style=shield)](https://circleci.com/gh/PrismarineJS/minecraft-data/tree/1.9)

Language independent module providing minecraft data for minecraft clients, servers and libraries.

Support minecraft 1.9 snapshots.

## Wrappers

Minecraft-data is language independent, you can use it with these language specific modules :

* [node-minecraft-data](https://github.com/PrismarineJS/node-minecraft-data) provides indexes and look up functions in node.js
* [python-minecraft-data](https://github.com/rom1504/python-minecraft-data) provides indexes and look up functions in python

If you want to use minecraft-data in a new language, we advise you to [create a new wrapper](doc/make-a-new-wrapper.md)

There are also some projects that wrap parts of minecraft-data in other ways :

* [ProtocolGen](https://github.com/Johni0702/ProtocolGen) that generate java files reading and writing the protocol
 from minecraft-data protocol.json file

## Documentation

 * See [doc/history.md](doc/history.md)
 * [Documentation generated using the json schemas and docson](http://prismarinejs.github.io/minecraft-data/?v=1.9)
 * [Textual documentation of the recipe format](doc/recipes.md)

## Extractors

Minecraft data provides a few extractors to update the data :

| Data file | Extractor | Source |
| --------- | --------- | ------ |
| [items](enums/items.json) | [item_extractor](tools/js/wiki_extractor/item_extractor.js) | minecraft wiki |
| [entities](enums/entities.json) | [entities_extractor](tools/js/wiki_extractor/entities_extractor.js) | minecraft wiki |
| [blocks](enums/blocks.json) | [block_extractor](tools/js/wiki_extractor/block_extractor.js) | minecraft wiki |
| [materials](enums/materials.json) | | manual : this file is very simple, it is there to make it easier to handle some edge cases |
| [instruments](enums/instruments.json) |  | manual : data coming from [wiki.vg](http://wiki.vg/Block_Actions) |
| [recipes](enums/recipes.json) | [recipe_extractor](tools/js/wiki_extractor/recipe_extractor.js) | minecraft wiki |
| [items](enums/items.json), [blocks](enums/blocks.json), [biomes](enums/biomes.json) and [recipes](enums/recipes.json) | [generate_enums](tools/js/burger_extractor/generate_enums.js) | burger.json file generated by https://github.com/mcdevs/Burger which is not up to date with minecraft 1.8 |
| [biomes](enums/biomes.json) | | manual : see https://github.com/andrewrk/mineflayer/pull/197 for more detail |
| [protocol](enums/protocol.json) | | manual but [protocol_extractor](tools/js/wiki_extractor/protocol_extractor.js) and [protocol_extractor](tools/js/decompiled_extractor/protocol_extractor.json) can be useful for updating it |


## Data quality

Minecraft data provides scripts to audit the data, they can be useful to check the data is correct :

 * tools/js/audit/audit_block_enum.js audits blocks.json : it checks for duplicates names and jumps in ids
 * tools/js/audit/audit_item_enum.js audits items.json : it checks for duplicates names and jumps in ids
 * tools/js/audit/audit_recipes.js audits recipes.json : it counts the number of recipes with a shape, without one and with an outShape 
 
Minecraft data also provides json schemas in enums_schemas/ that are used in test/test.js to check the json file are valid relative to these schemas.
These schemas can also be used to understand better how the json files are formatted in order to use it.
