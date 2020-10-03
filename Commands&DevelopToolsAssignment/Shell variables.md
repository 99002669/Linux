Practice7: shell variables

1. Use echo to display Hello followed by your username. (use a bash variable!)
	echo Hello $USER


2. Create a variable answer with a value of 42.
	answer=42


3. Copy the value of $LANG to $MyLANG.
	MyLANG=$LANG


4. List all current shell variables.
	printenv


5. List all exported shell variables.
	env 


6. Do the env and set commands display your variable ?
	No the command doesnt diplay my variable


6. Destroy your answer variable.
	unset answer


7. Create two variables, and export one of them.
	variable1=1; export variable2=2


8. Display the exported variable in an interactive child shell.
	bash
	echo $variable2


9. Create a variable, give it the value 'Dumb', create another variable with value 'do'. Use echo and the two variables to echo Dumbledore.
	v1=Dumb, v2=do
	echo ${v1}le${v2}re
	
		
10. Find the list of backslash escaped characters in the manual of bash. Add the time to your PS1 prompt.
	PS1='\t \u@\h \W$ 
