+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 3

## 0. Intro 

### 0.1 Icebreaker

I want today to be:
- faster: oooooo
- slower: ooooooooooooooooooooooooooooo
- same as yesterday: Oooooooooooooooooooooooooooo
- more exercises: ooooooo
- more type-along: oooooooooooooo
- more demos while just watching: oo
- same as yesterday but slight pauses during type-along: ooooooooooooo

If you could seamlessly share your work with others (your friends, or anyone in the world), what would you do?:
- Plankton meme: "I dont know, I never thought Id get this far"+3
- work with other researchers aruond the world that deal with similar geologic hazards based on our geology, latitude, weather, or other
- Connect with collaborators on similar topics that I might otherwise never meet.+2
- 1. Be afraid of sharing my code; 2. rejoice in sharing and the help of others; 3. One ring to bind them all.
- Use it to avoid "re-inventing the wheel".+1 Yes it is important to also know what didnt work in research
- Demolish the current society based on competition and build one based on collaboration! Let me dream... +1+1+1+1+1+1+1
- Get my work out and allow people to collaborate if they want to, preferably with a low entry level.
- I would share everything including the supporting materials etc.+1
- get more support to develope my code 
- ask for help on specific parts
- Put in small jokes in my code and see how long it takes for them to find them.


## Exercise repositories for live stream participants

If you would like to collaborate with other live stream participants and the instructors on the first exercise tomorrow (centralized collaborative workflow), can you please open an issue with the text "please add me as collaborator" in one of these two:
- https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues (this one will not be shown on stream and not recorded but changes will be public on GitHub until we remove this repository after the workshop)
- https://github.com/cr-workshop-exercises/centralized-workflow-exercise-recorded/issues (this one will be used on stream and recorded, only sign up if you are OK with us reviewing your pull request while teaching and streaming; we hope that some of you will so that we have something to review)

You can also choose not to join any of the two and either follow the lesson by watching us collaborate and comment and ask via HackMD. Alternatively you can also follow by creating your own exercise repository (we will describe how) and practice inside there, without other people.
If you open an issue in one of the two above, we will see your username and invite you as collaborator. You will then get an email from GitHub asking whether you accept the invitation. Please accept it. The rest of the exercise we will explain.

Livestream exercise repositories:

First exercise:
- https://github.com/cr-workshop-exercises/centralized-workflow-exercise (here nothing will be streamed or recorded)
- https://github.com/cr-workshop-exercises/centralized-workflow-exercise-recorded (this one we will show/use on stream and it will be recorded)

Second exercise:
- https://github.com/cr-workshop-exercises/forking-workflow-exercise (here nothing will be streamed or recorded)
- https://github.com/cr-workshop-exercises/forking-workflow-exercise-recorded (this one we will show/use on stream and it will be recorded)


## 1. git-collab - day 3
https://coderefinery.org/git-collaborative/

### Tip
Command to test that your SSH keys are being used correctly: `ssh -T git@github.com`


1. Is it normal that you have to enter your passphrase each and every time you push? (and authenticate for ssh)
    2. I did this: https://gist.github.com/nepsilon/45fae11f8d173e3370c3
    - If you added a passphrase when you created the key, you need to type it every time. You can create a key with an empty passphrase, but having a passphrase is naturally more secure.

2. Could we get a short overview of the exercises I need to prep as an exercise lead?
   - I'm not sure, but I think it is what is in the hackmd.  We can set it up during the course I think, that is part of it.
   - here's a list of the exercises: https://coderefinery.org/git-collaborative/exercises/

3. Should we have followed along for pull request? I got distracted by hackmd.
   - No, that was just a preview.  No one had to watch it, everything will be said again during the course.

---

## 1.1 Collaborative distributed version control
https://coderefinery.github.io/git-collaborative/

4. Regarding the conda installation: I managed to install the coderefinery packages natively on the M1 Macbook by removing the versions on the dependencies. Otherwise I got errors.
    - Good to know, thanks!  We will need to update our dependencies (we added them "just to be sure" but this shows why not!)
    - Thanks for this tip (from another M1 Mac user)

5. We cant connect zoom
    - What is the issue? Not everyone got the link due to a lack of exercise leads but we provide support in here as well for any questions, and zoom is mainly for exercises
        - Now it works... 


6. On the coderefinery.org workshop "documentation", how do I hide the left index bar?
    - Zoom in (or make it narrower) and it will go away.


7. I am still confused as to what origin means. Is that an alias for whatever server we use to host the repo remotely?
    - "origin" is just a name.  But in practice it means "the main remote repository you push/pull from"
    - When you have many remotes, the meaning gets more fuzzy

8. Possibly worth mentioning that there's nothing special about the name `origin`. It could be `elephant`, but some of these names/aliases are customary.
    - correct

9. Can we clone both origin repo and my forked repo to the same local repo? (e.g. origin/idea, user/idea)
    - you can add both as remotes to the single local repository.  You need to carefully manage the branches/pushing/pulling and all, but it works (and what we usually do).

10. Can you Fork from Gitlab to Github?
    - yes forking takes place in the online repository hosting platforms

11. So a fork is a concept from these git hosting services, and not a concept from git itself?
    - Good question!  Both:
    - "fork" is general term for making a copy in software
    - But also, on GitHub specifically, "fork" is a concept of personal repository built from another.  GitHub (and others) remembers this and provides extra features, like default pull request location, comparing them, etc.


12. But once we fork is it still linked to the parent reo? I mean the changes in forkedrepo reflects in the parent repo right?
    - yes it is linked as that it remembers where it is forked from and that the "original" repository has info of forks from it, but only if you use the "fork" on github, and not clone and push to a new repo on your github page. But when it comes to reflecting changes: No, your own fork does not automatically update when changes are made to the original repository. Only when you actively pull those commits from the original repository your own repo will be updated. (That's why, if you have a larger community project, you commonly have both "your" repo, where you make changes and the original repo in your local remotes, so that you can directly pull updates and it's easier to stay in sync.)

13. Dont we have to still clone the forked repo to edit it?
    - You *can* edit directly on GitHub.  Usually people clone locally.

14. Said another way, `git` repositories can exist (and do) completely without github. GitHub is just a handy place to share repos.
    - yes, Git is not github, github is the Storage provider, while git is the tool. (And admittedly github has made a bunch of additional features that make working with it easy/handy as you say)

15. What's the difference between distributed version control and centralized workflow?
    - In short: centralized, everyone has write permissions to the central repo.  With distributed, people need to fork
    - But really they work together, the only difference is who can push where.

16. Is a pull request a Github/(any other online git hosting service)'s feature? Is there a way to do pull requests without Github et al
    - A pull request commonly only makes sense between different forks, otherwise you could "simply" merge. But sometimes even within a project pull requests are created (e.g. between a development branch and a main branch). 
      In general a pull request can be made "without" a online service, but it doesn't make a lot of sense (imo). There is the `git request-pull` command, which can issue pull requests to a remote, but you would ned some kind of remote repository service for it to make sense (albeit that service could be minimal/command line)

17. I dont know who is in my team. 
    - If you aren't in Zoom, you don't have a team
    - If you are in our organized Zoom, team members are in the breakout room you have.
    - There are also xtra-rooms on Zoom that you may go to.

18. Even if you made it wider, we don't see the right side of your screen.
    - It's OK, that part isn't needed.


19. Please repeat where the link to the template is (for exercise leaders) or put it here, please.
    - https://github.com/coderefinery/template-centralized-workflow-exercise
        - thanks

20. I'm the only learner in my zoom team... can I join the livestream team instead?
    - which team? I can join in.
    - uib-bio
        - bio-uib correct? 

21. How the people will get the right to push to the repo? 
    - Teams: The team leader will give permission to them
    - Livestream: we will do that (open an issue on the repository)

23. Are exercise leaders supposed to set the repo on their accounts?
    - Yes

24. If I change my username at some point in GitHub, will I need to reset the SSH keys or make any other changes? Or is the link made only to the user email?
    - I think changing username should be OK (ssh keys linked to user)
    - Thanks :-).

25. I am confused on what the actual repo is, is it [this](https://github.com/cr-workshop-exercises/centralized-workflow-exercise) livestream
    - livestream or team?
    - I edited it, use that one (non recorded) 

25. Once the repository is set, what exerc lead should do?
    - hopefully the instructions provided so far are clear enough

26. it is a bit disturbing not to see all the screen... suggestion for next time: avoid it.
    - thanks

27. I do not see any settings on my git page. even  tho i accepted the invitation.
    - Only the leaders have settings

28. I am in zoom, but our exercise lead isn't there. Should we just follow along with the repo here?
    - Yes, sounds good.
    
29. I dont see "use this template" in centralized-workflow-exercise-recorded. I got the invitation in emaol before. Does that mean I do not need to do that step?
    - I had the same problem, one of the link point to the issues page somehow, so one does not see the "use template".
    - Yes, you may skip this step as the remote repo is already created.
 
30. Why are you streaming in portrait mode?
    - so that people can fit their own browsers and terminals next to the browser window showing the stream (see top of this hackMD to see a suggested setup: https://hackmd.io/12qv4mNTSSykfFaLqpmA2Q?both#tags-workshop)

31. Will it be clear as soon as the learners should do something? And the exercise leaders?
    - ELs: make repository from template, add learners to repo
    - Livestream learners: open issues here to request access https://github.com/cr-workshop-exercises/centralized-workflow-exercise

32. Protected branches are available to Pro, Team, and Enterprise users. Is it a paid option? 
    - Not on GitHub at least.
    - You need to have your repository visibility set to public in order to protect branches with a free account.

### Exercise: 
https://coderefinery.org/git-collaborative/centralized/#exercise-part-1-creating-a-pull-request

33. Where is the recorded version link again? I signed up last night, and accepted the invitation this morning.
    - https://github.com/cr-workshop-exercises/centralized-workflow-exercise-recorded

34. Exercise lead here: I cannot connect to Zoom at the moment...
    - Oh well.  Your team can use the livestream method.
    - if you share the room name i can send another exercise leader
      - "team-1"
      - Everything else is working fine, internet-wise. It is only Zoom I cannot connect to today.
    - I have managed to get in via web now :heavy_check_mark: 

35. Polite request. Please do not scroll up and down too much.
    - relayed

36. When you are explaining please also be inclusive of people doing this alone. To prevent confusion.
    - Thanks for the reminder


38. please explain what they need to do again pls
    - If working alone, you may start by create a remote repository non GitHub.
    - But you may also use: git@github.com:cr-workshop-exercises/centralized-workflow-exercise.git. Create an issue if you'd like to be added as collaborator:
        - https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues and click on "New issue", add "pls. add me as a collaborator" or something similar, and then "Submit new issue".

37. Is this currently for exercise leaders or all? 
    - Only the ELs should create a remote repository. The other team members will clone it in a moment.

38. Not a question, just thank you for being so patient. 
    - Thank you!

39. Are we typing along?
    - No, you should be writing your own recipe to push to the repo later.


### EXERCISE #1 until xx:25 (at xx:15 we will start going over it on-stream)
https://coderefinery.org/git-collaborative/centralized/#exercise-part-1-creating-a-pull-request
Do the exercise until **step 8** included.

If you have time, you can also try Centralized-3 exercise where you first create an issue and cross-reference
it in the commit message or the pull request title or form.

39. what should people without groups do. we have cloned the repo ?
    - in Zoom or live stream?
    - open an issue with the text "please add me as collaborator" in this repository: https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues
        - you will then be collaborating with other live-stream participants


40. we do not see the terminal on Twitch now (I don't know if we should?)
    - all good now

41. It is ok to have same repository name right? I named my local repository same as in the demo.
    - yes.

42. Demonstrate :yes

43. I see whole repository name before $. It makes my terminal work area small. How can i remove that repository name?
    - That is the directory name.  It can be removed, but maybe we should focus on this later.
    - But simple fix: `PS1='\$ '`

44. Personally, I would already like to do these steps in an exercise. Questions can always be asked to the exercise leader or on the hackmd. Is that possible, for some to already enter the zoom with their team (or by themselves) +1+1+1+1

45. It's confusing if we should type along or wait for the breakout session
    - We wil soon enter BO exercise time.

46. It is obvious that i do not have access.
    - Livestream: Open an issue in the repo and we will add access to you
    - Team: ask your leader to give you access.
    - See question #39 if working alone.

47. What is pull request? In the button in GitHub
    - Pull request means ask to merge branch onto the main one, but on GitHub.

48. Who requests what from who in a pull "request".
    - A contributer requests, that their changes are d into the repository. Most commonly that their branch is merged with the main (or development) branch of a repository. In bigger projects this avoids code coming in without being checked by others, and it is often (at least in large projects) considered bad style to directly push to common branches like dev or main. 

49. Feedback: don't do the entire exercise before we do.
    +1+1+1+1+1+1
    - I typed-along and finished the exercise. Will have longer break I guess. 
        - yes. :) nicely done!

50. I cannot add any file to the branch I made, i get an error:
    $ git add best-recipe.txt
    fatal: pathspec 'best-recipe.txt' did not match any files
    - Please make sure it's not a typo in the file name. Do `git status` and see if you can see there are modified changes for this file. Also, make sure you have initialized the local dir as a git repo. Done already if you `git clone...`

51. What is step 8? In the exercise it seems that the setps are A to E
    - https://coderefinery.org/git-collaborative/centralized/#exercise-part-1-creating-a-pull-request - sections numbered 1-8

52. In the website it says: 'The `-u` or `--set-upstream` will connect the local branch with the newly created upstream/remote branch and track it.' Can you explain what is meant by the "newly created upstream/remote branch"? Is upstream and remote the same word here 
    - Usage example: `git push -u origin branchname`. `-u` means "map the local branch `<branchname>` to the branch with the same name, but on the remote repository `origin`". This way, next time you do a `git push` of commits on the branch `branchname` it is enough if you specify `git push`.

53. Since the main stream will be doing the excercise in twitch all those who are in breakout rooms should mute twitch, I guess
    - we are discussing but yes.

54. I am getting this issue: fatal: 'main' does not appear to be a git repository
    fatal: Could not read from remote repository. And I am the excercise leader. 
    - Do you have any commits in the repository?
        - I have added some changes in the readme file and commited on the online interface.
    - What does `git remote -v` give? It could be the remote is not properly defined.
        - it executes properly and doesnt show any warning messages.
    - what about `git branch`?
        - empty no result
            - So the remote is defined but you have no local branches. I would `git pull origin`
            - This worked! I pulled the origin and now I see the master branch :).
              - Great! In the following you should create a new branch, checkout to it, create a commit, and push to the origin/ remote repo with `git push -u origin mybranch`, where `mybranch` is some branch name you wish to use. Then you got to GitHub(or your EL does) and do a pull request (step 8).
                    - Thanks!
55. GU-team: we have an issue with Mac, git saying `gpg failed to sign the data`
    - try `git commit --no-gpg-sign` to disable it.  Or `git push --no-signed`
    - I'm never seen this enabled by default, I wonder why it is on.

56. I just tried `git graph` and the Initial commit has 3 names, origin/master, origin/HEAD and master. Meanwhile the commit I made has the names HEAD, mybranchname, origin/mybranchname. Could you explain why there is 2 HEADs now? 
    - One is yours.  `origin/HEAD` means "this is what the remote sees as its default branch"

57. Just to confirm, we should not do Exercise Part 2 yet?
    - correct, that is next.

58. When I modifed the my recipe and pulled it again, I got this hint. What does it mean? `
    ```
    hint: Pulling without specifying how to reconcile divergent branches is
    hint: discouraged. You can squelch this message by running one of the following
    hint: commands sometime before your next pull:
    hint: 
    hint:   git config pull.rebase false  # merge (the default strategy)
    hint:   git config pull.rebase true   # rebase
    hint:   git config pull.ff only       # fast-forward only
    hint: 
    hint: You can replace "git config" with "git config --global" to set a default
    hint: preference for all repositories. You can also pass --rebase, --no-rebase,
    hint: or --ff-only on the command line to override the configured default per
    hint: invocation.
    ```
   - https://stackoverflow.com/questions/62653114/how-can-i-deal-with-this-git-warning-pulling-without-specifying-how-to-reconci
   - "If you have Git 2.29 or above, you can now set pull.ff to false, true or only to get rid of the warning.". e.g. `git config pull.ff true` to do fast-forwarded pull when possible

59. How can I cancel/undo the merged file?
    - Did it merge successfully?
        - What do you mean by merged file? Do you mean the new file included in the commit?
        - yes it has merged in git hub. but iheard that we should not merge the files yet
        - OK. No problem. It just means you're one step ahead. No tragedy. No need to undo.
        - Ok thank you, but is deleting would be enough for any possible mistaken merge?

60.  Problem with SSH key ( public key permission denied when doing the ssh-T git@github.com command). Was working before. 
    - I would redo the steps in the installation instructions. But make sure you did not type the wrong passkey by mistake. What error message do you get?

61. Instructor didn't use `-u` option with `git push`. Forgot or is there a reason not to use it sometimes?
    - `-u` means "remember where you pushed as the default place to push/pull".  Not needed here.
    - He may have used it before and then he needs not add `-u` again as the local and remote branche are mapped already. See question 51.
        - I think he just pushed it the first time? `git push origin instructor-git-trick`


62. `fatal: not a valid object name: 'master'`. what to do?
    - Try `main`.  Or whatever the branch name is
    - Should it be `master/main` or a different branch name?
    - Do a`git branch` to see what you have in your local repo.
    - ~/centralized-workflow-exercise (master) , and i am trying git branch Toppings master


63. My cntrl c and cntrl v is not working in gitbash.....
    - Try ctrl+shift+c/v
    - I found that you should make use of `ctrl`+`ins` (=`ctrl`+`c`) and `shift`+`ins` (=`ctrl`+`v`). (Here, `ins` is the "insert"-key.) Good to know: When selecting some text and pressing `shift`+`ins` will directly copy-paste the text to the place where you are typing; so you don't need to copy-paste in two steps, it does so in one step.

64. When I try to push the changes of my file in the branch to origin using 'git push origin -u branch-name' it tells me that ''origin' does not appear to be a git repository. fatal: Could not read from remote repository.'but when i replace the origin with the HTTPS repo url it works as such: 'git push [URL] -u branch-name. Do I need to define what is origin?
    - It means that the remote is not defined. You may do that by `git clone URL`, where URL is something like `git@github.com:username/remoterepo.git`
- I have cloned alredy early on. DO I do it again.
    - Do `git pull origin`.
    - It says the same error: origin does not appear to be a gift repo. Could not read from remote repo.
    - Maybe you did not enter the directory? If you `git remote -v` it should list the `origin`.
    - I did 'git remote -v'and it executed fine. Then I tried again to pull orgin and the same error happened.
    - I managed to solve it with 'git remote add origin [repo URL]. This seemed to solve the origin issue.

65.  fatal: unable to access 'https://github.com/linguist89/centralized-workflow-exercise.git/': gnutls_handshake() failed: The TLS connection was non-properly terminated.
  - If it doesnt' work when you try again, something is going wrong and we probably need to test later.  Some problem with the network I guess.
    - Did you submit and issue to be added as a collaborator? Also, is this when you `push`?
    - as collaborator yes
        - Strange. Did some googling but I don't know how to fix it yet.
  - So, I think we need to look later.  Something is going wrong with the network on the computer.
  - Might be related to this https://stackoverflow.com/questions/60262230/fatal-unable-to-access-gnutls-handshake-failed-handshake-failed#:~:text=This%20error%20means%20that%20Git,that%20setup%20process%20is%20failing. and they recommend you should make sure `git remote -v` is pointint to the SSH clone url instead of https://... (I am unsure myself if that is enough for fixing it)
  
66. Did we merge already?
    - no, I don't think so

67. how can we clone the repositories to a specific local folder? 
    - `git clone REPO_URL LOCAL_DIRECTORY_NAME`

68. How can you restrict who accepts merge request to a branch?
    - Various GitHub config within an organization. 
    - the distributed model does this by default (since others don't have write access at all).+1

69. How do you advise, when submitting a pull request, to reference when one is working on or fixing a git issue (for example)?
    - Best case: comment in the issue "working on it" (or assign it to yourself if that's your convention)
    - For fast things I would often just make the pull request without announcing it first (if am not worried about duplicate work)

70. [Not sure if it's relevant right now, but], I'd like to know what classifies as a "patch" versus something else? Is there a general convention?
    - "patch" is change to a file.  Terms are sort of fuzzy, it implies a single change to something.  Could also refer to a file containing the patch.
    - "diff" is similar term, the differences between the files (to my ear they are similar)

71. Why was my file deleted?
    - Where?
    - If you commit the file to one branch, and switch to another, file will disappear from the working directory since the new branch doesn't have it anymore.

72. If I have a repository in an organization account and I want to protect the master branch by only allow 1 maintainer to be able to merge pull request, how can I do this? Who does this option "Require review from Code Owners" (Require an approved review in pull requests including files with a designated code owner.) allow to merge pull request?
    - In the GitHub repo settings, you can "branches" → "protect a branch" and set rules like "who is allowed to push to a branch".
    - "Codeowners" might give similar effect (codeowners might be at a file level)
    - I have done things like this before, but in practice I would need to experiment to get the right effect.  Try it out!

73. Why `git mv` and not `mv`?
    - to let git know that the file was renamed/moved. Otherwise you would a: have to add the moved file to git again and b: git might (or might not) notice that this is just the same file in a new location and might thus loose the history. and c: The original file will remain in the repository, as git does not know that i was deleted unless you explicitly add this file (at the old location) again to tell git "this is no longer there."

74. Is git a could tool if I want to work on the same project on two different computer (e.g. laptop and desktop)?
    - Yes!  One of the most common use cases
    - It doesn't give simulataneous editing, you need to commit and push and all.

75. Why didn't instructor have to git add the file after moving it? +1
    - `git mv` includes the `git add` parts.

76. Why did it now show the old file with all red lines, (like it showed new file with all green lines) since all lines there were technically removed?
    - because of git mv, it knows that the old file was moved and not deleted/a new file created. So it only says "here is a file that was moved, and these are the changes to the file."
     
77. When you delete a branch after merging what happens?
    - It loses the sticky note pointing to it.  Commit still exists in the other branch so still exists.

78. When you revert a merge what happens? Was this why my file got deleted? So what should i do?
    - Hm, yes, seems likely
    - So you undo the merge, the file exists only on the unmerged branch.  Checking out that other branch should get it back.

79. I get this error message after pushing. What could be the reason ? 
    There isn’t anything to compare. master is up to date with all commits from usernam-some feature. Try   switching the base for your comparison. Why is this coming up?
    ```
    ERROR: Permission to coderefinery/template-centralized-workflow-exercise.git denied to username.
    fatal: Could not read from remote repository.
    ```
    - What was the command you used when getting this error?       
    - Please make sure you have the correct access rights
      and the repository exists.
      - I already have access.
          - This repo looks like it is the template, which is different to the actual repo that should be used. (even though this does not explain why you can't clone) +1
                - The correct one is: https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues
                
80. I am on the live stream, so can this merging and file deletion be addressed so that i can follow.
    - is it being addressed now?

81. Do all collaborators with push access, have access to all the different branches?
    - To all the branches that are part of this repsitory, yes. Not to forks.
        - Okay, thanks a lot

82. Why would you `squash and merge` instead of just `merge`? Don't you remove all these commits then?
    - If there are many small commits which can be easily combined into 1. Especially if changes are very small and related. If unrelated, I would maybe keep it in different commits.
    - To keep the history tree of the main/master branch cleaner.
        - Don't you remove all these commits then?
            -  You remove the history of the commits, but not the content as such, the content gets combined. Think of it as  if you had e.g. a supervisor giving comments for a thesis one in each mail, then you could easily combine those comments into one big comment. If the comments however overlap, than squashing might not necessarily be good (if its not just typos that are being corrected).
    - Yeah, I am wondering this too, when squashing, what happens to the side-branch? Does the commits show in the branch? So the commits of the branch are squashed into one and the history of the branch kinda transform into one commit?
      - It stays there, and needs to be deleted later.  The exact commit hashes do not show - it makes new hashes.
      - if you open a pr from `mybranch` to `master`, when you do squash and merge on `master` you will only see one commit doing all what was done in the PR, but `mybranch` will still have the original commit history
      - But any squashed commits will still be there on the branch. It's only on the branch the pull request targets that the commits get combined into one. Not on the original branch they originate from. Problem can be that this branch is then kind of out of sync with master.
       
83. When you do the commit suggestion, this will not update my local repository/branch, right?
    - Correct.  But you can fetch/merge to make those changes local (you would want to do this before continuing your work)
    - So you would not use pull?
    - Yeah, pull works too.  I would want to make sure that it pulls from the right place!
        - You can always double-check with `git remote -v` where it pulls from or pushes to. Good practice if you work with many remotes.

84. Now we're working on repo on personal account. what is the difference in the workflow if the repo is on organization account?
    - No difference. But you may want to have some common rules/guidelines what is to be merged into the main branch.
    - the main advantage of organizations is that you can make teams to manage who gets notifications for what and you can more easily share reponsibilities with others
    - Very often, your will directly push on your own repositories, but use pull requests when modifying collaborative projects. 


85. Now that we resolved the issue with the tea file, who is shown as origin author of the file?
    - The two original commits, with the original contents and authors, are still there.  So you can be sure who does what.  The person who did the merge is author on the merge commit.


86. So when you pull, you actually bring back the master branch to your branch and check if there are conflicts then ? But will other people will have access to my modifications, or is it still on my branch ?
    - When you pull from a remote (your own or a collaborative project), you modify your local copy, but without pushing whatever is on your local copy will not be available on the remote (online) repository. 
        - sorry I meant while you are online, there are these "pull request" (after pushing from local rep to online)
            - when you create a pull request your modifications that are made in that pull request will be made public (or at least visible to the owners of the repository you want to be pulled into). The modifications will still be on your branch, and others still can't modify your branches, but the modifications will be made available to others.
                - ok but we are not modifying the master branch because it is protected, but still people will have access to the modifications ? Don't we need some sort of common branch
                    - The master branch is protected against **direct** pushes, and potentially against merging without review. So you can't push from your local repository to the master branch. but you can still push your local branch to your (or your organizations if you have write access) remote repository and for that branch (with the modifications) you can create a pull request to master. IF you modified your local master branch, you will need to first create a new branch from that and push that to the remote, then create a pull request and have it merged into the remote master branch to get the remote master back in sync with your master. That's why, at least on collaborative projects you in general want to work on a branch that is different to main/master. Does this clarify thing
                    - yes thank you ! Now that the pull request are accepted online, master branch has incorporated the changes. Should I pull again from local to get the new recipes from others that have also been accepted to be merged with master ?
                        - yes since otherwise you are likely to run into conflicts if you create or modify files that others have changed as well. As a general rule of thumb: pull before you push, to see if there are changes.
                        - Thanks ! 
                        
87. What is the difference between doing just `git pull` and `git pull origin master`?
    - The first one uses your configuration to do some stuff by default.
    - If you are already on branch `master` it is probably the same.
    - If you are on another branch, the default pull target may be different.
        - ok thanks! So it's always good practice to to either `git pull` from the master branch, or just always do `git pull origin master`? It might get messy if you do `git pull` from another branch?
     


88. There isn’t anything to compare. master is up to date with all commits from username-some feature. Try switching the base for your comparison. Why is this coming up?
    - So, the branches are the same.  Can you look at each branch and see if they are as expected?

89. I get this error message trying to run the push command 
    error: src refspec; error: failed to push some refs to .....
    ```
    Enumerating objects: 4, done.
    Counting objects: 100% (4/4), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 304 bytes | 152.00 KiB/s, done.
    Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    remote: error: GH006: Protected branch update failed for refs/heads/master.
    remote: error: Changes must be made through a pull request.
    To github.com:linguist89/centralized-workflow-exercise.git
     ! [remote rejected] master -> master (protected branch hook declined)
    error: failed to push some refs to 'github.com:linguist89/centralized-workflow-exercise.git'
    ```
       - this is because the master branch is write-protected! You need to push another branch
         - git push origin -u ?    
         - ~/Downloads/centralized-workflow-exercise (name-flødekage)
           $ git push origin -u username-flødekage
           error: src refspec username-flødekage does not match any
    - I have already received the invitation but it seems I still don't have access
      - You might need to accept the invitation from a link in email or repo page.
        - I have accepted the invitation and can get into the folder. 
    - problem solved. turns out it's because of the ø! renaming the branch solved it.


90. On the new branch create a commit and in the commit message write what you did, but also add that this “closes #1” (if the issue that you refer to had the number 1).:
I get this:
nothing to commit, working tree clean

91. When adding comments, I do not see the +/- button to correct small typos. What do I do to see that?
    - Hm.  Are you in the pull request review view?
    - Are you a maintainer/collaborator on the project?
    - Yes. Others in my group were able to see that button but not me.


## 2. Distributed version control and forking workflow
https://coderefinery.github.io/git-collaborative/distributed/

92. What if I want to have separate admin rights per branch? Isn't it simpler to go for the distributed model, since this is not possible?
    - I don't think that's possible, since access rights are repository wide, not branch wide, essentially you either have certain access to a repository or you don't I don't think there is a possibility to control access on a branch level. 
        - I found that you can overprotect the branch with aprovals or disabling to do a merge without commenting for instance. This could be another mechanism to protect people from writing into an important branch. 

93. What is difference between `git remote` and `git clone`?
    - `git clone` is a wrapper of several commands: `git init`, `git remote add ...` and `git pull`.

94. What is actually the benefit of having multiple remotes? When would I use it?
    - In this case, when you don't have access to the central one.
    - Or when you need to view changes in someone else's private repo
    - Or you work on multiple computers and they need to directly connect to each other.

95. Fork is still unclear to me. 
    - It should become more clear after the demo/exercise (if not ask again)
    - Think of fork as a copy of a remote repository. Forks lets you make changed to the repository without affecting the original remote repository - maybe because you are not explicitly added as a collaborator or you just want to try something on your own before pull requesting to the original one.


96. Sorry if you showed this already, but where can we find an overview of how to navigate the github interface? I got lost in where to make comments, immidiate changes etc etc
    - A general overview?  I'm not sure the best place to look, try clicking around?  If you have a specific question we can guide you.

97. "fork" button was not visible because behind instructore face +1+1+1

98. Where can i get the repo (forking-workflow-exercise)?
 -https://github.com/cr-workshop-exercises/forking-workflow-exercise
 
99. Does forking protect the original developer's right to the code?
    - Well, if there is no LICENSE file on the repository (or a license info in each file) essentially you are not allowed to fork at all, because the things are under standard copyright/whatever is equivalent in your jurisdiction. And thus you don't have the right to create a copy. That's why LICENSE files are so important. 
    - The whole git infrastructure does not change whatever law is in effect under your jurisdiction and it does not affect as such any rights/obligations of developers.

100. Once forked, and that you have made changes to a branch of your fork, and that changes are accepted to the master on the fork. Imagine what you did is awesome, is there a way to suggest it to project where you forked from ?
     - Pull request, you can make one from fork to central (that is what we will do now).
     - PRs can go from any repo to any repo that Github knows as related.
     - Also, you don't need to create a pr to your own forks  master branch first, you can (and that's very common) directly create a pr from a branch on your fork to the master/dev of he original repo.

101. What is the difference between fork and clone, once again please?
     - Fork: GitHub concept for connected repos online ( forking tells github that you are creating a copy of a repository in your online github storage, and lets it know that they are connected)
     - Clone: Make a copy of a repo from GitHub to your computer (you could push this to an "empty" repository you have online, but then the link to the original repository would be lost)
     - (there are slightly more general)
     - Also see the workshop section https://coderefinery.org/git-collaborative/remotes/#commits-branches-repositories-forks-clones with terminology

102. Can we fork from the command line?
     - Not using the basic Git installation. But if you have the GitHub comand-line interface (CLI) tools you may do that. If you do not fork very often, I would not install Git CLI. But others find it very useful, please comment.

103. What if we fork a fork (or fork that etc)?
     - It is possible. But you may want to fork from the original repository as it is usually the most up to date with new features and bug fixes.
     - And yes, this does happen often, look at some of the settings.

104. I don't see "issue" in this "template-forking-workflow-exercise". How do I create an issue here?
     - Are you logged in to GitHub? The issue tab should be there.
         - Got it! I had to create a repository using this as templete. Then i saw "issue" there.
             - The template repo is public, so you should have been able to create an issue for that one as well.

105. I have the same issue I cannot see the issues in the forked version. Is it because it is the same as the original version? 
     - Issues ae repository specific. If you have a fork, the fork does not have the same issues as the original repository
     - Oh.  Yes, by default issues are disabled in forked repositories because usually you want development concentrated in the main one.
     - so shall we create the issue in the main repo now?
     - Yes,  Make the issues in the main repo.
     - but in the future, can I have issues in forks? because i am unable to see it.

106. will there be another exercise session?
     - No

107. When I pushed the new branch i used the code [`git push origin <branch name>`] and I only see the request on the main repository and not on my 'fork'. Did i do something wrong?
     - Do you mean you can only see the pull request button on the central repository? Could be that you did everything right, but can you check that you cloned the right repository? Type `git remote --verbose` and you should see your username in the address. If not, it's cloned from the central repository.
        -    yes. I checked 
        - OK, then I guess GitHub just did not notice... 
        
108. How do I verify where origin points to?
     - `git remote -v` lists all remotes and their URLs

109. At some point you mentioned what was needed to get a certificate of attendance. Could you repeat where to find the requirements?
     - Workshop webpage
        - I tried searching the webpage, but could not find it. Could you post link?
            - https://coderefinery.org/2022-03-22-workshop/#certificates-and-credits

110. i got this error. remote: Permission to coderefinery/template-forking-workflow-exercise.git denied to [name]. So what should i do?
     fatal: unable to access 'https://github.com/coderefinery/template-forking-workflow-exercise/': The requested URL returned error: 403
     - It seems you cloned the template repository, not a fork.
        -  So what should i do? to correct the 403 error. How do i clone a fork?
            - You should go to the GitHub page of the remote repo you want to fork. Click on "fork" - should show somewhere in the top right of the browser page.


111. Why is there no tick/x-mark on the top request at the very top.
     - "Waiting for approval" to run - GitHub made an approval step needed for non-collaborators to prevent abuse (cryptocurrency, etc)

102. So far, we have mostly looked at GitHub's features. Are these more or less the same in GitLab and other collaborative version control applications. Are there any crucial differences?
     - They are all pretty similar.  Minorly different names, but if you give it a try you can figure out.
    
    
113. where is the correct URL?
     - Just watch for now, I think.

114. `git push origin` without branch, what does it do?
    - Here an explanation of different behaviours that can be set by default https://stackoverflow.com/questions/948354/default-behavior-of-git-push-without-a-branch-specified

115. Maybe too biased opinion, but is it actually a good idea to translate software into other languages than english? I.e. keeping it updated can be a cumberstone and most people can speak english quite well. Even more: copule of times there was documentation in my language that was actually so poor that I've switched to english anyway... So IMO I would not translate unless there is a really good reason...
     - You essentially indicate why a lot of software is not translated. You need an attentive native speaker to get a reasonable translation. Effort wise: if you have enough people in a project that do speak a language (and the number of known users in that language-area is large enough), it might be worth the effort, but I would make sure that it's easily disabled, if the code gets out of sync with the translations, i.e. too many things changed. Even for games translations are often questionable, and they make money from it 
     - thinking about contributing by translating, [glosario](https://github.com/carpentries/glosario) is a great place to get started with open source contributions, practicing with git etc.
     - I'd say having documentation in several languages is defintely worth, the more languages the better. I'd also go as far as saying that a lot of open source projects would be very happy to have their docs in multiple languages :) 
         - Problem with that is really if things update, and docus need to be updated. Getting an initial translation is commonly the easy part (even a decent one), but keeping it current needs coordination essentially only allowing merges that change the english docu if someone also updates the other language docus..
            - true, keeping work constantly up to date is the tricky part, another way to get resources in multiple language is to publish blog-posts about your favourite features of a language/library in your favourite language.

116. It the session still going or is it finished?
     - you can go if you want, final thoughts/summary.


---
## Feedback

#### Today was:
- too fast: ooo
- too slow: ooo
- just right: ooooooooooooooooooooooooooooooooooooooooooooooooooooooo
- too disorganized: ooocoooooo
- organized enough: oooo
- wanted more exercises: oooo
- more demos: oo
- not enough time for the exercises: ooo


#### One thing that was good about today:
- Nice that the instructor said: Learners do this, helpers to that +2 +1
- Coordination among the presenters was excellent. +1+1
- Really increased my comfort level. :smile: 
- I finally understand what is happening in Github, after seeing these comments every now and then when searching for bugs etc.+1
- The exercises on Github were very useful in getting familiar with all its features +2+1
- I like the evenly spread talking of both presenters. Better than previous days +1
- Jargon-busting +1
- Much appreciation for the effort. 
- it was in a very good pace and the material was very informative and useful. I worked many years with Git but this lesson clarified many of my problems!
- Content is excellent, remember this even if we write many suggestions for improving: those are to get even better!
- I thought today was great actually and the best so far. Keep it roughly like this I'd say (with more time for exercises)
- It was nice to be able to follow exercises without beeing in a virtual room with others. 
- It was very nice to use Github finally :-)
- I enjoyed the change in 'host' today too, fun to have a new face to learn from
- Regular, short breaks with clear times indicated.



#### One thing to improve for today:
- It was a bit confusing when learners and when group leader should do different things
- It was unclear what to do during the forking exercise, and why we were forking instead of simply creating a branch. We understood it after a while, and it was explained in passing, but could have been made more clear. 
- Live sesions are just right, but too little time for excercises.
- The creation of the centralized repository (by helpers) should be done offline/before the course. It took too much time and added some confusion.
- In spite of the good exercise leader we had, I feel like I'd learn more by not switching back and forth to groups. It saves time, and I can spend more time "coding" or "gitting".
- I think if would have helped to have a type-along session for the GitHub online interface. It was a bit hard to remember how to navigate when doing the exercise afterwards
- The first exercise session felt a bit reduntant, since most of the exercise had already been demonstrated (which took quite a lot of time). It would have been nice to skip this demonstration and just let the participants try it out on their own. 
    - I agree: a quick overview about what one is supposed to do in an exercise would be sufficient; then there's more time to do the exercise (in spite of the very good walk-throughs)
    - I also agree.
- Time for the exercises should be drastically increased as it is the most pedagogical time having your hands on the subject. recipe, what change to add takes time, which is already too little
- The forking part felt a bit too fast and rushed.+1
- It seemed a bit chaotic when you were talking about the exercise, then doing the entire exercise while we were waiting, then giving us time to do the exercise ourselves. I'd /briefly/ explain the exercise, without much demos, then let people try it out. If a lot of confusion pops up, the leaders can help, or if you're getting many comments, you can interrupt the exercise and explain the stuff people are asking about. But there's no point in you doing the entire exercise before we do.
- Use simple coding examples like a python function, this provides more meaning to discuss a contribution or an issue. In my breakout session a learny did that and it improved the understanding. You can do it even with tacos by mixing all the ingredients into an array, or creating a python list of ingredients, perhaps with a ration to make a bigger batch of tacos :)
- GitHub is a jungle of icons and buttons and webpages, illustrating their organization in one go (maybe at the end) may help us orientate +1
- The Github parts of the exercises are not detailed enough on the exercise instructions. Either doing a follow-along during the github parts; or some pointers, maybe in form of screenshots, in the exercise instructions, will help. +2
- More time for people to try things and mess up a bit, you can get a lot of the concepts by also trying out stuff.
- It is a really interesting conversation, but I would suggest sticking to the workshop end time - many people need to leave on time. Maybe could have been doen as a reminder and start-up on tuesday?
- It was good that the presenters said things like 'helpers should do this' or 'learners should do this' or 'mute us if you're in a breakout room', but it's easy to miss these things with all the different things to pay attention to. Would it be possible to indicate these things in the HackMD in case people miss the original announcement?

#### Any other comments:
- waaaay too little time for 2nd and 3rd excercis session, we needed to use the break to finish (and understand what we where doying. Copy pasting commands takes very little time, but answereing questions like "what is this doing?" makes the difference in learning outcome.
- Distributed excercice needs higher resolution in the instructions (e.g., step A.1: fork, step A.2: clone) +1+1
- Centralized-3 was too general and inventing an excercise takes time because without context the meaning of the excercise gets lost. PErhaps, the centralized repository template should contain a couple of files that can be used for the cross-referencing excercise, regardless of what happened in steps 1-8.
- I am not too sure if this is planned for the future, but I would really appreciate if you could shortly talk about git submodules.
- live stream is good, but I see a danger in saying "just watch for now". A great value of these courses is the hands-on part. Every time you say "just watch" some of this value is lost.
- Have a prepared schedule for the exercise leaders so we know what to prepare and when (2nd exercise today seemed improvised, I was not expecting it). This can aid in having sufficient time during the exercises.+1+1
- Today's exercise session was EXTREMELY useful. 
- be more strick with messagges stating when the main stream is done talking, so audio can be switched to zoom rooms. Often we were overlapping or waiting for a green light to start talking in the zoom room.+1
- Can you please gather all comments you make after the 13.30 so we can have a look later, I have to go now and don't want to miss what was being talked about.+1
- I just want to say that despite the occasional pacing issues, this course has been very helpful and I have learned a lot :) Will recommend for other's interested in learning git
- Just adding something here now, a bit late : I find the graph representation of "what is happening in git" a bit confusing ! Could you run through it a little next time ? I feel this type of representation is great and would help getting an overview, but right now all I see is arrows pointing in several directions with c1, b1, m1 and I don't know what they refer to, as well as "HEAD" or stuff like that pointing to origin ... reading these graph feels like I did not grasp everything, that's why I think it might be a good way to synthetize, but not just for me, but to check general knowledge acquisition
     
