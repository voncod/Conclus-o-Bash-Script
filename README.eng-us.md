# Bash-Script-Conclusion
This repository documents my Bash Script learnings during the Technical Fundamentals phase of the DevOps + Cloud (2025) curriculum.
The goal is to consolidate basic concepts, commands, and practical examples that will serve as a reference for future automation.

# Basic Script Structure
#!/bin/bash # Shebang: Indicates the interpreter
echo "Hello, world" # Example Output

#!/bin/bash → Required at the beginning of the file to indicate that it will be executed by Bash.

chmod +x script.sh → Makes the script executable.

./script.sh → Runs the script.

# Variables
nome="Luan"
echo "My name is $nome"

Created without a space around the =.

Accessed with $variable.

# Input and Output
read user
echo "Welcome, $user"

read → captures user input.

echo → prints to the screen.

# Conditions and Flow Control
if / else / elif
if [[ $age -ge 18 ]]; then
echo "Of legal age"
elif [[ $age -gt 12 ]]; then
echo "Teenager"
else
echo "Child"
fi

case
echo "Choose an option: (1/2)"
read option

case $option in
1) echo "You chose one";;
2) echo "You chose two";;
*) echo "Invalid option";;
esac

;; → ends each condition block.

*) → works like "else".

#Loops
for
for i in {1..5}; of 
echo "Number $i"
done

while
counter=1
while [[ $counter -le 3 ]]; do
echo "Counter $counter"
((counter++))
done

# Operators
Numeric Comparison

-eq → equal

-ne → not equal

-gt → greater than

-lt → less than

-ge → greater than or equal

-le → less than or equal

String Comparison

== → equal

!= → not equal

-z → empty string

-n → non-empty string

Files and Directories

-e → exists

-f → is a file

-d → is a directory

-r → has read permission

-w → has write permission

-x → is executable

Logical

&& → AND

|| → OR

# Positional arguments
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"

$0 → script name.

$1, $2 ... → arguments passed.

$@ → all arguments.

# Exit codes
ls /non-existent_folder
echo $? # Show the exit code

0 → success.

Different from 0 → error.

# Useful commands in scripts
tar – compression
tar -czvf backup.tar.gz *.txt

tar → archive command.

c → create.

z → compress (gzip).

v → verbose (show progress).

f → file (file name).

.gz → gzip compression format.

sed – replace text in files
sed 's/old/new/g' file.txt

s → replace.

g → global (all occurrences).

cron – scheduling tasks

Edit tasks:

crontab -e

Example: run a backup every day at 2:00 AM:

0 2 * * * /home/user/backup.sh

# Practical examples
Backing up .txt files
#!/bin/bash
date=$(date +%F)
tar -czvf backup_$data.tar.gz *.txt

Check if a command exists
if command -v git &> /dev/null; then
echo "Git is installed"
else
echo "Git not found"
fi
