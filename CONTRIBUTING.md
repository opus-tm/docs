## Version Control: Structure
Our main branch is named "main", and will contain the code that Heroku uses for deployment
We have one branch off of main named "staging"
To merge new code into main, ensure that the code is functional on the staging branch both by running it locally and by checking the staging deployment.
From staging, each developer may create branches for their assigned bugs, enhancements, and so on.
Branch names should be concise and indicate to others what the new code is meant to do.

## Version Control: Merging
Once a developer has finished working on their individual branch, they should merge that branch back into staging by following the steps below.
* Stage your changed files (git add . or click “Commit” on SourceTree and stage all)
* Commit and add a message (git commit -m “{Insightful_Message}” or enter the message on SourceTree on the bottom and click commit)
* Push changes to remote (git push --set-upstream origin {branch_name} or click push on SourceTree)
* Next, create a merge request on GitHub
* Choose the source repository/branch and destination repository/branch
* Destination branch should always be “staging” for merging an individual branch
* Add a title and a brief description to indicate what reviewers should be looking for in your changes
* Assign the pull request to one or two other people
* Reviewers should follow the code review guidelines and ensure that their review is complete before approving new changes.
* Once the original developer has receieved approval from their reviewers and resolved any comments, they may complete the merge into staging.

When merging staging into main, ensure that the staging branch is fully functional before doing so. Failure to do this could introduce breaking changes into the deployed version of the main branch.
Merge conflicts can typically be resolved by back-merging the target branch into your branch before merging your changes back in. Consult with other developers if your new code has contradictions with theirs.
