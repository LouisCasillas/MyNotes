# Vim Notes

## Learning resources I've used:
	- videos
		- Doing some real-world work in VIM! - https://www.youtube.com/watch?v=mH1GGI2Jpbs.mp4
		- Start Turning vim into a _comfy_ IDE! - https://www.youtube.com/watch?v=Q4I_Ft-VLAg.mp4
		- Improving Vim Speed - https://www.youtube.com/watch?v=OnUiHLYZgaA.mp4
		- Vim Navigation Commands - https://www.youtube.com/watch?v=Qem8cpbJeYc.mp4
		- Mastering the Vim Language - https://www.youtube.com/watch?v=wlR5gYd6um0.mp4
		- Talk on going mouseless with Vim, Tmux, and Hotkeys - https://www.youtube.com/watch?v=E-ZbrtoSuzw.mp4
		- How to Do 90% of What Plugins Do (With Just Vim) - https://www.youtube.com/watch?v=XA2WjJbmmoM.mp4
		- vim + tmux - OMG!Code - https://www.youtube.com/watch?v=5r6yzFEXajQ.mp4
	- courses
		- Vim for Advanced Users
	- articles
		- https://www.drbunsen.org/writing-in-vim/
		- https://hashrocket.com/blog/posts/8-great-vim-mappings
		- https://bennetthardwick.com/beginner-advanced-vim-tips/

## Notes
### spell checking
	- :set spell
		- turn on the feature
	- ]s
		- move to next miss-spelled word
	- [s
		- search for miss-spelled words backwards
	- z=
		- show possible corrections
	- zg
		- the word the cursor is on is added to the list of acceptable spellings
		- zug - undo add
	- zw
		- the word the cursor is on is removed from the list of acceptable spellings
		- zuw - undo remove

### code completion
	- :set omnifunc=?
		- turn on the feature using completion for ? code
	- [insert mode] {ctrl+x} {ctrl+o}

### tab usage
	- :tab new
		- open new buffer in a new tab
	- :tab close
		- close the current tab
	- :tabe <file>
		- open file in new tab
	- :tab split
	- {ctrl+w} T
		- open current buffer in new tab
	- :tab[n/p/f]
		- go to the [n]ext tab, [p]revious tab, [f]irst tab
	- :tabs
		- list all tabs currently open, current tab is shown by '>'
	- :tabdo {command}
		- execute a command in the current buffer of each tab
		- :tabdo norm ZZ
			- close, and potentially write, the current buffer in each tab
	- window usage
	- :windo {command}
		- execute a command in each window
		- :windo difft
			- create diff output for each open window
	- {ctrl+w} s
	- :sp[lit]
		- open the current window in a horizontal split
	- {ctrl+w} v
	- :vsp[lit]
		- open the current window in a vertical split
	- new
		- open a new window in a horizontal split
	- vnew
		- open a new window in a vertical split
	- {ctrl+w} r
		- rotate all windows down/right by one position
	- {ctrl+w} x
		- exchange current window with the next one
	- {ctrl+w} [K J H L]
		- move the current window in the direction given
	- {ctrl+w} <number> [- +]
		- decrease or increase the current window height by <number> or by 1 if no number is given
	- {ctrl+w} <number> [< >]
		- decrease or increase the current window width by <number> or by 1 if no number is given
	- {ctrl+w} =
		- make all windows equal size
	- {ctrl+w} {ctrl+f}
		- if the cursor is on a filename open that file in a split window, works with either an absolute or relative path as well as a single filename in the current path
	- :set scollbind
		- bind this window to other windows you have set scrollbind on so that when scrolling in one window the other windows scroll at the same time

### undo
	- :undolist
		- show list of current changes to the buffer
	- :earlier/later [5m/5]
		- move back/forward to changes made [5m]inutes ago/forward or [5] changes ago/forward
	- :undo <number>
		- return the buffer to an exact undo number position

### bracket jumping
	- %
		- while the cursor is over a bracket press % to jump to the matching closing bracket

### deletion commands
	- Note: these commands can be performed with other actions such as y for yank or v for visual select, just replace d with y or v or some other action letter
	- daw
		- delete the whole word, which is delimited by alphanums and underscore, up to the next word including any spaces
	- daW
		- delete the whole word, which is only delimited by spaces, up to the next word including any spaces
	- das
		- delete the whole sentence the cursor is on up to the next sentence including any spaces
	- dit
		- delete everything between an HTML tag
	- dat
		- delete an HTML tag
	- df<character>
		- delete from the cursor to the next found character, including the character itself
	- dt<character>
		- delete from the cursor to the next found character, not including the character itself
	- d/<string>
		- delete from the cursor to the next found string, not including the string itself
	- da<beginning or ending enclosing characters>
		- delete all text inside the enclosing characters including the enclosing characters themselves
		- for example: {} [] () " ' <> p(for paragraph) s(for sentence)
		- da< or da> or da{ or da} so on
	- di<beginning or ending enclosing characters>
		- delete all text inside the enclosing characters not including the enclosing characters themselves
		- for example: {} [] () " ' <> p(for paragraph)
		- di< or di> or di{ or di} so on
	- d0
		- delete from the cursor to the first character
	- d$
		- delete from the cursor to the last character
	- d^
		- delete from the cursor to the first non-blank character
	- dg_
		- delete from the cursor to the last non-blank character
	- dd
		- delete the line and put it into the copy register
	- "_dd
		- delete the line but do not put it into the copy register, goes into the black hole register similar idea to /dev/null
	- d'<character> or d`<character>
		- delete from the current line to the set mark line
	- ct<character>
		- delete all characters from the cursor to the <character> not
			 including <character>, and start insert mode

### abbreviations
	- :ab <abbreviated text> <long text>
		- example: :ab #h /* Header Text */
		- Note: to be able to type out the abbreviated text type the text and hit CTRL-v before hitting space or exiting insert mode
	- :redir @<register letter>|silent verbose ab|redir END
	- :put <same register letter>
		- print all abbreviations to the current file

### repeating insert edits
	- after you make some edit to the document and exit insert mode you can repeat the edit by hitting the period '.' key
		- Example use case: interactive search and replace - search for a word, without changing position, change the word, hit n to go to the next result, either hit period '.' to make the same change or hit 'n' to go to the next result
			- this could also be done with the command :%s/oldword/newword/gc

### show all white space characters
	- turn on
		- :set list
	- turn off
		- :set nolist

### remove DOS line endings
	- :%s/{ctrl+v}{ctrl+m}//

### repeat executable commands
	- :!ls
		- repeat with @:

### see possible command/file completion choices
	- :r {ctrl+d}
	- :edi {ctrl+d}

### search for a character in the current line
	- f<character>
		- search forward to each character
	- t<character>
		- search forward to the character before the character
	- ;
		- go to the next character
	- ,
		- go to the previous character

### search for a word in the document
	- /<text to find>
	- *
		- will make the closest forward word the search term and move forwards through the results
	- #
		- will make the closest forward word the search term and move backwards through the results
	- n
		- move forward to the next search result
	- N
		- move backward to the next search result

### macros
	- q{macro character}
		- start macro
	- q
		- end macro
	- <number of times>@{macro character}
		- execute the macro saved in {macro character} x <number of times>
	- @@
		- repeat the last macro
	- :exe "normal <macro actions>"
		- easy way to test a macro before setting it in the macro register
	- :let @q="<macro actions>"
		- set the text into the macro register
	- "{macro character}p
		- paste the macro text so you can edit the macro directly
		- once the macro is edited select the macro and yank it into the "{macro character} register
		- move first then execute commands, if you execute commands first and it fails the move input will be lost on the error message and the macro will be stuck on the same line
			- example:
				- :s/ /_/g^Mjj
					- fails if the line does not contain any spaces and the macro will get stuck
				- jj:s/ /_/g^M
					- moves to the next line even if the line does not contain any spaces, allowing the macro to continue as expected

### global commands
	- search and delete matching lines
		- :g/wordtomatch/d
	- search and delete non-matching lines
		- :g!/wordtomatch/d
	- search and run normal mode edits on matching lines, as you would type them
		- :g/wordtomatch/norm >>
			- add a level of indentation to all matching lines
		- :g/wordtomatch/norm YGP
			- copy each matching line and paste it at the end of the file
	- search and execute normal commands, this allows you to represent special characters
		- :g/wordtomatch/exe "norm \<s-y>\<s-g>\<s-p>"
			- copy each matching line and paste it at the end of the file
		- :g/wordtomatch/normal ddggP
			- delete the line and paste it at the top of the file

### line navigation commands
	- <number>H
		- go to the <number> line from the top of the window
	- M
		- go to the middle of the window
	- <number>L
		- go to the <number> line from the bottom of the window
	- zz
		- center current line in the window, keeping the cursor in the same column
	- zt
		- make the current line at the top of the window
	- zb
		- make the current line at the bottom of the window
	- {ctrl+e}
		- move the screen down one line without changing the cursor position, unless you scroll past the current line
	- {ctrl+y}
		- move the screen up one line without changing the cursor position, unless you scroll past the current line
	- {ctrl+d}
		- move the cursor down half a screen
	- {ctrl+u}
		- move the cursor up half a screen
	- <number>%
		- go to the <number> percentage of the file

### marks
	- m<character>
		- set a mark on the current line
	- '<character> or `<character>
		- return to the line previously marked
	- ''
		- move back and forth from the current position and the last jump position
	-
		- return to the line and column where the last change was made
	- `.
	- '.
		- return to the beginning of the line where the last change was made

### character navigation commands
	- 0
		- go to the first character
	- $
		- go to the last character
	- ^
		- go to the first non-blank character
	- g_
		- go to the last non-blank character
	- <number>|
		- go to the <number> column on the line
	- gj,gk,g$,g0
		- perform the movement per visual line rather than the absolute line, helpful with wrapped lines

### character editing commands
	- gU<object/motion>
		- make letters uppercase
	- gu<object/motion>
		- make letters lowercase
	- ~
		- switch letter case

### line editing commands
		- J
		- join the current line with the next line, add a space between them
	- gJ
		- join the current line with the next line, do not add a space between them

### object editing commands
	- [d y ?]aw
		- perform an action to the word the cursor is on including the whitespace at the end of the word
	- [d y ?]iw
		- perform an action to the word the cursor is on not including the whitespace at the end of the word
	- [d y ?]w[' { } < > [ ] ?]
		- perform an action on whatever the specified object encloses including the specified object
	- [d y ?]i[' { } < > [ ] ?]
		- perform an action on whatever the specified object encloses not including the specified object

### open files
	- find <filename>
		- either directly or through fuzzy search open a file
	- sfind <filename>
		- either directly or through fuzzy search open a file and split it vertically
	- {ctrl+w} {ctrl+f}
		- in a new window open the filename that the cursor is currently on

### tag navigation commands
	- {ctrl+]}
		- jump to the definition of the keyword under the cursor
	- :stj
		- create a split window with the definition of the keyword under the cursor
	- {ctrl+t}
		- jump to the previous tag
	- :tags
		- list the tag stack

### auto-completion
	- <while in insert mode> {ctrl+n}
		- autocomplete the current word or show a list of possible matches, looks at the current file and tag files
	- <while in insert mode> {ctrl+x} {ctrl+n}
		- autocomplete the current word or show a list of possible matches, only looks at the current file
	- <while in insert mode> {ctrl+x} {ctrl+f}
		- autocomplate file names

### help
	- :help <query>
		- search for your query in the vim help manual and display the first result, will generally show normal moode command help
	- :helpgrep <query>
		- run a grep search throughout the entire vim help manual
		- :cn
			- go to the next found result
		- :cp
			- go to the previous found result
		- :cl
			- list every found result
		- :cc <number>
			- go to the <number> result
	- :help i_<query>
		- search for a query relating to insert mode
	- :help v_<query>
		- search for a query relating to visual mode
	- :help c_<query>
		- search for a query relating to command-line mode, editing
	- :help :_<query>
		- search for a query relating to command-line mode, command
	- :help pattern.txt
		- everything there is to know about search strings and vim regex
	- :help pattern-multi-items
		- info on special matching operators
	- :help perl-patterns
		- compare differences between perl  and vim regex
	- :help magic
		- review vims flavor of regex and what various characters mean

### ex mode
	- :vi
		- exit ex mode

### file types
	- :set ft
		- show what type of file vim thinks we are in

### indentation
	- gg=G
		- vim will go through the file and try to put each line at the proper indentation level

### options
	- :set
		- print all set options
	- :redir @<register letter>|silent verbose set|redir END
	- :put <same register letter>
		- print all options to the current file
	- :set <option name>?
		- query the current state or value of the option
	- :set <option name>=<value>
		- set the option to a value, the value might be a number or a string, if the value is a string you can set the string to empty with <option name>=
		- if using a backspace before the space
	- :set <option name>
		- turn on the boolean option
	- :set no<option name>
		- generally to turn off a boolean option you type no + option name
	- :set <option name>!
		- toggle the boolean option

### Leader key
	- <Leader>
		- this key can be used to start the control sequence of your own commands which you would define in your ~/.vimrc

### search and replace
	- :s/regex
		- on the current line, delete the text matched by the given regex
	- :s/regex/replacement text/
		- on the current line, make a search and replace for only the first matching text found
	- :s//replacement text/
		- if no regex is given the last search will be used
	- :s+regex+replacement text+
		- a normal search and replace but doesn't delimit options with forward slash so you can easily use forward slashes in the regex and replacement text
	- :s/regex/replacement text/g
		- on the current line, make a search and replace for all matching text found
		- Note: if the option 'gdefault' is on then using [g] will stop the search and replace after the first match
	- :%s/regex/replacement text/g
		- in the whole file, make a search and replace for all matching text found
	- :%s/regex/replacement text/gc
		- in the whole file, go through each matching text and answer the prompt [y]es or [n]o for whether the current text instance should be replaced
	- :%s/regex/replacement text/gi
	- :%s/regex/replacement text/gI
		- normal search and replace but the search text is either case-insensitive [i] or case-sensitive [I]
	- :%s/regex//gn
		- search the whole file and report the number of matching strings found and on how many lines the strings were found
	- :%s/regex/"&"/
	- :%s/regex/"\0"/
		- the symbol '&' and escaped 0 '\0' in the replacement text section will reference the entire matched portion of the text, use \& if you want the literal '&' character
	- [action letter]gn
		- perform the action on the next found match of the previous search
	- g&
		- repeat the previous search and replace over the entire file

### using registers (clipboards)
	- :reg
		- show all the current registers
			- Note: yy or dd will by default copy the text into the "" register
			- Note: text you yank will also be copied into register "0
	- :redir @<register letter>|silent verbose reg|redir END
	- :put <same register letter>
		- print all registers to the current file
	- "<register letter or number>yy
	- "<register letter or number>dd
		- copy the text into the the specified register
	- "<register letter or number>p
	- :put <register letter or number>
		- paste the contents of the register into the file
	- :{ctrl+r}<register letter or number>
		- paste the contents of the register onto the command line

### visual selection
	- :'<,'>w ! <command><Enter>
		- send all the selected text to the given terminal command
	- <while in visual block mode> o
		- change the cursor position to the opposite corner

### escaping insert mode
	- Esc
	- {ctrl+[}

### insert mode
	- {ctrl+w}
		- backspace an entire word
	- {ctrl+u}
		- backspace to the beginning of the line
	- {ctrl+v}<character>
		- input the literal character
	- {ctrl+v}u<unicode character number>
		- input a unicode character
	- {ctrl+o}
		- go into normal mode for one command
	- {ctrl+r}<register letter or number}
		- paste the expected register into the next
	- {ctrl+r}=
		- allows you to write vimscript, execute it, and paste it into the file
	- {ctrl+t}
		- add indentation level to the current line 

### folds
	- zR
		- open all folds in the file
	- zM
		- close all folds in the file
	- zA
		- toggle folds the cursor is on, recursive

### message redirection
		- :help redir
		- :redir > <filename>
	- :redir =><variable>
		- :redir @<a-zA-Z>
		- redirect all messages to the given file, variable, or register
	- :redir END
		- stop all message redirection

### autocommands
	- :redir @<register letter>|silent verbose au|redir END
		 :put <same register letter>
		- print all autocommands to the current file
		- Note: must be two commands for some reason

### remapping
	- :redir @<register letter>|silent echo "nvo mappings:"|silent verbose map|silent echo "\nic mappings:"|silent verbose map!|silent echo "\nl mappings:"|silent verbose lmap|silent echo "\nt mappings:"|silent verbose tmap|redir END|silent put <same register letter>
		- print all mappings to the current file

### variables
	- :let <variable> = <value>
		- set a local variable
	- :let g:<variable> = <value>
		- set a global variable
	- :let
		- print all variables
	- :redir @<register letter>|silent verbose let|redir END
	- :put <same register letter>
		- print all variables to the current file

### functions
	- :redir @<register letter>|silent verbose function|redir END
	- :put <same register letter>
		- print all functionsto the current file

### commands  
	- :redir @<register letter>|silent verbose command|redir END
	- :put <same register letter>
		- print all commandsto the current file
		- Note: must be two commands for some reason
