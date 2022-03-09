## GIT Cheatsheet

### Commands related to a remote repository:
- `git clone git@github.com:USER-NAME/REPOSITORY-NAME.git`
- `git push or git push origin main (both accomplish the same goal in this context)`
### Commands related to the workflow:
- `git add .`
- `git commit -m "A message describing what you have done to make this snapshot different"`
### Commands related to checking status or log history:
- `git status`
- `git log`
### Best practices
- Atomic commits.  A commit that includes changes related to only one feature or task of your program
- Leveraging those atomic commits to make your commit messages more useful to other collaborators
-- If your change causes some problems, it is easy to revert the specific change without losing other changes
-- It enables you to write better commit messages
