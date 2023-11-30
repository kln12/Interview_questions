
**1.write a program even or prime.   
Answer**:def is_even(number):
    if number % 2 == 0:
        return True
    else:
        return False

 Example usage:
num = int(input("Enter a number: "))
if is_even(num):
    print(f"{num} is even.")
else:
    print(f"{num} is not even.")

**2.How to take a backup of a file, write a script?  
Answer**:import shutil
from datetime import datetime

def backup_file(file_path):
    try:
         Get the current date and time
        timestamp = datetime.now().strftime("%Y%m%d%H%M%S")

         Split the file path into directory and filename
        directory, filename = shutil.os.path.split(file_path)

         Create a backup filename by appending the timestamp
        backup_filename = f"{filename}_{timestamp}"

         Construct the full path for the backup file
        backup_path = shutil.os.path.join(directory, backup_filename)

         Copy the original file to the backup file
        shutil.copy2(file_path, backup_path)

        print(f"Backup created successfully: {backup_path}")

    except Exception as e:
        print(f"Error creating backup: {e}")

**Example usage:** 
     file_to_backup = input("Enter the path of the file to backup: ")
backup_file(file_to_backup)


**3.select the user from a group?
Answer**:import random

def select_user(group):
    if not group:
        print("The group is empty.")
        return None

    selected_user = random.choice(group)
    return selected_user

 Example usage:
group_of_users = ["User1", "User2", "User3", "User4", "User5"]

selected_user = select_user(group_of_users)

if selected_user is not None:
    print(f"The selected user is: {selected_user}")

4.write a automation file?
5.
