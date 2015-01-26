#Git workflow for project

##Part 1: Create a git oranization
Go to github and create a new organization

##Part 2: Add team members

##Part 3: Create a new repository for that organization

###Initialize with readme

##Part 4: Have all members clone the repository

```bash
git clone THE_NAME_OF_THE_REPOSITORY_GOES_HERE
```

##Part 5: Create a `dev` or `working` branch

```bash
git branch dev
```

```bash
git push -u origin dev
```

##Part 6: Pick a branch to work on

```bash
git branch NAME_OF_BRANCH_YOURE_WORKING_ON
```

```bash
git checkout NAME_OF_BRANCH_YOURE_WORKING_ON
```

##Part 7: Make a pull request to dev or working

```bash
git push -u origin NAME_OF_BRANCH_YOURE_WORKING_ON
```

Then go to github and click on the button that asks if you'd like to make a pull request

Assign the pull request to one of your team mates

##Part 8: after you've made a significant number of changes and everything is working make a pull request from dev or working into master
