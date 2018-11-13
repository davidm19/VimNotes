# VIM NOTES!

### MODES:
```
    i         Insert mode
    <ESC>     Normal mode
    v         Visual mode
    V         Visual Line mode (highlight entire lines)
    <CTRL-V>  Visual Block mode (highlight columns as opposed to rows)
    R         Replace mode
```

### COMMANDS:
```
    :w        Write changes
    :q        Quit (when changes are written)
    :q!       Quit without saving
```

### INSERTING TEXT:
```
    i         Insert text before the cursor
    I         Insert text at the beginning of the line
    a         Insert (append) text after the cursor
    A         Insert (append) text at the end of the line
    o         Insert text at a new line below the current line
    O         Insert text at a new line above the current line
    ea        Insert text after a word
    <ESC>     Exit insert mode
```

### MOVEMENT:
```
    h         Left
    j         Up
    k         Down
    l         Right
    
    w         Next word
    e         End of current word
    b         Previous word
    
    H         Topmost line in the screen
    L         Middle of screen
    M         Bottommost line in the screen
    
    0         Beginning of line
    $         End of line
    
    gg        First line of the file
    G         Last line of file
    <n>G      Go to to line <n>
    
    <CTRL-e>  Move screen down one line (without moving cursor)
    <CTRL-y>  Move screen up one line (without moving cursor)
    <CTRL-b>  Move back one full screen
    <CTRL-f>  Move forward one full screen
    <CTRL-d>  Move forward 1/2 a screen
    <CTRL-u>  Move back 1/2 a screen
```

### EDITING AND DELETING:
```
    r        Replace a character
    R        Enter replace mode
    u        Undo
    <CTRL-r> Redo
    cc       Change (replace) entire line
    c$       Change (replace) to the end of the line
    ciw      Change (replace) entire word
    ci)      Change inside parentheses
    
    y        Yank (copy)
    yy       Yank (copy) a line
    yw       Yank (copy) a word
    y$       Yank (copy) to end of line
    p        Put (paste) the clipboard after cursor
    P        Put (paste) before cursor
    
    x        Delete a character
    dd       Delete (cut) a line
    dw       Delete (cut) the characters of the word from the cursor position to the start of the next word
    d$       Delete to end of line
```

### SEARCH AND REPLACE:
```
    /(pattern)
             Search for pattern
    ?(pattern)
             Search for pattern in the opposite direction
    n        Cycle through iterations of pattern forwards
    N        Cycle through iterations of pattern backwards
    
    :noh     Remove searching highlighting
```

### VISUAL MODE:
```
    v         Visual mode
    V         Visual Line mode (highlight entire lines)
    <CTRL-V>  Visual Block mode (highlight columns as opposed to rows) 
    
    >         Shift text right
    <         Shift text left
    y         Yank (copy) marked text
    d         Delete marked text
```

### BUFFER CONTROL:
```
    :e <file> Edit a file in a new buffer
    :bn       Go to the next buffer
    :bp       Go to the previous buffer
    :bd       Delete a buffer (close a file)
    :ls       List all open buffers
    :sp <file>
              Open a file in a new buffer and split window
    :vsp <file>
              Open a file in a new buffer and vertically split window
              
    <CTRL-ws> Split window
    <CTRL-ww> Switch windows
    <CTRL-wq> Quit a window
    <CTRL-wv> Split window vertically
    <CTRL-wh> Move cursor to the left window (vertical split)
    <CTRL-wl> Move cursor to the right window (vertical split)
    <CTRL-wj> Move cursor to the window below (horizontal split)
    <CTRL-wk> Move cursor to the window above (horizontal split)
```

### VIMDIFF:
```
    vimdiff <file1> <file2>
              Find the differences between two files
```

-------------------------------------------------------------------------------
# WE'RE DONE!
Vim is Copyright (c) 1988-2003 Bram Moolenaar.
These notes were taken by davidm19 based on the built-in Vimtutor as well as [this online cheat sheet](https://vim.rtorr.com/).
