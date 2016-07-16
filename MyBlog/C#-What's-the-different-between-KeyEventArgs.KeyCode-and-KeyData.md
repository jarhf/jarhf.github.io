# What's the different between KeyCode and KeyData

> Example :  
* Press (and hold) CTRL. `KeyDown` will be raised, `KeyCode` will be `Keys.ControlKey`, `KeyData` will be `Keys.ControlKey | Keys.Control`.
* While still holding CTRL pressed, press SHIFT. `KeyDown` will be raised, KeyCode will be `Keys.ShiftKey` and KeyData will be `Keys.ShifKey | Keys.Shift | Keys.Control`.


## C# Code
```
public string ShortcutKeyDisplay
{
  if (this.ShortcutKey == Keys.None) return "";
  string str = "";
  if ((this.ShortcutKey & Keys.Control) == Keys.Control) str += "Ctrl+";  //设置快捷键的时候使用 Keys.ControlKey | 
  if ((this.ShortcutKey & Keys.Shift) == Keys.Shift) str += "Shift+";
  if ((this.ShortcutKey & Keys.Alt) == Keys.Alt) str += "Alt+";
  Keys keyCode = this.ShortcutKey & Keys.KeyCode;
  if (Enum.IsDefined(typeof(Keys), (int)keyCode))
  {
    str += keyCode.ToString();
  }
  return str;
}
```
