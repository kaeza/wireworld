wireworld by [pithydon]

Wireworld for Minetest.

See [wikipedia] for more on wireworld.

Forum at https://forum.minetest.net/viewtopic.php?f=11&t=14741.

Licensed under unlicense see LICENSE.txt

API:

node groups

* wireworld = 1
* wireworld = 2
* wireworld = 3
* wireworldhead
* wireworldstop

Group wireworld = 1 will run on_wireworld on next generation.

Group wireworld = 2 will run on_wireworld on next generation if 1 or 2 wireworldhead is near by.

Group wireworld = 3 like wireworld = 2 but inverted.

Group wireworldstop can be stopped with a wireworld switch.

on_wireworld is a part of the node definition.

```lua
on_wireworld = function(pos)
```
For your node to be used by wireworld when placed use

```lua
after_place_node = function(pos)
  table.insert(wireworld.nodes, pos)
end,
```

There is a lbm to catch nodes that have already been placed.

example

```lua
minetest.register_node("new:node", {
	groups = {wireworld = 2},
	on_wireworld = function(pos)
		minetest.swap_node(pos, {name = "new:node_head"})
	end,
	after_place_node = function(pos)
		table.insert(wireworld.nodes, pos)
	end,
})
```

[pithydon]: <https://github.com/pithydon>
[wikipedia]: <https://en.wikipedia.org/wiki/Wireworld>
