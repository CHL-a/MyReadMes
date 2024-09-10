# [Enum](https://github.com/CHL-a/JunkLuaIdeas/blob/main/Stuff/RobloxObjects/Enum_Attempt.lua)

This document is made to how to use the non-official resource, [`@CHL/Enum`](https://github.com/CHL-a/JunkLuaIdeas/blob/main/Stuff/RobloxObjects/Enum_Attempt.lua). Documentation is subject to change.

## Package:
```lua
{
    name = '@CHL/Enum';
    targetRepository = 'Shared';
    packageType = 'url';
    dependencies = {
        '@CHL/Map'
    };
    url = 'https://raw.githubusercontent.com/CHL-a/JunkLuaIdeas/f1c15afd6bad19d1832012c0467296c4e45dbb98/Stuff/RobloxObjects/Enum_Attempt.lua'
},
```

## Sample:
```lua
local CEnum = require(game.ReplicatedStorage.Objects["@CHL/Enum"])

type enum_item<A> = CEnum.enum_item<A>

local sample_enum: CEnum.enum<
	'Value1' | 'Value2' | 'Value3',
	{
		Value1: enum_item<'Value1'>;
		Value2: enum_item<'Value2'>;
		Value3: enum_item<'Value3'>;
	}
	> = CEnum.new({'Value1', 'Value2', 'Value3'})

type a = typeof(sample_enum.union)
local b: a = 'Value2'

print(sample_O, sample_enum.enum_items.Value2:equals(b))
```

> Note 1: Due to the way metamethod `==` functions, Enum can't equate to strings nor numbers. It is for that reason that `enum_item<T>:equals(other)` should be used instead.

> Note 2: Yes it is this stupidly complicated. This is why the documentation is made.

## `enum<UNION, MAP>`
Responsible for holding most of the enum_items.

> Note: An explicit type had to be declared. Yes, it is simply `Enum<UNION, MAP>` but it is up to the developer that those types are of a specific type, otherwise the intellisense won't work.
> For all types:
>  * `UNION`: Must strictly be a union of values.
>  * `MAP`: Must strictly be a map of `UNION` on `enum_item<UNION>` or more generally, `map<UNION, enum_item<UNION>>`, as seen in the example. If the map is generalized instead of speciifc, the intellisense and autocomplete won't be invoked.

### Constructors
Call constructors return `enum<UNION, MAP>` unless stated otherwise.

|Name|Description|
|---|---|
|`.new<UNION, MAP>(items: {INTERSECTION})`|To make this constructor work, an explicit type had to be declared. Meaning a stand alone constructor call won't do. (such as `Enum.new({'1','2','3'})`). See the explicit type note. Furthermore, the list denotes the order of `enum_item<U>`|

### Properties
|Name|Type|Description|
|---|---|---|
|union|`nil`, `UNION` (autocomplete)|A property only accessed by `typeof()`, this allows developer to access the type.
|enum_items|`MAP`|A property which allows the developer to access `enum_item<UNION>`.

## `enum_item<U>`
A value which allows the developer access specific `UNION` value, denoted as `U`.

### Properties
|Name|Type|Description|
|---|---|---|
|value|`U`|
|number_value|`number`|Determines the order.

### Methods
#### `:equals(other)`

|Parameter|Type|Description|
|---|---|---|
|Other|`U`, `number`, `enum_item<U>`|Other value to compare, more generalized than `==`.

