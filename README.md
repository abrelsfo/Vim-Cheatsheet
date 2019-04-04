# Vim-Cheatsheet

This is a compilation of the most useful tips and tricks for vim that I use on a daily basis and a few that aren't as useful but still come in  handy. This is designed to help you speed up your workflow but it's up to you to learn when to best apply these tricks. This is not meant to be a full comprehensive guide on how to use Vim and if you want to dive deeper into Vim then I highly recommend "Practical Vim" by Drew Neil or the long lost man pages or help page (:h) of vim.

## Table of Contents
- [**Modes**](#modes)
  - [Normal Mode](#normal-mode)
    - [Motions](#motions)
    - [Deletions/Operators](#deletionsoperators)
  - [Insert Mode](#insert-mode)
  - [Visual Mode](#visual-mode)
  - [Command-line Mode](#command-line-mode)
  - [The Dot Command](#the-dot-command)
  - [Vim Tabs](#vim-tabs)
  - [Things to do](#things-to-do)


## Basics

> This section is designed so you should be able to create a document. If you only read this part then you will technically be able to use Vim, but you will be missing out on it's  best features. If this is all you are using in Vim then I recommend switching to a different editor that will more than likely speed up your workflow. This section is the very basics of Vim and does not show to powerful tools Vim has to offer.

- how to open a file in vim
- how to type
- how to change modes and exit them
- how to save and quit a file

## Modes

> There are four main modes in Vim: Normal mode, Insert mode, Visual mode, and Command-line mode. Each of which has it's own set of commands. You should be able to tell what mode you are in  by looking at the bottom left

__Normal mode__ is the normal state of Vim. When you open Vim it will naturally be in normal mode and for good reason. The majority of your time will be spent in this mode and you will drastically speed up your editing if you are utilizing the commands normal mode has to offer.

__Insert mode__ is used to insert text. Most commands will be executed outside of this mode.

__Visual mode__ is used to select sections of text and is very useful for copying or editing specific sections of text

__Command-line mode__ this is one of Vim's most powerful tools. You can jump to a specified line, search for specific text, do a search and replace, and much more if you are willing to dig into it. This mode gives you full granularity so you can work on the entire document or just a specific section.

__Ex mode__ is similar to command-line mode but allows for batch processing. This mode allows a user to enter multiple commands without returning to normal mode. I will not be covering this mode since this is a document on the basics of Vim. However, I recommend looking into this if you see a need to execute multiple commands in a row, or if you have a good understanding of the bash command line.

## Normal Mode

> Normal mode is the default mode in Vim and the one that you will spend the majority of your time in. This is the mode that you will be navigating your documents with and the better you get at this mode the faster you will move, guaranteed. All of the following commands must be performed while in normal mode. They can have a different use in another mode.

### Motions
---
The basic motions in Vim are<br>
`h`, `j`, `k`, `l` which are `left`, `down`, `up`, and `right`, respectively.<br>
If you just really hate using those then you can also use the arrow keys

Beyond the basic motions there are all sorts of ways to move around your document at blistering speed
- `b, B`: move to the beginning of the previous word
- `w, W`: move to the beginning of the next word
- `e, E`: move to the end of the next/current word
- `$`: move to the end of the line
- `^`: move to the beginning of the line
- `gg`: move to the top of the file
- `G`: move to the bottom of the file
- `f{char}`: move forward to the first occurrence of `{char}` (Brackets are not necessary)
  - `F{char}`: moves back to the first occurrence of `{char}`
- `t{char}`: move forward to position before `{char}` on same line
  - `T{char}`: moves back to position after `{char}` on same line
- `;`: repeats last `f, t, F, or T` command
- `.`: repeats last change (More on this [later](#the-dot-command))

### Deletions/Operators
---
On top of moving around the document you can also do some limited editing, such as copy, cut/delete, and paste/put <br>
`c`, `d`, and `y` are called operators and are combined with a motion.<br>

`y` is our yank (copy) operator.
- y :right_arrow: : Copy the char under the cursor
- `y :left_arrow:`: Copy the char before the cursor
- `y :down_arrow:`: Copy the text on the current line and the line below
- `y :up_arrow:`: Copy the text on the current line and the line above
- `y$`: Copy text from cursor to end of line
- `y^`: Copy text from before cursor to beginning of line
- `yy, Y`: Copy the current line of text
- `yaw`: Copy a word (includes whitespace before word if cursor isn't on the word)
- `y{motion}`: Substitute your own motion in here if you don't think any of the previous motions fit your case!

`d` is our delete/cut key and works in a similar fashion to yank
deleting in Vim is more like cutting in Vim since it places your deletion in the buffer you paste from
- `d :right_arrow:`: Cut the char under the cursor
- `d :left_arrow:`: Cut the char before the cursor
- `d :down_arrow:`: Cut the text on the current line and the line below
- `d :up_arrow:`: Cut the text on the current line and the line above
- `d$, D`: Cut text from cursor to end of line
- `d^`: Cut text from before cursor to beginning of line
- `dd`: Cut the current line of text
- `^D`: Cut the current line without removing the newline (This is actually two separate commands rather than an operator and a motion. It is move to beginning of line delete to end of line)
- `daw`: Cut a word (includes whitespace before word if cursor isn't on the word)
- `d{motion}`: Substitute your own motion in here if you don't think any of the previous motions fit your case!

`c` works just like d but is an interesting one since it puts us in Insert mode after using it.

`p` is how we actually paste what is in the buffer<br>
- cutting or copying one or more lines will be pasted on the next line.<br>
- cutting or copying a word will be pasted before the cursor

All of these are quite useful but where they become truly powerful is when we combine them with Visual mode which I will come back to [later](#visual-mode).

## Insert Mode

> Insert mode is how you insert text and can be entered in a number of ways
- `i`: Switch to Insert mode
- `I`: Enter Insert mode at the beginning of the line
- `a`: Move cursor one space forward and enter Insert mode
- `A`: Move cursor to end of line and enter Insert mode
- `o`: Insert new line below current line and enter Insert mode
- `O`: Insert new line above current line and enter Insert mode
- `c{motion}`: cut selected text and enter Insert mode

## Visual Mode

> Visual mode is how you highlight text but is a little different than most people are used to. There are three versions of Visual mode, character-wise, line-wise, and block-wise and they are all entered from `Normal mode` and `Visual mode`. All of these can be combined with motions.
- `v`: Enter character-wise visual mode which is the most granular form of Visual mode
  - Character-wise visual mode I usually use with selecting a part of a line to either copy or delete it.<br>
- `V`: Enter line-wise visual mode which selects entire lines
  - I tend to use line-wise visual mode the most for selecting large sections of text to either copy or delete it.<br>
- `<C-v>`: Enter block-wise visual mode which selects a square of text
  - Block-wise visual mode seems to be the most convenient yet under utilized visual mode in my opinion. It's great to comment out blocks of code in Python or add the same characters to the same spot on multiple lines. in fact, I used it in this README to add the asteriks before all of the commands to make them bold

   In order to comment out a block of code with block-wise visual mode you need to do

   | commands | text |
   | --- | --- |
   | `<C-v>`  | line 1<br> line 2   |
   | `jj`     | `l`ine 1<br> `l`ine 2   |
   | `I`      | `l`ine 1<br> `l`ine 2   |
   | `#<esc>` | `#`line 1<br> `#`line 2 |
- `gv`: reselect last visual selection
- `o`: toggle the free end of selection


## Command-line mode

> Command-line mode is incredibly powerful and diverse. In one command you can edit an entire document, perform simple arithmetic, or change the look of your editor. There are a lot of things you can do with the command line but I am only going to describe the commands I use the most.

Command-line mode can be accessed while in `Normal mode` or `Visual mode`. It can be entered using either `:` or `/`

The two I use the most are
- `:{number}`: Move cursor to beginning of specified line number
- `/{search term}`: search the file for all occurences of search term
  - You can move to the next occurence with `n` or move backwards with `N`
  - You can highlight the matching occurences with `:hlsearch`. Add `set hlsearch` to your vimrc if you want it always on
- `:%s/{pattern}/{replacement}/g`: replace all occurences of `pattern` with `replacement`
  - `%` makes it a global search and replace. Removing `%` will only search and replace on the current line
  - You can also add a range `1,5 s/...` to search and replace on lines 1 through 5
  - Adding `i` to the end will make it case insensitive
  - Adding `c` to the end will ask for confirmation of each replacement
  - Since the search function finds all occurences, including substrings of words, this can cause unintended results
  - If you only want to replace whole words then use `:%s/\<{pattern}\>/{replacement}/g`
- `:{range} {command}`: Ranges are very helpful for when you only want to execute a command on a subset of lines
  - Ex: `:1,3 join` will join lines 2 and 3 to the end of line 1

These are the commands I use the most but there are plenty more such as delete, yank, put, copy, move, join, normal, and executing commmands on all lines that match a pattern. I haven't found a way to use these in an effective way to speed up my workflow but I recommend checking them out to see if they help you.

## The Dot Command

> This can be a huge time saver but it takes some time to get used to. The dot `.` command repeats the last changes you made.

This is easier to understand when you understand what a change is. It could be anything from a tab, deletion, an appended character, or writing an entire function. Some examples could be appending `;` to the end of a line or indenting json. In order to truly utilize this command you need to edit in a way that is repeatable.

Let's say you have a line that calls the function `foo()` four times but instead of typing it out four times you wrote it once and copied it three more times with a typo. One way to fix it is to go to each spot and fix it, do a search and replace, or the dot command since it's a small problem

`bar = soo(x) + soo(y) + soo(z) + soo(w)`

In order to do this with the dot command you could do `fsrf` followed by `;.`. This will find the first `s` and replace `r` it with `f`  which can be followed by repeating `;` the last find and then repeating `.` the change

All together this looks like `fsrf;.;.;.`. This is a rather simple problem to fix but one at time but imagine instead of the single typo you needed to change the entire function name to something more lengthy. In order to change the entire function the only part of those commands you would need to change is the `rf` part. Granted, if you had to make this change 20 times it would be faster and easier to use a search and replace.





### Things to do:
- [ ] add table of contents<br>
- [ ] add links to sections where I say to reference later<br>
- [ ] add gifs<br>
