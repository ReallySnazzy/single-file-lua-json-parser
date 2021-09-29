# Single File Lua JSON Parser

Simple embeddable JSON parser written in under 350 lines of Lua. Compatible with Lua 5.1 and Lua 5.3.

## Sample
```lua
require('json')

local obj = {
	["henry"] = 1,
	["james"] = {"becky", "anna", "jimmy"},
	["some_bool"] = true,
	["deep"] = {
		{["more_nesting"] = true},
		{["other"] = {1, 2, 3}}
	},
	["some_null"] = nil
}

local obj_str = to_json_str(obj)
print('Converting to JSON string:')
print(obj_str)

local new_obj = parse_json(obj_str)
print('What value is obj.henry? ' .. tostring(new_obj['henry']))
print('What value is obj.james[2]? ' .. tostring(new_obj['james'][2]))
print('What value is obj.deep[1].more_nesting? ' .. tostring(new_obj['deep'][1]['more_nesting']))
print('Converting to object and back again:')
print(to_json_str(new_obj))
```

Output:
```
Converting to JSON string:
{"deep":[{"more_nesting":true},{"other":[1,2,3]}],"henry":1,"james":["becky","anna","jimmy"],"some_bool":true}
What value is obj.henry? 1
What value is obj.james[2]? anna
What value is obj.deep[1].more_nesting? true
Converting to object and back again:
{"deep":[{"more_nesting":true},{"other":[1,2,3]}],"henry":1,"james":["becky","anna","jimmy"],"some_bool":true}
```
