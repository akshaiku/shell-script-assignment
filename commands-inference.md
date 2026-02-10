
# Linux Basic Commands – Inference

## 1. Setup and Directory Creation
mkdir ev4 : Created a new directory named ‘ev4’.  
cd ev4 : Changed current directory to ‘ev4’.  
**Resultant Path:** /home/akshai/ev4  

mkdir 6 : Created a directory named '6' (roll number).  
**Resultant Path:** /home/akshai/ev4  

cd 6 : Entered the directory '6'.  
**Resultant Path:** /home/akshai/ev4/6 

---

## 2. Navigation Commands
cd - : Switched back to the previous directory (ev4).  
**Resultant Path:** /home/akshai/ev4  

cd - : Toggled back to the directory I was just in (6).  
**Resultant Path:** /home/akshai/ev4/6 

cd . : No change occurred (represents current directory).  
**Resultant Path:** /home/akshai/ev4/6

cd .. : Moved up one level to the parent directory (ev4).  
**Resultant Path:** /home/akshaiev4  

cd ~ : Moved immediately to my Home directory.  
**Resultant Path:** /home/akshai

cd / : Moved to the Root directory.  
**Resultant Path:** /  

ls -l : Listed files in Root.  
**Resultant Path:** /  

cd media : Entered the 'media' directory inside Root.  
**Resultant Path:** /media  

cd : Returned to my Home directory.  
**Resultant Path:** /home/akshai  

pwd : Printed the absolute path of the current directory.  
**Output:** /home/akshai  

cd media : Error ("No such file"). Stayed in the current directory.  
**Resultant Path:** /home/akshai  

cd /media : Successfully entered media using absolute path.  
**Resultant Path:** /media  

ls -l : Listed contents of media.  
**Resultant Path:** /media  

cd ~/ev4/6 : Navigated directly back to my work folder.  
**Resultant Path:** /home/akshai/ev4/6 

---

## 3. File and Directory Management
(Current Path: /home/akshai/ev4/6)  

mkdir emptydummy : Created folder 'emptydummy'.  
mkdir dummy : Created folder 'dummy'.  

cd dummy : Entered the dummy folder.  
**Resultant Path:** /home/akshai/ev4/6/dummy  

touch file1 : Created empty file 'file1'.  
touch file2 : Created empty file 'file2'.  

ls -l : Checked that files exist.  

rm -i file2 : Deleted 'file2' after confirmation.  

cd .. : Moved back to parent directory (6).  
**Resultant Path:** /home/akshai/ev4/6  

rm emptydummy : Failed (Error: Is a directory).  
rmdir emptydummy : Successfully removed the directory because it was empty.  
rmdir dummy : Failed (Error: Directory not empty).  
rm -r dummy : Recursively removed the 'dummy' directory and the files inside it.  

---

## 4. File Content and Redirection (I/O)
(Current Path: /home/akshai/ev4/6)  

cat > file1.txt : Created file with text 'My first line'. Press CTRL+D to save.  
cat > file2.txt : Created file with text 'Hello Second line'. Press CTRL+D to save.  
cat > file3.txt : Created file with text 'Hello line'. Press CTRL+D to save.  

cat file1.txt file2.txt > file_combined.txt : Combined file1 and file2 into a new file (overwrite).  
cat file_combined.txt : Displayed combined content.  
cat file3.txt >> file_combined.txt : Appended file3 to the combined file.  
cat file_combined.txt : Displayed total content (File1 + File2 + File3).  

grep -i hello file* : Listed lines containing "hello" from all files.  

cp file1.txt ~/ev4 : Copied file to parent folder (/home/akshai/ev4).  
mv file_combined.txt combined : Renamed file to 'combined'.  

---

## 5. Permissions (chmod)

### Method A: Symbolic Mode
chmod u+x file.sh : Added execute permission for the owner.  
chmod g-w file.txt : Removed write permission for the group.  
chmod a+r file.txt : Added read permission for everyone.  
chmod u=rwx,g=rx,o=r myfile : Set exact permissions (Owner=rwx, Group=rx, Others=r).  

### Method B: Numeric (Octal) Mode
chmod 754 file.txt : Owner=7=rwx, Group=5=r-x, Others=4=r--.  
chmod 600 file.txt : Read/write for Owner only.  

chmod u+x combined : Added execute permission for the owner to 'combined'.  
Observation: Checked with ls -l, owner permissions include 'x'.  

chmod g-r combined : Removed read permission for the group.  
Observation: The 'r' was removed from group in ls -l.  

chmod 777 combined : Full read/write/execute for User, Group, Others.  
Observation: ls -l confirms full permissions.  

**File/Directory Permission Reference:**  

| Permission | File                   | Directory             |
|------------|-----------------------|----------------------|
| r          | Read file             | List files (ls)      |
| w          | Modify file           | Create/Delete files  |
| x          | Run file              | Enter directory (cd) |

---

## 6. User Management (sudo)
sudo useradd alice : Created new user 'alice' (requires admin password).  
sudo passwd alice : Set login password for 'alice'.  
sudo userdel alice : Deleted user 'alice'.  

---

## 7. Communication
write alice : Initiated a real-time message to 'alice'.  
Observation: If 'alice' is logged in, message appears on their terminal.  

mesg y / mesg n : Enabled/disabled ability to receive messages from other users.  

**Note:** Optional `tty` argument specifies terminal session if multiple sessions exist.


