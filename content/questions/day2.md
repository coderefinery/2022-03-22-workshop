+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 2

## 0. Intro

### 0.1 Icebreaker

I am watching:
- by myself: oooooooooooooooooooooooooooooooooooooooooooooooooo
- in a small group: oooooooo
- in an organized group: ooooooo
- group is online: ooooooooo
- group is in-person: ooooo

What has been your most collaborative project so far? (tech or not)  How many people and how did you work? **Do not put names or identifying information on this page**:
- A density functional project in collaboration with several universities and institutes in Europe
- Scientific software development, more than 130 contributors
- A paper with 192 other co-authors.
- Some project related to long term effects of COVID-19. Rather small project overall however , 3 people involved, and we did not "properly" use git, testing etc.
- Did not have the chance yet :smile: 
- a robotic project with other 10 people, using GitHub and especially issues to track pretty much every activity!
- A course project (game) with a couple of other students. (Git used)
- Ongoing project, 5 people, github to create our script.
- Start-up, 10 people, chaos!
- Scientific research with 5 collaborators skattered around the world
- Nothing big yet :(
- Start-up + government collaboration, ~10 people (data scientists, software developers, subject matter experts), Git + Github used, specific workflows followed to keep everything tidy
- nothing yet, looking forward to a shared project in the future
- a paper collabration via overleaf
- nothing yet
- Myself with the me that forgot what the project was about
- It is just myself and probably couple other people who are reviewing my code rather than adding anything to it.
- Work on a code with one other person
- I am working on a code developped by my supervisor, but I have not commit for a year :O is merging even possible anymore ?
- European-wide data collection (for a survey); with interviewers; field managers; national institutes; translators; central coordinator; data cleaning teams; statisticians; etc; Communication via emails (:
- University collaboration on a Java piece of software about Genetic algorithms for chemical optimization
- Working on an institution-driver, open-source scientific software package development with 6–12 fellow researchers
- Took part in the organization of the refreshment of some big magnetic particle detectors, I have to admit i am not sure how many people were involved, but the meetings were hold in the canteen, because we did not fit in a meeting room
- Small univeristy projects. Slack and a bit the BitBucket
- Does writing a paper with two other outhors that have no clue about version control and insist on using Word and renaming file that circulate via emails? It counts as a challenge, right?
    - It's definitely a challenge. 
- Online physics competition, ~ 40 coworkers
- Discord bot first in Python and now in Java
- Group project across 4 different universities
- Jupyter Notebooks for teaching, 2 people

What do you think of how we run this livestream workshop?
- Revolutionary. +1+1+1+1+1
- Really cool! The portrait aspect ratio Twitch stream is a really neat idea :) +1
- Too many screens to keep an eye on. My headphones can't keep up. Course is great!
- Nice, keep up the good work! :) 
- Really nice, I would wish be with the rest of my group in person but the way its going is already amazing
- Good, I am learning. 
- I love it! I have been gushing to friends about how cool HackMD is, how easy Twitch is for tuning in to livestream.
- Very nice!
- I like there are more teachers, so that one can focus on presenting something and other replies questions etc.+1
- Very well organized! +1+1
- Very good, but it need to become something people can get university credits for. Thus, probably attendance records and accessment of learning outcome might become more important than allowing hidded participants. I.e., perhaps the (too?) many concerns about privacy are getting in the way to having a bigger impact.
    - Long-term our plan would be "local organizers can manage attendance, tracking people as they need for their requirements" :+1:
- Nice ! But sounds is somethimes low, I need to put sound to the max, and then ubuntu sounds really hurt (like when autocompletion fails, you know the sound)
    - is it still low now?
    - If you have pulseaudio volume control, it can adjust the volume of individual applications, or sometimes even individual videos in your browser. (apt install pavucontrol)

What should we do differently today?
- Ligth background for the terminal please +
    - We worked on this!
    - I'm probably a vampire, but I preferred the dark one... ;-)
- Can't think of anything +2
- Hope it's not super fast today though because I am here to really learn and apply immediately.+2
    - I'll try to keep it slower.


### 0.2 Intro Q&A

1. any tips to make sure HackMD updates changes (& that changes not remain in local cache specially when 100s of edits are ongoing)
    - Refresh the page when needed.  Switch to edit mode once and then back.  But these aren't perfect, so if you notice lag let us know and we will make it shorter.

2. Can you give a broad explanation about how git works? Inner dynamics, etc.
    - You may check our ["under the hood lesson"](https://coderefinery.org/git-intro/under-the-hood/) that shows what happens in the .git/ directory as a result of different `git` commands.
    - Great question. Maybe we can comment on this during start. It stores entire state of the project every time, but it does so very efficiently by storing the data in a tree structure, reusing existing data. It does not store differences. Differences are computed. Branches are pointers (a branch is a file with a 40-char string in it).


3. What does the Twitch portrait aspect ratio refer to?
    - Not sure what exactly you mean. 
    - The twitch stream is taller than it's wide, so that you can have it on the side and it leaves room for other windows.
       - This question was answered from the Theatre mode conversation, thanks!


4. Let's `git started`!
    - We really need to use this!

5. Finding multiple conflicts when trying to install conda environment for coderefinery (MacBook M1 freshly installed miniconda)
    - Oh, I think we saw this for someone else.  It seems like some software isn't supported there: can you try installing using the non-M1 installer, that seemed to work.


## 1. git-intro (continued, day 2)
https://coderefinery.github.io/git-intro/

### 1.1 Sharing repositories online
https://coderefinery.org/git-intro/remotes/


6. Does the name of online repository has to correspond to the local one?
    - By default it will, but you can use a different name if you want to
        - if you clone a repository and don't give a local name it will use the repository name as the name for the local folder.

7. For those who are working on their own (No team), would it still be possible to experience colaboration on github?
    - In general: yes. If your project looks interesting to someone else, they might start to contribute.
      Similarily, if you find a project/repository online that you think is useful and want to implement some feature, you can fork (create a copy in your account), start developing, and finally contribute back via pull requests.


8. Can you share the repository URL that I can import?
    - https://github.com/dianaiusan/recipe-guacamole ?  (or the previous one?)
    - When I go to my repository, it is empty. I missed the first part, so I was wondering if I should import one for today.
    

9. Should the repo be public or can we also choose private?
    - If the repository is private, others will not be able to find it and try contributing to it. Otherwise it does not matter.

10. In my local repository the directory is named differently, just "recipe", is it OK to have different names in github and local?
    - Yes.  Might be confusing at some point but you can manage.
    - If you talk about the repository name (base folder), there is no problem. If it is a folder within your repository, they should not differ, mainly because they should contain the same information.
    

11. I've used version control included in vscode some for projects already - this uses signin with https with online authentication - isn't this safe? In many ways it seems smoother in use, as it's purely gui
    - https and password auth is fine. But most tools actually also allow using ssh keys (I'm pretty sure Vscode as well), and you essentially don't need to enter passwords any more (except for your ssh key password if you have set one)

12. If I've already set up github with https and can use it comfortably, can I continue the workshop using the https protocol?
    - yes, using ssh keys just makes it a bit more convenient since you don't have to put in passwords all the time.

13. Can we change names of our local folders as and when we want or does it affect the link with Git?
    - You can change the name in the settings tab on the GitHub repository. It will change the URL. 
        - What happens if we change the location of the local folder? Eg from C drive to D drive manually by copy/cut pasting?
            - This does not change anything other than the location on your system. Make sure to copy/move the entire folder, not just the files in it.

14. I see that my branch is now called (master|MERGING)... I guess I did someting wrong yesterday, is there a quick explanation and how to fix it?
    - You have not yet fixed your merge-conflict.

15. How can I see the remote repositories that are linked to my local one?
    - `git remote -v` shows all your remotes. In most cases there will be one remote, but it's possible to have many.

16. Can you copy all local branches (not only main) to the remote (github)?
    - Yes, you can push all the local branches to the remote.

17. What does the -u argument in the push command do?
    - it sets the "upstream" repository, i.e. connects your local e.g. master branch to the remote origin/master branch. This means that you won't need to specify the branch and remote later on, a `git push` or `git pull` will be enough.

18. It did not ask me passcode. But I can see the files in github now. Why?
    - Did you set up SSH keys?  That is probably it, they log you in.  (this is big benefit of ssh + git)

23.  I received this error:
     ```
       src refspec main does not match any have this 
       error: failed to push some refs to 'github.com:username/recipe-guacamole-coderefinary-.git'
       What would be the reason of it?
     ```
     - maybe you have to rename your local branch first: `git branch -M main`
     - tried but still recieved the same error
         - ah, probably it's just a cryptic error message when you haven't actually committed anything! So there's nothing to push

24. i already have a project directory with lots of files and scripts. I dont think i can push the whole thing to github like how we did now. How do I do in that case?
    - If it's a git repository, you should be able to push it. The only possible problem is if you have very large files (not code or scripts) in the repository..
      - It is not a git repository yet. 
      - I do have large files. and high resolution figures. So my question was also like should i push one by one.
          - Github is not really for data storage. It's intended for code versioning. Data "should" be rather constant, so there is no real need for versioning, or well, sometimes there is.
              - Oh I got it. I can may be put all large files and figures as git ignore. 
                  - yes , essentially put everything that can be reproduced by running code into gitignore, and if you have very large data input files, better store them in some other place (e.g. zenodo, as mentioned below).
      - You can create an empty repository online, and push your current project there by initialising your project directory as a git repo and afterwards adding all files you want under version control to git. 
    Thanks :)
      - One more thing: If you do want to publish data files, check out zenodo.org (we will also talk about this a bit next week)
          - cool! thanks.

25. My git does not ask me for my password, but I have not set up an ssh key. Is this a sign that something is not as secure as it should be?
    - Is this when cloning or pulling from a public repo? This is possible to do also without authenticating.
        - No, I was thinking just now for instance when pushing up my local repository to git
            - i think pushing without ssh keys (using https) will always ask for a password

26. What is the difference between pull and fetch?
     - The pull command does more than fetch. With fetch the metadata for a repo is updated. With pull also the contents are copied.
     - You can also see this by doing `git pull --help`
     - pull is a combination of `fetch` followed by `merge`: if you are pulling the same banch as you are already working on (e.g. pulling remote `main` into local `main`), the effect is to (try to) add all the remote commits into your local branch, syncing up from remote to local. But, if you are on a different branch locally than the one you `pull` from the remote repository, you need to be aware that this automatic merging behaviour might not be what you want (many times, I have accidently pulled the wrong branch and had to take some time to undo that merge :cry:)

27. Problem: 
    ```
    remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
    ```
   - this means that you need to upload your ssh keys to push changes to GitHub
   - Problem was that I used `git remote add origin https://github.com/username/recipe-guacamole.git` instead of `git clone git@github.com:username/recipe-guacamole.git` 
     - That can be fixed:
       ```
       git remote set-url origin git@github.com:username/recipe-guacamole.git
       ```
       (replace "username" by your username.)


28. I have the following error. I tried the HTTPS, but that also does not work... 

29. Terminal asks for authentication which then fails for some reason
    ```
    $ git push -u origin main
    The authenticity of host 'github.com (...)' can't be established.
    ECDSA key fingerprint is SHA256:...
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added 'github.com,...' (ECDSA) to the list of known hosts.
    git@github.com: Permission denied (publickey).
    fatal: Could not read from remote repository.
    
    Please make sure you have the correct access rights
    and the repository exists.
    ```
    - I follow instructor's advice, and I get the following: 
    ``` $ ssh -T git@github.com
        git@github.com: Permission denied (publickey).
    ```
    
    - Could you double-check that the `ssh key` you pasted to GitHub is in your computer?
        - If not then check if a public SSH-key exists and add it to GitHub in profile -> settings


31. when we share the repos, should we use HTTPS or SSH link?
    - better to set up the repository to use SSH, because authentication via username/password not supported any longer for pushing changes (it's also possible to create a [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token))

33. username for "https://github.com"? should be my username on github?
    - yes 

34. I've added SSH key, but have this error. Is the public key unique to each IP adress? Do I have to add a new key when connect to different network?
    ```
    Warning: Permanently added the RSA host key for IP address '...' to the list of known hosts.
    git@github.com: Permission denied (publickey).
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    ```
     - This probably means that you don't have an ssh key set up on GitHub. [Here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) is a tutorial how to set up your ssh key in github
         - I have done this. But it was when I connected to a different network. I've created a new SSH key from my current network, and it worked.
             - it doesn't matter what network you're on, you only need to have the ssh key on your computer
     - or you are not pushing to your but someone else's repository
    - maybe you have to rename your local branch first: `git branch -M main`
       - I tried this bu still the same error:
       - plus I recieved this after ssh- T git@github.com :-1: $ ssh -T git@github.com
           - When you connect the first time, you need to accept the fingerprint by typing "yes".
   ```
   The authenticity of host 'github.com (...)' can't be established.
   ED25519 key fingerprint is SHA256:...
   This key is not known by any other names
   Are you sure you want to continue connecting (yes/no/[fingerprint])?
   ```

35. Even with SSH key set up I was asked to generate an authentication token, after using that for password it worked
    - As long as it works, best to just move on and get back to this if you have time
    - That said, did you use the ssh address?
        - I did! `ssh -T git@github.com` works as well...


36. Everytime I `push` (or type `ssh -T git@github.com`), I have to re-enter my password. Wasn't the reason for using `ssh` that you can skip this re-entering your password everytime?
    - did you set a password for your ssh key? >> Yes, this was stated in the instructions on creating a `ssh`-key.
    - One would use "ssh agent" to remember the passphrase.  Some operating systems do this automatically, some needs to be set up.  Unfortunately we don't discuss this in detail. 
    - It's also possible that you have created the ssh key with a password. In that case you need to type the password every time you use the key. If this is the case, you can create a new key with an empty password.

37. @instructor, what tool are you using to partition your screen?
    - He uses some tiling window manager (not sure which, he'll update this question later)
    - is this within Twitch?
        - the tiling window manager is set up on his computer

38. How much support will there be for the GitHub cli? So I want to create the repository with gh repo create, rather than going to github.com, but will gh commands be explained?
    - We don't explain them in this course.  Basically for simplicity of the teaching/better online visualization.

39. How can I change my passphrase? Redo the steps in the tutorial?
    - Yeah, you would need to make a new ssh key

40. Is it important for tomorrow that we set up an ssh key, or is if ok to continue to use http?
    - If https works to push/pull from the command line, that works for this course.  ssh is very converient long-term though.

41. I get the message Fatal: could not read remote repo. Please make sure you have correct access rights.
    - Let's go on and debug later.
    
42. Did we not collapse all branches in yesterday's session?
    - We merged them, but the branches (sticky notes) probably still exist.
    - I think some deleted the branches, but you can still see the history.

43. I do not see the ssh option when I try to copy the url inorder to clone from diana's repository. Why is that? It is only two! Https and Github CLI. I got my answer. I was opening Github on two different browsers and that is why I could not see it :+1: On the second borwser I was not loged in. Could to my github account. Could that explain it? The second browser is "Brava". I can share screen shot if that helps ![](https://i.imgur.com/dfDiihG.png)

    - I've never seen that before! Have you added an ssh key on GitHub? 
    - What browser are you using? 
    - That is still kind of weird
        - if one is not logged in on GitHub one doesn't see the ssh option
    
44. How to delete cloned repository. Now I have two repositories "recipe" and "recipe-glucamole" and It will be confusing to make changes. 
    - do you have two local repository folders or do you have two different online repositories?
    - If they are local, just remove the entire folder.
    - If on GitHub, you can delete a repository on its settings page

45. Does the command `git branch -M main` require you to in the master branch? I think I changed the name of branch "dislike cilantro" to "main".
     - yes, it renames the branch that you are sitting on (where HEAD is pointing to)
         - The branch has now a quite strange name: "(HEAD -> main, tag: Guatamale-recipe, origin/main, master, like-cilantro)". I don't really get what it means? What is origin/main?
             - `origin` is a shorthand for the remote repository you have set; check out with `git remote -v `; you could choose another name than `origin` and a more descriptive name is often handier when you have several remotes, even on different repositories (say GitHub **and** GitLab),

46. Where do we clone the link? In the recipe folder? 
    - From the parent directory of recipe folder.  As in, not within the other git repository.
    - In general can be anywhere you want.
        - I do not recommend cloning inside another repository, though.    


47. In case someone sees my fancy `git graph` alias and wants to have it too. Is there a way to see the actual lines of the alias? (in case I cant remember anymore)
    - `git config alias.graph` or `git config --list` to show all.


48. If you do `git remote add blabla` will the origin then be called blabla for this repo or does that not work?
    - yes, you can choose any name for the remote when you add it. 'origin' is the convention/standard, but you can choose whatever name you like. (you can also rename a remote with `git remote rename oldname newname`)


49. Getting this error message after trying the `push` command
    ```
    info: please complete authentication in your browser...
    remote: Permission to coderefinery/recipe.git denied to username.
    fatal: unable to access 'https://github.com/coderefinery/recipe.git/': The requested URL returned error: 403
    ```
    - are you using https to connect? In this instance you will need to authenticate via browser to push.


50. It might be good to notice that even if you change the repository from public to private it will not delete the forks if someone has forked it.
    
### 1.2 Inspecting history
https://coderefinery.org/git-intro/archaeology/

51. If one uses `git grep`, can we use extended regular expressions?
    - you can use regular expressions, not sure about extended regular expressions
    - :heartpulse: `git grep`
    - `git grep -E` or `git grep --extended-regexp`
52. What if you manage to push to the repository private information (e.g. some password). How can you remove it from the history?
    - If you search "rewriting git history", you can find different options.  Let's not get to it here.
    - "Undoing and recovering" in git-intro has "rewinding branches" which is a basic starting point.

53. Since you can see repositories we created in GitHub, can you now provide a certificate or credits based on that? Would be great to have a certificate for this. 
    - yes!  We thought this but not all will be published (and some people may public, and sharing them takes a lot of time).  But in some courses, we do this.

54. I will need to use GitLab for my PhD with my supervisor, there is a considerable difference between GiHub and GitLab?
    - Mainly in some names (Merge request vs pull request).
        - They are essentially the same, and heavily based on git. With similar features for issue tracking, automation, etc. Some things are done differently, but the concepts are almost the same from a user point of view. 

55. How can I save Dianas cloned repo to mine? I cloned, but its not being shown in my GitHub acount :D
    - when you clone a repo it only shows up on your local machine. The most common mechanism to copy an online repository to your own GitHub/GitLab account is **forking**. We'll talk about that tomorrow


56. So moving e.g. from GitLab to GitHub is just change of the remote?
    - That, and you need to create the repository on GitHub, like Diana did a while ago.
    - There are a couple of points here:
      - Do you have Continuous integration set up? this can be migrated, but it is a bit complciated
      - Issues and pull/merge requests will not move automatically. They can be migrated.

57. I get this error after I put my username and password
    ```
    Username for 'https://github.com': username Password for 'https://username@github.com':  
    remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.  
    remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.  
    fatal: Authentication failed for 'https://github.com/username/recipe-guacamole.git/'  
    ```
    - I think you did not set an SSH key properly. Can you run the test command successfully?
    - Yes: 
        ```You've successfully authenticated, but GitHub does not provide shell access.```
    - You are using https instead of ssh. This means it's not using the key. Use the link that starts with `git@github.com`
        - When I run 'git remote add origin git@github.com:username/recipe-guacamole.git' I get 'error: remote origin already exists'
        - You have set up the remote with the https address. You need to change the url with `git remote set-url origin new.url`
        - Use `git remote set-url origin <git_url>` to change the url git will push the repo to.
            - It worked! Thanks!

58. is there a way to undo the push commands because I have an error in it and need to redo it: 
    ```
    git remote add origin git@github.com:username/recipe.git
    fatal: remote origin already exists.
    ```    
    - if the error was in the URL, you can correct the URL with `git remote set-url origin https://new.url`; if you want to remove the remote altogether and add it again, you can use `git remote remove origin`


59. could you repeat how to do the animation?
    - https://github.githistory.xyz/networkx/networkx/blob/main/README.rst
    - (githistory.xyz)
    - left- and right-arrow keys to scroll back and forward through the git commit history for that file.

60. if `git grep` searched in the current copy, what is the difference with `grep`? 
    - Git grep will only search files that have been added to git (you can have other files in the directory, that are not in git)
    
    
61. What does the -i in the function mean?
    - case insensitive, otherwise it would only match fixme lower case
    
62. Since git changes the files according to the branch I checked out, why should we use git grep instead of grep?
    - Git grep does not check files that are not in git. This can occationally be useful, but if you want to search all files, use `grep` instead.
    - for example if you have output files that are not tracked by git, but only want to search in the code, git grep will ignore those output files.


63. I got this error after I type " git push -u origin main", and type in my github username and password in terminal
    ```
    remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
    remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
    fatal: Authentication failed for 'https://github.com/username/recipe-guacamole.git/'
    ```
    - You have set up the remote with the https address. You need to change the url with `git remote set-url origin new.url`
    - Use `git remote set-url origin <git_url>` to change the url git will push the repo to.
    - See question no. 57.
    
64. Which VS Code extension do you recommend for git?
    - Git graph: good for visualizing the history, accessing commits and inspecting history.


65. I got the following error when I use `git log -S test_weakly_connected_component`:
    `$: command not found`
    - does a normal `git log` work? 
        - yes it works
            - did you also clone the NetworkX repository?
              - yes I cloned it with "git clone https://github.com/networkx/networkx"
                  -  Did you cd to the repository? 
                    yes, i'm in it
    - did you include the `$ ` at the start of the command? This `$` should not be included in the command.
      - yes, I made that mistake. This fixed it. Thanks
        - great! :+1: 

66. Why use `git grep` instead of just `grep`?
    - `git grep` only searches in files tracked by git, it may be significantly faster than `grep`

68. Does `git log -S` only search in the commit messages or also within the documents?  
    I refer to https://coderefinery.org/git-intro/archaeology/#git-log-s-to-search-through-the-history-of-changes and *While git grep searches the current state of the repository, it is also possible to search through all changes for “sometext”*
    - `git log -S` doesn't search commit messages, it searches in tracked files. Useful to find when a particular code line was introduced and/or removed
    - it is unfortunate that this look so similar to `git log` :| To me it suggests searching in the log (which is wrong!) +1
        - It returns commit messages, though!
            - yeap, that's the right interpretation of "log", I guess
                - Is it a scheizophrenic command? ;-)
                - This point should be clarified IMHO :+1:
        

69. Does `git show`, show the differences between the hash we search for and the current version?
    - it shows the changes in that particular commit, i.e. removed lines and added lines

70. Typing the `git annotate` command shows `>>>>` on front of some lines in the right side. What does the >>>> mean?
     - I've never seen this, and cannot find an example :(  Often ">>>>>" refers to changes in your latest version
     - perhaps you still have some merge conflicts in the file, left over from yesterday? 
     - no i think it's just showing text from comment blocks in the code which actually contain >>> ! (if this is the networkx repo)
         - indeed. it's just part of that line in the source code
     - ah!

71. when I type in "git push -u origin main",ask for 
     `Enter passphrase for key '/Users/jinzhang/.ssh/id_rsa'`
      - When you created the key, you added a passphrase. If you want a key without a passphrase, you need to create a new one and when is asks for one, leave it empty
      - ok,thank you, then I got it


72. Using the hash will take you to the code as it was right after that commit with that hash, yes? Not just before it?
    - yes, it will check out the indicated commit, which is the status after this commit was processed


73. Can we have a quick training to setup a remote repo in version.aalto.fi?
    - it's the same as for git. The only difference are the addresses. 
        - so instead of `git:github.com:` you have `git@version.aalto.fi:` and you will need to add your keys to gitlab instead of github.


74. git: 'graph' is not a git command. See 'git --help'. The most similar commands are branch, grep
    - `git graph` is an alias we defined yesterday. Run this: `git config --global alias.graph "log --all --graph --decorate --oneline"`

75. Does the content for the following days depend on what we are doing today?
    - we will be learning how to collaborate using git and GitHub tomorrow, but don't worry the instructions will hopefully be very clear!
    - exercise-wise it doesn't. Tomorrow we will start with a new exercise.

76. I have SSH key set up but still it has asked my for usename and password when setting up remote repository. Is this OK?
    - Are you using the ssh address or the https address for the repository? If you use https, you will get asked for username/password. if you use ssh it should only ask for your username, and might ask for the password for the ssh key if you have set any

77. Can we create a branch inside a branch?
    - yes. You can create a branch based on branch. Essentially main/master is only a branch too, so any branch just branches off another branch.
    - good to remember that branches are like sticky notes and you can create a new one pointing at the same place the other sticky note pointed to

78. What is the difference between tags and branches?
     - Tags are connected to a single commit.
     - When you add a commit to a branch, the branch moves to the new commit. If you have a tag on the previous commit, it just stays there.
     - Tags are good for version numbers, for example. The tag "v0.1" would always point to exactly the same version.
    - Both tags and branches are references. tags point to one commit, the branch reference points to the latest commit of that branch. But we usually think of a branch as the time line of the commits, with the tip of the branch moving as more commits are added.
     - Tag is like a branch that never moves and which can carry some extra metadata.

79. When I clone the networkx repo to my laptop, I get an error on Git Bash, but it works when I do it from the Anaconda prompt. 
    - Can you copy the error message here?
      ```
      PUT ERROR MESSAGE HERE
      ```

80. With `git bisect` I get this:
    ```
     You need to run this command from the toplevel of the working tree.
    ```
    But I am already in main. What should i do?
      - but are you in a subfolder/subdirectory of the project?
      - Top working tree in this case is `<somepath>/networkx`
      - the reason git bisect asks for this is that as you bisect through history, some subfolders may come and go so it wants to make sure you are in the root folder of the project and don't disappear together with a removed subfolder

81. When i checkout a new branch as given in the exercise, then I did a git log to find the last commit before the changes have been made.
    Now, with the hash given i can checkout using "git checkout ....." but then I am not on my newly created branch anymore right?
    - yes, you will be in whatever branch you named, or a so called detached head, which is not on any branch.
        - Yeah, it says detached head, but was that the goal of the exercise? 
            - well, can you from this point figure out what happened before? The thing is, if you don't want to actually work with a specific version not being on a branch is not a bit issue. Only if you want to work (i.e. develop) using a specific version you should be on a branch so that you can commit and store your changes. You can at any point (even from a detached head - as far as I know), check out a new branch that starts at this specific commit.
              - Ok, so we only created the branch so that git log shows the commit right before? 
                  - I'm not entirely sure what you mean. 
                    - in the exercise it says we should create a new branch with the hash we found with git log ... and then find the commit right before the one we found. Was that the purpose of creating the branch?
                        - ahh. I think it's more so that you know (or rather test it yourself) how to create a branch based on a given commit. Just for inspecting, you would not need to create the branch, and could do that in a detached head.
                            - ok, so then the question is: if I find the hash from git log... is there a way to show the history before a given hash? or maybe in an epsilon area around the hash
                            - `git log <hash>` will print the commit history of the given hash: legendary! thanks
                            - same with `git show <hash>` giving you the infowhat a given commit changed.

82. How do I search when using git annotate?
    - Type `/`, then type the search term and press Enter
    - also have a look here: https://coderefinery.org/git-intro/archaeology/#git-annotate-to-annotate-code-with-commit-metadata


83. Want to check which commands I have used with git and better yet save them for some future use (without duplicates)
    - Command `history | grep git | sort -u > git-commands.txt` checks out the command history, selects only those that include `git`, removes duplicates and outputs the result into a file.

84. If I want to go to the commit just before a tag or when a branch was created (in the case I use `git checkout -b temp-branch <tag/branch name>`), can I just append "~1".
    - That should work. 


85. When I do "git show hashcode", I end up in something that looks like a different "environment". The line starts with a wave symbol, not a dollar sign. What is thsi How to I get back to git? 
    - Try pressing `q`
    - commands like `git log` and `git show` use a "pager" in your terminal. In many cases it's the `less` pager, which is exited with `q`, scrollable with up/down arrows or `Enter`, searchable with `/` followed by some pattern (and `n` to find next match) 


86. When I look for the branches available after cloning the networkx repository, it shows 7 branches (including stale branches). This has a branch called v2.6, but I could not find one named v2.6.3. How do I know what are the available branches in the repository including say v2.6.3,v2.6.4 etc.?
    - `network-2.6.3` is a tag pointing to a particular commit on the main branch. `git tag` will list all defined tags. Sorry for the confusion.



87. For the exercise, when I use 
    git log -S "Logic error in degree_correlation" it does not give the correct commit, instead in solution it goes in two steps, to grep and then to annotate. When one should use git log -S then? I sort of expected that it will give me the correct commit.:+1:
    - To some extent log -S is actually correct. The commit indicated by git annotate as a change in the Line is actually not changing the parts of the line we searched for. if you have a closer look at the actual commit (i.e. `git show`) you can see, that the part we greped for wasn't changedOnly spaces in the print statement in this line were changed. So`git log` is correct in indicating, that the las change of that full expression was earlier.


88. Bisect example: why does -- git log -S "483" -- work, but -- git log -S "number 483" -- does not work?  
    - is there any change (addition or deletion) which contains the text "number 483"? 
        - yes, the first command gives me a hash with the commit message "commit number 483". So I am not sure why the second one does not find it?q
              - oops sorry I did not see this was git bisect example. looking there ...
    - "Git log -S" does not look at commit messages. It only searches the lines that were changed in that commit.
    - if you `git show` the commits that `git log -S "483"` finds, you see that this is part of the change also
        - Ah, that's sneaky! thanks, got it

89. When using git annotate networkx/threshold.py. Im not able to find the "/Logical error". I think that it doesnt give the results in the less program. It outputs everything like when using a cat. How can I find 'Logic error'? Thanks!! When behaving as cat how can I find 'Logical error' I will do it again, maybe I have done something wrong earlier. Thanks!! I was no an other branch upps
    - It only outputs the lines that exist in your current working tree. 
    - It behaves like `cat` if the output is short and like `less` if the output is long.
    - How much output is there? If the output is short enough to use cat, you should be able to read it with a glance. Are you sure the line should be there? `Git annote` only prints lines that are in the current working tree, and the line might have been removed in an earlier commit.

90. What does this mean? I use the first commit in 'git bisect good'
    
    ```
        running get_pi.py
        C:/Program Files/Git/mingw64/libexec/git-core\git-bisect: line 189: get_pi.py: command not found
        Some good revs are not ancestors of the bad rev.
        git bisect cannot work properly in this case.
        Maybe you mistook good and bad revs?
        bisect run failed:
        'bisect_state bad' exited with error code 1
    ```
     - It tried to run `get_pi.py` as a terminal command, which I would not expect to work. What command did you run?
         - I used "python get_pi.py"
     - The command it should run is `python get_pi.py` insted of `get_pi.py`
         - Yes
         - Anyway, I found the problem. I should have run "git bisect bad master" instead of "git bisect bad main" like in the example, because the name of the main branch is "master".
    
91. Why didn't the tags from yesterday show up on GitHub?
    - did you push the repository including those tags to gihub?
    - `git push --all` would maybe push also tags
    - `git push --all` pushes all branches, but not other references, such as tags
    - You need to push the tags to the remote repository with `git push origin <tag_name>`
        - or `git push --tags <remote>`

92. aaaaaaah, git bisect actually does a bisection sorting algorithm? Ok now it is clear what is happening. I did not understand this from the course material
    - Yes, 


93. `git bisect bad main` gave the error ```fatal: Needed a single revision. Bad rev input: main```
    - It was `master` not `main`

94. SPOILER: I think this is a better solution than the Python script provided: if [ `python3 get_pi.py` == 3.14 ]; then git bisect good; else git bisect bad; fi

95. Out of curiosity: ` git diff past-code past-code~1` and ` git diff past-code~1 past-code` return the same output, so the addition/delation color coding seems bound to time rather than to first vs second thing being diff-ed.
    - On my system they are different. Maybe this depends on git configuration?
        - Also the "+" and "-" sings are the same on my system (git 2.32.0 (Apple Git-132)). Weird...

96. To easily find the line number with grep, use the -n flag
    - And you can use annotate with the -L <start_line>,<end_line> to only show certain line numbers so you don't have to search or scroll there

97. I am somewhat confused as to what git bisect does. When doing git bisect good from the excersise I got commit number 376, whereas when I did git bisect bad I got commit number 313. Should these not give commit numbers that differ by 1?
      - git bisect returns the commit half way between the points that you have told it are good and bad. you can then compile/run the code in this state and tell git bisect again whether this commit is "good" or "bad" - based on that new information, it will return another commit, now half way between the new "good" and "bad" points. You repeat this process, narrowing down the range of commits where the breaking change was introduced until there is only one commit left - that commit will be where the change you were looking for was made. (This explanation is long and probably not the best - please let us know if you are still confused!)
      - I understand now, I just thought that the bisect function did all you describe above. Now I understand that I have to implement this myself.
      - as the instructor just mentioned, it is possible to write a shell script to automate the process, based on logic added around the command you would run to see whether the code runs correctly or not. this is definitely outside the scope of this workshop though



98. I think the extra exercise is a very good idea ... however, it should be better if an  instructor could take time after to do it online so we can follow...in order to fully understand. We do not have all the same level of git and programing which you, as instructor fully understand :smile: +1
     - Git bisect is an optional extra partly because we don't usually have time for a detailed explanation (but see the question above)
        - Thanks I was actually reading the comment on the question above


99. `Detached HEAD` <- Thank you for the explanation! This happens often and is confusing.


100. does `git checkout -b` mean creating a braching and going into that branch? 
     - Yes. It creates a branch from where you are and moves to that branch


101. When writing `git log -S "Logic error in degree_correlation"` I was expecting at first that this would help me find the commit where this was introduced, but this did not work. It gave me the wrong commit, wrong date etc 
     -  It gives you a list of commits that change any line with that text (so add that text or remove that text).
         -  But then shouldn't the commit I'm after be included here? I only get one commit, and not really a list of commits

102. After finding the commit, do we have to do anything else for this optional exercise?
     - The exercise is just to find it. In a real case, you would now look at the changes in the commit and try to figure out what caused the problem. Then return to the main branch and fix the problem.

103. After the optional exercise is done, do we have to do anything about the `git bisect start`? I feel like the effects of that command may lay dormant.
     - `git bisect reset` to end the bisecting process and go back to where you started

104. Lets go for a video if possible ! that would be great !
  `+ 4`

105. Can you explain the concepts of parent and children again?
     - A parent commit is the commit that comes before a commit in the history. Parents are defined, when the commit is made (and one commit can have multiple parents, if it merges things from multiple branches). At the moment when a commit is created and its parents are set, it becomes a child commit of those parents. Commits can have multiple childs, e.g. if two developers branch of at the same commit, than that commit will have the first commits in each branch as children. However, while a parent can always be found, a child is only visible on the branch it was created in unless that branch gets merged into another branch, while the parents are visible from other branches (because the child knows where it is coming from, but the parent doesn't necessarily know whether it has childrens in some other branch). Is this clear(er)?

106. When doing the exercise, I ended up using git log -S "Logic error in degree_correlation". This gave me only one result from 2005, and not the last edit as I could find with git annotate. What exactly is git show -S? Why didn't subsequent changes show up with this command?
     - see #88, `git log -S` looks for changes in the exact matching string. And the search sring actually didn't change in the commits noted `git annotate` only additional things (spaces) in the line changed. 

106. What webpage are we looking at right now?
     - https://coderefinery.org/git-intro/recovering/


107. I am getting this error when i try to run "$ python get_pi.py"
      - Either Python is not installed, or the terminal cannot find it. See installation instruction here: https://coderefinery.org/installation/conda/ and then https://coderefinery.org/installation/conda-environment/
        - Miniconda comes with Python, so installing it and creating an environment is enough to get Python.
            - I also get this error, but I have already miniconda installed.
                - hopefully this helps: https://coderefinery.org/installation/conda/#setting-path-to-conda-from-your-terminal-shell

108. What if I stage, and then clean only the local repository? What will happen to the stagged?
     - staging essentially writes the changed files to the git database (creates object for them). But without being commited, they will not be part of any branch. So (but I'm not entirely certain), if you have used `git add file1` and then delete file 1 (not with `git rm` but with something outside git), you could recover the file or still commit it and it will be in the state that it was before you deleted it. If you `git add` it again after you deleted it, git will consider it as deleted and the next commit will contain a deletion of the file.


### 1.3 Undoing and recovering
https://coderefinery.org/git-intro/recovering/

109. Does Staged mean commit? I forgot.
     - Stage means "added" i.e. `git add` stages a file for a commit.

110. If I have commited some changes to master. But later want these changes to be in a different branch, and reverse master to before, what steps should I take?
     - Maybe simplest is to 
         - rename master
         - checkout a past commit
         - create a new branch called master (`git checkout -b master`)
     - Or
        - Create a new branch from master
        - Move master to a previous commit (git reset --hard commit_hash) 

111. What is the difference between revert and going to parent hash as we did in the exercise?
     - Revert create a new commit that undoes the earlier one. Earlier we "checked out" the old hash, which gets you the files but does not move the branch.
     - `git revert` makes a *new* commit that undoes something (so the old history is preserved)


112. I got this for `git revert master\~..master\~2 `
     `fatal: bad revision 'master~..master~2'`
     - Is the default branch named `master` or `main` ?

113. when doing `git revert -n master~..master~2`, isn't that skipping the most recent commit? Wouldn't it be tidier to `git revert -n master..master~2`?
     - Correct, I think that would skip the most recent one.  I guess that's what they want?
        - Ok thanks, so that won't necessarily make a mess although the most recent commit might be dependent on changes made in the two previous commits?

114. `Python was not found; run without arguments to install from the Microsoft Store, or disable this shortcut from Settings > Manage App Execution Aliases.` it could be that my git bash cant find python... I have miniconda installed any solution for this?
     - hopefully this helps: https://coderefinery.org/installation/conda/#setting-path-to-conda-from-your-terminal-shell


115. I spaced out for a sec, what is `git revert -n master~..master~2` supposed to do?
     - `master~..master~2` is "second and third most recent commits"
     - `git revert` is "make new changes that undoes htose changes"
     - `-n` is "don't make a commit, just apply the changes, you can do it yourself"


116. If you amend a commit, is the old commit still present in the repo if you have the hash?
     - `amend` replaces the commit, but does not delete the old data, just makes it not visible (you can `git show` the hash)
     - I just tested it and yes you can still access the old commit.
         - right, it still exists! But it's orphaned 
            - orphaned?
                - Not connected to any branch or tag. Orphaned commits get removed periodically.
                    - so essentially, a "replaced" commit will linger for an unspecified amount of time and then be deleted from the database?
                    - yes

117. How can we see `git graph` for remote branches?
     - The alias should have `--all` which includes (known) remote branches.
     - If the remote isn't added as a remote, can't be seen. 
     - You may need to `git fetch --all` to update

118. Why not to call `git reset` as `git move` (the branch label)?
     - `git mv` moves files.  `git move-branch` might make sense, but there's a *lot* of confusingly named stuff in git.  Too bad for us... 
     - To make it worse `git reset` does two types of things, update the index and update a branch.
         - Aaargh!

119. What is the difference between `git rebase` and `git reset`? when to use which command?
     - `git reset` is "force change a branch"
     - `git rebase` moves commits from one branch to another, if you want to keep the commits (look it it as another way of merging, sort-of)
     - `git rebase` can make very general changes to git history: delete commits, reorder them, pick commits from a different branch...

120. How do I delete a cloned repository?
     - delete the local folder. If you forked it to your own git account, you can delete that copy/fork online in the github interface

121. What will happend if I `git commit --amend` after I shared with someone else (e.g. `git push` to github)? 
     - Your git history is now different from what they have. You can still merge by pulling the version from github and then pushing back the merged version. Or, if you are sure no-one has pulled from the github repository, you can `git push --force`, which will overwrite history in github. This is rarely a good idea.

122. Is it possible to ``git commit --amend`` for older version by ``git checkout`` ```<hash>``` before?
     - no, not like this since modifying one commit in the past would require to modify all commits that follow
       - what about commit text?
         - same. also this will change hashes. i would do that with an interactive rebase, see below 
     - but you can modify commits in the past with an interactive rebase `git rebase -i` which offers lots of options of deleting commits, reordering commits, editing them or their logs. but note that this will change hashes for all commits that follow. this is a good safety mechanism that we cannot change the past without noticing.    

123. I get error saying "fatal: bad revision '.'" ???
     I have made changes to readme  and staged and commited with message
     and then try to run git revert . on recepe-guacamole clone
      - Git revert needs a commit to revert to. "." is a folder.
      - there is possible confusion between revert and restore which do different things. the former needs a hash, the latter needs a path.

124. What is the difference between git show and git log --oneline? samething?
      - `git show` shows only one commit. If you don't give it a hash, it shows the latest.
      - `git log --oneline` lists all commit messages but only their first line and the beginning of each hash

125. I just recoginzed, that the "old" commits after amend still exist, is there any option to list either all commits in the repo or maybe even those, that are no longer associated with a branch?
     - `git reflog --all` will list also orphaned commits

126. Can a `git reset --hard` be undone? In the video they said that a new commit will be created intern so the "real" history is still there?
     - The files in working directory that have not been committed cannot be restored
     - Changes that have been committed can still be found, but they are not connected to any branch. `git reflog --all` will list the commits.
     - It's a good habit to create a temporary branch before `git reset` to make it easier to find these changes.


127. In undoing-2 `git commit --amend file` throws the message 
     ``` You asked to amend the most recent commit, but doing so would make it empty.  
     You can repeat your command with --allow-empty, or you can remove the commit entirely with "git reset HEAD^".
     ```
     - This is the message you get if the changes you are amending to the commit would undo the commit. Try changing something and amending again.
         - Clear. I do not have to precisely apply a change that corresponds to a revert operation


128. Are there going to be any more exercises today?
	 - Only type-along.

129. If I deleted a file, is it possible to restore it from log history?
     - Yes, for example with `git checkout file_name`
     - You may have to identify the last commit where the file existed and then `git checkout [commit] file_name` where `[commit]` is the commit hash you have identified.  
       You will then need to `git add` the file etc. anew if you want it to exist again in the repo from now on.

130. How can you undo `git reset --hard` ?
    - See question no. 126.
    
131. Does git reset --hard creates a new commit
     - No, it moves a branch to an existing commit.
     - then how git reflog --all keeps track of those resets

132. If i deleted a file in a git repo (from my file explorer), will that show up in my log history in git?
     - You need to delete it from git as well, and then commit the change. You can either `git rm deleted_file` or `git add deleted_file` and then commit.
         - So for the sake of clarity, would you recommend not changing/deleting files from your file explorer?


133. **To the instructor**. Slow down please **and** show more commands from the history at the bottom of the screenful. Catching up is impossible at this point in time. Thx +1
     - thank you

134. slower please: yes, please- stopping few seconds after one script is enough :)
     - thanks for feedback

135. Which is the best platform to use git on? Windows, Linux or Mac? And why?
     - all are fine :-) difficult to say
     - there is also github desktop and other graphical interfaces
     - many editors have plugins and integrations


136. why the `git reset --hard HEAD`? it did not change anything, right? ah, she just explained...
  - Indeed.

137. can you run git graph once more please, at the end, so i can see what changed
    - Before `git reset --hard HEAD~`
```
`4f1200f (HEAD -> main) add some crunchiness`
`e061a75 (tag: 1st-guacamole, origin/main) tweaking the amount of cilantro`
`c767df3 no cilantro please`
```
  - After:
`e061a75 (HEAD -> main, tag: 1st-guacamole, origin/main) tweaking the amount of cilantro`
`c767df3 no cilantro please`
    - So what `git reset --hard HEAD~` do is:
        1. move the HEAD reference to `<hash>`, in this case the parent commit
        2. move the branch reference - tip of the branch - to ````<hash>``
        3. the `--hard` option means clean the staging area and the working directory so that it matches the new HEAD

138. Getting the following error with cherry-pick: error: commit 207091e3818a377c1984554b2284106e28b5fc9a is a merge but no -m option was given.
     - Hm, I guess cherry-pick doesn't work so well with merge commits.  Well, it does, but:
     - the merge commit (usually) has no contents itself, it just brings in two other branches.  So this `-m` option is needed.
     - Can you cherry pick the non-merge commit that has the change?

139. Could you paste where are we in the schedule? Will there be another exercise session?
     - no more exercise session
     - after break we will discuss https://coderefinery.org/git-intro/staging-area/ and https://coderefinery.org/git-intro/level/

140. In some cases this file <<.ingredients.txt.swp>> appears as unstagged. Why does this happen?
    - Usually, these `.*swp` are temporary files created by your editor. It tells "I am modifying this file, don't touch it". I usually gitignore them, i.e. write `*.swp` in `.gitignore`
---
### 1.4 Using the Git staging area
https://coderefinery.org/git-intro/staging-area/


141. Can you change the text of older commits?
     - `git commit --amend` can do that
        - is it only for the last commit? can we do that for previous commits?			- `--amend` only works with the last commit
    
142. Can you add only part of an edit to a file. So if you change two things in 1 file, but you only want to stage part of what you changed for structured commits, is that possible? 
    - Possible with `-p`

143. Can you explain the `-p` options of `git commit` and `git add`? 
    - `-p` means in patches. It allows to be selective about which modifications to include.

144. Did we learn how to combine commits today?
    - Unfortunately not. One way to do it is with `git rebase`, especially with the `-i` (interactive) option.

145. What exactly is staging area?
    - The staging area is a snapshot of what is to be included in the next commit. It is also referred to as the index in the Git documentation.

146. So is it possible to put files that I have already pushed to github (git push origin main) to git ignore? I realize i need to clean up my giuhub to contain only scripts. 
     - If it's already added, it will continue to be tracked (.gitignore won't do anything)
     - You can `git rm --cached` these files to remove them from the current version of the repo (while not deleting them locally).  They will *still* be in the history, but maybe that's OK.
     - Removing from all history is possible, but advanced (search web for instructions).

---
## Feedback, day 2

Today was:
- too fast: ooooooooooooooooooooooooooooooooooo
- too slow: ooooooooo
- just right: ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo
- better than day 1: oooooooo
- better than in-person-only: ooo
- same or worse than in-person-only: o

### One good thing about today
- learn to retrive up to tree step before without the hassle of going through all the history and finding the one hash key needed for that.
- create branch from some historical snapshot
- Understanding git bisect! :+3: 
- git bisect completly blew my mind, I love it +1
- git bisect seem to be THE TOOL I was missing. Knowing it does exist will probably simplify my life a bit +1
- numerous new commands (annotate, bisect, grep) +2
- Analogies +1
- Finally, clarity on `Detached HEAD` state. :smile: +1 :+1:
- The idea of bisect was very interesting.
- Learnt how to undo or reset a commit, which I think would be super helpful for me. +1
- `git bisect` is amazing 
- `git add -p` is cool!
- I liked the longer exercises, and really appreciate having the solutions available for each exercise +1
- very informative and comprehensive. I can't belive how much I learned in this short amount of time. 
- It is very useful, thank you all!
- the archeaology skills are so useful
- good to learn about archeaology tools and reverting commits etc


### One thing to improve for tomorrow
- It was a bit fast paced at the end. Difficult to catch up if you stuchk at some point and needed to catch up by yourself.
- It felt somewhat slow especially in the beginning. The later parts were way better paced.+1     
- It felt very fast at the end. +6
- Some explanation on what is going on with your files (eg. they 'disappear') when you change the index/staging area and the WIP with `add` and `commit` actions.
- some times it good to slow down. Specially during the time we code along.
- Would be great to have some extra exercises to do at home for those who are interested.
    - Check out anything optional/advanced (if any), or the extra pages we didn't go to.
- I think you can be better at letting one speak at once, e.g. less interruption of each other - especially radovan +1
- Please next time put different backgound colours for the terminal, hackmd, etc.
- The pace of the lecture was good but the exercises had a little too much time.
- I take my complaint back for the speed being too fast. Apart from "sometimes", the speed was catchable. Pausing even two seconds after you type your git command would allow us time to catch up, especially today when we were jumping branch to branch. (would feel inclusive for us slow learners), at the same time i think the exercise part where we could do freely, the time was too much. That could be reduced a little. 
- needed a bit more explanation on differences between e.g. reset/revert, restore / restore --staged
 

### Any other comments?
- I wonder if you can stream via Youtube. Because on youtube, viewer can go back a few seconds while streaming if they miss (or stuck at) something to continue following.
    - Good point.  We didn't think about streaming services *that* much.  Do you know if youtube would support the portrait video for streams?  (for playback, it is not great, hard to make it use the full window).
        - not sure. it seems to work fine if streaming from mobile.
    - in my case, this platform twitch was not the ideal one as it asked me to register in order to enable the chat. I have registered for many platforms in the past and really I don want to have another registration unless I know that I will be using it on a regular basis. Thus, YouTube would we a very good option for me
        - No registration on twitch is expected at all.  We don't want anyone to use Twitch chat.
- I would like to review and practice with the material and exercises on the website. Can I do this for some time in the future? How?
    - All the materials are public and you can revisit them later. Recordings will be posted on youtube and you can re-watch them. There are other educational initiatives by CodeRefinery that you might want to follow, for example Research Software Hour https://researchsoftwarehour.github.io/
- I think the archeology exercise was a bit confusing, but this is porbably because it takes some time to get used to the differences between show, grep and annotate
- Today there was quite a lot of "I use this thing now, but we will learn about it tomorrow", which I find suboptional. Perhaps, it might be more clear for learners to avoid mentioning of things that are not explained in the very moment.

- You mentioned that tomorrow the exercises would be group based. I am not on zoom. Usually I do the exercises myself. How can I participate tomorrow?
    - We realize this and will set up something for you.
    - ... or find some friends to join?!
Really hope you would set something up. 
    - Yes we will set up an exercise repository for everybody also live stream watchers so please be there. We will post it in tomorrow's hackmd.
Thanks!
- Maybe it has been said before. Will the recordings be online always? on twitch?
    - yes, on twitch for 14 days, but also youtube: https://coderefinery.org/lessons/#video-recordings (contains link to youtube channel)
        - also 21 days on youtube?
          - on youtube "forever" 👍
