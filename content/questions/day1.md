+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 1

## Icebreaker

I have attended a livestream workshop before:
- yes: ooooooooooooooo
- no:  oooooooooooooooooooooooooooooooooooooooooooooooooooopoooooooooooooooooooooo

What is your prefered programming language and what do you like most about it?

- R easy to learn and great for visualization, also basic linux but is it called a language?
- Python +1
- python: low barrier-to-entry, many resources
- python and R (STATA forced by my supervisor :D). Python for development aspect and implementation as well as spatial analysis. R for the statistics and econometrics STATA is for econometrics but just because I need my supervisor needs to review my methods.
- Python - FOSS & versatile
- Python
- Python and Rust: Rust for the tooling and the type system, Python for quick prototyping
- Python: Constantly evolves and gets improved by the community
- Matlab (simulink)
- Python: it's versatile and easy to learn.
- Virtual studio 
- Java: I discovered a great software written in this language
- Python(versatailty) and fortran(first language) 
- Matlab (ease of use), Python (openness), C++ (speed)
- Python
- ...Fortran and Python, very good for different purposes(Numerical calculations and python for data analysis)
- Python: versatile, easy to learn, used more and more in academia
- Matlab (and Pyhon): very well documented
- MATLAB : widespread in the scientific/academic community
- Fortran - first love
- C# I kind of like the structure, I am not too sure, why...
- I kind of like the structure, I am not too sure, why...
- Python, because there are a lot of helpful resources to be found
- R - great for data analysis and visualisation
- Python - simple learning curve
- Python - being very intuitive, R for anything correlation analyses and plotting
- Python 
- PYTHON
- My favourite language is the one that overcomes all limitations of the languages I have been using so far :-)
- Python and Fortran
- Learning Python so that I can use Google Earth Engine! Have a little familiarity with JavaScript too
- Python, C++
- Python, C++, I like the versatility of C++ and the easiness to learn of Python
- Python
- Julia. It's high level yet fast!
- Python - good for data analysis
- Python
- Fortran, Java or any typed language
- R - great for working with tabular data and keeping it tidy
- Python because it's the only language I can remember ((((((((((most of)))))))))) the syntax for,,,,,,,,,, without having to look much up in the docs
- Python: easy to learn, open source and many users. 
- Python ( open source) - 
- R: it's the one I use the most
- R and Python 
- Python:open source, docuentation
- Python: simple
- Python
- Python: rapid development
- Python for code readability
- Python
- Matlab
- I only know python and fortran. Fortran is fast, python is simpler. Mathematica is a black box.
- Python and Mathematica sometimes....
- Python, similar to matlab (what I used before), open source, (often) good documentation. 
- Python, versatile!
- IDL, Python, R
- Julia, easy to write and very fast + great community
- Python and Julia
- Python and Matlab: Easy and fast
- R: very good for graphics, visualisation, and statistics
- Python and FORTRAN.
- Python
- Python
- Python
- Python
- Python
- Python
- Matlab
- Python
- Python


## Try me


- This is so cool! Question: do you recommend switching in and out of edit/visualize mode to when not typing?
     - Yes, better view only mode when not typing to not overload the server
          - Thanks!!
- How cool is it to see 70+ people edit the same file form 0 to 10? 100!
    - Cool :)
    - interesting

## 0. [Workshop introduction](https://github.com/coderefinery/workshop-intro/blob/master/livestream.md)

- The zoom link says "the host has another meeting in progress". Did I join the wrong link or am I supposed to wait? 
    - I can join via the link provided in the invitation mail. 
        - I was also able to join using the link
        - I think right now it's only Twitch?
            - The Zoom rooms for exercises are open, but the Course information is streamed via twitch only
- I registered weeks ago but didn't receive a zoom link. Not one that works at least. Could that be a mistake or was I only approved for livestream?
  - RB: ca. half the participants watch only via livestream. hopefully this was not a mistake. we were a bit limited by the number of exercise leads. 
  - I registered for everything but didn't get the zoom link. They explained why in the email. 

- Can we have a **link for the introduction page** you are showing now?
    - It's at the top of this hackMD (https://coderefinery.github.io/2022-03-22-workshop/)
    - Added a workshop intro section with the link.
    - For the materials follow the links at the schedule https://coderefinery.github.io/2022-03-22-workshop/#schedule



## 1. [Git-intro](https://coderefinery.github.io/git-intro/)

1. What is the difference between Git and Gitlab?
    - Gitlab is an online service that uses Git
    - Git is a version control software you can run anywhere. Gitlab is cloud storage for code and uses Git to track it.
    - GitLab is an alternative to GitHub. Both are web services that store Git repositories together with discussions, issue tracking, forum, automated testing, and more.
  
2. Issue: Portrait view not taking advantage of screen
    - it is intended to keep screen space for the participants' terminal
    - setting twitch in **theater mode** the screen scales nicely and you can have it on half screen while live coding/watching hackmd /etc next to it 
    - You might need to hide chat before going to theater (or some) mode.
        - How do you do that?
            - on the lower right of the twitch stream, there is a button "theatre mode"
            - alt+T
            - there is an arrow on top right to hide chat (or collapse)
                - worked, thanks!
                
3. I am a bit lost. So right now are we also supposed to be trying the exercise or will be have some time later for that? I am not on zoom, only livestream.
    - watching only, exercise time will be very clear

4. Twitch blurs from time to time here, I tried different computers. Are only us? We have a dedicated, wired computer :-( May be the network, yes.
   - That happens when your internet connection is slow, or something else is taking bandwith (maybe Zoom). 

5. Do we have any hastag on Twitter or LinkedIn so we can share our expereince with this workshop?
    - Not yet, any suggestions?
    - Some ideas: #CodeRefinery22, #CodeRefineryGit, #WorkshopCodeRefinery :)I'm not so good at this maybe others can have more creative suggestions.
    - Let's use #CodeRefinery22

6. What are the differences between Github and Gitlab  
    - GitHub, GitLab and Bitbucket do mostly the same things. The biggest practical difference is the interface. Some things have different names (like "pull request" on GitHub vs "merge request" on GitLab)
    - GitLab is open source, so anyone can run their own GitLab server. Many research institutions have their own service.
    - GitHub is the most known and has a lot of code on it, so code published there is a bit more findable
    
7. What do you mean by "snapshot"? Is it something like commit?
   - Essentially a preview of the commit. But snapshot might be a more "general" term, while commit is more git-speach 
   - you can also think of it as a state of the software at a given time instant

8. Do we need to open the example image repos now?
    - no, this is just for demonstration

9. How do you make a link to a code portion that was just showed?
    - you can make a link to the specific ID (hash) of a given snapshot/commit 
    - hovering mouse around the line numbers lets you select the lines/rows.

10. Is there a way to see what part of a file were altered with what commit from the command line? Or is this a github utility?
    - yes, you can do it from the command line, it will be demoed soon :)
    - `git annotate <file>` - we practice this on day 2

11. How did you activate the side-to-side view in https://github.com/achael/eht-imaging/blame/main/ehtim/imaging/starwarps.py? If I start from another file, say
    - You need to click on "blame" on the upper right side of the file. Check out https://github.com/achael/eht-imaging/blob/main/ehtim/imaging/starwarps.py
      - side note: "blame" is an unfortunate name for historical reasons. A better name would have been "annotate" 

12. Do we have any nice tutorial for shell script and linux?
    - crash course: https://scicomp.aalto.fi/scicomp/shell/
    - or software carpentry: https://swcarpentry.github.io/shell-novice/
    - longer: https://aaltoscicomp.github.io/linux-shell/

13. Is the terminal the Git Bash ? Or how do I open terminal on windows?
    - On Windows we use Git Bash, unless you are used to something else.
    - On other systems (Mac, Linux), it's different.
    
14. Should we use the conda env or just "our own" shell?
    - We'll need the conda env from week 2 only.

15. So when there's a merge conflict and git asks me to commit first, it's to avoid having the code overwritten without snapshot, right?
    - When there is a merge conflict, git asks you to fix it and then commit the fixed files.
        - And it wants to make sure that you checked what you changed to fix it and you actually "commit" to use those changes
    - Git asks you to merge because there are two versions of the  code and it cannot figure out what to do on it's own. 
  
16. How do I get this "on master" after the directory on the command line? I assume there is an easy way to do it?
    - sorry, this is a customization which I only explained much later. I use this: https://coderefinery.github.io/git-intro/customizing/

### Poll: What is your editor?

- vim: ooooooooooooooooooooooooooooooooooooooooooooooooo
- emacs: oooooooo
- vscode: ooooooooooooooooooooooooooooooooooooooooo
- nano:ooooooooooooooooooooo0oooo0ooooooooo
- atom: Oooooooo
- spyder: o
- notepad++
- notepad: o
- gedit: oo
- eclipse: onano
- notepad++:oo
- Sublimetext: oo
- Jupyter notebook: o
- PyCharm: o,o vscode
- Editpad pro: o
- pycharm: o


::avocado:: Love guacamole! :)

I didn't notice the keyboard sound but when it was mentioned it started bothering me lol
   - oops yes I should not have mentioned this

Would love to meet the fellow emacs enthusiasts :)

### Questions continue here:

16. How do you know which editor is  configured? I am writing in git bash terminal, but I have no clue whether that involves an editor
    - `git config --list` and check core.editor. Or `git config core.editor`.
        - Ah nano it is, thanks.
    -  It is possible to change the editor with `git config --global core.editor "nano", for example`. More info: https://coderefinery.github.io/git-intro/aliases/

17. Sorry, maybe some one asked this already, how can you get this page in github? https://github.com/achael/eht-imaging/blame/main/ehtim/imaging/starwarps.py
    - No problem
    - Is the URL an answer? Not sure I understand the question.
    - you mean the 'blame'?
    -yes! 
        - See above #11

18. Why is the core.editor relevant? Why does is matter what text editor you use, if in the end only the code and language matter?
    - It doesn't matter for git.  it's a convenience for you, what will git start when it needs to?
        - This is e.g. used to modify commit messages, or alter things when using git commands. It's not about how you write your code.
        - As far as I know it only appears when editing commit message or doing an interactive rebase (we haven't shown this).

19. What is the difference between git stage and git add?
    - Tip: we are working with `git status` not `git stage`
        - Yes, I understand that
    - `git stage` is synonym for `git add` (try `git stage --help`)
        - Thanks!
    - `git stage` is perhaps newer and more descriptive. But we are a bit careful not to advertize new options because some participants use older Git versions.

20. how do you go back from nano to git bash?
    - Ctrl + X to  save, then press Y to confirm and finally enter
        - hm doesnt work
    - Check the bottom of the editor, you may be in the middle of a different command. If so, it lists command keys or asks a question.
    - Try Ctrl + O for Write Out, which means Save, follow the instruction and  afterwards hit Ctrl + X for Exit.

21. I get a warning `warning: LF will be replaced by CRLF in ingredients.txt. The file will have its original line endings in your working directory` I assume that that is not a problem?
    - For this course's purposes, not a problem.
        - For what purposes would it be a problem?
            - This is almost always what you want. If someone has set up their git to use CRLF line endings, they would not be able to read your code properly. In practice, everyone uses LF
        - https://en.wikipedia.org/wiki/Newline for generalities

22. How do I remove files/changes from the staging area?
    - We'll get to this more later, is that ok?
        -Yes, thanks. 

23. I am on  a windows machine. Is there a way to surpress the "LF will be replaced by CRLF..."-mesage?
       - Run `git config --global core.safecrlf false`. This turns of the message, but does not change what git does

24. What is the createmode 10644?
    - Internals about the file "regular file, user readable/writeable"
        - So similar as the ls -alh info from a file in the shell?

25. the `git help commit` opened a new browser with git commands. was it the same for you ?
    - That probably depends on the setup of your system. git help opens a manual page, and your system might be configured to open those in a browser. On other systems it might simply open the contents within the same window
    
27. Do we do the exercieses in the zoom group?
    - if you're on Zoom then yes, please join your exercise room! (press the breakout room button in the bottom toolbar on Zoom)
    - If on Twitch only, please do them on your own and ask questions in the HackMD.


:::info 
**Exercise until xx:11, then break until xx:21**
:::

:::info
https://coderefinery.github.io/git-intro/basics/#exercise-record-changes
Try to do most of the exercise

We'll continue with Git history after the break.
If you are already familiar with Git you may continue until the end of the Basics episode.
:::

 27. Is the workshop recorded by the way ? to be rewatched later on
     - Yes, should be posted by this evening (anyone want to help do that?).  Twitch saves for 14 days (immediately available)

28. What is the difference between using `git diff` after staging and after committing?
    - Git diff compares to staged files by default, so there is not difference. There is also a command to compare to committed files.

29. what does the index in git diff tell us? For example I see this when I do git diff "index 6a8b2af..f7dd63a 100644"!
    - It tells you what you are comparing to what, but in a very cryptic way :) The code like "6a8b2af" refer to specific commits in git history.
    - each commit has a unique identifier (40-character string) and Git here shows the beginning of each and you can compare them if you know the identifiers. Later we will see that there are also other ways to refer to commits.

30. when I do git add in Git Bash I get an error message that says "warning: LF will be replaced by CRLF in ingredients.txt. The file will have its original line endings in your working directory" It seems to work anyway, but is that error bad? can I make it stop? Thank you!!
    - This is not a problem, it's what we want git to do.
    - You can disable the message by running `git config --global core.safecrlf false`. This turns of the message, but does not change what git does.

31. Why does this "recipe" directory not show up in my github, when checked on browser? What should I do to make that happen (for future projects)?
       - We will come to this. For now, the directory is just on your computer.
       - In day 2 we will push the repository to GitHub and only then the changes will show up there.

32. Why do we have two stages of git add and then git commit?
    - Sometimes it is helpful to get a view of what is going on before committing.  We'll see more of this later.  You can also bypass this and commit directly when it's not needed.
    - You can commit directly with `git commit <file>`. But you need to add files at least once, the first time they get added to Git.

33. what these codes which appears after the git diff menas? how we can read these? I mean these code "@@ -1,3 +1,4 @@". I was thinking whether we code use it at some point for tracking the unwanted changes?
    - Something about line numbers in old and new files (I'm actually not fully sure...)
    - Found [this](https://en.wikipedia.org/wiki/Diff#Unified_format) online 

34. How can we cancel a commit or git add, if we did something mistakely, can we go some steps back to un-add, or un-commit?
    - Yes, more on this later.
    - Easy way to cancel a commit before saving the commit message is to use an empty message. Then the commit does not get saved.
    - We'll learn about unstaging and fixing mistakes.

35. xtra-room1: How can we set `git difftool --tool=opendiff` on MacOs, It requires Xcode , but it is not finding it somehow ? error: tool 'opendiff' requires, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
    - we will find a macOS expert who can help us. the good thing is that the difftool is not required for the rest of the course but good to know it exists to compare larger changes that are easier to see side by side.
    - I had this error yesterday and after installing XCode from the app store, it worked. I think the XCode command line tools aren't enough, you need to actually have XCode the app.

37. Exercise Issue: I've managed to edit both ingredients and instructions, stage and commit commit ingredints, but my instructions doesn't appear on my git status. Why?
       -  If it is committed and there are no changes from what is committed, `git status` appears empty (=clean).
       -  oh, even if I haven't commited?
           -  no.
       -  `git status` only outputs uncommited or unstaged changes.

37. GU-team : could we get help with windows?
    - relayed to expert helpers. somebody will be there soon
    - I hope this worked out. If not, can you write the problem at the end of the questions document and we try to help asynchronously or tomorrow?

38. Is there a possibility to lose the whole directory and all changes in github, for eg if we delete the directory in our computer, or ..if we did something stupid?
       - If you delete the entire directory, even changes committed to git are removed (git saves things in a hidden directory called .git in the source directory.)
       - But if the repository is on GitHub or GitLab or similar, then it is also backed up there. Then if I accidentally delete it locally on my drive, I can still recover from there.

40. Is github only for version control of codes or could we save our data, results, figure, like the whole project?
    - In principal you can have git to follow any files. I think it is not recommended to store (large) datasets in git though – at least not in GitHub or the cloud
    - Though often small files that support other stuff are used in git.
    - But there are solutions to also version control large data files such as git-annex or git LFS (large file storage).
    - GitHub is not a good place for sensitive data such as patient data, for this you need secure storage.

41. Is there a way you can use git difftool to open two versions in split vim windows?
    - Unsure but surely the a web search will tell you how to
    - there is vimdiff and you can tell git to use vimdiff as difftool

42. Do we run out of space in github?
    - There is some quota, it's not too tiny though.
    - Above 100 MB it starts to be too large. Code repositories are typically much smaller.

43. Are we supposed to be only one learner in Team-2 group? 
    - No, bu possibly people who signed up did not show up.
    - RB: there were more people planned. Normally I tried to put 5-6 people into a group. If nobody shows up, I recommend to join another group with too few learners. Sorry for this but this is what sometimes happens.
    
44. When (what time) will we continue?
    - Shared on stream/above in hackmd
    - it is "xx:21"?
    - Yes.

45. Suppose I've added and commited file, but now I'd like to ignore it, but keep it locally. E.g. it might be some big output file I don't want to track.
    - We'll show a way to do it with ``.gitignore`.
    - Sure `.gitignore` is the correct way, but suppose I've already commited that. `git rm` is a way, but it deletes it locally as well...
    - I would copy to file somewhere, then `git rm`, then add it to `.gitignore`, then copy it back. Maybe there is a more elegant way to solve this. **Note that it will stay in the history**.
        - +1 that solves it (not elegant, but working)
    - If you first commit all changes, then  update your `.gitignore` and then run `git rm  -r --cached .` it will 'untrack' all files. (https://sigalambigha.home.blog/2020/03/11/how-to-refresh-gitignore/)
    
46. Hi, I am getting the syntax error: 
    `$ git difftool --tool=meld <hash>`
    bash: syntax error near unexpected token `newline`   
    - `<hash>` needs to be replaced with the Git commit hash
    - same with me. what do you mean by the git version?
      - alrighty! Is this the hash? 1412989c6d3c32dbdcfe8e985c1e73144ee1e5ec
        - where did you get the hash from? There are many hashes. Three in my case. and it seems they are unique for each user.
        - yes
    - The hash commits are listed with `git log --oneline`, for example. It's the first column of the output.
      - Okay now I recieve this below : even though I made the command git config -- glbal mergtool.mel etc. 
      - The diff tool meld is not available as 'C:\Program Files (x86)\Meld\Meld.exe' 
        fatal: external diff died, stopping at ingredients.txt
        - Maybe this could help you: https://stackoverflow.com/questions/54389844/unable-to-set-meld-as-a-diff-tool-in-git-bash

47. What comes next after xx:21 exercises further or lectures?
    - 10 min lecture/discussion and then we go to branching where we start with 10 min lecture/discussion and then another 15 min exercise 
    - we will restart here: https://coderefinery.github.io/git-intro/basics/#git-history-and-log and discuss git log, commit messages and when to use gitignore.


48. When trying the git difftool --tool=meld, my system says that the diff tool meld is not available as 'meld'. What should be done here to fix this?
    - See https://coderefinery.github.io/installation/difftools/ 
    - I guess meld isn't installed.  I would ignore that part, it won't be important right now.

49. [feedback] At https://coderefinery.github.io/git-intro/basics/, you don't really want to use "my recent changes" as example commit message :D
    - good point :-) thanks, we will discuss this

:::info
- I am done: ooooooooooooooopoooooooooooo
- I want more time: o
- I am not trying: o
:::


50. git diff returns something not easily readable, and leads me to a page I can't seem to get out 
    ```
    ESC[1mdiff --git a/ingredients.txt b/ingredients.txtESC[m
    ESC[1mindex e7fa4e2..3cf588f 100644ESC[m
    ESC[1m--- a/ingredients.txtESC[m
    ESC[1m+++ b/ingredients.txtESC[m
    ESC[36m@@ -1,3 +1,4 @@ESC[m
     -2 avocadosESC[m
    ESC[32m+ESC[mESC[32m-1/2 onionsESC[m
     -1 limeESC[m
     -2 tsp saltESC[m
    ESC[1mdiff --git a/instructions.txt b/instructions.txtESC[m
    ESC[1mindex 2e1e784..2d9cd0e 100644ESC[m
    ESC[1m--- a/instructions.txtESC[m
    ESC[1m+++ b/instructions.txtESC[m
    ESC[36m@@ -3,4 +3,4 @@ESC[m
     -squeeze limeESC[m
     -add saltESC[m
     -and mix wellESC[m
    ESC[31m-ESC[m
    ESC[32m+ESC[mESC[32m-enjoy !ESC[m
    lines 1-19/19 (END)
    ```
    
    - does `q` help?
        - oh yes thanks
    - This is something about color codes and the terminal.  I will look up how to disable
    - `git config --global color.ui false` - turns off for this computer/git install.
    - I think `git config --global --add color.ui auto` might work too - it should keep the coloring of git output in the shell, but disable it when the output is opened in another progream (e.g. in `less`, as it was in the case above)
    - True.  maybe don't do that yet, unless it is completely broken in every shell


51. Had diffuculties with typing the commit message after command `git commit` 
    - Helped when I changed the editor to nano
        - `git commit -m "This is the commit message"` might make it easier to put in commit messages, without needing an editor.
            - but good to configure an editor if you need multi-line commit messages (but you can do them also with -m)

52. Why do we not have to `git add` but go straight to `git commit` after renaming a file?
    - if you used `git mv` to rename the file, it essentially combines `mv` and `git add`, and in particular it will tell git, that those files have a connection, which it might otherwise not detect
    - (Questioner: Didn't think about it when using `git mv`, thought I just typed `mv` -Thanks)

53. Unique indentifiers: long or short? Are they equivalent?
    - The short identifier is essentially equivalent. It's actually the first few characters of the long one
        - But, due to being shorter, the chances are a bit higher that you get an accidential collision, that's why internally git uses the longer ones, and if you happen to encounter a duplicate hash, you will have to use the long version too. 

54. When adding the momment with git commit -m I get the error : "
    ```  Please tell me who you are.
    Run

      git config --global user.email "you@example.com"
      git config --global user.name "Your Name"

    to set your account's default identity.
    Omit --global to set the identity only in this repository.
    ```
    - You have not set your name and email yet. You can do so by running the commands in the message. Git adds your name and email to every commit. 
        - I have run the options but it doens't work
        - Did it print any errors when you ran the commands?
        - It says (base), but when I add with git status it shows nothing was added
        - I don't quite understand. Did you run the "git config" commands in the message above?
        - Yes and they show no error message but nothing happens 
        - They don't print any output if everything worked. Now you can try `git add filename` (if you did not already) and `git commit`.

55. How do you have command suggestions in terminal?
    - This might be OS specific, but e.g. on Linux systems you can get suggestions by tab.
    - the instructor uses a special shell called "fish" that shows some of these things.

56. Please talk about meld.
    - We can see if we have time later, it is a minor point for now.
    - I tried to start it in Windows cmd but I guess I forgot to install something? 
      ```
      "C:\Users\kalle\coderef\recipe>git difftool --tool=meld ebe33e8
      `
      Viewing (1/1): 'ingredients.txt'
      Launch 'meld' [Y/n]? Y
      The diff tool meld is not available as     'meld'
      fatal: external diff died, stopping at     ingredients.txt
      C:\Users\kalle\coderef\recipe>"
      ```

57. Is there easy way to get bash tab-completition for commit identifiers? I.e. commit "571be6fe29e84b...", but I get no completition when typing 571 (tab)
    - It can for branches/tags, but seems not hashes.  There are so many different hashes it might not be that useful to implement.
    - Positive twist. It could also mean that Git is happy with `571` because the shortcut is already a unique identfier for your repository
    - Git matches unique prefixes.  You don't need a whole hash, just the first part (= enough to make it unique, same you would tab complete)
    - Seems like git internally does it, when you run a command with a sub-hash, but it doesn't offer auto-completion (too much complexity for large repositories), So if you run something with a hash 12345 it will internallysearch for a unique hash that is matched by 12345, but will (probably) fail if there are multiple.

58. In a directory (eg. `top`), I add an `.init` git repo. Then I create a subdirectory `top/sub`. Can I create a git repo (with `.init`) here as well? What should I consider?
    - If you want to add a git repository inside another, you should use git submodules (https://git-scm.com/book/en/v2/Git-Tools-Submodules). I would only recommend this if you are comfortable with git already.
    - Without submodules, this will cause the git repository in `top` to track the repository in `top/sub`. This will make things complicated.


59. Since we need to add manually a file to git by "git add", do we really have to tell to git what to ignor?
    - It makes `git status` appear more useful (like not forgetting to add things)
    - Yes, since sometimes you want to use wildcards like git add *.py or similar, or whole directories git add newCode/* and those might e.g. contain .pyc files which you don't want to add, so having*.pyc in gitignore makes sure, that you never accidentially add a .pyc file.

60. Where do you place the `.gitignore` file for it to be recognized by Git?
    - In the main folder of the project (but it also works in any other folder,  Ithink)
    - According to the material if you put it in a subfolder it affects there


61. Is there something like ! gitignore, so specify all files that should be considered? Like in the example that was mentioned using only *.tex and *.bib files?
    - I don't quite understand this question  
        - I mean like "not gitignore", the opposite of gitignore. The thing is that latex produces sooo many additional files and i do not want to add them all in the gitignore
        - You can write `.gitignore` (!!! This might be bad practice. What if something (what you did not originally expect) appears in the repo untracked -- you want to avoid it -- you clearly know, what you DO NOT want, but can't say in advance, what everything will appear in the project -- from personal experience with LaTeX projects, it might be a Makefile -- you want to keep them in git)
          ```
          *
          !*.tex
          !*.bib
          !*.sty
          !*.cls
          ```
            -> that's clever, exactly what I wanted. but yeah, probably bad practice...
    - `gitignore` doesn't prevent adding files: you could also ignore`*` and then explicitely add what you want.  but `git status` won't help you remember them in that case...
    - `git add .` adds everything recursively, is that what you want? (or `git add -A` does the same IIRC)

:::info
### Test your understanding:

- 1:
- 2:
- 3: ooooooooooooooopooooooooooooooooooooo
- 4:
:::


62. I added a binary by mistake - can I remove it?
    - If not committed yet, `git rm`.  If it has been committed, that is "editing the history" and can we talk about that later?

63. can we define restrictions or pattern for adding files? for instance:
    git add *.py    
    - yes, wildcards work perfectly fine
    
64. Is it possible to gitignore the .gitignore file? Have had trouble with this before
    - Yes (but normally it would be committed)
    - For "local only ignore" there is `.git/info/excludes` which works the same way
`
65. What is the .gitignore? A folder or text file? I understand what it does: tell git what to ignore. But what is it? and how do I build it? Given I have a folder of data that I don't want on git, do I make a textfile and write "data/" in it?
    - file, git reads each line and uses those patterns as information.
    - It's a plain text file in the main folder.

66. how to rename a file?
    - `git mv oldname newname` and, if you are not using a tool that supports git for your folder management, using `git mv` instead of renaming manually allows you to keep the history of the file (i.e. git will then know, that this file was named something different before)

67. Why don't I find a .gitignore file in my directory? I tried using ls . and only find ls ./git
    - by default, `ls` will not show hidden files. files whose name begins with `.` are hidden. To list also these hidden files, try `ls -a`
        - Also, a new git repository does not have a .gitignore. It has to be created by yourself.

68. Just want to share this https://sigalambigha.home.blog/2020/03/11/how-to-refresh-gitignore/. I often struggle with trying to add files to the .gitignore that were previously tracked. This method solves that :) 
    - thanks

---

## [Branching and merging](https://coderefinery.github.io/git-intro/branches/)

For people too young to know where the term "HEAD" comes from, it is inspired by tape recorders: https://en.wikipedia.org/wiki/Tape_recorder#/media/File:Akai_GX_635D_-_edit.jpg


1. can you increase the font size in the terminal?
      - thanks, I will mention
      - thank you

2. Is this alias configuration permament? What if I want it back to the default options?
    - I would `git config --global --edit` (user-wide) or `git config --edit` (this repo) and remove it (this can be used to view and adjust any configuration)
    - Or edit the correct `.gitconfig` file directly.
    

3. What does the link between C1 and X1 commits mean? In the branch graph
    - X1 is the next commit after c1 on the same branch, but it's a special "merge commit" where changes from the main (green) branch is merged into the side (purple) branch
        - Thanks!


4. this gave me an error: "switch `l' expects a numerical value"`
   `git config --global alias.graph "log --all --graph --decorate --oneline"`
    - It looks like git thinks you wrote `-l`. Can you paste the command you used?
        -  git log -all --graph --decorate --oneline
        -  You need a second "-" before "all"
        - ah i see, sorry
          - many command line tools have the convention that one-character options have one dash and longer ones have two dashes: `-l` and `--long` as an example.

5. can we visualize the branches?
    - the `git graph` alias command which is configured above will show a simple tree structure which is quite useful 
    - after pushing a repository to GitHub (or other similar services) it will also be possible to see the branch tree in the browser
        - for this go to insights and network

6. Is this alias configuration global to all my repositories?
   - in this case we defined it global but you can also define them per-repo only. I recommend to have this one global (I don't have any per-repo aliases)

7. why it shows 'git: 'graph' is not a git command. See 'git --help'.'
   - you need to define the alias first: `git config --global alias.graph "log --all --graph --decorate --oneline"``

8. In the example, the master is still on m4, right?
    - no master/main has moved forward by merging the side branches! f x2
    - sure? it seems like x2 is a branch and x3 looks like c2 merged into the branch o
        - Admittedly, the color scheme does not look nice, but x2 is the b-branch merged into the main branch, and (at least from the graph) I would assume, that main is now at x3
          - ah yes, I see!

9. Are there certain aliases you can't use because they are 'git specific' words?
    - Existing git commands are reserved (or should not be used even if they are not).
    - actually i just tested to overwrite `git add` by `git config  alias.add "log --all --graph --decorate --oneline"` but it doesn't error and it doesn't change what `git add` does
        - OK, not the best behaviour from git, but not the worst either :smile:

10. why did she write "git branch experiment master" and not just "git brnach experiment"?
    - to explicitly create the branch from the master branch (default is to branch out from current branch)

11. is the name 'HEAD' just indicating the current branch?
    - yes. HEAD always points to what is in your working directory.
    - current position. branch is a label pointing to a commit, HEAD is a pointer pointing to a branch.


12. What does the following error message mean? 
    ```
    $ git add ingredients.txt
    warning: LF will be replaced by CRLF in ingredients.txt.
    The file will have its original line endings in your working directory
    ```
    - This is not a problem. It's pointing out that git uses different encoding for line endings than Windows usually does. 
    - You can disable the warning with `git config --global core.safecrlf false`
    
13. It was a bit too fast (her saying and typing), we need to listen and also follow steps, need few seconds more in each step.
    - I will relay

14. How do we delete a branch?
    - `git branch -d branch_name`
    - git branch -d or --delete
    - note that Git will complain if you try to delete a branch that has not been merged to any other branch (to prevent you from accidentally deleting work). But you can insist with `git branch -D` (uppercase D).

15. It might be useful to create a log of things changed in our general git setup (eg. git global alias) so that we can reset all the right things after the workshop. This is in case we already have a setup for git (or other things).
    - You could also alternatively skip the --global command and then it will do the changes in you local config only. For example git config alias.graph "log -- --graph --decorate --online" will create the alias in youre local git repository and will then not work in other projects you have.


### Exercise until xx:15, then break until xx:25
:::info
https://coderefinery.github.io/git-intro/branches/#exercise-create-and-commit-to-branches
Try to do most, there are also optional exercises at the end
Stop at [merging branches](https://coderefinery.github.io/git-intro/branches/#merging-branches) unless you know how to merge already.
o
I am:
- done: ooooooooooooooooooooooooooooooooooooooooooooooo
- need more time: o
- not trying: oo
:::


16. Do I need to swith to master first or can I just run `git branch less-salt master` from the experiment-branch?
    - Either method should work
    - the command will create the new branch from master so in this case you don't need to switch to master first
    - if you leave out the "master" it will create the new branch from right where you are, in this case check with `git status` or `git branch` or `git graph`
      Just remember to checkout to the branch where you want to have the following commits.

17. Will you cover some best practice tips for when to branch / merge etc.? I imagine it is easy to run into a situation where the merger becomes very messy.
    - we will discuss conflicts later and how to avoid them and also motivate to create branches for one purpose only. in short: don't put unrelated things into one branch.


18. What happens if I commit to the wrong branch and want to undo this?
    - One option is to rename the branches (assuming you they are the same except for the one commit). To rename, use `git branch -m old_name new_name`
    - If there are more differences between the branches, this gets complicated. Maybe 
        1. copy the changes to a safe place
        2. revert the commit
        3. checkout the other branch
        4. apply the changes
        5. commit
    
    
19. Let us assume that we have already two branches. And if we are already in second branch, when branching from an firstbranch, we use "git branch thirdbranch firstbranch". Since we make it clear to from which branch we want to branch, Why should we change to the firstbranch?
    - in this case you don't need to switch. this was just a safeguard because in the past participants created commits from wrong branch. see also question 16.


20. Lets say I messed up and I want to restart with the new branches...how can I delete the branch called less-salt for exemple ?
    - see above (#14) `git branch -d less-salt`
      - Thanks, it was not working because I was still on the branch ... I had shift to an other one
        - true, you can't delete the branch you are on (which makes soe sense, if you think about sitting in the "git tree" :smile:)
           - it would hurt
               - yes I aggree


21. If I modify a file, do I need to be in the branch before modifying, or can I just change branch before commiting ?
    - I would always only work on the branch (i.e. having it checked out)  where I want to modify things. Mainly because files can differ between branches. If youo for example modify a file which is different on the two branches git won't allow you to switch because of those differences.


22. What is the best way to undo a commit?
    - We'll do undoing tomorrow. "Best" option dependes whether you have already shared the commit(s) you want to undo with others or not. In short, `git reset` if not yet shared, `git revert` if already shared.
    - but also you can already have a look in https://coderefinery.github.io/git-intro/recovering/


23. After `git merge experiment` I get a much simpler graph than the [web page](https://coderefinery.github.io/git-intro/branches/#merging-branches).
    ```bash=
    git graph 
    * 0a14973 (less-salt) reduce amount of salt
    | * ba7da14 (HEAD -> master, experiment) maybe little bit less cilantro
    | * 65ea3a5 let us try some cilantro
    |/  
    * 503b183 Add final instruction
    * 54622a6 add half an onion
    * b892eb0 adding ingredients and instructions
 
    ```
    - It did do a fast fwd:
    ```bash 
        git merge experiment
        Updating 503b183..ba7da14
        Fast-forward
         ingredients.txt | 1 +
         1 file changed, 1 insertion(+)
    ```
    - The graph shows two branches that have not been merged, less-slat and master.
        - I understand this. The point is that the code in the web page may not be correct, unless I have skipped something of course 
    - Are you comparing to this?
    ```bash
     $ git graph
 
     *   4f00317 (HEAD -> master) Merge branch 'less-salt'
     |\
     | * bf59be6 reduce amount of salt
     * |   c43b24c Merge branch 'experiment'
     |\ \
     | * | 6feb49d maybe little bit less cilantro
     | * | 7cf6d8c let us try with some cilantro
     | |/
     * | 40fbb90 draft a readme
     |/
     * dd4472c we should not forget to enjoy
     * 2bb9bb4 add half an onion
     * 2d79e7e adding ingredients and instructions
    ```
    
    -  yes I am
        - In that one, "experiment" has already been merged. In your output, experiment has not been merged. Did you intend to do that?
        - Thanks for holding on. I simply did `git merge experiment` following the  web page
        - Sorry, the one that is not merged is "less-salt". In the example, both are merged.
        - OK then there is a mismatch in the website
            - It get's merged a bit above the example output. We should add numbers to the examples to make it easier to refer to them.
            - I can explain myself the difference now. I move on. Thanks
            - Breaking news. I found a mistake on my part looking back at my `history`; I had not committed the README.md file in the master branch. This can explain the difference. 


24. If you works in the terminal, you see the files that are in your current branch. But if you navigate to the folder in a graphical tool like nautilus, what files do you see?
    - You will see he same files as those in the terminal. 
        - hm, a person in my group said they saw the master files. 
          - then I would assume, that thy did not change the branch in the terminal, OR that nautilus does nto automatically refresh its view.
          
25. When you "ls", depending on the branch that is checked out, you don't see the same files ! That is so weird, so are the different copies of the files (different versions from different branch) stored hidden somewhere in the folder ? It is as if git was modifying the files in the folder everytime you check out
    - yes, the folder contains only those files that are in the branch that is currently active. Git hosts an internal database of these files/folders and essentially replaces what is seen/listed. 
  
  
26. If I have a project with many files on my local computer and want to add them all to a new repository, how would I do that quickly without adding each one separately? How does this work with many directories?
    - `git add -A` should add everything in the folder and all subfolders (iirc). But in this instance, I would recommend first setting up a .gitignore file that lists temporary or compiled files (like .pyc for python projects, .o for C, .class for java, .asv for matlab etc ) as those are normally not the files you want to keep under version control, as they are directly reproducible by the source files 
        - Or use https://sigalambigha.home.blog/2020/03/11/how-to-refresh-gitignore/ to update the gitignore later
            - The issue with this is that the unintended files will stay in the repo. Guit will no longer track them, but they will be in the history and thus increase your project size without adding value.
                - By using the `--cached` option with `git rm -r` you remove the files from the repo, but keep them locally, so if you then commit everything again, you will have removed all the things in the gitignore from the repo as well
                    - true. But you still keep the history for those files.
     - I use `git add .` to add everything
    
27. is it possible tha master get merged into the other branch
    - Yes, there are cases you might do that (developing and need updates in your feature branch)

28. (Not urgent just a comment) I have a ghost branch, I created an 'experiment-2' branch, created some commits. When running `git branch` there were two 'experiment-2' branches. After deleting the branch there was still a 'experiment-2' branch remaining. I couldn't checkout to the branch, nor could I delete the remaining branch. 
    - Git should not allow two branches with the same name, but sometimes characters that are different look the same
    - Can you copy & paste the output of `git branch`?
        - I tried reopening the terminal window, so my history is gone
          ```
          11:22:46 0 CodeRefinery/recipe % git branch                                                                                    master
          experimemt-2
          * master
          ```
    - typo: experime**m**t instead of experiment
        - Oh god, thanks
            - Very common problem :smile:
 

            
29. How do I monitor the commits in my guthub account which was configured previously?
    - The changes we have made today have not yet been added to GitHub. We will get back to this
    - Okay thanks!

30. What if we use "git branch less-salt" without mention "master"?
    - I will create the branch from whatever branch you are currently on.

31. Will The git graph alias be available in other terminals? How can you see overview of created aliases?
    - it will be available in other terminals on the machine where you set it up (and with the user you currently use) unless your IT deletes theplace where git stores the git config when you log out folders.
        - thanks and is there an overview of aliases?
          - I think `git config --list` should show you the current config including any aliases you set
          
32. Will pull requests be discussed, if yes, when?
    - absolutely! during the Collaborative-Git lesson on Thursday



### Demo of exercise
:::info
How is it going?:
- Too fast: ooooooooo
- Too slow: oooo
- Too basic: ooooo
- Too advanced: o
- Just right: oooooooooooooooooooooooooooooooooooooooooooooo
- Amazing: ooooooo
:::


33. I will have to leave the workshop now. Do we continue with this git example tomorrow, i.e. should I do the exercises in the afternoon or is it ok just to watch the videos??
    - The video will be available on Twich immediately.
    - Looks like the plan is to go up to "conflicts" today (but it might be postponed)   

34. What is preferable: git checkout or git switch?
    - git switch is clearer what it does. but it is not available in old git versions so we were careful not to advertise it too much. see also https://github.com/coderefinery/git-intro/issues/326

35. git: 'graph' is not a git command. See 'git --help'.
    - this is an alias command that we defined earlier: `git config --global alias.graph "log --all --graph --decorate --oneline`
    - i.e. it's a short-hand form for git-log with many useful flags`
36. I change my files in Rstudio, rather than from the terminal. Lets say, few people are working on same project and use rstudio to make changes rather than terminal. How would branch be relevant in that case?
    - The way you modify the files does not really matter for git (as long as you are not renaming the files with a tool that doesn't interact with git). In case of this type of collaborative effort, it would for example make sense that people work on their own branch and only create pull-requests(or directly merge) to a master branch from time to time. This way everyone can work on their copy, and when merging, you have to take other modifications into account. Optimally people work on distinct files and not the exact same files, because that makes merging much easier. 
      If you need to rename files, I would strongly recommend to use `git mv` 
      - how do people work on their own branch. I mean how do I make sure i make changes in R studio only in my branch?
        - you would need to either have some graphical UI that allows you to change branches, or you would need a terminal to switch to "your" branch from the terminal. RStudio will use whatever git currently places in the folder. However, if we are talking about the project being currently stored in one central place and everyon modifying the actual same files, then this is the issue here. You would need to put the project into an online repository and everyone checks out the project to their local system, creates a branch for themselves (that they can sync with the online repository) and work on that branch locally and push/pull online. But tis collaborative work will be discussed in more detail later (Should be on Thursday)
  
37. If I add a tag to a certain commit, and then rebase that branch to another branch. What happens to that tag?
    - I would need to try. Would you like to try it to check?
        - I'm listening to the stream now, but  I will try in a sec, just wondering if somebody knew of the top of their head
    - rebase does not modify commits, it creates new commits (commits in git are immutable). I expect the commit to stay there and tag to still refer to the pre-rebase commit.

38. Why it is important to delete the references of branches ?
    - Its not really important, but it keeps the repository clean. Because if the branch was merged, all information from the branch is no part of the merged branch, and thus there is not much use in keeping it.

38.  Why would you delelete branches and not keep them?
     - Mostly just to declutter. If the output of `git branch` is too long, you might not find what you need.
     - You might want to reuse the name
     - In doubt, keep them. You can always delete later once there are too many.

39. I have the followng error :

    ```
    git branch --merged
    error: Merging is not possible because you have unmerged files.
    hint: Fix them up in the work tree, and then use 'git add/rm <file>'
    hint: as appropriate to mark resolution and make a commit.
    fatal: Exiting because of an unresolved conflict. 
    ``` 
    How can I solve this out?
    - You have started a merge that had a conflict, but not finished it. We will talk about conflicts later, so you might want to start over for now.
    - If you do want to solve the conflict, run `git status` to get a list of conflicting files. Then edit them so that they make sense, `git add` them and `git commit`
      - Okay, What might cause a conflict in this case ?
        - Both branches have modified the same lines in the file. e.g. originally you had "tsp salt", the new branch changed his to "1/2 tsp salt" and the old branch has changed to "2 tsp salt". This is a conflict, because 1/2 and 2 are conflicting modifications. 

40. Am I the only one who could not merge branch because of conflict that could not be auto resolved ?
    - It was designed to be auto-resolved, but if some other lines were modified, then this might happen.
    - You can ignore it for now and we can synchronise in the next lesson

41. (question from in-person otaniemi participant) When is rebasing useful? Do we ever need to use rebase?
    - a nice thing of rebase is that it gives a linear history of time on the main branch, it can be useful to make browsing easier.
    - downside it changes history
        - I guess it's mainly a org practice thing, some open source orgs prefer rebasing, some prefer merging, best to check the contributing guidelines or ask what people in teh project are used to do
    - more interesting reading [here](https://rse.shef.ac.uk/blog/2020-06-23-git-rebase-vs-merge/)

42. Still a bit unclear, How are tag and branch different?
    - When you commit, the branch moves to the new commit. Tags always stay where they are.
    - Tags are labels for a specific commit, a branch is a different direction.

43. I did not really get what exactly happens when I merge two branches.
    - You combine the code development from the two branches into one common code base. e.g. one branch develops feature A, and another feature B. Your merged branch will have both features A and B. Essentially allowing simultaneous development, even if some common files need to be modified (e.g. both branches add some new functionality to an existing object, both need to modify that file, and their merge will contain both modifications)


44. what does this mean "@@@ -1,5 -1,4 +1,5 @@@?
    - It tells us something about how many lines where added or removed, but I never learned how to read it.
    - "-" mean lines were removed, "+" means lines were added, first number is the line number of the differences
    - http://www.gnu.org/software/diffutils/manual/diffutils.html#Detailed-Unified 

45. Is there a command that allows to add and commit without using 2 commands?
    - `git commit FILENAME [...]` for whole files or `git commit -p` to interactively select what to include.  Plus more options
    - `git commit -a -m "message"` allows to add and commit everything, but you may accidentally add and commit files that you don't want to, use with care :) 

46. If I have edited some files but not committed them and then checkout a previous commit, do I loose my edits?
    - Git usually does not allow you to checkout if you have uncommitted changes, at least in files that are tracked by git. If it's "new" files (i.e. not tracked by git) git simply doesn't care about them and leaves them as they are.
    - You may use `git reset --soft <hash-commit>`. This will keep the staging area and the working directory intact.
    - if you need to urgently switch branch for a quick change and want to continue working on the current branch later, you can also stash the changes with `git stash`, change branch and do what you need, then come back and do `git stash apply` for resuming. Stashing is basically git slang for save a draft
    - More on stashes in this CR episode: https://coderefinery.github.io/git-intro/interrupted/


## [Conflict resolution](https://coderefinery.github.io/git-intro/conflicts/)


47. Never worked on a recipe this much before :D, not a question :D :+1::+1::::

49. With the currect example of of different cilantro the strings themselves are different in 2 and 1/2 values, so why there can be a conflict?
    - The conflict is because the same line has been changed in two different ways. We might want to
      1. Keep both
      2. Keep 1/2
      3. Keep 2
      and git does not know which one we want.

50. Will the row number be important? what if putting the cilantro change in another line. Will it be spotted by git?
    - Git is smart about which line is which. For example, adding an empty line does not change annd the lines below it.
    - Yes. Line number is important if you want to create conflicts.
    - This would be a change.
         - so the file will end up with two conflicting lines with cilantro? because git will not see them as conflict?

51. It seems to me that there are some people in Zoom that are not muted. Could we ask people to mute? 
    - In breakout rooms?
    - Main rooms seems all muted, others feel free to ask yourself

52. What does git do if you change a part of the code (in two different branches) that is later reused by a different part of the code and then you merge the two branches? Like in the example if cilantro shows up later in the recipe again. 
    - If its in different branches, they don't see each other. Essentially you can think of different branches as being indipendent implementations in different places, as long as they are not merged, they can't interact. 
      If your question is: What happens when some code that was modified on branch A influences functionality that was modified in branch B, then git itself doesn't care about it (as long as the files are not conflicting). This is where you need a so called continous integration system, that tests, whether a change has an effect on something else. 
      In the cilantro example, if two people add cilantro in different branches, the merged recipe will likely have cilantro two times in the recipe. Because git does not make a distinction.

53. Is it possible to tab autocomplete git commands?
    - Yes, search how depending on your shell.
    - This depends on the terminal. You migth need to set it up, or it might work directly.
    - You may check the [Customize Git episode](https://coderefinery.github.io/git-intro/customizing/) for some solutions.

52. how restore to old point/commit
    - There are several commands for this, depending on if you mean a single file or the entire project. See https://coderefinery.github.io/git-intro/recovering/.
    - To get a single file, `git checkout commit_hash filename`

53. Say I make a branch and change a bunch of stuff. Then I change stuff in the main branch. Can I pull the changes from the main into the branch without fully merging?
    - You can get individual files from any commit or branch using `git checkout branch/commit filename`
    - If you have uncommitted changed in one branch, but you want to commit them in another branch, you should `git reset --soft <ref>` where `<ref>` is the reference for the branch where you want to commit your changes. The `--soft` option means that the modifications in the stagng area/index and in the working directory are kept. But the `HEAD` is changed to `<ref>`, which may be the tip of the branch you want to commit to.
    - Also, `git checkout <ref>` will complain if you have uncommited modifications in your working directory.

54. I'd suggest a ligth background for the terminal. The coloured text is not very clear :-)
    - relayed, will be better tomorrow!
    - thanks for feedback!

55. After git merge --abort, how do you come back? do you merge again?
    - It will bring you back to the state just before the merge. You can then merge again and if there was a conflict you will see the same conflict again but now you are better prepared to tackle it (you discussed with a colleague or you slept on it).

56. Just out of curiosity which terminal is the instructor using?
    - it's the [fish shell](https://fishshell.com/)
       - what I like most about it is clever autocompletion which is context-aware. But perhaps I should not use it during teaching. But then again I think it can be useful to mention that there are many different ways to customize our tools and also wanted to show our "real" tools.


57. How is merge related to pull requests on github?
    - Especially in bigger projects, you don't want anyone to merge any code to master, but you don't want to prevent people to suggest. Therefore, anyone who wants to merge his/her branch will create pull request, which has to be approved by others. If pull request is accepted, merge is done (not before). (correct me, not sure here)
    - Something partly related, I have found that it is common practice to have a `master` and a `develop` branch, where the `develop` branch is kind of a protection for `master`. And indeed, the `pull request` is not merged until the `manager` of the repo (or anyone else) has checked the `pull request` and accepted it. Before merging (or creating a `pull request`), it is good practice to first merge the `develop` (or `master`) branch into your "experimental" branch to resolve possible conflicts outside the main branches (i.e. `develop`/`master`). Hopefully, this helps; albeit a bit more context on workflows, etc. All in all, a `pull request` is a kind of official `merge`; marking a clear completion of a branch (at least, that is how I consider them).
    - Adding to the earlier comments, a pull request can also be a good way to explain what changes were made on the branch you want to merge to help other team members understand them; can also start pull requests before you're ready to merge for the same reason- to make it clear what you're working on

58. [off-topic] Some people mentioned Fortran at the beginning -- can anybody recommend a good tutorial?
    - I can recommend this book: https://milancurcic.com/book/

60. How do we delete everything we created today, and re-create it again?
    - You can remove the working directory. Everything git does is in a directory called ".git" in the working directory.
    - You can also recreate everything in a new folder, without deleting the original.
     
61. If you recover a certain commit, is any posterior work lost or does it branch out?
    - It will not branch out automatically.
    - You should create a new branch before trying to recover. That way you have a way to access the version you had before recovery. (so run `git branch not-recovered-branch-name`)

61. Do you recomend any other Visual diff tools for OS different from opendiff? I prefer not to install xcode because I don't need all its functions, and I can't find a way around installing the whole xcode app.
    - "Meld" is IMO lightweight and quite handy. +1
      - but is it available on macOS? Also editors like vscode have nice side-by-side comparison plugins so this may be another route.

63. Between GitHub and Bitbucket, why would you use one or the other? Advantages and disadvantages?
    - The differences are small. Github has more users.
    - bitbucket has jira integration, which is pretty good for project management, but github has greatly developed recently and differences are very small indeed
    - GitHub has better integration with Zenodo and more generous automated testing infrastructure

64. Since it might be the case the I have to leave at 10:30 tomorrow, would the session be recoded?
    - The stream is recorded and will be published on Youtube. You can also watch the stream on Twitch for 21 days.

65. How could we get more involved in open repositories (if that exists)? Where could we find those?
    - do you mean how to get involved in open source projects? yes!
    - my personal suggestion: don't ask to ask, just go for it! Open source communities are in my experience pretty friendly and welcoming. Pick something you are interested in, start using it, if/when you encounter issues ask for help (most open source projects have chat services like slack, zulip, etc.). Before you notice it, you will end up being the one answering questions. Once you get some experience, browse the issues, find something you could fix and open a PR, or simply open an issue if you find something missing/not working. Finally, there are also programs like Google Summer of Code to get started contributing to open source projects.
    - Note also that contributing is not just coding, opening issues, answering questions, even just writing a blog post about your experience, they are all contributions... my point simply being: don't be afraid if you feel you are not "hard core coder", the threshold to contribute is way lower than you may imagine :)
    - Thank you, this is really exciting!

66. Regarding Github: Do we need to prepare a repo for tomorrow? Will we clone? I was also wondering if it is possible to "push" a git repo I have created locally completely to Github, i.e. more or less cloning on github from my local repo?
    - no need to prepare. the idea is that we will push the one we created during day 1. But if that one is gone or not created yet, it can be any other locally created repository. We will first push the repo from today and later also clone it again to see the two options.


## Extra questions

- Style Question: is there a standard practice to document 'failed' branches? For example, if I had an experiment that didn't work out, I would possibly not want to delete that branch so that another collaborator doesn't duplicate that effort?
    - hm, I haven't done much here.  Could be renamed to include this warning, e.g. 'unused-...' ?
    - But good idea, I do this too!
    - I use `archived-...` or `readonly-...` or `retired-...`

- Is the tags attched to a branch?
    - NO, tags are attached to a commit
    - They are kind of a label for the commit
    - One way to look at them is like a branch label that never moves

- What are your (Twitter) hashtags?
    - #coderefinery22

- Do you already have an advertise/tweet somewhere for sharing?
    - Unfortunately not...

- how can we enroll for these voluntary services , i already folllowed you ?Please provide details. 
    - https://coderefinery.org/organization/get-involved/
    - Best is join chat if you want to get more involved, we aren't that organized beyond chatting yet!: https://coderefinery.github.io/manuals/chat/
    - Chat, GitHub, also you can join a community call: https://coderefinery.org/organization/meetings/

POST-LECTURE DOUBTS:

- While I was trying the "rebasing" excercise I got stuck in an error. The branch I am trying to delete (-d) seems to be not fully merged. If I checkout to that branch and I check "git status" I got "nothing to commit, working tree clean". How can I solve this issue?
    - You can get more information by running "git status" in the master branch.
    - This is probably because of a conflict. Check "git status" in the branch you are merging to. If there is a conflict, edit the files, `git add` them and `git commit`.
    - If there is no conflict in the master branch, try running `git merge` again.


## Feedback, day 1
### One thing that was good about today:
- HackMD Q&A is fantastic! +55555556+1
- step-wised tutorial and exercise
- Lots of material and alternate learning paths
- The tutuorials were well writtena nd helped clear most questions. +1 +1 +1 +1 +1 +1 +1
- Good amount of material for one day, not overwhelming
- I really liked the explanation about branches.
- Great content! I learned a lot of thing I know I will use!of thing I know I will use!
- The tutorials were really helpful. I really appreciated the inclusion of git graphs once we were branching so that I could frequently confirm that I was getting the same results
- The tutorial was helpful. +3
- Most things were good.
- Very well managed across the platforms and communication channels; well done!
- Well planned content and approach, expert instructors
- the "git graph" alias is cool and useful to get a glimps of things in a somewhat visual way. AND it makes explaining of branches much more intuitive. +1
- You really pay attention to the questions participants have :-) thanks!
- the exercise leader in breaking room is really helpful. Thanks!
- Excellent session. I think you did a great job (+1) with the exercises, not too technical but something fun and then we could focus more on the git commands. Good flow of the lecture.
- I liked the combination of discussion lecture, excercices and also redoing and discussing the excescises.
- This was very informative. Really like it :+1: 
- Great!! Super useful :)
- the combination of twitch and hackmd works really well! 
- HackMD is great. A bit hard to follow with things jumping around, but it's still great.

----

### One thing to improve:
- I still think it was fast.I was familiar to today's material, but on thursday I might be completely lost, esp I am working by myself. +3
- I would avoid copy-pasting from the website, typing things gives us time to catch-up.+3
- 
- The `rebase` should be more explained on the web. An excercise mentions it and you explained here (awesome, it's clear now) -- but not on the web. +3 (not solved yet)
- Could add preseemo for questions that you ask. 
- the interaction between the speak (could be more fluid and help not to loose focus)+1
- It was relatively fast. I could keep up because I had some familarity with `git` before. +1
- Maybe you could show a bit more of the code that you are typing so it is easier to follow when typing at the same time. +1
- don't feel necessary to introduce conflict resolution today. It is important, but may cause more confusion wheen just beginning +1
- felt like conflict resolution section was a litte rushed. Could have spent more time in working along with the instructor.
- Scrolling can disrupt the flow and the focus, slides can help reduce the information and keep the focus +1
- The pace is quite fast but so far the content is easy to follow. +1
- redoing excercises in the stream, which are already done in the breakout rooms is unnecessary. better use that time for some of this delicious extra materials :)
    - (not everyone has access to the breakout rooms though...) 
    - how about to grant more people into zoom room tomorrow?
    - We've found that many people want a live "solution", and it is also good for the recording.  We can try to make the demos more efficient to get to other parts.
- Great tip that a branch is effectively just a sticky-note.
- The part with coflict resolution was a bit rushed, perhaps we could do a small exercise on this as well.+1
- I did not like HackMD very much. It was messy to work in. Text dissapeared and other persons wrote over the text etc. Perhaps better if fewer people write in the same time. 


### Any other comments?:
- Perhaps, having a catch-up script to quikly copy-paste to get things in line with the material could be useful. I see the material includes all, but one needs to scroll and find, and copy paste multiple times. +1 
- I had reviewed the tutorials a couple weeks ago at the recommendation of a friend and it was really useful. I think I would have fallen behind if I didn't have that brief preview. Maybe others could try the same!
- The optional exercises for branches don't really work as they rely on still to be introduced teaching materials and the accompanying repository changes
- I did not like HackMD som much. It
- Maybe it could be nice to have the answers by instructors in bold or italic, that way other participants can share their ideas and we can have a nice discussion but it will still be clear which answers are 'correct'



