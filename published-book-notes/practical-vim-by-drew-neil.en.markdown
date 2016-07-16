# Practical Vim
## de Drew Neil

[![Practical Vim](img/practical-vim.jpg)](https://pragprog.com/book/dnvim/practical-vim)

### Taken notes

Echar un vistazo a `vimtutor`, dentro de Vim. Quizá es una buena forma de empezar, aunque uno ya haya dado algunos pasos con Vim.

## Chapter 1 the vim way

Vim is optimized for repetition

### tip 1    meet the dot command

The dot command lets us repeat the last change

### tip 2    don’t repeat yourself

Vim provides dedicated commands that combines two steps into one. `A` command compounds two actions `$a` into a single keystroke

## tip 3    take one step back, then three forward

The `s` command compounds two steps into one: it deletes the character under the cursor and then enters insert mode

### tip 4    act, repeat, reverse

The optimal editing strategy is making both the motion and the change repeatable.

For example, `@:` can be used to repeat any ex command. Or we can repeat the last `:substitute` command (which itself happens to be an ex command as well) by pressing &

### tip 5    find and replace by hand

Change the first occurrence by hand and then find and replace every other match one by one

Be lazy: search without typing with the `*` command

### tip 6    meet the dot formula

One keystroke to move, one keystroke to execute

## Chapter 2 Normal Mode

### Tip 7    Pause with Your Brush Off the Page

Just as painters spend a fraction of their time applying paint, programmers spend a fraction of their time composing code

### Tip 8    Chunk Your Undos

So we can make the undo command operate on words, sentences, or paragraphs just by moderating our use of the `<Esc>` key

### Tip 9    Compose Repeatable Changes

We have to be mindful of how we compose our changes

### Tip 10    Use Counts to Do Simple Arithmetic

### Tip 11    Don’t Count If You Can Repeat

Consider the pros and cons of counting versus repeating. Specially when undoing. It's easier to undo repeatable changes than non repeatable ones: `2dw` Vs. `dw` and `.`

### Tip 12    Combine and Conquer

Much of Vim’s power stems from the way that operators and motions can be combined. The combination of operators with motions forms a kind of grammar. Learning new motions and operators is like learning the vocabulary of Vim. If we follow the simple grammar rules, we can express more ideas as our vocabulary grows.

## Chapter 3 Insert Mode

### Tip 13    Make Corrections Instantly from Insert Mode

Commands `<C-h>`, `<C-w>`, `<C-u>`

### Tip 14    Get Back to Normal Mode

Insert Normal mode is a special version of Normal mode, which gives us one bullet. We can fire off a single command, after which we’ll be returned to Insert mode immediately.

Remap the Caps Lock Key. Many Vim users remap the Caps Lock button to make it act like another key, such as `<Esc>` or `<Ctrl>`. The simplest way to remap the Caps Lock key is to do it at the system level

### Tip 15    Paste from a Register Without Leaving Insert Mode

The general format of the command is `<C-r>{register}`

The `<C-r><C-p>{register}` command is smarter. It inserts text literally and fixes any unintended indentation

### Tip 16    Do Back-of-the-Envelope Calculations in Place

The expression register allows us to perform calculations and then insert the result directly into our document. The expression register is addressed by the = symbol. From Insert mode we can access it by typing <C-r>=.

### Tip 17    Insert Unusual Characters by Character Code

From Insert mode, we just have to type `<C-v>{code}`

### Tip 18    Insert Unusual Characters by Digraph

### Tip 19    Overwrite Existing Text with Replace Mode

From Normal mode, we can engage Replace mode with the `R` command. Virtual Replace mode is triggered with `gR` and treats the tab character as though it consisted of spaces.

## Chapter 4 Visual Mode

### Tip 20    Grok Visual Mode

Visual mode is just another mode, which means that each key performs a different function. According to Vim’s built-in documentation, it “resembles the selection mode in Microsoft Windows”. We can toggle between Visual and Select modes by pressing `<C-g>`. But if we type any printable character in Select mode, it will replace the selection and switch to Insert mode.

### Tip 21    Define a Visual Selection

Vim has three kinds of Visual mode.

- character-wise Visual mode, from the `v` command
- line-wise Visual mode, `V` command
- block-wise Visual mode, `<C-v>`

`gv` reselect the last visual selection

The range of a Visual mode selection is marked by two ends: one end is fixed and the other moves freely with our cursor. We can use the o key to toggle the free end.

### Tip 23    Prefer Operators to Visual Commands Where Possible

Visual mode may be more intuitive than Vim’s Normal mode of operation, but it has a weakness: it doesn’t always play well with the dot command.

### Tip 24    Edit Tabular Data with Visual-Block Mode

### Tip 25    Change Columns of Text

We can use Visual-Block mode to insert text into several lines of text simultaneously.

### Tip 26    Append After a Ragged Visual Block

Visual-Block mode it’s not confined to rectangular regions of text.

The `I` and `A` commands both do it, placing the cursor at the start or end of the selection, respectively.

In Visual and Operator-Pending modes the `i` and `a` keys follow a different convention: they form the first half of a text object.

## Chapter 5 Command-Line Mode

### Tip 27    Meet Vim’s Command Line

Command-Line mode prompts us to enter an Ex command, a search pattern, or an expression. When we press the `:` key, Vim switches into Command-Line mode. Command-Line mode is also enabled when we press `/` to bring up a search prompt or `<C-r>=` to access the expression register

`<C-w>` and `<C-u>` delete backward to the start of the previous word or to the start of the line, respectively. We can insert the contents of any register at the command line using the `<C-r>{register}`

The greatest feature that distinguishes Ex commands is their ability to be executed across many lines at the same time.

### Tip 28    Execute a Command on One or More Consecutive Lines

Many Ex commands can be given a `[range]` of lines to act upon. If we enter an Ex command consisting only of a number, then Vim will interpret that as an address and move our cursor to the specified line. If we had issued the command `:3d`, then we would have jumped to line 3 and deleted it in a single move.

The range `:2,5` selects lines from `2` to `5`

We can use the `.` symbol as an address to represent the current line. The `%` symbol also has a special meaning—it stands for all the lines in the current file

Ranges can also be specified by visual selection, or by patterns. `:{start},{end}`. The `{start}` address in this case is the pattern `/<html>/`, while the `{end}` address is `/<\/html>/`.

Offsets can also be defined: `:/<html>/+1,/<\html/>/-1`

### Tip 29    Duplicate or Move Lines Using ‘:t’ and ‘:m’ Commands

The one notable difference between these two techniques for duplicating the current line is that `yyp` uses a register, whereas `:t`. doesn’t. When duplicating a distant line, the `:t` command is usually more efficient. Repeating the last Ex command is as easy as pressing `@:`

### Tip 30    Run Normal Mode Commands Across a Range

If we want to run a Normal mode command on a series of consecutive lines, we can do so using the `:normal` command. The `%` symbol is used as a range representing the entire file. So `:%normal A;` instructs Vim to append a semicolon at the end of every line of the file. I find it most powerful when used in combination with one of Vim’s repeat commands: either `:normal .` for simple repeats or `:normal @q` for repeating the las macro

### Tip 31    Repeat the Last Ex Command

The `@:` command can be useful when iterating through items in the buffer list. We can step forward through the list with the `:bn[ext]` command and backward with the `:bp[revious]`. After running `@:` for the first time, we can subsequently repeat it with the `@@` command. The `<C-o>` command goes back to the previous record in the jump list.

### Tip 32    Tab-Complete Your Ex Commands

Just like in the shell, we can use the `<Tab>` key to autocomplete commands at the prompt. The `<C-d>` command asks Vim to reveal a list of possible completions. We can scroll backward through the suggestions by pressing `<S-Tab>`.

We can customize this behavior by tweaking the `wildmode` option:

    wildmode=longest,list
    wildmenu
    set wildmode=full

We can scroll forward through the items by pressing `<Tab>`, `<C-n>`, or `<Right>`, and we can scroll backward through them with `<S-Tab>`, `<C-p>`, or `<Left>`.

### Tip 33    Insert the Current Word at the Command Prompt

At Vim’s command line, the `<C-r><C-w>` mapping copies the word under the cursor and inserts it at the command-line prompt. We didn’t have to type the search pattern either, thanks to the `*` command. While `<C-r><C-w>` gets the word under the cursor, we can instead use `<C-r><C-a>` if we want to get the WORD

### Tip 34    Recall Commands from History

We can use the `<Up>` key again to go further back through our Ex command history or use the `<Down>` key to go in the opposite direction. By default, Vim records the last twenty commands.

    set history=200

As well as recording a history of Ex commands, Vim keeps a separate record of our search history. If we press `/` to bring up the search prompt, we can also scroll backward and forward through previous searches with the `<Up>` and `<Down>` keys. In addition to the `<Up>` and `<Down>` keys, we can also use the `<C-p>` and `<C-n>` chords to go backward and forward through our command history.

But there’s a disadvantage to the `<C-p>` and `<C-n>` commands: unlike `<Up>` and `<Down>`, they don’t filter the command history. We can get the best of both by creating the following custom mappings:

    cnoremap <C-p> <Up>
    cnoremap <C-n> <Down>

`q/` open the command-line window with history of searches, `q:` open the command-line window with history of Ex commands, `ctrl-f` switch from Command-Line mode to the command-line window

### Tip 35    Run Commands in the Shell

From Vim’s Command-Line mode, we can invoke external programs in the shell by prefixing them with a bang symbol `:!`

On Vim’s command line, the `%` symbol is shorthand for the current file name

What if we want to run several commands in the shell? In that case, we can use Vim’s `:shell`

We can use the `:read !{cmd}` command, which puts the output from the `{cmd}` into our current buffer. As you might expect, the `:write !{cmd}` does the inverse: it uses the contents of the buffer as standard input for the specified `{cmd}`

For example, both `make` and `grep` have wrapper commands. Not only are they easy to execute from inside Vim, but their output is parsed and used to populate the quickfix list.

## Chapter 6 Manage Multiple Files

### Tip 36    Track Open Files with the Buffer List

Files are stored on the disk, whereas buffers exist in memory. We can quickly toggle between the current and alternate files by pressing `<C-^>`. I use these mappings from Tim Pope’s unimpaired.vim plugin:

    nnoremap <silent> [b :bprevious <CR>
    nnoremap <silent> ]b :bnext <CR>
    nnoremap <silent> [B :bfirst <CR>
    nnoremap <silent> ]B :blast <CR>

### Tip 37    Group Buffers into a Collection with the Argument List

Now let’s examine the argument list: `:args`. The argument list represents the list of files that was passed as an argument when we ran the vim command.

We can change the contents of the argument list at any time with `:args {arg list}`

We can traverse the files in the argument list using `:next` and `:prev` commands. Or we can use `:argdo` to execute the same command on each buffer in the set.

### Tip 38    Manage Hidden Files

If we want to discard the changes, we can instead run `:edit!`, which rereads the file from disk, overwriting the contents of the buffer. If we want to quit Vim without reviewing our unsaved changes, we can issue the `:qall!` command. Or, if we want to write all modified buffers without reviewing them one by one, we can use the `:wall` command.

If we enable the ‘hidden’ setting. If the active buffer is modified, Vim will automatically hide it when we navigate away from it.

### Tip 39    Divide Your Workspace into Split Windows

`:sp[lit] {file}` split the current window horizontally, loading `{file}` into the new window
`:vsp[lit] {file}` split the current window vertically, loading `{file}` into the new window
`<C-w>w` or `<C-w><C-w>` cycle between open windows
`:cl[ose]` or `<C-w>c` close the active window
`:on[ly]` or `<C-w>o` keep only the active window, closing all others  

### Tip 40    Organize Your Window Layouts with Tab Pages

Think of a tab page as a container that can hold a collection of windows. Vim’s tab pages can be used to partition work into different workspaces. The `:lcd {path}` command lets us set the working directory locally for the current window. If we create a new tab page and then use the `:lcd` command to switch to another directory, we can then comfortably scope each tab page to a different project.

If we have a tab page containing two or more split windows, we could set the local working directory for all of them by running `:windo lcd {path}`.

We can open a new tab page with the `:tabedit {filename}` command. The `<C-w>T` command, which moves the current window into a new tab page

`:tabclose`, if we want to close all tab pages except for the current one, we can use the `:tabonly` command.

`:tabn[ext] {N}` or `{N}gt` switch to tab page number `{N}`
`:tabn[ext]` or `gt` switch to the next tab page
`:tabp[revious]` or `gT` switch to the previous tab page  

## Chapter 7 Open Files and Save Them to Disk

### Tip 41    Open a File by Its Filepath Using ‘:edit’

Try sourcing this line in your vimrc file: `cnoremap <expr> %%  getcmdtype() == ':' ? expand('%:h').'/' : '%%'`

Now when we type `%%` on Vim’s `:` command-line prompt, it automatically expands to the path of the active buffer, just as though we had typed `%:h <Tab>`. Besides

### Tip 42    Open a File by Its Filename Using ‘:find’

The `path` option allows us to specify a set of directories inside of which Vim will search when the `:find` command is invoked. In our case, we want to make it easier to look up files in the `app/controllers` and `app/views` directories. We can add these to our path simply by running `:set path+=app/**`

### Tip 43    Explore the File System with netrw

If we launch Vim with the path to a directory rather than a file, it will start up with a file explorer window

We can open the parent directory by pressing the `-` key or by positioning the cursor on the `..` item and pressing `<CR>`.

We can open the file explorer window with the `:edit {path}` command by supplying a directory name

The dot symbol stands for the current working directory, so if we run the `:edit .` command, we can bring up a file explorer for the project root.

`:Explore` has the same effect as ':edit .'. And `:Explore` can be truncated right down to `:E`. `:Sexplore` and `:Vexplore` commands, which open the file explorer in a horizontal split window or vertical split window

### Tip 44    Save Files to Nonexistent Directories

# Part 3 Getting Around Faster

## Chapter 8 Navigate Inside Files with Motions

### Tip 46    Keep Your Fingers on the Home Row

Vim is optimized for the touch typist.

### Tip 47    Distinguish Between Real Lines and Display Lines

Vim makes a distinction between real lines and display lines (wrapped part of large lines)

The `gj` and `gk` commands move down and up by display lines.

`0` to first character of real line, `g0` to first character of display line, `^` to first nonblank character of real line  

### Tip 48    Move Word-Wise

`ge` backward to end of previous word  

Each word-wise motion we met earlier has a WORD-wise equivalent, including `W`, `B`, `E`, and `gE`. The definition of a WORD is simpler: it consists of a sequence of nonblank characters separated with whitespace

### Tip 49    Find by Character

### Tip 50    Search to Navigate

We’re not limited to using the search command in Normal mode. We can use it from Visual and Operator-Pending modes just as well

### Tip 51    Trace Your Selection with Precision Text Objects

Whenever you see `{motion}` as part of the syntax for a command, you can also use a text object.

### Tip 52    Delete Around, or Change Inside

- `is` current sentence
- `as` current sentence plus one space
- `ip` current paragraph
- `ap` current paragraph

As a general rule, we could say that the `d{motion}` command tends to work well with `aw`, `as`, and `ap`, whereas the `c{motion}` command works better with `iw` and similar.

### Tip 53    Mark Your Place and Snap Back to It

The `m{a-zA-Z}` command marks the current cursor location with the designated letter. Lowercase marks are local to each individual buffer, whereas uppercase marks are globally accessible.

`'{mark}` moves to the line where a mark was set

Vim’s Automatic Marks

- `“` position before the last jump within current file
- `‘.` location of last change
- `‘^` last insertion
- `‘[` st change or yank
- `‘]` end of last change or yank
- `‘<` start of last visual selection
- `‘>` end of last visual selection  

### Tip 54    Jump Between Matching Parentheses

`%` command

When the **matchit** plugin is enabled (included with Vim), the `%` command can jump between matching pairs of keywords. For example, in an HTML file, the `%` command would jump between opening and closing tags. In a Ruby file, it would jump between `class/end`, `def/end`, and `if/end` pairs.

## Chapter 9 Navigate Between Files with Jumps

### Tip 55    Traverse the Jump List

Vim records our location before and after making a jump and provides a couple of commands for retracing our steps: `<C-o>` and `<C-i>`

### Tip 56    Traverse the Change List Vim records the location of our cursor after each change we make to a document. Traversing this change list

We can inspect its contents by running `:changes`

Using the `g;` and `g,` commands, we can traverse backward and forward through the change list. If we leave Insert mode and then scroll around the document, we can quickly carry on where we left off by pressing `gi`

### Tip 57    Jump to the Filename Under the Cursor

Vim treats filenames in our document as a kind of hyperlink. When configured properly, we can use the `gf` command to go to the filename under the cursor.

The `suffixesadd` option allows us to specify one or more file extensions, which Vim will attempt to use when looking up a filename with the `gf` command. When we use the `gf` command, Vim checks each of the directories listed in `path`

### Tip 58    Snap Between Files Using Global Marks

The `m{capital letter}` command creates global marks.

Try to get into a habit of setting a global mark before using any commands that interact with the quickfix list, the buffer and argument lists

# Part 4 Registers

## Chapter 10 Copy and Paste

### Tip 59    Delete, Yank, and Put with Vim’s Unnamed Register

The `diw` command doesn’t just delete the word: it also copies it into the unnamed register.

How can you remove text from the document and not copy it into any registers? Vim’s answer is a special register called the black hole, from which nothing returns. The black hole register is addressed by the `_` symbol, so `"_d{motion}` performs a true deletion.

### Tip 60    Grok Vim’s Registers

We can specify which register we want to use by prefixing the command with `"{register}`. If we don’t specify a register, then Vim will use the unnamed register.

Vim also provides Ex commands for delete, yank, and put operations. We could cut the current line into register `c` by running `:delete c`

The Yank Register ("0): when we use the `y{motion}` command, the specified text is copied not only into the unnamed register but also into the yank register, which is addressed by the `0` symbol

It’s not set by the `x`, `s`, `c{motion}`, and `d{motion}` commands.

When we address a named register with a lowercase letter, it overwrites the specified register, whereas when we use an uppercase letter, it appends to the specified register.

If we use the cut or copy command to capture text in an external application, then we can paste it inside Vim using `"+p` command (or `<C-r>+` from the Insert mode).

- `"=`: expression register
- `"%`: name of the current file
- `"#`: name of alternate file
- `".`: last inserted text
- `":`: last Ex command
- `"/`: last search pattern

### Tip 61    Replace a Visual Selection with a Register

When we use the `p` command in Visual mode, Vim replaces the selection with the contents of the specified register

### Tip 62    Paste from a Register

`gp` and `gP` commands. These also put the text before or after the current line, but they leave the cursor positioned at the end of the pasted text instead of at the beginning.

### Tip 63    Interact with the System Clipboard

## Chapter 11 Macros

### Tip 64    Record and Execute a Macro

### Tip 65    Normalize, Strike, Abort

- Normalize the Cursor Position
- Strike Your Target with a Repeatable Motion
- Abort When a Motion Fails
- If a motion fails while a macro is executing, then Vim aborts the rest of the macro.

### Tip 66    Play Back with a Count

### Tip 67    Repeat a Change on Contiguous Lines

To execute macro in parallel, select lines with `VG` and then execute the macro with `:normal @q`

### Tip 68    Append Commands to a Macro

If we type `qa`, then Vim will record our keystrokes, saving them into register `a` by overwriting the existing contents of that register. If we type `qA`, then Vim will record our keystrokes, appending them to the existing contents of register `a`.

### Tip 69    Act Upon a Collection of Files

The `:argdo` command allows us to execute an Ex command once for each buffer in the argument list. `:argdo normal @a` will run the macro saved on register `a`

If we want to make it act upon multiple buffers, we could append a final step that advances to the next buffer in the list with `:next`

Another useful command is `:wnext` which is equivalent to running `:write` followed by `:next`. If you are executing a macro in series across several files in the argument list, you may prefer to use this.

### Tip 70    Evaluate an Iterator to Number Items in a List

Using the `let` keyword, we can create a variable called `i` and assign it a value of `0`. We can insert the value stored in variable `i` just by running `<C-r>=i<CR>` in Insert mode.

### Tip 71    Edit the Contents of a Macro

the `~` command, which toggles the case of the letter under the cursor

The registers that we use for recording macros are the very same with which the yank and put operations interact. So if we want to make changes to the macro saved in register `a`, we simply have to paste it into the document. Now we can edit the macro as plain text. So we can yank it from the document back into a register: `"ay$`

## Chapter 12 Matching Patterns and Literals

### Tip 72    Tune the Case Sensitivity of Search Patterns

We can make Vim’s search patterns case insensitive by enabling the `ignorecase` setting.

We can override Vim’s default case sensitivity using the `\c` and `\C` items. Lowercase `\c` causes the search pattern to ignore case, while the uppercase `\C` item forces case sensitivity

When enabled, `smartcase` has the effect of canceling out the `ignorecase` setting any time that we include an uppercase character in our search pattern.

### Tip 73    Use the \v Pattern Switch for Regex Searches

the `\v` pattern switch. This enables very magic search, where all characters assume a special meaning, with the exception of `_`, uppercase and lowercase letters, and the digits `0` through `9`

### Tip 74    Use the \V Literal Switch for Verbatim Searches

Using the `verynomagic` literal switch, we can cancel out most of the special meanings attached to characters such as `.`, `*`, and `?`.

### Tip 75    Use Parentheses to Capture Submatches

When specifying a pattern, we can capture submatches and then reference them elsewhere. Anything that matches inside of parentheses is automatically assigned to a temporary silo. We can reference the captured text as `\1`. The `\0` item always refers to the entire match

The `<` and `>` symbols match word boundaries, the `\_s` item matches whitespace or a line break

### Tip 76    Stake the Boundaries of a Word

In very magic searches, these are represented by the `<` and `>` symbols. So if we amended our search to `/\v<the> <CR>`, otherwise, we would select text such as `their`, `these`, `tthey`,...

`\w` matches word characters, including letters, numbers, and the `_` symbol, while `\W` matches everything except for word characters.

### Tip 77    Stake the Boundaries of a Match

The boundaries of a match normally correspond to the start and end of a pattern. But we can use the `\zs` and `\ze` items to crop the match, making it a subset of the entire pattern

### Tip 78    Escape Problem Characters

## Chapter 13 Search

### Tip 79    Meet the Search Command

If we execute a search without providing a pattern, Vim will just reuse the pattern from the previous search

### Tip 80    Highlight Search Matches

### Tip 81    Preview the First Match Before Execution

`<C-r><C-w>` autocompletes the search field using the remainder of the current preview match.

### Tip 82    Count the Matches for the Current Pattern

`:%s///gn`

### Tip 83    Offset the Cursor to the End of a Search Match

Here, we search for `/lang/e <CR>`, which places the cursor at the end of the search match,

### Tip 84    Operate on a Complete Search Match

Here’s the trick: `gU //e <CR>`. We’re using `//e <CR>` as a motion, which reaches from the start to the end of the search match.

My favorite solution is the textobj-lastpat plugin, by Kana Natsuno, which adds an `i/` text object for operating on search matches. Using this, we can make the same change as before just by running `gUi/`.

### Tip 85    Create Complex Patterns by Iterating upon Search History

Press `q/` to summon the command-line window. This acts more or less like a regular Vim buffer, but it’s prepopulated with our search history, one item per line. We can use the full power of Vim’s modal editing to amend the last pattern.

### Tip 86    Search for the Current Visual Selection

You can either paste this into your vimrc file directly or install the *visual star search* plugin.

## Chapter 14 Substitution

### Tip 87    Meet the Substitute Command

- `g` flag makes the substitute command act globally, causing it to change all matches within a line rather than just changing the first one.
- `c` flag gives us the opportunity to confirm or reject each change.
- `n` flag suppresses the usual substitute behavior, causing the command to report the number of occurrences
- `&` flag simply tells Vim to reuse the same flags from the previous substitute command.
- `\={Vim script}` token is very powerful. It allows us to execute code and use the result as our replacement {string}.

### Tip 88    Find and Replace Every Match in a File

### Tip 89    Eyeball Each Substitution

The `c` flag causes Vim to show us each match and ask “Replace with copy?” We can then say `y` to perform the change or `n` to skip it.

### Tip 90    Reuse the Last Search Pattern

### Tip 91    Replace with the Contents of a Register

Pass by value: we can insert the contents of a register by typing `<C-r>{register}`. Pass by reference: `:%s//\=@0/g`

In the replacement field, the `\=` item tells Vim to evaluate a Vim script expression. In Vim script, we can reference the contents of a register as `@{register}`.

We create a record in our command history that reads `:%s//\=@a/g`. It can do very different things, depending on the contents of the `/` and `a` register. You might love it or you might hate it. But either way, it’s a pretty neat trick!

### Tip 92    Repeat the Previous Substitute Command

We can repeat the command across the entire file just by pressing `g&`, which is equivalent to running the following: `:%s//~/&``

Making `&` trigger the `:&&` command is more useful. These mappings fix the `&` command in Normal mode and create a Visual mode equivalent: 

    nnoremap & :&&<CR>
    xnoremap & :&&<CR>

### Tip 93    Rearrange CSV Fields Using Submatches

### Tip 94    Perform Arithmetic on the Replacement

### Tip 95    Swap Two or More Words

### Tip 96    Find and Replace Across Multiple Files

Running `:args **/*.txt` loads all files from the current project into the argument list. Then when we run `:argdo %s//Practical/ge`, Vim proceeds to execute the substitute command in every one of those files.

To perform a project-wide search, we’ll reach for the `:vimgrep` command

    :vimgrep {pattern} {files pattern}
    :vimgrep /<C-r>// **/*.txt

Each match returned by vimgrep is recorded in the quickfix list

With [vim-quargs plugin](https://github.com/nelstrom/vim-qargs), we can run `:Qargs`, and it will populate the argument list with each of the files named in the quickfix list.

## Chapter 15 Global Commands

### Tip 97    Meet the Global Command

The `:global` command allows us to run an Ex command on each line that matches a particular pattern.

### Tip 98    Delete Lines Containing a Pattern

Delete Matching Lines with `:g/{regular expression}/d`

Keep Only Matching Lines with ‘:v/{regular expression}/d’

### Tip 99    Collect TODO Items in a Register

First we’ll need to clear it by running qaq. Now we can go ahead and yank the TODO comments into the register: `:g/TODO/yank A`

### Tip 100    Alphabetize the Properties of Each Rule in a CSS File

Suppose that we want to sort the properties of each rule into alphabetical order. We could do so using Vim’s built-in `:sort` command

## Chapter 16 Index and Navigate Source Code with ctags

### Tip 101    Meet ctags

Mozilla runs a project called Doctor JS which includes a `jsctags` program. `jsctags` produces output in the same format as ctags, so it works seamlessly with Vim.

### Tip 102    Configure Vim to Work with ctags

Creating a mapping for it: `:nnoremap <f5> :!ctags -R<CR>`

Automatically execute ctags each time a file is saved with `:autocmd BufWritePost * call system("ctags -R")`

Automatically execute ctags with version control hooks: [Effortless Ctags with Git, by Tim Pope](http://tbaggery.com/2011/08/08/effortless-ctags-with-git.html)

### Tip 103    Navigate Keyword Definitions with Vim’s Tag Navigation Commands

Pressing `<C-]>` makes our cursor jump from the keyword under the cursor to the definition. The `<C-t>` command acts as the back button for our tag history. But if it has multiple matches, then the `g<C-]>` command presents us with a list of choices from the tag match list. These Ex commands can accept a regular expression when used in the form `:tag /{pattern}` or `:tjump /{pattern}`

## Chapter 17 Compile Code and Navigate Errors with the Quickfix List

### Tip 104    Compile Code Without Leaving Vim

From inside Vim, we can now run the `:make` command. Instead of just echoing the output from make, Vim parses each line, extracting the filename, line number, and error message. For each warning, Vim creates a record in the quickfix list.

### Tip 105    Browse the Quickfix List

- `:cnext` jump to next item
- `:cprev` jump to previous item
- `:cfirst` jump to first item
- `:clast` jump to last item
- `:cnfile` jump to first item in next file
- `:cpfile` jump to last item in previous file
- `:cc` N jump to   nth item
- `:copen` open the quickfix window
- `:cclose` close the quickfix window  

The location list has equivalents for all of these commands, each beginning with `:l`, such as `:lnext`, `:lprev`, and so on.

For every command that populates the quickfix list, there’s a variant that places the results in a location list instead. While `:make`, `:grep`, and `:vimgrep` use the quickfix list, `:lmake`, `:lgrep`, and `:lvimgrep` use the location list.

There can be only one quickfix list, but we can create as many location lists as we want.

Any commands that interact with a location list (`:lnext`, `:lprev`, and so on) will act on the list that is bound to the currently active window.

### Tip 106    Recall Results from a Previous Quickfix List

We can recall an older version of the quickfix list (Vim holds onto the last ten lists) by running the `:colder` command. To revert from an old quickfix list back to a newer one, we run `:cnewer`

### Tip 107    Customize the External Compiler

The `makeprg` setting allows us to specify the program that will be called when we run `:make`

The `errorformat` setting allows us to teach Vim how to parse the output generated by running `:make`. This `errorformat` string is not something we would want to commit to memory. Instead, we can save it to a file and then activate it with the `:compiler` command

## Chapter 18 Search Project-Wide with grep, vimgrep, and Others

### Tip 108    Call grep Without Leaving Vim

### Tip 109    Customize the grep Program

Two settings: `grepprg` and `grepformat`.

### Tip 110    Grep with Vim’s Internal Search Engine

    :vim[grep][!] /{pattern}/[g][j] {file}

We can compose a regular expression by searching in the current file. When we’re satisfied that it matches where it should, we execute `:vimgrep` using the exact same pattern.

## Chapter 19 Dial X for Autocompletion

### Tip 111    Meet Vim’s Keyword Autocompletion

- `<C-n>` Generic keywords
- `<C-x><C-n>` Current buffer keywords
- `<C-x><C-i>` Included file keywords
- `<C-x><C-]>` tags file keywords
- `<C-x><C-k>` Dictionary lookup
- `<C-x><C-l>` Whole line completion
- `<C-x><C-f>` Filename completion
- `<C-x><C-o>` Omni-completion  

### Tip 112    Work with the Autocomplete Pop-Up Menu

- <C-n> Use the next match from the word list (  next match)
- <C-p> Use the previous match from the word list (  previous match)
- <Down> Select the next match from the word list
- <Up> Select the previous match from the word list
- <C-y> Accept the currently selected match (  yes)
- <C-e> Revert to the originally typed text (  exit from autocompletion)
- <C-h> (and <BS>) Delete one character from current match
- <C-l> Add one character from current match
- {char} Stop completion and insert   {char}

### Tip 113    Understand the Source of Keywords

Vim understands the C way of including files, but it can be taught to follow the corresponding directives in other languages by tweaking the `include` setting (see `include`

### Tip 114    Autocomplete Words from the Dictionary

The easiest way to do this is by running `:set spell` to enable Vim’s spell checker. All of the words in the spelling dictionary become available through the `<C-x><C-k>` command.

### Tip 115    Autocomplete Entire Lines

The beauty of line-wise autocompletion is that we don’t have to know the location of the line we’re duplicating. We need to know only that it exists.

### Tip 116    Autocomplete Filenames

Filename autocompletion is triggered by the `<C-x><C-f>` command. Just like in the shell, `cd -` switches to the previous working directory

### Tip 117    Autocomplete with Context Awareness

Omni-completion is Vim’s answer to intellisense.

## Chapter 20 Find and Fix Typos with Vim’s Spell Checker

### Tip 118    Spell Check Your Work

We can jump backward and forward between flagged words with the `[s` and `]s` commands

we can ask Vim for a list of suggested corrections by invoking the `z=` command.

- `]s` Jump to next spelling error
- `[s` Jump to previous spelling error
- `z=` Suggest corrections for current word
- `zg` Add current word to spell file
- `zw` Remove current word from spell file
- `zug` Revert `zg` or `zw` command for current word

### Tip 119    Use Alternate Spelling Dictionaries

We can change this by tweaking the `spelllang` option. This isn’t a global setting; `spelllang` is always local to the buffer.

### Tip 120    Add Words to the Spell File

### Tip 121    Fix Spelling Errors from Insert Mode

Alternatively, we could fix the error from Insert mode using the `<C-x>s` command,

## Chapter 21 Now What?

Apply Customizations to Certain Types of Files

    if has("autocmd")
      filetype on
      autocmd FileType ruby setlocal ts=2 sts=2 sw=2 et
      autocmd FileType javascript setlocal ts=4 sts=4 sw=4 noet 

We can have more than one autocommand listening for the same event.

Instead of declaring our JavaScript preferences in the vimrc using autocommands, we could place them in a file called ~/.vim/after/ftplugin/javascript.vim:

