# What's the different between KeyCode and KeyData

> Example :  
* Press (and hold) CTRL. `KeyDown` will be raised, `KeyCode` will be `Keys.ControlKey`, `KeyData` will be `Keys.ControlKey | Keys.Control`.
* While still holding CTRL pressed, press SHIFT. `KeyDown` will be raised, KeyCode will be `Keys.ShiftKey` and KeyData will be `Keys.ShifKey | Keys.Shift | Keys.Control`.
