- The BASH or Bourne Again Shell is a sh-compatible shell that stores command history in a file called bash history. You can view the saved command history using the more ~/.bash_history command. This feature of BASH is a problem for hackers, as investigators could use the bash_history file to track the origin of an attack and learn the exact commands used by the intruder to compromise the system.
- Open Terminal
	> export HISTSIZE=0 (to disable the BASH Shell from saving the history)
		- **HISTSIZE**: determines the number of commands to be saved, which will be set to 0.
	> history -c (to clear the stored history)
		- This command is an effective alternative to the disabling history command; with **history -c**, you have the convenience of rewriting or reviewing the earlier used commands.
		- Similarly, you can also use the **history -w** command to delete the history of the current shell, leaving the command history of other shells unaffected.
    > shred ~/.bash_history (to shred the history file, making its content unreadable)
		- This command is useful in cases where an investigator locates the file; because of this command, they would be unable to read any content in the history file.
		> more ~/.bash_history (to view the shredded history content)
		
- We can use all above mentioned commands in a single command
	> shred ~/.bash_history && cat /dev/null > .bash_history && history -c && exit
	
	- **This command first shreds the history file, then deletes it, and finally clears the evidence of using this command. After this command, you will exit from the terminal window.**
	