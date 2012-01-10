!SLIDE

# Using and Abusing Git hooks

Joseph Hsu, developer at Academic Software Plus

@jhsu

github.com/jhsu

!SLIDE

# What are git hooks

!SLIDE

# Scripts that are called at different steps when working with git.

!SLIDE

# Created on `git init`

## copied from /usr/share/git-core/templates/hooks/ to .git/hooks/

!SLIDE

# Setting up git hooks

* remove ".sample" suffix from hook inside .git/hooks/
* create a new script, `chmod +x` it

!SLIDE

# Hooks exist on your local checkout of the repository

!SLIDE

# Don't Forget:

`chmod +x .git/hooks/pre-commit`

!SLIDE

# When the hook is called, exit with non-zero to abort

`exit 1`


!SLIDE

# `git commit` => pre-commit

* `git diff --staged --name-only` to find what files are about to be commited
* check for `console.log(...)`


!SLIDE

# `git commit` => post-commit

After the entire commit process is completed.

* get list of open issues
* automatically push if on master

!SLIDE

# [or...](http://collectiveidea.com/assets/4c58e4c1dabe9d50eb000087/happykids.wav)

`afplay ~/.git/happykids.wav > /dev/null 2>&1 &`

!SLIDE

# `git commit` => commit-msg

* gets passed the path to the proposed commit message 

!SLIDE

# `git merge` => {pre,post}-merge

* run migrations if any changes to db/migrations (check using `git diff HEAD^`)

!SLIDE

# post-receive

* useful for shared repos
* use for notifications (ie, irc, email, ci server, etc.)

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
    git log --format='%aN' | sort -u | while read x; do echo \
    "`expr $RANDOM % 1000`:$x"; done | sort -n| sed 's/[0-9]*://' | head -n 1
@@@

!SLIDE

# Githooks

[https://github.com/jhsu/githooks](https://github.com/jhsu/githooks)
