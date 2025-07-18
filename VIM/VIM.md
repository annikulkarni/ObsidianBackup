h - move left
j - move down 
k - move up

Press 'i' to enter Insert Mode
Press Esc to enter command Mode

:q - quit (will ask do you want to save changes if you have made any changes, generally exits if                  you don't have any change)
:q! - quit without saving

:w - save the current changes

:wq - save and exit

While in command mode

Pressing
w - cursor points to the start of the next word
e - points to the end of the current word

dw - will delete the current word from the point where your cursor is currently pointing to and               points to the start of the next word
de - will delete the current word from the point where your cursor is currently pointing to and              points after the end of the word

dd - will delete the current line

u - will undo the changes
Ctrl+r - will redo the changes

d[number]w/e - will perform the action the times you enter the number

<mark class="hltr-boom-bam">operator [number] motion </mark>

ex: 2dd will delete two lines

:d$ - To delete from the cursor to the end of a line type:

ce - delete the words and places you in insert mode
cw - delete the word. Remember e/w

# Lesson 3 SUMMARY

 1. To put back text that has just been deleted, type [p](p). This puts the
    deleted text AFTER the cursor (if a line was deleted it will go on the
    line below the cursor).

 2. To replace the character under the cursor, type [r](r) and then the
    character you want to have there.

 3. The [change operator](c) allows you to change from the cursor to where
    the motion takes you. Type `ce`{normal} to change from the cursor to the
    end of the word, `c$`{normal} to change to the end of a line, etc.

 4. The format for change is:

        c   [number]   motion

# Lesson 4 SUMMARY

 1. `<C-g>`{normal}     displays your location and the file status.
    `G`{normal}         moves to the end of the file.
    number `G`{normal}  moves to that line number.
    `gg`{normal}        moves to the first line.

 2. Typing `/`{normal} followed by a phrase searches FORWARD for the phrase.
    Typing `?`{normal} followed by a phrase searches BACKWARD for the phrase.
    After a search type `n`{normal} to find the next occurrence in the same
    direction or `N`{normal} to search in the opposite direction.
    `<C-o>`{normal} takes you back to older positions, `<C-i>`{normal} to
    newer positions.

 3. Typing `%`{normal} while the cursor is on a (, ), [, ], {, or } goes to its
    match.

 5. To substitute new for the first old in a line type
~~~ cmd
        :s/old/new
~~~
    To substitute new for all olds on a line type
~~~ cmd
        :s/old/new/g
~~~
    To substitute phrases between two line #'s type
~~~ cmd
        :#,#s/old/new/g
~~~
    To substitute all occurrences in the file type
~~~ cmd
        :%s/old/new/g
~~~
    To ask for confirmation each time add 'c'
~~~ cmd
        :%s/old/new/gc



#Lesson 5 SUMMARY

 1. [:!command](:!cmd) executes an external command.

     Some useful examples are:
     `:!dir`{vim}                   - shows a directory listing
     `:!del FILENAME`{vim}          - removes file FILENAME

 2. [:w](:w) FILENAME              writes the current Neovim file to disk with
                             name FILENAME.

 3. [v](v)  motion  :w FILENAME   saves the Visually selected lines in file
                             FILENAME.

 4. [:r](:r) FILENAME              retrieves disk file FILENAME and puts it
                             below the cursor position.

 5. [:r !dir](:r!)                  reads the output of the dir command and
                             puts it below the cursor position.


# Lesson 6 SUMMARY

 1. Type `o`{normal} to open a line BELOW the cursor and start Insert mode.
    Type `O`{normal} to open a line ABOVE the cursor.

 2. Type `a`{normal} to insert text AFTER the cursor.
    Type `A`{normal} to insert text after the end of the line.

 3. The `e`{normal} command moves to the end of a word.

 4. The `y`{normal} operator copies text, `p`{normal} pastes it.

 5. Typing a capital `R`{normal} enters Replace mode until `<Esc>`{normal} is
    pressed.

 6. Typing "[:set](:set) xxx" sets the option "xxx". Some options are:

        'ic' 'ignorecase'   ignore upper/lower case when searching
        'is' 'incsearch'    show partial matches for a search phrase
        'hls' 'hlsearch'    highlight all matching phrases

    You can either use the long or the short option name.

 7. Prepend "no" to switch an option off:
~~~ cmd
        :set noic
~~




