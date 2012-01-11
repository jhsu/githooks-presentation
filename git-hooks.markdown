!SLIDE

# Using and Abusing Git hooks

## Joseph Hsu, developer at Academic Software Plus

@jhsu

github.com/jhsu

view slides at: [http://jhsu.github.com/githooks-presentation](http://jhsu.github.com/githooks-presentation)

!SLIDE

# What are git hooks

!SLIDE

# Scripts that are called at different steps when working with git.

!SLIDE

* applypatch-msg
* commit-msg
* post-commit
* post-receive
* post-update
* pre-applypatch
* pre-commit
* pre-rebase
* prepare-commit-msg
* update

!SLIDE

# Hooks exist on your local checkout of the repository

!SLIDE

# Created on `git init`

## copied from /usr/share/git-core/templates/hooks/ to .git/hooks/

!SLIDE

# Setting up git hooks

* remove ".sample" suffix from hook inside <repo_dir>/.git/hooks/

!SLIDE

# Don't Forget:

`chmod +x .git/hooks/pre-commit`

!SLIDE

# prepare-commit-msg

!SLIDE

# pre-commit

* `git diff --staged --name-only` to find what files are about to be commited
* check for `console.log(...)`

!SLIDE

# When the hook is called, exit with non-zero to abort

`exit 1`

!SLIDE

# post-commit

After the entire commit process is completed.

* get list of open issues
* fetch changes to see what others pushed
* automatically push if on master

!SLIDE

# [or...](http://collectiveidea.com/assets/4c58e4c1dabe9d50eb000087/happykids.wav)

`afplay ~/.git/happykids.wav > /dev/null 2>&1 &`

!SLIDE

# commit-msg

* gets passed the path to the proposed commit message 

!SLIDE

# {pre,post}-merge

* run migrations if any changes to db/migrations (check using `git diff HEAD^`)

!SLIDE

# {pre,post}-receive

* useful for shared repos
* use for notifications (ie, irc, email, ci server, etc.)
* authentication / ACL

!SLIDE

# [post-]update <branch> <orig_sha> <new_sha>

similar to pre-receive except run once for each branch that is updated

!SLIDE

!SLIDE

# Fun!

!SLIDE

# I respect you, bro.
![brodown](http://southparkstudios.mtvnimages.com/images/shows/southpark/vertical_video/season_15/south-park-1511-broadway-bro-down-clip11.jpg?width=200)

![Bro](http://dl.dropbox.com/u/114389/Screenshots/1v.png)

* allows you to append ", bro" to the end of the message


!SLIDE

# whatthecommit

@@@ bash
    #!/usr/bin/env bash
    curl -s http://whatthecommit.com/index.txt > $1
@@@

!SLIDE

> "i think i fixed a bug..."

!SLIDE

> "committing according to the Prophecy."

!SLIDE

> "tl;dr"

!SLIDE

# Random author

## pre-commit

@@@ bash
    #!/usr/bin/env bash
    username=`git log --format='%aN' | sort -u | while read x; do echo \
    "\`expr $RANDOM % 1000\`:$x"; done | sort -n| sed 's/[0-9]*://' | head -n
    1`
    git config --global user.name "$username"
@@@

!SLIDE

# Githooks

[https://github.com/jhsu/githooks](https://github.com/jhsu/githooks)
