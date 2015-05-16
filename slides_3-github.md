<!-- Notes on setup

The 'cheffian' user (pburkholder+cheffian@gmail.com) in ~~~GH is akin to an organization,
and no commits should be made by that user~~~ No, we'll expedite and skip PRs
give the time constraints.

The 'pburkholder' user has commit bits to the 'cheffian'
repos, so I can make PRs as myself. (But mostly I'll use the
cheffian_github key. Per https://gist.github.com/jexchan/2351996)

The 'intro2devops' user (pburkholder+intro2devops) also has
write bits, and can make PRs and accept them. The user is the lab
test user for the exercises.

I'll need to make heavy use of tags with 'git reset --hard TAG' and 'git push -f'
to reset the repositories to their pre-lab state.

UPDATE: It's hard to keep remote forks up to date, since there's no GitHup UI shortcut for that, https://help.github.com/articles/syncing-a-fork/.

So we'll use local forks instead....

?? Prevent accidental merges to master?
http://dev.ghost.org/prevent-master-push/

Requires adding a .gitconfig file and .git_templates/hooks/precommit to each user.

I can't imagine running a Chef workshop without having Chef to run the workshop.

-->
