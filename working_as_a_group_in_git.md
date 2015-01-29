# Working Together in a Single Git Repo

You are all working together from a single Git Repository. One person manages. I've separated the instructions into commiter, and manager sections.

## Steps for Committing Changes

### 1. Pull Down Latest Changes to Your Working Branch
```bash
$ git checkout working
$ git pull
```

At this point git will try to "fast-forward" your working branch so it matches the remote copy of working. This will work unless multiple people have been working on the same file(s). 

If git cannot fast forward, it will try to merge recursively. To do this, it will bring up a commit window in Vim asking you to approve the merge. All you have to do is type ':wq' (without the quotes) and hit enter to save the preset merge message and exit vim.

Unless git cannot automatically merge, you're all set. If Git says there's a merge conflict, see "Fixing Merge Conflicts" below before continuing.

### 2. Create a New Branch to Work In

You want to create a new "feature branch" to work in. Make sure you've checkout out the "working" branch (per the instructions above), and then do:

```bash
$ git checkout -b <feature_branch_name>
```

### 3. Do Your Work

Now just work as you normally would. When you're ready, commit your changes with:

```bash
$ git add . -A
$ git commit -m "Commit message"
```

### 4. Push Your Changes to Remote

Now push your completed feature branch to the remote repository.

```bash
$ git push origin <feature_branch_name>
```

Next, go to Github.com and make a pull request. The "Base" Branch should be "working" and the compare branch should be your new feature branch.

### Done

That's it. Notify admin that a pull request has been made. Once your changes have been merged, start again at step 1.


## Steps for Repository Admin

When a new pull request comes in, you can try to use the Github interface to merge the changes. Make sure that the pull request specifies "working" as the target of the merge. 

If you can merge on GitHub.com, great! You're done and you can notify your team members (and yourself) its time for them to start again at "Step 1" of committing changes.

If GitHub.com tells you that it cannot do the merge for you, it will provide command line instructions. Most likely, the merge cannot be done automatically because two people modified the same locations in the same file. You'll have to resolve these changes yourself.

```bash
$ git fetch <feature_branch_to_be_merged>
$ git branch <feature_branch_to_be_merged> origin/<feature_branch_to_be_merged>
$ git checkout working
$ git merge <feature_branch_to_be_merged>
```

Now Git will try to perform the merge recursively. If it fails, you'll have to follow the steps below to manually resolve the conflict. Otherwise, you're almost done —— all that's left is to push the changes to working.

```bash
$ git push origin working
```

Done!


### Additional Info: Manually Fixing Merge Conflicts
If it needs you to fix the merge, it will tell you, and will also tell you which files you need to look at. Find the merge brackets, they look like this: 

```
<<<<<HEAD
Something here
"=====
Different version here
">>>>>> 129109591901515
```

Compare what is above and below the === signs and pick one version or the other to keep. Once you have resolved all the conflicts, save the file.

Now use `git add <filename>` to add the files where you resolved the merge conflicts. Then type `git commit` to finish the merge.

Once you have finished this, you'll be able to continue.