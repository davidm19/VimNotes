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

### MORE SEARCH EXAMPLES!
# Original text
Does a boy get a chance to paint black a fence every day? That put the thing in a new light. Ben Rogers stopped nibbling his apple. Tom swept his brush daintily back and forth–stepped back to note the effect–added a touch here and there–criticised the effect again–Ben watching every move and getting more and more interested, more and more absorbed.
# Commands
```
:s/black/white/	Replace the first occurrence of the string ‘black’ by ‘white’
:s/Ben\( Rogers\)\@!/Ben Rogers/g	Replace every occurrence of the string ‘Ben’ by ‘Ben Rogers’ except when ‘ Rogers’ was already present
:s/.*/<p>\r&\r<\/p>/	 Wrap the line between <p> and </p>
:-1s/–/\&mdash;/g	 Replace every occurrence of the string ‘–‘ by ‘&mdash;’ in the preceding line
```
# Modified text
```
<p>
Does a boy get a chance to paint white a fence every day? That put the thing in a new light. Ben Rogers stopped nibbling his apple. Tom swept his brush daintily back and forth&mdash;stepped back to note the effect&mdash;added a touch here and there&mdash;criticised the effect again&mdash;Ben Rogers watching every move and getting more and more interested, more and more absorbed.
</p>
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

### WRITING IN PLAINTEXT:
```
    :set spell     Turn on spellchecking
    ]s             Jump to next mistake
    [s             Jump to previous mistake
    z=             See spelling suggestions for word under cursor
    zg             Add current word to regular dictionary
    zG             Add current word to the current session dictionary
    zug            Remove current word to regular dictionary
    zuG            Remove current word to the current session dictionary
    :ab [ABBREVIATION] [EXPRESSION]
                   Creates an abbreviation called ABBREVIATION which, when typed, will expand into EXPRESSION
    <CTRL-V>       Cancel use of abbreviation
    :una [ABBREVIATION]
                   Remove abbreviation ABBREVIATION
    :digraphs      List characters not present in current keyboard layout
    <CTRL-k> [##]  Add character with code ## (two numbers)
```

### BONUS ROUND! CMUS...
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
    o              Toggle play sorted
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
    ]              vol +0 +1 (right speaker up 1%, left speaker stays same)
    [              vol +1 +0 (left speaker up 1%, right speaker stays same)
    +, =           Raise volume by 10%
    }              vol -0 -1 (right speaker down 1%, left speaker stays same)
    {              vol -1 -0 (left speaker down 1%, right speaker stays same)
    -              Lower volume by 10%
    enter          Play selected song
    E              Add song to beginning of queue
    a              Copy selected tracks to library
    y              Copy selected tracks to playlist
    e              Add song to end of queue
    G, end         Go to end of screen
    down, j        Go down
    p              Move marked tracks to the position immediately after the selected track
    P              Move marked tracks to the position immediately before the selected track
    ^F, page_down  Page down
    ^B, page_up    Page up
    D, delete      Remove selected song from current view
    i              Select current track/toggle hidden files
    space          Toggle song/change (or show albums)
    g, home        Go to top of screen
    k, up          Go up
```

-------------------------------------------------------------------------------
# WE'RE DONE!
Vim is Copyright (c) 1988-2003 Bram Moolenaar.
These notes were taken by davidm19 based on the built-in Vimtutor as well as [this online cheat sheet](https://vim.rtorr.com/) and [this StackOverflow answer](https://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs).
