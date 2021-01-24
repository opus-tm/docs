## Version Control: Structure
Main branch will be named “master”, and will contain the code that Heroku uses for deployment
We’ll have one branch off of that called “dev”
This will be merged back into master only when we’re certain that it’s fully functional and doesn’t introduce any bugs that we aren’t ok with being in production
From “dev”, we’ll create our own separate branches for various work that we’re doing.
For example, if Josh is adding some functionality to the backend while Swopnil is doing something on the backend, they’ll both be on separate branches off of “dev” -- Josh’s might be called “Add_Event_Table” while Swopnil’s is “Add_Dark_Mode”
Names aren’t super important, but they should probably be descriptive of what the branch should do

## Version Control: Merging
Once someone has completed their work on their individual branch, they’ll need to merge it back into “dev”
Steps:
* Stage your changed files (git add . or click “Commit” on SourceTree and stage all)
* Commit and add a message (git commit -m “{Insightful_Message}” or enter the message on SourceTree on the bottom and click commit)
* Push changes to remote (git push --set-upstream origin {branch_name} or click push on SourceTree)
* Next, create a merge request on GitHub
* Choose the source repository/branch and destination repository/branch
* Destination branch should always be “dev” for merging an individual branch
* Add a title and a brief description to indicate what reviewers should be looking for in your changes
* Assign the pull request to one or two other people
* It would be nice to have at least one other person look through your code before you complete the merge request -- you can assign it as an issue to someone for them to look over

When we merge “dev” into “master”, it’ll introduce some major changes, so we’ll need to double check and probably have everyone look over code that they’re unfamiliar with and make sure we don’t blow the whole thing to pieces. 
If you get issues with conflicts, merge the “dev” branch into your own feature branch first (“back-merging”) and resolve the conflicts there using VSCode. Once you’ve done that, commit and create a pull request


## Pulling Code
If you’re having trouble with imports, it’s probably a good idea to double check the Pipfile.lock and make sure you have all the necessary packages installed and up-to-date (It’s likely that we’ll each be adding in new libraries and dependencies throughout). I believe that running “python manage.py migrate” should install anything you’re missing
