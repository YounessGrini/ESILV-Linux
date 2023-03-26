# TD2/9: Fundamental Linux functionalities

# Exercise 1: Access general computer informations

## 1. Put system up to date
sudo apt-get update
sudo apt-get upgrade

## 2. Display
### Current processes, memory and network use
top
### More human readable
htop
### Number of processors
lscpu
### L1, L2 and L3 cache size
lscpu | grep cache
### Disk space
df -H /dev/root
lsblk -e 7,11
### Mounted devices
cat /proc/mounts
### Connected usb device
lsusb
### Hostname
hostname


# Exercise 2: Shell - Variables and scripts scope

## 1. Create a variable x and assign it the short text piri pimpin
x="piri pimpin"

## 2. Display the value of this variable
echo $x

## 3. Add to this value the following text piri pimpon
## It should contain the following : piri pimpim piri pimpon
x="$x piri pimpon"

## 4. Create a folder named my_programs, then enter into that folder
mkdir my_programs 
cd my_programs

## 5. Create a script named pilou that displays pilou pilou
vim pilou
echo "pilou pilou"

## 6. Run this script
source pilou

## 7. Make this script executable
chmod +x pilou

## 8. Run the script by writting its name only
./pilou

## 9. Programs called from the terminal are usually found thanks to a variable named PATH
## Display the content of the variable PATH
echo $PATH

## 10. Add the path of your current location to the global variable PATH
PATH="$PATH:$(pwd)"

## 11. When you are sure of the result, export it
export PATH

## 12. Go to your home directory
cd 

## 13. Run your script by writting its name only
pilou

## 14. Change the value of the PATH in the .profile file in order to make it
vim. profile
PATH="$PATH:$HOME/my_programs"

## 15. Create a new shell and run your script using its name only
pilou

# Exercise 3: Scheduling task - daemon

## 1. Create a script say_hello.sh
vim say_hello.sh 
  echo "$(date) - Hello" >> hello.txt

## 2. Make the script executable
chmod +x say_hello.sh 

## 3. Use crontab to schedule the running of the script every minute crontab -e
crontab -e

# Exercise 4: Hashing

## 1. Create a folder named hash_checksum. Go into this folder
mkdir hash_checksum 
cd hash_checksum

## 2. Inside this folder, create two files named .sensible_addresses and .sen sible_passwords
touch .sensible_addresses touch .sensible_passwords

## 3. Display the list of files of the folder
ls -a

## 4. Still inside the folder hash_checksum, create a script named gentle_script.sh.
## This script should display the following text "Have a good day"
nano gentle_script.sh echo "Have a good day

## 5. Run the script
source gentle_script.sh

## 6. Compute the sha256sum of gentle_script. Store it into a file named log_sha
sha256sum gentle_script.sh > log_sha

## 7. Now corrupt the file by adding a line of code that deletes any file starting with : ".sensible"
echo "rm -rf .sensible*" >> gentle_script.sh

## 8. Compute again the sha256sum of gentle_script. Store it into the log_sha file
sha256sum gentle_script.sh >> log_sha

## 9. Run the script
bash gentle_script.sh

## 10. Display again the list of files of the folder
ls -a

## 11. Display the log_sha content : are the hashes any different ?
cat log_sha

# Exercise 6: ACLs : Access Control Lists

## 1. Create users
## — Create a user named client_1 with password passwd-client_1
## — Create two other users named contributor_1 and contributor_2 with respective passwords passwd-contributor_1 and passwd-contributor_2
sudo useradd client_1  
sudo useradd contributor_1  
sudo useradd contributor_2  
sudo passwd client  
  passwd-client_1  
sudo passwd contributor_1  
  passwd-contributor_1  
sudo passwd contributor_2  
  passwd-contributor_2

## 2. Create groups
## — clients
## — contributors
sudo groupadd clients  
sudo groupadd contributors

## 3. Add users to their respective group
sudo adduser client_1 clients  
sudo adduser contributor_1 contributors  
sudo adduser contributor_2 contributors

## 4. Check the users and groups have been successfully created
cat /etc/passwd | awk -F: '{print $1}'  
cat /etc/group | awk -F: '{print $1}'

## 5. Create a folder lika_project and give it the following authorizations to groups
## — clients : read
## — contributors : read and write
sudo setfacl -m g:clients:r -R / lika_project/  
sudo setfacl -m g:contributors:rw -R / lika_project/

## 6. Also use the command ls -l and notice the change on lika_project folder
ls -l

## 7. Change user and become as a client, then try deleting the folder
su client_1  
passwd-client_1  
rmdir lika_project/  

## 8. Now change user and become as a contributor, then try deleting the folder
su contributor_1  
passwd-contributor_1  
rmdir lika_project/

## 9. Check who is the current user
whoami
