# Tanuk_CodeSequence
Provide a cheat code function / sequence recognition for Playdate games. Credits are not required, but let me know if you used this code somewhere, it is always nice to hear :))

# Usage
## Import the Code Sequence function
Add `import "Tanuk_CodeSequence"` where you need the function. 
Note that the CodeSequence will read inputs but will not stop their propagation.
**This class relies on timers and sprites, make sure that you import the timer and sprite files and update the both of them in the update loop**
```lua
import "CoreLibs/sprites"
import "CoreLibs/timer"

function playdate.update()
	gfx.sprite.update()
	pd.timer.updateTimers()
end
```

## Create a CodeSequence
Once the function is imported, you can easily create potential code with
```lua
-- Example: local myCode = Tanuk_CodeSequence(sequence, callbackReward, [isAllowMultipleCalls])
local sprCode = Tanuk_CodeSequence({"down", "left", "right", "left", "right"}, function() print("Code Complete") end)
local sprCode2 = Tanuk_CodeSequence({"up", "down", "up", "down", "left", "right"}, function() print("Not the Konami code") end, true)
```

## Parameters
A Tanuk_CodeSequence is initialized with 2 or 3 parameters:
- **sequence** A sequence of input, in order. It takes the standard Playdate input up, down, left, right, a, b
- **callbackReward** function to call when the code is successful
- **isAllowMultipleCalls** set to false by default. If set to yes, the code may be triggered multiple times. If set to false, it will only be registered once

## Important Note
All CodeSequence are considered as sprites. It means they will be removed if you call `playdate.graphics.sprite.removeAll()`

# Credits
CodeSequence was originally written by Toad, who came up with the idea of using sprites and their update function.
The function was then modified by Schyzophrenic
