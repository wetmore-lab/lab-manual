
Section X: Additional VI Commands

10.1: Cutting and Pasting/Deleting Text

" Specify a buffer to be used any of the commands using buffers. Follow the " with a letter or a number, which corresponds to a buffer.

D Delete to the end of the line from the current cursor position.

P Paste the specified buffer before the current cursor position or line. If no buffer is specified (with the " command.) then 'P' uses the general buffer.

X Delete the character before the cursor.

Y Yank the current line into the specified buffer. If no buffer is specified, then the general buffer is used.

d Delete until _where_. "dd" deletes the current line. A count deletes that many lines. Whatever is deleted is placed into the buffer specified with the " command. If no buffer is specified, then the general buffer is used.

p Paste the specified buffer after the current cursor position or line. If no buffer is specified (with the " command.) then 'p' uses the general buffer.

x Delete character under the cursor. A count tells how many characters to delete. The characters will be deleted after the cursor.

y Yank until putting the result into a buffer. "yy" yanks the current line a count yanks that many lines. The buffer can be specified with the " command. If no buffer is specified, then the general buffer is used.

10.2: Inserting New Text

A Append at the end of the current line.

I Insert from the beginning of a line.

O (letter oh) Enter _insert_ mode in a new line above the current cursor position.

a Enter _insert_ mode, the characters typed in will be inserted after the current cursor position. A count inserts all the text that had been inserted that many times.

i Enter _insert_ mode, the characters typed in will be inserted before the current cursor position. A count inserts all the text that had been inserted that many times.

o Enter _insert_ mode in a new line below the current cursor position.

10.3: Moving the Cursor Within the File

^B Scroll backwards one page. A count scrolls that many pages.

^D Scroll forwards half a window. A count scrolls that many lines.

^F Scroll forwards one page. A count scrolls that many pages.

^H Move the cursor one space to the left. A count moves that many spaces.

^J Move the cursor down one line in the same column. A count moves that many lines down.

^M Move to the first character on the next line.

^N Move the cursor down one line in the same column. A count moves that many lines down.

^P Move the cursor up one line in the same column. A count moves that many lines up.

^U Scroll backwards half a window. A count scrolls that many lines.

\$ Move the cursor to the end of the current line. A count moves to the end of the following lines.

% Move the cursor to the matching parenthesis or brace.

^ Move the cursor to the first non-whitespace character.

( Move the cursor to the beginning of a sentence.

) Move the cursor to the beginning of the next sentence.

{ Move the cursor to the preceding paragraph.

} Move the cursor to the next paragraph.

| Move the cursor to the column specified by the count.

\+ Move the cursor to the first non-whitespace character in the next line.

\- Move the cursor to the first non-whitespace character in the previous line.

_ Move the cursor to the first non-whitespace character in the current line.

0 (Zero) Move the cursor to the first column of the current line.

B Move the cursor back one word, skipping over punctuation.

E Move forward to the end of a word, skipping over punctuation.

G Go to the line number specified as the count. If no count is given, then go to the end of the file.

H Move the cursor to the first non-whitespace character on the top of the screen.

L Move the cursor to the first non-whitespace character on the bottom of the screen.

M Move the cursor to the first non-whitespace character on the middle of the screen.

W Move forward to the beginning of a word, skipping over punctuation.

b Move the cursor back one word. If the cursor is in the middle of a word, move the cursor to the first character of that word.

e Move the cursor forward one word. If the cursor is in the middle of a word, move the cursor to the last character of that word.

h Move the cursor to the left one character position.

j Move the cursor down one line.

k Move the cursor up one line.

l Move the cursor to the right one character position.

w Move the cursor forward one word. If the cursor is in the middle of a word, move the cursor to the first character of the next word.

10.4: Moving the Cursor Around the Screen

^E Scroll forwards one line. A count scrolls that many lines.

^Y Scroll backwards one line. A count scrolls that many lines.

z Redraw the screen with the following options. "z&lt;return&gt;" puts the current line on the top of the screen; "z." puts the current line on the center of the screen; and "z-" puts the current line on the bottom of the screen. If you specify a count before the 'z' command, it changes the current line to the line specified. For example, "16z." puts line 16 on the center of the screen.

10.5: Replacing Text

C Change to the end of the line from the current cursor position.

R Replace characters on the screen with a set of characters entered, ending with the Escape key.

S Change an entire line.

c Change until . "cc" changes the current line. A count changes that many lines.

r Replace one character under the cursor. Specify a count to replace a number of characters.

s Substitute one character under the cursor, and go into insert mode. Specify a count to substitute a number of characters. A dollar sign (\$) will be put at the last character to be substituted.

10.6: Searching for Text or Characters

, Repeat the last f, F, t or T command in the reverse direction.

/ Search the file downwards for the string specified after the /.

; Repeat the last f, F, t or T command.

? Search the file upwards for the string specified after the ?.

F Search the current line backwards for the character specified after the 'F' command. If found, move the cursor to the position.

N Repeat the last search given by '/' or '?', except in the reverse direction.

T Search the current line backwards for the character specified after the 'T' command, and move to the column after it is found.

f Search the current line for the character specified after the 'f' command. If found, move the cursor to the position.

n Repeat last search given by '/' or '?'.

t Search the current line for the character specified after the 't' command, and move to the column before the character if it's found.

10.7: Manipulating Character/Line Formatting

~ Switch the case of the character under the cursor.

< Shift the lines up to _where_ to the left by one shiftwidth. "<<" shifts the current line to the left, and can be specified with a count.

\> Shift the lines up to _where_ to the right by one shiftwidth. ">>" shifts the current line to the right, and can be specified with a count.

J Join the current line with the next one. A count joins that many lines.

10.8: Saving and Quitting

^\\ Quit out of "VI" mode and go into "EX" mode. The EX editor is the line editor VI is build upon. The EX command to get back into VI is ":vi".

Q Quit out of "VI" mode and go into "EX" mode. The ex editor is a line-by-line editor. The EX command to get back into VI is ":vi".

ZZ Exit the editor, saving if any changes were made.

10.9: Miscellany

^G Show the current filename and the status.

^L Clear and redraw the screen.

^R Redraw the screen removing false lines.

^\[ Escape key. Cancels partially formed command.

^^ Go back to the last file edited.

! Execute a shell. If a is specified, the program which is executed using ! uses the specified line(s) as standard input, and will replace those lines with the standard output of the program executed. "!!" executes a program using the current line as input. For example, "!4jsort" will take five lines from the current cursor position and execute sort. After typing the command, there will be a single exclamation point where you can type the command in.

& Repeat the previous ":s" command.

. Repeat the last command that modified the file.

: Begin typing an EX editor command. The command is executed once the user types return. (See section below.)

@ Type the command stored in the specified buffer.

U Restore the current line to the state it was in before the cursor entered the line.

m Mark the current position with the character specified after the 'm' command.

u Undo the last change to the file. Typing 'u' again will re-do the change.

:q Quit VI. If there have been changes made, the editor will issue a warning message.

:q! Quit VI without saving changes.

:s/_pattern_/_to_pattern_/_options_

Substitute. This substitutes the specified pattern with the string in the to_pattern. Without options, it only substitutes the first occurrence of the pattern. If a 'g' is specified, then all occurrences are substituted. For example, the command ":1,\$s/Reggie/Wayne/g" substitutes all occurrences of "Reggie" to "Wayne".

:set \[all\]

Sets some customizing options to VI and EX. The ":set all" command gives all the possible options. (See the section on customizing VI for some options.)

:vi filename

Starts editing a new file. If changes have not been saved, the editor will give you a warning.

:w Write out the current file.

:w _filename_

Write the buffer to the filename specified.

:w >> _filename_

Append the contents of the buffer to the filename.

:wq Write the buffer and quit.