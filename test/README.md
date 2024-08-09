# [Personal Donation Place](https://github.com/CHL-a/JunkLuaIdeas/blob/main/Stuff/RobloxPlaceShowcases/Donate.rbxl)

Honestly, seeing people make gamepasses, display them on their website and requiring their clients to delete and rebuy the gamepasses sounds pretty tedious. 

## Lets use Developer Products Instead.

Hey, after you publish your place, you should use developer products. Here's a step by step guide on how to do it: 

![Step 1: https://raw.githubusercontent.com/CHL-a/MyReadMes/main/test/step%201.jpg](https://raw.githubusercontent.com/CHL-a/MyReadMes/main/test/step%201.jpg)

![Step 2: https://github.com/CHL-a/MyReadMes/blob/main/test/step%202.jpg?raw=true](https://github.com/CHL-a/MyReadMes/blob/main/test/step%202.jpg?raw=true)

Then add your name and price. Mind the Product Ids for later.

## Variables:

This part is editing the Variables Module in `game.ReplicatedStorage.Objects.Variables`

|Variable|Type|Description|
|---|---|---|
|`donate.dev_products.all`|`bool`|Denotes that all Ids are donation ids.|
|`donate.dev_products.specific`|`{int}`|Denotes specific ids as donation ids. Only used if `donate.dev_products.all` is `false`. But if you choose to use this, paste your ids along with a seperator (`,` or `;`) after.

## Server Variables:

This part is editing the Variables Module in `game.ServerScriptService.Objects.ServerVariables`

|Variable|Type|Description|
|---|---|---|
|`webhook`|`string`|Webhook for comminicating back. Any webhook is welcome but `game.ServerScriptService.Objects.WebhookInvoker` implementation uses Discord webhooks.|

## Is that it?
Barely, make sure httpservices are enabled to make the webhook work, publish your game and edit the implementation `game.ServerScriptService.Objects.WebhookInvoker`'s method `get_data` for webhook customization.
