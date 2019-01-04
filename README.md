# Vim-Cheatsheet

---

This is a compilation of the most useful tips and tricks for vim that I use on a daily basis and a few that aren't as useful but still come in  handy. This is designed to help you speed up your workflow but it's up to you to learn when to best apply these tricks. This is not meant to be a full comprehensive guide on how to use Vim and if you want to dive deeper into Vim then I highly recommend "Practical Vim" by Drew Neil.

# Modes

---

## Normal Mode

> Normal mode is the default mode in vim and the one that you will spend the majority of your time in. This is the mode that you will be navigating your documents with and the better you get at this mode the faster you will move, guaranteed.

### Motions

The basic motions in Vim are
h,j,k,l which are left, down, up, and right, respectively.
If you just really hate using those then you can also use the arrow keys

beyond the basic motions there are all sorts of ways to move around your document at blistering speed
- b, B: move to the beginning of the previous word
- w, W: move to the beginning of the next word
- e, E: move to the end of the next/current word
- gg: move to the top of the file
- G: move to the bottom of the file
- f{char}: move to the first occurrence of {char} (Brackets are not necessary)

### Deletions/Operators

on top of moving around the document you can also do some limited editing, such as copy, cut/delete, and paste
c, d, and y are called operators and are combined with a motion.
y is our yank (copy) operator.
- y&rarr;: Copy the char under the cursor
- y&larr;: Copy the char before the cursor
- y&darr;: Copy the text on the current line and the line below
- y&uarr;: Copy the text on the current line and the line above
- yy: Copy the current line of text
- yaw: Copy a word (includes whitespace before word if cursor isn't on the word)
- y{motion}: Substitute your own motion in here if you don't think any of the previous motions fit your case!

d is our delete/cut key and works in a similar fashion to yank
deleting in Vim is more like cutting in Vim since it places your deletion in the buffer you paste from
- d&rarr;: Cut the char under the cursor
- d&larr;: Cut the char before the cursor
- d&darr;: Cut the text on the current line and the line below
- d&uarr;: Cut the text on the current line and the line above
- dd: Cut the current line of text
- daw: Cut a word (includes whitespace before word if cursor isn't on the word)
- d{motion}: Substitute your own motion in here if you don't think any of the previous motions fit your case!

c works just like d but is an interesting one since it puts us in Insert mode after using it.

All of these are quite useful but where they become truly powerful is when we combine them with Visual mode which is a little farther down. I will come back to these there.

## Visual Mode

## Insert Mode

## Replace Mode


