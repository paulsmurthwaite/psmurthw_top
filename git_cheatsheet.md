### Commands related to a remote repository:
- <PRE>git clone git@github.com:USER-NAME/REPOSITORY-NAME.git
- <PRE>git push or git push origin main (both accomplish the same goal in this context)
### Commands related to the workflow:
- <PRE>git add .
- <PRE>git commit -m "A message describing what you have done to make this snapshot difference"
### Commands related to checking status or log history
- <PRE>git status
- <PRE>git log
### Best practices
- atomic commits.  A commit that includes changes related to only one feature or task of your program
- leveraging those atomic commits to make your commit messages more useful to other collaborators
-- if your change causes some problems, it is easy to revert the specific change without losing other changes
-- it enables you to write better commit messages