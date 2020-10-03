Practice8: shell history

1. Issue the command 
echo The answer to the meaning of life, the universe and everything is 42.
	o/p: The answer to the meaning of life, the universe and everything is 42.


2. Repeat the previous command using only two characters (there are two solutions!)
	!! or !e


3. Display the last 5 commands you typed.
	history 5


4. Issue the long echo from question 1 again, using the line numbers you received from the command in question 3.
	!<line_number>    (!1469)


5. How many commands can be kept in memory for your current shell session ?
	echo $HISTSIZE
	O/P: 1000


6. Is the current session history stored to ~/.bashrc_history?
	Yes,the session history os stored to ~/.bashrc_history


7. Where are these commands stored when exiting the shell ?
	echo $HISTFILE


8. How many commands can be written to the history file when exiting your current shell session ?
	echo $HISTFILESIZE


9. Make sure your current bash shell remembers the only 10 commands you type.
	HISTSIZE=1O


10. When is command history written to the history file ?
	The history command simply provides a list of previously used commands. That’s all that is saved in the history file. For bash users, this information all gets stuffed into the .bash_history file; for other shells, it might be just .history.
When you enter command "history" then that command got written into history file. 
