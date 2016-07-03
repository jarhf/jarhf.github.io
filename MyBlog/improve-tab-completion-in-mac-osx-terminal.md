Tab completion is a wonderful feature of shells that make power users lives easier, 
letting you automatically complete commands, paths, file names, and a variety of other
things entered into the command line.

1. Using emacs, nano, vi or whatever your favorite text editor is to edit .inputrc.
```
nano .inputrc
```
2. Paste in the following three rules on unique lines:
set completion-ignore-case on
set show-all-if-ambiguous on
TAB: menu-complete

3. Hit Control+O to save changes to .inputrc followed by Control+X to quit.

4. Now you open a new Terminal window, start typing a command, path, or something else and hit the Tab key
to see the improvements firsthand.
