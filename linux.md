**2.what is Inode in linux   
Answer:**    an "inode," which stands for "index node," is a fundamental data structure that is used to store metadata about files and directories on a file system. Each file and directory on a Linux file system is associated with a unique inode that contains information about the file's attributes and data block pointers.  
**3.how to check the connections are going    
Answer:**    To check the network connections on your computer or a remote server, you can use various command-line tools depending on your operating system. Here are some common commands to check network connections:  
netstat -ano  
**4. what is the default permission of linux system    
Answer:**    
**5.how to knwo the ip address    
Answer:** Use the ifconfig or ip a command. Look for the "inet" or "inet addr" entry under the network adapter you are interested in "'ipconfig""
**6. write a script which accepts file or folder, if its folder delete it else print "this is a file"?   
Answer**You can write a simple shell script in Linux that accepts a file or folder path as an argument and then determines whether it's a file or a folder. If it's a folder, the script deletes it, and if it's a file, it prints "this is a file." Here's a sample script in bash:
#!/bin/bash

** Check if the script is given an argument** 
if [ $# -ne 1 ]; then
  echo "Usage: $0 <file_or_folder>"
  exit 1
fi

**Get the argument**  
path=$1  

**Check if the argument exists**
if [ ! -e "$path" ]; then
  echo "The file or folder does not exist."
  exit 1
fi

**Check if it's a file**
if [ -f "$path" ]; then
  echo "This is a file."
elif [ -d "$path" ]; then
**Check if it's a directory (folder)**
  echo "This is a directory."
**Delete the directory**  
  rm -r "$path"  
else  
  echo "This is neither a file nor a directory."
fi  
Save this script to a file (e.g., check_file_or_folder.sh), make it executable using chmod +x check_file_or_folder.sh, and then you can use it to check and handle files and folders as described. For example:  

./check_file_or_folder.sh /path/to/your/file_or_folder  
Replace /path/to/your/file_or_folder with the actual path you want to check and potentially delete. Please be cautious when using scripts that involve deleting files or folders, as data loss is irreversible.  

**7.Commands you will use it for configuring ssh connectivity between 2 machines and what files will be present in .ssh folder?   
Answer**SSH keys are used for authentication. If you haven't already generated SSH keys, you can do so using the ssh-keygen "ssh-keygen -t rsa" This will generate a pair of RSA keys and store them in the ~/.ssh directory.

**8.How to schedule a shell script in unix machines?   
Answer**To schedule the execution of a shell script on a Unix-based system, you can use the cron service. cron is a time-based job scheduler in Unix-like operating systems  
Open your crontab file for editing by running the following command:  
**crontab -e**  
This command will open your user's crontab file in a text editor.  

Add an entry to the crontab file specifying when and how often you want your script to run. The format of a cron job entry is as follows:  
* * * * * /path/to/your/script.sh
| | | | |
| | | | +----- Day of the week (0 - 6) (Sunday is 0)
| | | +------- Month (1 - 12)
| | +--------- Day of the month (1 - 31)
| +----------- Hour (0 - 23)
+------------- Minute (0 - 59)
You can use asterisks (*) to specify "every" for a particular time unit. For example, * * * * * means "every minute, every hour, every day, every month, every day of the week."  
Specify the path to your shell script (e.g., /path/to/your/script.sh) in the cron job entry.
Save and exit the text editor.  
The cron job is now scheduled, and it will run at the specified times or intervals. Make sure your shell script has the execute permission (you can use chmod +x script.sh to add it).  
Here are some common examples of cron job entries:  
To run a script every day at 2:30 PM:  
30 14 * * * /path/to/your/script.sh  
To run a script every Sunday at 3:00 AM:  
0 3 * * 0 /path/to/your/script.sh  
To run a script every hour:  
0 * * * * /path/to/your/script.sh  
To run a script every 15 minutes:    
*/15 * * * * /path/to/your/script.sh  
After saving your crontab file, the scheduled script will automatically run at the specified times or intervals.
Remember that the paths to your scripts and the exact timing will depend on your specific use case and requirements.    
**9.Need to identify ip addresses in log file and count of ip addresses in log file?   
Answer**grep -E -o "([0-9]{1,3}\.){3}[0-9]{1,3}" logfile.txt | sort | uniq -c  
-E enables extended regular expressions.  -o prints only the matched part of the line. 
sort sorts the IP addresses.  uniq -c counts the occurrences of each unique IP address.  
**10.what is command for checking the running process? how to get PID of process?   
Answer**If you want to get the PID of a specific process, you can use commands like pgrep.**pgrep process_name** 

**11.what is command for checking the running process? how to get PID of process?   
Answer**The ps command provides information about the current processes running on your system. **ps aux**
**12How to indentify the number of params that has been sent to shell script?   
Answer**In a shell script, you can identify the number of parameters (also known as arguments) that have been passed to the script or a function using the special variable $#. This variable stores the count of the positional parameters, which are the arguments supplied to the script or function when it is called.  
Here's how you can use $# to determine the number of parameters  
**#!/bin/bash

 Check the number of parameters
if [ $# -eq 0 ]; then
  echo "No parameters provided."
elif [ $# -eq 1 ]; then
  echo "One parameter provided."
else
  echo "Number of parameters provided: $#"
fi**    
In this example, we use an if-else statement to check the value of $#. If it's equal to 0, we display a message indicating that no parameters were provided. If it's equal to 1, we indicate that one parameter was provided. Otherwise, we print the actual count of parameters.  

You can run the script with different numbers of parameters to see how it responds:  
**$ ./script.sh         # No parameters provided.
$ ./script.sh param1  # One parameter provided.
$ ./script.sh p1 p2   # Number of parameters provided: 2**
You can access individual parameters within the script using $1, $2, and so on, where $1 refers to the first parameter, $2 to the second, and so forth.

**13.is it possible to store a commands output, either success or failure to the same file?   
Answer**Yes, it is possible to store both the success and failure outputs of a command in the same file in a shell script. You can achieve this by redirecting the standard output (stdout) and standard error (stderr) to the same file. In Unix-like operating systems, you can do this using the 2>&1 syntax. Here's an example:    
 Run a command and store both success and failure outputs in the same file  
**command_name > output.log 2>&1**   
In this example, command_name is the command you want to run, and output.log is the name of the file where you want to store the combined output. The > operator is used to redirect stdout to output.log, and 2>&1 is used to redirect stderr (file descriptor 2) to the same location as stdout (file descriptor 1), which effectively combines both streams into a single file.  
If you want to append the output to an existing file rather than overwriting it, you can use >> instead of >:
 Append both success and failure outputs to an existing file    
**command_name >> output.log 2>&1**  
This way, you can capture both success and error messages generated by the command in a single file, making it easier to review and analyze the command's output  .   
**14.In shell script can we supply parameters to functions?   
Answer**Yes, in a shell script, you can supply parameters (also known as arguments) to functions. Functions in shell scripts are defined with the function_name() { ... } syntax, and you can pass arguments to them just like you would with a regular command or script.   
#!/bin/bash   
 Define a function with parameters     
my_function() {   
  echo "Hello, $1 and $2!"
}

 Call the function with arguments  
my_function "Alice" "Bob"   
n this example, the my_function function takes two parameters, and when you call it with "Alice" and "Bob", it prints "Hello, Alice and Bob!" to the standard output. You can access these parameters within the function using $1, $2, and so on, to refer to the first, second, and subsequent arguments passed to the function.   
$ chmod +x myscript.sh   
$ ./myscript.sh


