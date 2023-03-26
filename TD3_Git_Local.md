# TD6/9: Git Filesystem & Commits

# Exercise 1: Configure Git

## 1. Check that Git is installed on your environment.
git --version Output : git version 2.39.0.windows.2

## 2. Configure your name and e-mail globally.
git config --global user.name "YounessGrini" git config --global user.mail "younessgrini@hotmail.fr"

## 3. Check that Git has correctly recorded these two pieces of information.
git config --list

# Exercise 2: Basic workflow with a single file

## 1. Create a git repository
mkdir repository1 cd repository1 git init

## 2. Check that git has correctly initiliazed a repository by displaying the files wihtin your current folder
ls -A

## 3. Check the current git status
git status

## 4. Create a text file named “readme.md” whose content is “# Test repository”
echo "# Test repository" > readme.md cat readme.md

## 5. Check the current git status
git status

## 6. Stage the file
git add readme.md

## 7. Check the current git status
git status

## 8. Commit the file
git commmit -m "Add readme file

## 9. Check the current git status
git status

## 10. Check the git logs
git log --oneline

## 11. Which informations are displayed ?
Commited files and their dates

# Exercise 3: Basic workflow with multiple files treated separately

## 1. Create two empty python files named “main.py” and “functions.py”
main.py function.py

## 2. Check the current git status
git status

## 3. Stage only the file “main.py”
git add main.py

## 4. Check the current git status
git status

## 5. Commit the file with an appropriate message
git commit -m "Add main file"

## 6. Check the current git status
git status

## 7. Now stage and commit the file “functions.py”
git commit -m "Add file"

## 8. Check the current git status
git status

## 9. Check the git logs
git log --oneline

# Exercise 4: Basic workflow with multiple files treated all at once

## 1. Create three empty files named “requirements.txt”, “.gitignore” and “.private”
touch requirements.txt   
touch .gitignore   
touch .private

## 2. Check the current git status
git status

## 3. Stage all the files at once
git add .

## 4. Check the current git status
git status

## 5. Commit the current staged files
git commit -m "Add staged files"

## 6. Check the current git status
git status

## 7. Check the git logs where each log is displayed on a single line
git log --oneline

# Exercise 5: Private files

## 1. Emulate a temporary empty file by creating a file named “temp.ipynb”
touch temp.ipynb

## 2. Check the current git status
git status

## 3. Add an instruction to .gitignore to prevent git from tracking this temp file
echo "temp.ipynb" >> .gitignore

## 4. Check the current git status
git status

## 5. Create other temporary files named “temp.aux” and “temp.log”
temp.aux temp.log

## 6. Check the current git status
git status

## 7. Change your instruction in .gitignore to prevent git from tracking any file which name starts with “temp”
vim .gitignore insert : temp*

## 8. Check the current git status
git status

## 9. Now let’s consider your personal notes will be added to the “.private” folder. Use the “exclude” git file to ## prevent git from tracking this “.private” folder
echo ".private*" >> exclude cat exclude git status

# Exercise 6: Difference between versions

## 1. Add a online description of your repository in the “readme.md” file
vim readme.md

## 2. Stage your “readme.md” file
git add readme.md

## 3. Display the changes in your root directory since the last commit (not just the current status)
git diff --staged

## 4. Commit your change
git commit -m "Add change"

## 5. Display the changes since the last commit
git diff

## 6. Display again the changes in your root directory since the last commit
cd git diff

## 7. Change some words in the description of the “readme.md”
vim readme.md 

## 8. Display the changes since the last commit
git diff

# Exercise 7: Undo

## 1. Suppress all your files.
rm *

## 2. Use Git to restore your files.
git restore

## 3. Backup your Git repository elsewhere (pretending a copy exists on another colleague’s computer or on a remote server).
mkdir backup cp -r .git backup

## 4. Suppress your root directory, create a new empty one and use your backup to restore everything.
rm -rf repository1

## 5. Unstage your first file


## 6. Commit your two file changes directly, without staging them.

## 7. Check your commit log history. Do you see your new commit ?
git log --oneline

## 8. Without affecting your Git repository, set your root directory state as of the snapshot of your first commit.


## 9. Check your commit log history. You do not see all commits, do you ? How can you see all of them ?
git log --oneline

## 10. Return to the snapshot of your your last commit.

## 11. Undo your second commit by adding a new commit that reverts it.

## 12. Check the content of your root directory. Have your previous changes disappeard ?
cd 
ls -A

## 13. Check your commit log history. Do you see your revert commit ?
git log --oneline

## 14. Remove the last 2 commits from the history.
git checkout HEAD~2


# Exercise 8: Aliases

## 1. Create a “s” alias for the git status command.
git config --global alias.s status

## 2. Create a “co” alias for the git checkout command.
git config --global alias.co checkout

## 3. Create a “b” alias for the git branch command.
git config --global alias.b branch

## 4. Create a “ci” alias for the git commit command.
git config --global alias.ci commit

## 5. Create a “dog” alias for the git log –all –decorate –oneline –graph command.
git config --global alias.dog "log --all --decorate --oneline --graph"

## 6. Create a “dag” alias for the git log –all –decorate –graph command.
git config --global alias.dag "log --all --decorate --graph"

## 7. Create a “list” alias for the git diff-tree –no-commit-id –name-only -r command.
git config --global alias.list "diff-tree --no-commit-id --name-only -r"

## 8. Create a “unstage” alias for the git reset HEAD – command.
git config --global alias.unstage "reset HEAD --"

## 9. Create a “last” alias for the git log -1 HEAD command.
git config --global alias.last "log -1 HEAD"

# Exercise 9: Hashing

## 1. Create a root directory.
sudo mkdir /root_directory

## 2. Create a text file inside whose content is “Hello World”.
echo "Hello World" > helloworld.txt

## 3. What is the size of the file ?
ls -l helloworld.txt

## 4. Display the file content on the screen.
cat helloworld.txt

## 5. Compute the SHA-1 hash of the file content. hint : You can use the GNU core utilities sha1sum command.
sha1sum helloworld.txt



