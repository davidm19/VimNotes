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
    
    :(FIRST LINE NUMBER),(SECOND LINE NUMBER)w FILENAME
              Write out chosen lines to a separate file named FILENAME
    :r FILENAME
              Read in a file named FILENAME
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
    :g/PATTERN/d
             Delete all lines containing any occurences of PATTERN
    
    <CTRL-a> INCREASE the value of the current NUMBER by 1
    <CTRL-x> DECREASE the value of the current NUMBER by 1
```

### SEARCH AND REPLACE:
```
    /(pattern)
             Search for pattern
    ?(pattern)
             Search for pattern in the opposite direction
    n        Cycle through iterations of pattern forwards
    N        Cycle through iterations of pattern backwards
    
    *        Cycle through each line forwards where pattern occurs
    #        Cycle through each line backwards where pattern occurs
    
    %        Cycle between alternating bracket pairs
    
    :s/foo/bar/g
             Change the first instance of 'foo' to 'bar'
    :s/foo/bar/g
             Change each 'foo' to 'bar' in the current line
    :%s/foo/bar/g
             Change each 'foo' to 'bar' in all the lines
    :5,12s/foo/bar/g
             Change each 'foo' to 'bar' for all lines from line 5 to line 12 (inclusive)
    :.,+2s/foo/bar/g
             Change each 'foo' to 'bar' for the current line (.) and the two next lines (+2)
    :%s/\<foo\>/bar/gc
             Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation
    
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

### VIMDIFF/MERGETOOL:
```
    vimdiff/vim -d <file1> <file2>
              Find the differences between two files
              
    dp        diffput: puts changes under the cursor into the other file
                        making them identical (thus removing the diff).
    do        diffget: (o => obtain). The change under the cursor is replaced
                        by the content of the other file making them identical.

    ]c        Jump to the next diff
    [c        Jump to the previous diff
    
    :diffg LO Merge files from LOCAL (the file from your current branch)
    :diffg BA Merge files from BASE (current file from the previous commit)
    :diffg RE Merge files from REMOTE (the file from the branch you're merging with)
```

### BUFFERS, TABS, WINDOWS, AND SESSIONS:
```
    BUFFERS:
    :e <file> Edit a file in a new buffer
    :bn       Go to the next buffer
    :bp       Go to the previous buffer
    :bd       Delete a buffer (close a file)
    :ls       List all open buffers
    <CTRL-6>  Switch between current and previous buffer
    
    TABS:
    :tabnew <file>
              open a file in a new tab
    Ctrl + wT move the current split window into its own tab
    gt        move to the next tab
    gT        move to the previous tab
    <n>gt     move to tab number n
    :tabmove <n>
              move current tab to the #th position (indexed from 0)
    :tabc     close the current tab and all its windows
    :tabonly  close all tabs except for the current one
    :tabdo <command>
              run the command on all tabs (e.g. :tabdo q - closes all opened tabs)
    
    WINDOWS:
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
    <CTRL-wH> Move window to the left
    <CTRL-wL> Move window to the right
    <CTRL-wJ> Move window to the window
    <CTRL-wK> Move window to the window
    
    SESSIONS (saving workflows and reloading them at later times; BE SURE YOU'RE SAVING YOUR WORK!):
    :mksession ~/current_session.vim
              Creates a session (current workspace, location, and all that jazz) titled session.vim
    :source ~/current_session.vim / vim -S ~/current_session.vim
              Loads session.vim
```

### A QUICK NOTE ON WHEN USING BUFFERS, TABS, AND WINDOWS (adapted from [this StackOverflow answer](https://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs)):
- Usually you'll have 2, 30 or 97 **buffers** loaded at a time
- Use **windows** when you need to compare two files or work in one part of the current buffer while keeping another as a reference
- Load a brand new **tab page** when you need to work for a while on a separate part of the project without messing with your current view

### EXECUTING CODE (for those stubborn enough to not want to use the shell)
```
    C/C++ FILES
    :make     Make the makefile
    :make %:r Compiles the current C/C++ file without a makefile
    
    FOR EVERYTHING ELSE: Just use :! (language command) to run it
    You might even look here for a more in-depth guide on how to run code, I won't judge:     http://ajmccluskey.com/2015/01/executing-your-code-from-vim/
```

### BONUS ROUND! CMUS... !!!FINISH ME!!!
```
    q              Quit CMUS
    I              Print location of current song
    b              Next song
    c              Pause current song
    x              Play current song
    z              Previous song
    v              Stop song
    ^L             Refresh
    /              Search for songs containing a pattern
    n              Next entry in search
    N              Previous entry in search
    TAB            Move between artist/album windows and songs
    .              Skip forwards in current song by a minute
    l, right       Skip forwards in current song by 5 seconds
    ,              Go backwards in current song by a minute
    h, left        Go backwards in current song by 5 seconds
    m              Toggle between all songs, only songs by current artist, and only songs in current album
    C              Toggle continuous play (when a song ends it's not followed by the next song)
    M              Toggle between album and playlist
    o              toggle play_sorted
    r              Toggle Repeat play
    ^R             Toggle Repeat current song
    t              Show remaining time
    s              Toggle shuffle mode
    F              push filter<space>
    L              push live-filter<space>
    u              Update cache
    1              View tree (albums/artists)
    2              View sorted
    3              View playlist
    4              View queue
    5              View browser
    6              View filters
    7              View settings
    !              push shell<space>
    ]              vol +0 +1
    [              vol +1 +0
    +, =           Raise volume by 10%
    }              vol -0 -1
    {              vol -1 -0
    -              Lower volume by 10%
    enter          Play selected song
    E              win-add-Q
    a              win-add-l
    y              win-add-p
    e              win-add-q
    G, end         win-bottom
    down, j        win-down
    p              win-mv-after
    P              win-mv-before
    ^F, page_down  win-page-down
    ^B, page_up    win-page-up
    D, delete      win-remove
    i              win-sel-cur
    space          win-toggle
    g, home        win-top
    k, up          win-up
```

### ...AND RANGER !!!FINISH ME!!!

-------------------------------------------------------------------------------
# WE'RE DONE!
Vim is Copyright (c) 1988-2003 Bram Moolenaar.
These notes were taken by davidm19 based on the built-in Vimtutor as well as [this online cheat sheet](https://vim.rtorr.com/) and [this StackOverflow answer](https://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs).
