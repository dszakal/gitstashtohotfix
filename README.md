# Gitflowsync

Installation:

1. Install gitflowsync from dszakal's github account
2. Go to the folder in your terminal where you checked out the repo, there type


    sudo cp gitstashtohotfix /usr/bin/gitstashtohotfix
    
    sudo chmod o+x /usr/bin/gitstashtohotfix

Updating to latest version:

Are you up to date?

    diff ./gitstashtohotfix /usr/bin/gitstashtohotfix && echo 'up to date' || echo 'not up to date'

If not, repeat the steps stated in installation. You need to do it manually after "git pull".

Usage:

You need to be on master branch, and you should not have any untracked files for safety reasons. 
Whatever the stash contains will become part of a new hotfix branch

    $ gitstashtohotfix hotfix_tagname 'my commit message'
    
For example if the previous version was 3.1.214 and your next release is a small bugfix release, you want to create a hotfix branch of 3.1.215    
    
    $ gitstashtohotfix 3.1.215 'template grey line in div fixed'

This automatically starts a hotfix, commits the stashed changes and finishes the hotfix, clears the stash, pushes the merged develop and master branches and tags.

The script will stop with exit code 1, whereever any git, git-flow or any other command fails, and will tell you which step failed and which steps did not run, you may want to intervent manually in these cases with extra care.

