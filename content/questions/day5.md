+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 5

---
## 0. Icebreaker questions

### 0.1. What tools do you use to **write** your code?
- Vim (+ YouCompleteMe and bunch of addons) +2+1
- IdeaJ 
- VScode +12
- Eclipse +1 :+1:
- Atom +
- Jupyter notebook (incorporated in VScode) +3
- Jupyterlab +1
- Rstudio, just R in terminal +1 +3 +2
- Emacs (+ Vim keybindings etc) +1
- Vim +1+1+1+1+1
- Matlab editor+1+1
- cmake
- Jupyter +1
- emacs
- spyder +5
- Sublime 3 editor / RStudio +1
- PyCharm +33333333333333
- Clion
- Nsight (for C++ and CUDA)

### 0.2. What tools do you use to **test** your code?
- pytest (via GitHub workflow, but I don't really know how to use it)
- GoogleTest (in cLion; still struggling to set it up properly :'( )
- makefiles
- pytest +1 +3
- cargo test
- ctest
- junit
- Valgrind (memory checks in C/C++)
- catch2
- I do not test my code much +8
    - hopefully it will change after this workshop :)
- pytest + github actions
- my brain +4
- run the code manually +8
    - With many print statements to check what is going on the code.
- Rstudio, Jupyter, in the past emacs.
- Collegues +1
- test code written by colleagues
- Eclipse

### 0.3. What tools do you use to **debug** your code?
- walking, sleeping, and print statements +7+1+2
- eclipse debugger +1
- valgrind
- using compile flags to initialize variables with unusual values
- using compile flags to activate matrix/cubix prints in a nice form
- Collegues :D +1
- A lot of print statements +4
- spyder debugger and my brain +2
- `pytest --pdb`
- `import sys ; sys.set_trace()` or `import IPython ; IPython.embed()`
- pudb package (Python debugger)
- PyCharm debugger
- I would love to have a gdb on mac, I know there is an equivalent for clang but I was not able to get it to run :(
- I can't even get a fortran compiler to work on my computer :P I always just run it on the computation cluster of my department
- Eclipse
- flyswatter

---
## 1. Jupyter
https://coderefinery.org/jupyter/version-control/

### 1.1 Jupyter notebooks 
https://coderefinery.org/jupyter/motivation/

1. I don't use python so far (planning to learn). Can we use jupyter for R? Or is it similar to R studio?
    - Yes, you can.  Many people use RStudio instead, but some of the Jupyter lesson here still applies (the Binder part might be especially useful)
    - Jupyter should work for more languages IIRC, so far I know Julia, Python, R and Ruby should somehow work in notebooks 
    - Jupyter was originally designed around R, Python and Julia, so R should be well supported
    - Otherwise, Rstudio with RMarkdown works similar
    - https://github.com/jupyter/jupyter/wiki/Jupyter-kernels

2. Would be great to get options for testing codes, debugging in R (apart from collegues help)
    - Rstudio has a built-in debugger and can automate testing.
    - Here is some documentation on this: https://r-pkgs.org/tests.html. Hopefully it makes sense, at least after the testing lesson

3. What does the magics `%` do behind the scenes?
   - `%` in Jupyter is actually a function of the IPYthon kernel.  It's an escape character that triggers IPython's magic function handling, and does whatever the magic wants.

4. How do I ensure that Jupyter is using the correct python terminal and conda environment? (I've had dissonance with this in the past.)
   - To check what is running: `import sys ; print(sys.executable)`
   - Then, setting it up the right kernel.  Perhaps too long to write here.  For what is going on inside, check this PR I wrote: https://github.com/jupyterhub/jupyterhub/pull/2726/files

5. Where is the link to install jupyter? I saw it before, but can't find it now. 
    - Jupyter and JupyterLab are part of the CodeRefinery environment.yml file which was part of the installation instructions
    - Instructions for creating the environment: https://coderefinery.org/installation/conda-environment/

6. Can Jupyter be used for MATLAB codes or is there any alternative for that?
   - There is a MATLAB "kernel" that runs matlab code within Jupyter.
   - Do you still need a MATLAB license then? :-)
   - Yes.  Matlab still needs to be installed locally for this to work (and you can't share it to run on Binder, obviously)
   - Not a real answer: Isnt there kind of a 'native' MATLAB solution with *.mlx files?

7. `503 Service Temporarily Unavailable` when starting Binder from the GitHub page of the GW example
    - I guess they have some difficulties right now.  If you try again in a bit it might work (I think they might have some resource problems now)

8. You CAN write notebooks in VSCode! +1
    - interesting! do you need a plugin or extension for this?
        - The python extension is enough! :)

9. Possibly worth mentioning one can easily convert jupyter (ipynb) files to a python code file: `jupyter nbconvert ...`
    - Indeed. I think it will be mentioned later during the lecture. Thank you for adding it here as well.
    - you can also export to .py from the web interface.

10. A compliment. Johan is very clear to follow. +1 +1
    - Thank you for the feedback. I am sure he'll be happy to hear.

11. Are there tools to convert jupyter notebooks to python (or Julia or R) when the project grows? If so, which?
    - In most ipynb editors is a button for that.
    - Yes, you export to raw source.  Usually needs some clean-up and adapting.
    - See comment #9 above.

12. Is there a way to ignore outputs and execution count of jupyter notebook in git? I.e. I want git to 
    - https://pypi.org/project/nbstripout/ can work as a git filter to strip outputs, etc. to normalize to a standard form.  Maybe others exist.
       - excellent! I was looking for that but never searched :-) +1
       

---
### 1.2 JupyterLab and notebook interface
https://coderefinery.org/jupyter/interface/

13. In my coderefinery environment, I get error with ´sphinx-build --version´. 
    `ImportError: cannot import name 'environmentfilter' from 'jinja2'`
    - I recognize this error. Give me a min to look for the workaround ...
    - Can you please try to find out what your sphinx version is? `sphinx-build --version` but that might fail. You can also try: `python -c "import sphinx; print(sphinx.__version__)"`
    - When did you make the enviornment? Did you make it from our environment.yml ?
        - yes, it is the same environment that we used yesterday: https://coderefinery.org/installation/conda-environment/
          - sorry I forgot to follow up here. what sphinx version do you have?

14. Why can't I see the CodeRefinery conda environment in JupyterLab? +1
    - did you start it from within the activated conda environment? or how did you start it?
        - Yes, I ran JupyterLab from the terminal after activating the environment with `conda activate coderefinery`. I just created an notebook with a kernel of Python3 as in the lesson, I was just wondering why there is not a kernel that says coderefinery.
            - just a clarifying note to avoid confusion: `coderefinery` is an environment, `Python3` is the kernel in this case.

15. (Im guessing this will be covered later but asking in case) What are the best practices/options for version control of Jupyter notebooks, when I started using them I noticed the git files became very large very fast
    - `git` and `nbdime` is one solution. Other solutions are listed in a follow-up episode of the Jupyter lesson: https://coderefinery.org/jupyter/version-control/?highlight=nbdime

16. How can I use a different environment when I have the JupyterLab tab opened?
    - You can install other *kernels* which are for other Python environments.  Looking...
    - Well, search how to install kernels of other environments.  General idea: [activate other environment] then `python -m ipykernel install --user`

17. Headsup: When I have many environments the jupyter launcher shows many environments as well. The problem is that I store my environments locally and give them the same name. This makes very difficult to find out wich environment you want to select in the jupyterlan application. On the otherhand in vscode the IDE provides a clear path to the environments that you can use to select the env and connect it to the kernel.
    - This doesn't help much by default, but these kind of things are configurable.

18. Instead of renaming the Untitled, we now have 2 files? How do we actually rename a file?
    - rightclick on the file name which then opens a menu and then "Rename Notebook ..."

19. Any idea why conda is not found ? It was working fine until yesterday ... I'm on ubuntu 20.04
    - are you in the right terminal? assuming this is windows make sure you are in the anaconda prompt. depending on your settings, git bash may not see the python environment.
        - I closed the terminal and open a new one ... its working now ... but I was already in the right place in order to activate cona environment.

20. Why is the notebook ui is different when opening from git bash and other through anaconda?
    - They could be using a different version of the Jupyter library. Did you activate the coderefinery environment in git bash?
		- Yes I did. I repeated the steps with the teacher and it is diffferent from how I usually open the jupyter through anaconda.
			- Maybe in the one you started jupyter-notebook and in the other jupyter-lab?
				- Yeah, probably as you said.

21. Where are the contents for this exercise, eg where is this markdown content copied from?
    - Is it from here?: https://coderefinery.org/jupyter/interface/

22. I activated the coderefinery environment with conda but now I get the following message when trying to run jupyter-lab $ jupyter-lab
    ```failed to create process.```
    - Is there a longer error message? What operating system are you on?
    - Nope that is it. Im running Windows 10
    - An this happens every time?
    - It's the first time I use Jupyter :-)
    - Is this in git bash, an Anaconda shell, or WSL or similar?
    - It's in git bash
    - Can you start Jupyter through the Anaconda Navigator instead, if you installed Anaconda?
    - Maybe try removing the environment and recreating from the yaml file?
    - I tried in Anaconda and it says: 'jupyter-lab' is not recognized as an internal or external command, operable program or batch file.
    - Will try thanks! :-)

23. What should I press to print? Sorry missed that. Shift+enter did not print anything for me.
    - shift-enter and control-enter both run a cell (and move on/stay in same cell).  Does the cell have any prints in it?
    - if it's a markdown cell then shift-enter only shows the rendered version of the markdown (no output as such)

24. Can you use less shortcuts? We can't see what you are doing when using a shortcut
     - click on the cell and left of the cell you will see which cell you are on. then shift+enter does not produce anything?
     - No, I am on the cell where i have ´print("hello world")´. I am on mac, does that make a difference?
     - Actually now it did. I copied the same to second cell and it magically worked.
        - interesting. what you might also try is to restart kernel and rerun all cells (under the menu item "Run"). it's the equivalent of "rebooting the notebook"-👍🏽

25. Is Atom an IDE or a Code editor?
     - maybe something in between +1

---
### 1.3 A first computational notebook
https://coderefinery.org/jupyter/first-notebook/#a-first-computational-notebook

#### Exercise until xx:49

- https://coderefinery.org/jupyter/first-notebook/#an-example-computational-notebook
- Do what you can, nothing in the rest of the lesson depenends on this.
- Optional exercises: Installing a kernel for your favorite language: https://coderefinery.org/jupyter/first-notebook/#notebooks-in-other-languages


26. Would you show the exercise on the twitch screen please? It saves me a window to look at...
    - I'll switch back and forth.  But can you open a new tab in that Twitch browser instead of Twitch, and get the same effect?
        - Only for the exercise time the current view is pretty handly.
        - In the past we found that sharing HackMD is a good reminder (has the times) and increases engagement there.  Maybe I could set up a split screen... well, this exercise is too long anyway.

27. How the if `x*x + y*y < 1.0` indicates a hit?
    - The point is inside the circle of the distance from the origin is smaller than 1 (the radius). The distance is actually sqrt(x*x + y*y), but if take the square on both sides of the equation, you get the above.
        - alright got it! Thanks

28. A **compliment**. You code in Python following PEP8
    - excellent :-) it's good to follow this for Python developers to have a consistent style
    - side-note for Python code that is not in a notebook: one can autoformat with `black`
    - has anybody tried to use `black` within a notebook? and if yes, how?

29. Don't we need terminal anymore? Will closing my terminal close my jupyter notebook?
    - It will probably close your jupyterhub server, and thereby the notebook.

30. A nice shortcut : to switch a cell from code to markdown, you press escape (if you were in the cell typing) and then press M, then enter to "enter" and type again in the cell. (Y is for switching back to code)
    - thanks!

31. I am not sure if this was already discussed: what's the difference between jupyter-hub and jupyter-notebook? Is Jupyter just the "backend" and the other two the interfaces?
    - JupyterHub: a multi-user server that provides access to single-user Jupyter servers.  JupyterHub provides login and starting the single-user servers    
    - Jupyter-notebook: An individual notebook file, containing code (and comments and additional explanations, or whatever your put in).
    - `notebook` is also the name of the server that provides a web interface that lets you edit notebook files.
        - So, for this example a jupyter-notebook would have been more suitable since its just me who is editing the file?
    - jupyter-lab: A server that can interpret notebooks and provides a web-interface for editing/managing notebooks.
    
32. When do we use "raw" cell?
    - I have never used it
    - What do you mean for raw cell?
        - When you create a new cell, there are 3 options: Markdown, code, raw
    - There might be situations in which you want to show code without running it; as an example. You can use the `style` commonly used in `markdown` but also the `raw`.
    - https://stackoverflow.com/questions/47852733/what-are-raw-cells-in-jupyter-notebook
        - Following the links you bump into "This is typically not useful at all" for the case https://nbsphinx.readthedocs.io/en/0.3.1/raw-cells.html#None

33. Personally, my biggest problem with notebooks is the lack of debugging capabilitites. I normally use VSCode to write my code and it is so straightforward to put breakpoints. Do you have a demo for debugging? +1
    - You can `%debug` or `%%debug` to start a debugger when there was a previous exception.  Remember to `q` to quit otherwise it locks up the notebook.  Not perfect but perphaps ok...

34. Wow, if num_points are set to a bigger number than the pi gets a closer values, and vise versa!
    - Yeah! I noticed that it takes quite a large number to get pretty close though :/ (see answer below! :smile: )
    - Great observation. One could add it's very easy and also very bad way to calculate $\pi$, since it converges as $N^{0.5}$, i.e. you have to sample 4 times more points to half the error.
    - Really interesting and nice exercise. Is

---
### 1.4 Notebooks and version control
https://coderefinery.org/jupyter/version-control/

35. I usually use Jupyter notebook and not jupyter-lab. Are the things we go through now about version control the same for jupyter notebook?
    - Many are the same, the main difference is the user-interface.
    - but in terms of nbdime (notebook diff and merge) that we will show in a bit, they behave the same. only the git integration shown now is a jupyterlab extension

36. Will these tools also work within VS Code's implementation of Jupyter Notebooks?
    - as for git: VScode has git integrations as well, and I would use those as they are more general.
    - but nbdime? Is that specific to Jupyter Lab? 


37. when is there gonna be a break?
    - thanks for this question. checking with instructors ...
    - in few minutes

38. bash: emacs: command not found - What is the alternative? Or how to install emacs?
    - e.g. nano; About installation: that depends on the OS.
    - mac
        - You may install it via Homebrew: https://www.gnu.org/software/emacs/download.html
        - https://wikemacs.org/wiki/Installing_Emacs_on_OS_X

39. what did he add in the gitignore file? Was not fast enough......... 
    - maybe `.ipynb_checkpoints` (I was also distracted but this is what I ignore in my Git repos)
    - .ipynb_checkpoints/

40. Sorry, may you explain again how to open the terminal in Jupyter?
    - Go to the folder icon on the upper left, the click the "+" sign, scroll down and click on the terminal button.
    - Alternative: File -> New -> Terminal

41. **Tip.** Not fair. Instructor had .gitignore ready while I had to make it so no I'm lagging behind :-( 
    - Totally agree, This is very fast in presenting mode
    - for the sake of exercise it is OK to not gitignore this and leave that file unstaged. But I agree it's a bit too fast and I recommend to watch and not follow along typing
        - too late now, I'm already lost, it does not make much difference
    - +1, we should not do this!
    - Agree, very fast and it is a loss of oportunity if it's only demonstration, not type along

42. I keep getting this message: 
    `[IPKernelApp] WARNING | Parent appears to have exited, shutting down. After which the juypterlab refuses to connect. What can i do to resolve this issue?`
    - Maybe this helps: https://stackoverflow.com/questions/58563333/jupyter-notebook-kernelrestarter-restarts-and-then-notebook-killed
    - Did you close the terminal in which you ran the jupyter server?

43. Do you regularly use diff feature of version control in notebooks?
    - I always have them in a git repository. Even when not using nbdime and comparing, I like that I can go back to a working version if I mess up. Also when sharing a notebook as part of publication.

44. I did git init in my regular terminal outside of Jupyter Lab, and Jupyter couldn't see that it was a git repository. I made a new version of the notebook in a new location and initialized it from Jupyter lab and it worked. Should Jupyter have been able to see my git init from outside Jupyter?
    - I think it would see the repository after you restart Jupyter Lab

45. The jupyter-shell uses my style from the regular terminal. unfortunately not the background color. now I write white text on white background. Is there a way to change the background color of the jupyter shell?
    - hmmm. unsure how but looking for a solution ...
    - is this a problem related to "dark mode"?
    - One solution: use the "inherit" theme, then use or create a custom theme plugin with the colors you desire.
        - I found that one can use a "dark mode" theme for the shell in the settings menue. that works with the white text!

46. My git button is gray, I can't click it. What did I miss. i already did git init and git add in terminal. +1
      - Restarting Jupyter might help
      - I did it in the terminal of jupyter notebook.

47. A general question: Are the links going to be active after the workshop?+1
    - Yes, all the material remains: https://coderefinery.org/lessons/
    - but also it evolves but everything is on GitHub and you can contribute: https://github.com/coderefinery/jupyter
        - You are awesome! Thanks.
    - everything open source and will remain to be available

48. Is there any difference when running jupyter-lab on a HPC server? I'm asking due to the graphic nature of jupyter-lab, is it possible?
    - Yes and yes.
        - Could you elaborate a bit? XD
            - Optimally, your Cluster-admins have a jupyter installation that you can use, since it should not be run on the login node. Also setting things like environments up will probably need some system specific instructions. But if it is set up, i works the same way as your local jupyter installation. Running it yourself will probably become messy, as you will need a lot of tunneling or other setup to reach the machine where your jupyter server is running.
            - Thanks!
    - I have been using jupyter notebooks on cluster, what I did is to launch the notebook from my computer to a login node, and then redirect the login node to a computing node with resources. I would have to ask a node, launch the notebook there, then on the login do some sort of transfer and then I could open it from laptop.
    - I've done it once. Most admins publish a manual for that. In my case, it was necessary to submit job with allowed user interaction (e.g. `qsub -I ipynb_job_parameters_here` in PBSPro), which redirected me to the node. Then I've run `jupyter notebook` the normal way. Finally, I've `ssh -L` to computational node and opened the jupyter notebook url in my browser. Sounds bit complicated on the first time, but it gets easy.

49. When I opened a terminal in the same jupyter-lab, the terminal was on the base environment. Shouldn't it be at the environment that I called the jupyter-lab? 
    - Unfortunately the Jupyter terminal does no know about the environment. (or it does not know where it was started from)

50. how to Copy the “darts” notebook into it the  (from the previous episode) git repo? I initialized the repo but how to add the notebook there?
    - you can save the notebook, close the notebook, move the file to the Git repository. In there you `git add` and `git commit` it, then reopen it in the new place.

51. Are we suposed to type-(click)along or just watch. I kindof missed everything when typing along and also mentioning problems in hackmd. I feel lost. 
    - You can just type-along, other things shouldn't depend on this.  It was rather fast.

52. I keep getting this message: 
    `[IPKernelApp] WARNING | Parent appears to have exited, shutting down. After which the juypterlab refuses to connect. What can i do to resolve this issue?`
    - Maybe this helps: https://stackoverflow.com/questions/58563333/jupyter-notebook-kernelrestarter-restarts-and-then-notebook-killed
    - Did you close the terminal in which you ran the jupyter server?
    - yes i did at some point. but i restarted the terminal, and the problem persisted.
        - Did you also restart jupyter? A closed terminal means any processes started from it (which are not told to run independently) will close, and just opening a new terminal will nto restart them (same as office, when you reopen it, the files you had open before closing are - commonly- not automatically reopened)

53. Dummy question i know: but how to restart jupyter?
    - I would go to "Run" pannel and then "restart kernel and run all cells"
    - Alternative (less elegant) is to stop it inside the terminal (with CTRL+C) and restart it there +1
    - Kernel > Shut down all kernels. Then File> Shutdown. Then "jupyter lab" again
    - Or you stop it from the web interface and then restart in terminal


54. **Tip**. You should be more clear on when we should type along and when we shouldn’t. I think a lot of people are lost now because they tried to type along but couldn’t follow. +1+1
    - thanks, I will relay this

55. **Tip**. A comment: I understand that you modified your shell to your preferences, but the fancy style somehow irritates me because so many things are popping up while you are typing something.
    - good point. we should deactivate these extensions before teaching.

56. I recieved this err: 
    `$ git add .gitignore`
    `fatal: pathspec '.gitignore' did not match any files`
    I was able to add the checkpoint file but could not gitignore. What might be the problem?
      - It seems there is no file named `.gitignore`. Did you create one? Note that it's `.gitignore`, not `gitignore`, the `.` needs to be there. 
      - I havent' add any .gitignore file. How can I procesed? Deleting the checkpoint first adding a `.gitignore` than adding the checkpoint into `.gitignore`?

57. I got completely lost when the git part started. Could you repeat it after the break? I tried git add,git commit, and git push but git push origin main did not work. (in jupyter terminal) +2
    - we should have emphasized more that it's better to watch that part only. main message here is: it can be done from within jupyterlab but the details can be figured out later. sorry for the high pace.
        - No worries, but I doubt that at that pace I would have even made it to jot down some notes 

58. ```import matplotlib.pyplot as plt
        ModuleNotFoundError                       Traceback (most recent call last)
    Input In [6], in <cell line: 4>()
          1 # importing modules that we will need
          3 import random
    ----> 4 import matplotlib.pyplot as plt

    ModuleNotFoundError: No module named 'matplotlib' ```
    
How do I fix this?, was working fine jupyter notebook, but not in jupyter lab?
Yes

  
 - Somehow the *kernels* are different in them.  We would need to look more into this later.
    - you started both from the same (coderefinery) environment?

59. Is it possible to see the teachers commands in terminal, I am having trouble to repeat the steps. 
    - thanks for feedback. we will adjust to this and remind instructors to share command history if they can.


#### Thor's command history:
``` 
git init
git status
emacs -nw .gitignore
git add .gitignore
git add first_notebook.ipynb
git status
git commit -m "first commit"
git status
git log
git diff
nbdiff
nbdime config-git --enable --global\n
git diff
```

61. Are we moving back to using terminal? If so, could you please go step-by-step showing us how to safely quit the Jupyter session? 
    - my understanding is that we are staying in the jupyterlab but to safely quit: save the notebook and then File -> Shut Down in top left web menu
        - thank you.

62. I would like to repeat the Comparing changes without jupyterlab-git/nbdime session which i think is very useful, but cannot proceed, hey someone had passed the commands now i will be able to repeat.
    - I'd recommend watching it in the videos (available immediately on twitch, this evening on youtube.  see website.)

63. emacs -nw .gitignore command is not working 
    - `nano .gitignore`
    - perfect! thanks

64. How do install plugins in JupiterLab in the first place?
    - Search the plugins and they will tell how to.  We probably don't have time to go in-depth enough now.

65. Why is not my "git"-button in the jupyter-lab (next to the clock-symbol in the jupyter notebook toolbar) clickable?
    - I wonder if it knows it is in a 
    - I have the same problem. I initialized the git repo from the terminal but somehow the jupyter-git tool does not realize this

---
### 1.5 Sharing notebooks
https://coderefinery.org/jupyter/sharing/#sharing-notebooks

66. I get `503 Service Temporarily Unavailable` when trying Binder +1+
    - Unfortunately binder has been a bit unstable today.

67. Can't we use Colab?
    - we could but did not want to require using google account for this but thanks for suggesting this good resource

68. I got the same error when we tried this in a previous lesson, so maybe Binder is not a good service to use?
    - it is a wonderful service. this is the first day that I remember that it is so down. Unlucky timing.
    - I have known it for a few days and it is the second day that it is down. It was also down for a while last week when it was included in one of the demos 

69. What is the link with the status of the Binder servers? It can be useful to have
    - https://mybinder.readthedocs.io/en/latest/about/status.html

70. So, if Binder can be down do we foresee having problems in the future due to lack of founding in central Binder server?
    - Please don't use the Aalto jupyter one
    - this is a possibility but even if it happens, the notebooks are hopefully still on GitHub and Zenodo and can be downloaded from there.
        - Yes!  Notebooks are completely portable anyway, binder is just a viewer.  So research is still reproducible.

71. Could it be because many of us are opening my binder at the same time?
    - A lot of people use binder. There are not enough of us to make a difference.
    - Today's troubles are unusual. I have been using this service for years without this problem. It's unlucky timing.

72. With this message https://mybinder.readthedocs.io/en/latest/about/status.html#site-reliability-goals I can't say it looks very attractive to use

       >As mybinder.org is a research pilot project, the main goal for the project is to understand usage patterns and workloads for future project evolution. While we strive for site reliability and availability, we want our users to understand the intent of this service is research and we offer no guarantees of its performance in mission critical uses.

    So, is it wise to invest our efforts on it? Interesting to discuss with strategic decisions makers.
       - I think it is. Alternatively we can encourage university leadership to invest into their own instance or to support the service financially.
           - yes, that was exactly my point.
    - The idea of binder is "support standard tools you would use anyway".  If you would make requirements.txt/environment.yml, it's already made ready for binder.  Then, you can also deploy it on other services when they exist, or run locally.
    - Personal opinion: I think it is more likely that mybinder lives longer than Google Colab lives longer. Of course I don't know what will really happen.

73. In my file browser of Jupyterlab, I cannot see .gitignore file. I guess it's hidden. How do I see this file?
    - Try `ls -a` in the terminal. And if it works try also the alias `la` to same effect, in case that alias is already available for you

74. Could you say that jupyter-lab and jupyter-notebooks are IDEs with specific features centered on notebooks and data science?
    - Yes, I think this is a good description. IDE geared for linear execution (cell after cell after cell).

75. Is the bynder application then another service we can use to make our repository focused on analysis even more reproducible and easy to test? What are other alternatives and why this is widely adopted?
    - binder is a service that can run notebooks dynamically. but it can do much more than only jupyter. it can run R Studio, or in fact any container. +1

76. How can we deal with the limitation of memory when running on Binder (e.g. when notebook need to download and store some large data to run)?
    - this is not exactly an answer but what I would do is to put a smaller example that demonstrates the method on binder and the larger example can then be run locally and I would give clear instructions on how to run the big example locally

77. When someone clicks in our binder link, which kernel will he use to run the notebook?
    - It is defineable in the repository
    - **To expand this question**, are the packages in the `requirements.txt` file the packages that binder reads? Does it work with a `.yml` file?

78. I see that almost everyone uses present tense to write commit messages. I find it counter intuitive. Shouldnt we use past tense to indicate what change we did?
    - It is considered "standard" to use the present tense in some communities/developer groups.
    - Imperitive tense, as in you are telling someone to do what you just did.  "Add feature X"
        - yes like in cooking recipes
        - motivation: if you have a commit that says "increase scaling to 2", and later you change your mind and revert the commit, also the revert will read naturally: "reverts 'increase scaling to 2'"
            - "reverts 'increased scaling to 2'" does not read less naturally to me though. I think it is just a matter of being consistent what tense you use and set the "standard" within your group

79. environments and venv are somewhat virtualizations, could it be an analogy to mention that containers are another more advanced level of environment management? Why would a user need to use a container in contrast to a simple python environment?

    - One case can be that your workflow doesnt work only with python but also with other software.
    - It can be also that your environment depends on an operating system like Linux.
    - in other words if all the other person needs to do to get my code to run is `pip install` or `conda install/activate`, then a Conda/venv is probably enough and probably preferrable. But if they need to do more (such as `apt-get install this and that`, install libraries, set environment variables, ...), it might be useful for them to have access to the container. Even if they end up not using the container, one advantage is that the container has to document all install steps very explicitly so it can even serve as documentation.

80. The "git" button on top of the Jupyter notebook remains unselected (grayed). 
    - It might not know there is a git repo in the current place
        - I've initialized already the repo and committed changes.
    - I had same problem. After restarting jupyter lab, it is clickable.
        - Great! Thanks. Now it works. 
    
---
### Poll

#### If you are already using Jupyter, what tasks do you use it for?
- Start a code from scratch, the cell tool is very useful to test +1
- I first started "coding" in Wolfram Mathematica which has a notebook structure, so it's very comfortable and familiar to me to test out new things and play around in a notebook first before making a concise `.py` file
- Teaching programming to students +1
- As a testing playground - I first write the code in the .py files then import them into Jupyter and run them there to see if the plots make sense etc
- Demonstrate how to use a package
- Prototyping code
- Haven't really. But will start using after the course. 
- Save outputs of a script in a coherent way
- I use it to test small code ideas, and to run light-weight data analysis tasks (making plots/figures). If some piese of code needs to be used many times for some analysis, then I move it into a script for making it much more easy to run.
- As tutorials/examples in my repositories
- Working with large data. I don't want to load several GiB everytime I make a typo in my code.

#### If you are new to Jupyter, do you see any possible use cases?

- Maybe journals could require a notebook as an exemplar of the code in the manuscript so that editors would not be bothered with understanding lots of code. In a way, an implementation between raw code and psuedocode.
- Could be useful as a teaching tool
- I use RMarkdownin RStudio and compared to that I found Jupyter to be very complicated. The RMardown document is an ordinary text file where you set code snippets as ```{r}  ``` and everything inside is considered code and what you write outside is considered markdown text. No need to switch between `code` and `Markdown`. Being a text file it can directly be compared with diff and integrated with git and opened in any text editor of choice. It also, as far as I understood, have all the capabilities as jupyter, converted to HTML, PDF etc. You can even write in other languages inside the code snippets by stating e.g. ```{py}  ```, and mix languages within the same notebook.


#### Do you think Jupyter Notebooks can help tackle the problem of irreproducible results?
- Not really, I think containers and environments are more suitable to tackle this problem.
    - It can even be counterproductive as the problem of the running order of the cells makes it prone to human mistakes when running :+1:
- Yes! Any code at all being available is good for reproducibility. If it's nicely presented in a notebook, even better. +1
- Yes, when calculations are light weigth and in the preparation of figures and plots. So, in general in data analysis, rather than data generation, as the latter might be computationally demanding in some fields.
- I find it is somehow, especially when I (or someone else) need to rerun my script to get new output, I can see what output is expected for each cell based on the previous run. Usually if I only have .py and a folder of outputs, it's more difficult.
- Yes, if you keep them clean.
---

81. What is the script for git remote add to add my-frist-jupyter to git?
    - `git remote add origin https://github.com/user/repo.git` Is this what you mean?

82. What is best practice to sharing? Say, I can share my work on GitHub. Or, I can also provide there link to Binder. Or, also link to DockerHub, Google Colab and a million other services. But that's probably too much duplication, isn't it? Would sharing on GitHub + 1 service be ok?
    - People will often share the Github repo, and then the README has a link to binder (or whatever).  People can paste/clone the repository into whatever other service they want.


83. How to make a page like "https://coderefinery.org/jupyter/extra-features/". Can it be done using github?
    - We are about to see in the upcoming documentation lesson!
    - But yes, this is git + Sphinx (next lesson) + Github Pages (next lesson).

84. My jupyter configuration is broken. or my network settings. i don't know :(
    - We are moving on to another topic now, so we can take time to debug later on.

85. In the last lession we created a requirement.txt manually, but we didn't see how to use it. When to call it? Does binder understand it automatically?
    - We don't go into depth here, but our python-for-scicomp course did: https://aaltoscicomp.github.io/python-for-scicomp/dependencies/
    - In short, it's a standard format for Python dependencies, and different programs read it
    - In this case, BinderHub understands it automatically.

#### Break until xx:55

86. Can we import ipy notebook?
    - I guess you mean into another Python script?
    - There is something that does that, searching...


---
## 2. Documentation
https://coderefinery.org/documentation/

### 2.1 Motivation and wishlist
https://coderefinery.org/documentation/wishlist/#motivation-and-wishlist

### Poll

#### **Wishlist for good documentation:**

What would you like to see in the documentation of something you use?

- Never have to wonder *what you are talking you about?*
- Explain the logic of what I am going to read +1
- Announcing each new thing that is talked of
- requirements that clarify assumptions made upon coding.
- good examples (use cases)++++
- Clear mathematical notation+
- steps to follow for installation of required material +2
- What does each block of code do (briefly)+3
- function documentation +1
- What are the variables that are used (nomeclature)+1
- A purpose, what is the code etc suppose to do.
- Examples +9
- Expected inputs and outputs + +1
- Guidelines and common practices.
- versioning
- Easy to read - good language
- Guideline to navigate the code; especially if the programm is very long and complex
- Concise sentence for functionality/general purpose of piece of code
- Hello world !
- references for equations used in code
- Installation guides+2
- Instructions for running/installing things that don't leave out a lot of steps +
- If it's a library of some sort, a clear guide of the inputs and outputs of functions.
- the lest possible text (i.e., concise) with the most information possible (i.e., informative).
- Can people contribute? Will new issues be adressed or not?
- md5 or similar hashing for security
- Maybe mark stuff to be rewritten (avoid bad code if possible of course, but elegant solution is often not the first one you come up with)
- make clear assumptions and limitations
---

87. Interesting point: you look at the API after years of using a package. I guess, this explains why I often fail to learn how to use a function by looking at the API :D.
    - or when the examples are insufficient.
      - what to do if there is no example that does exactly what you want? Should examples cover everithing? Doesn't this expectation lead to combinatorial explosion of examples?
        - but more often than not there are too few examples than too many. a nice way to contribute to a project is to share an example walkthrough.
88. Maybe asked before but will the "script" which we work through be available forever or is it only there during workshops?
    - you mean the lesson material or something else?
        - yes, the lesson material
          - yes, it will remain available and open source: https://coderefinery.org/lessons/
              - Amazing, thank you!
          - everything is on github and we welcome ideas/contributions: https://github.com/coderefinery/documentation/
    - The remote repositories will also continue to be available.


---
### 2.2 Tools and solutions
https://coderefinery.org/documentation/tools/#popular-tools-and-solutions


89. Any general guidelines what should always have docsrting and what not necessarily? I.e. I often found that all classes and some functions have them...+1 
    - Depending on language. In languages, where you have non-accessible private functions they can get away without a doc-string since they are not accessible from the outside and are not intended to be used by anyone else, so "outsiders" don't necessarily need more info. But in general: Everything :smile:, since you do potentially want other developers to underttand what something does.
    - I would put into a docstring everything that should be readable without looking at the source code and should be readable when accessing only help text.

---
### 2.3 In-code documentation
https://coderefinery.org/documentation/in-code-documentation/#in-code-documentation

Skipped, but feel free to go through the material above after the workshop. 

---
### 2.4 Writing readme files

https://coderefinery.org/documentation/writing-readme-files/

90. Do we *have* to scream `README`?
    - No, github does that automatically :smile:, but well. It is to some extent derived from too many people not reading the manual/readme. 
    - Services like GitHub will render it correctly also if it's `readme` but it is a historical convention to uppercase certain files like `README`, `CONTRIBUTING`, `LICENSE`, `AUTHORS`
    - According to stackoverflow the historical reason is that in the terminal, with `ls/DIR`, uppercase letters are displayed first.
       - hm! today i learned!
    - Yes because some users might forget to read.


#### Exercises until xx:30
https://coderefinery.org/documentation/writing-readme-files/#exercises

Do exercises README-{1,2,3}, whatever interests you the most.

For getting **help in an exercise room**, please write the room name here or in the relevant Zoom chat.
#### Break until xx:43



---
### 2.5 Sphinx and Markdown
https://coderefinery.org/documentation/sphinx/

91. When writing `sphinx-build --version `inside the coderefinery environment (already activated in conda), I get the following message: `bash: sphinx-build: command not found`
    - Try running `conda install sphinx
    - When doing that I get ERROR conda.core.link:_execute(699): An error occurred while installing package 'defaults::python-3.9.11-h6244533_1'. Rolling back transaction: done [Errno 13] Permission denied: 'C:\\Users\miniconda3\\envs\\coderefinery\\python.exe'`
    - is the CodeRefinery environment activated (if you followed our instructions): `conda activate -n coderefinery` ?
    - Yes, I followed the instructions on the website and yesterday it seemed to work. AFAIK I did not change anything
    - are you using anaconda prompt?
    - I was using Git Bash (with the conda command), should I use Anaconda instead? 

92. Is there a way to preserve environment when opening new terminal? I.e. I do `conda activate coderefinery`, then `Ctrl+Shift+t` (open new terminal window) -- but the new window has `base`. Is there a way to tell `activate the environment from previous terminal`?
    - I would personally not recomment to [re-]activate an environment every time you open a new terminal. But if you insist, you may add a line in your `.bashrc` or similar that activates a certain environment: `source /some/path/activate environment`.
    - Thanks for that, but I've rather meant: Does bash terminal remember where was it opened from? If yes, is there anything like `source terminal.parent.env`?
        - Maybe, but I don't know. Asking colleagues...
        - This is not an answer but in my terminal (not bash) I wanted new terminals to open in the same folder as I was last time. And that was possible. I believe what you want to do is definitely possible but I would not know how to do that without searching. In my terminal (fish) I had to do some workarounds for this.
        - Alternative could be to use a terminal multiplexer like tmux. Could that make sure that new terminals are spawned in the same envionment? (it's been a while I used tmux so I don't remember)

93. Did we find a solution to `ImportError: cannot import name 'environmentfilter' from 'jinja2'`? I got this error with `sphinx-build --version`
    - Try updating sphinx with `conda install sphinx==4.4.0`
    - worked 👍🏽
        - awesome

94. What does `(sphinx)=` mean in top of source document?
    - in myst-parser, that is a reference anchor that you can link to.  (rather than link to heading names, give them an ID that won't change, and link to that).

95. I get the following, what to do?
    ```
    You have two options for placing the build directory for Sphinx output.
    Either, you use a directory "_build" within the root path, or you separate
    "source" and "build" directories within the root path.
    > Separate source and build directories (y/n) [n]:
    ```
     - We will get there in a moment. In the instructions for it says `<hit enter>` on this and some of the following lines

96. Sphinx doesnt seem to be able to import extension 'myst_parser'
    - It should be installed as part of the enviornment, but if not `conda install myst-parser` or `pip install myst-parser`
        - that worked, thanks (although I had to use pip, conda did not find the package...)

97. Feedback: the speed is just right :)
    - Good to hear.
        - totally agree, much better speed!

98. I am trying to reinstall the coderefinery environment because there were some errors popping up, and now I get the following message there were some errors popping up, and now I get the following message when installing: ERROR conda.core.link:_execute(699): An error occurred while installing package 'conda-forge::python-3.10.4-h9a09f29_0_cpython'.
    - hmmm. unsure what this means. was this all the error? or are there any hints inside the error?
    - I suggest you update `conda`.

99. Is the rst file intent sensitive? Ah, she just answered it...
    - answered
    - adding the answer here for the record: yes.

100. Is this documentation in addition to readme or an alternative?
     - often: in addition. it can be a good solution if the documentation gets a bit too long for a readme and gets too difficult to browse. but we often start with a readme file.

101. In Sphinx: are empty lines between things as important as the indentation?
     - yes, empty lines may be important before/after certain directives but it won't matter to sphinx if there is one or 3 lines between paragraphs or headings.

102. If I tab, I get four spaces, whereas the `toctree` subelements (eg. "caption") have three. Does this matter if I have _more_ spaces?
     - Sphinx cares about the difference between spaces and tabs, so it should be 3 spaces in any case.
     - More should be OK, I think (try and see).

103. (to be moved to previous section, sorry...) Is it possible to use snakemake within Jupyther? Crazy idea, perhaps... The goal would be to skip cells that have no updated input
     - first of all, no problems to ask questions about previous episodes. this is good.
     - it can be done but I am thinking whether I would do it this way. for me a notebook is often to do one thing and snakemake can be good to process many similar things in multiple steps. maybe you can describe the use case that you have in mind?
        - have the preparation of some data run only when the input has been updated, to avoid rerunning it from whitin the jupyter notebook that visualize some plots, but I guess it is too wilde.
           - thanks for explanation. this sounds reasonable to me.

104. The underscore could be to get the files listing at the top when sorting by name.
        - Or indicate that it contains generated files that will be overwritten every time and changes made to these files will be lost. Thinking of Python variables with underscores to indicate they should not be modified
        - I've also seen it as "semi-hidden file, you should mostly ignore it, but it shouldn't be really hidden."
            - And should therefore perhaps be added to your .gitignore

105. Could you explain when do you go for sphinx and when you dont use it? Perhaps some clarification on the level of complexity a project might have and adding some examples of a research software project? 
     - Commonly depends on the size of the project. If you have a "simple" script/a few functions, that can be handled reasonably in one README file sphinx is likely overkill. But as soon as you have some kind of package, or multiple code files that contain individual classes, a single README will probably not be sufficient (or gets extremely large), and you want some kind of "better" structure for your documentation. Same as your code actually. 

106. Got error:
     `There is a syntax error in your configuration file: EOL while scanning string literal (conf.py, line 26)`
     - You might miss a `"` in line 26.

107. I got this error. 
     ```
     usage: sphinx-build [OPTIONS] SOURCEDIR OUTPUTDIR [FILENAMES...]
     sphinx-build: error: the following arguments are required: outputdir, filenames
     ```
     - what was the command you used? Could you copy/paste it here?
       - sphinx-build ._build
         - There is a space missing between . and _build `sphinx-build . _build`, those are two input arguments (SOURCEDIR and OUTPUTDIR), where . refers to the current folder and _build to, well, the _build folder in the current directory.
           - thanks!!!

109. Could you clarify a bit the role of static website generators in code and project documentation, and why they are quite adopted in combination with github pages for instance? Why is html needed and what is its advantage? (This can also be related to explaining why jupyter lab is a server and is web based)
     - HTML is every site
     - "static site" is much, much simpler to host than something dynamic, so is easier to provide for free (e.g. university staff web hosting is often static).  And avoids the matter of needing to manage databases, servers, etc.
     - By making more things static sites, it's easier to deploy and share.
     - We technologies are also quite portable and cross platform since most computers have a browser, this allows to use applications in different contexts including local computers, servers, etc. Actually vscode is based on web technologies as well. 
     - Github pages also facilitates the publishing of static websites, therefore you dont need to host your website in a server to deploy it, very often projects rely on this github feature to share their project documentations, but there are other examples of this.

110. Could someone type the command that she used to open the `html`again ? :smile:
      - `xdg-open _build/index.html`
          - Thanks! Worked for me in Ubuntu!
      - Depending on operating system:
        - Linux users type: `xdg-open _build/index.html`
        - macOS users type: `open _build/index.html`
        - Windows users type: `start _build/index.html`

111. Extension error:
     Could not import extension myst_parser (exception: No module named 'myst_parser')
     - Are you in the coderefinery environment? You need to install myst-parser with `conda install myst-parser` or `pip install myst-parser`

112. is there a `sphinx clean` command like `make clean`or `mvn clean`?
     - not built-in, but `rm _build` (or whatever dir) does it
     - there is a Makefile-based way of sphinx (sphinx actually makes it automatically) and `make clean` does work there.

113. Where I can find a list of themes for sphinx?
     - https://sphinx-themes.org
     - https://www.writethedocs.org/guide/tools/sphinx-themes/
     - https://sphinxthemes.com
    
114. How did you change the style to look like the CodeRefinery docs?
     - in `conf.py` look for "theme" and for the lessons we use one derived from `sphinx_rtd_theme` (the Read the Docs theme)
     - Shameless advertisement: https://coderefinery.org/sphinx-lesson/ (but it's basically default sphinx featueres + sphinx_rtd_theme, nothing fancy here)


114. Can you inlcude an exisiting html file in spinx? I'm reffering to an exisiting .html-page. Do you need to include anything in extensions and source_suffix (in conf.py)? 
     - Yes, (not sure how)
     - you could add your own html to `_templates`

115. I am a little bit confused with the latex extensions: I added the 'sphinx.ext.mathjax' which works fine. Then I followed the link you gave to the myst documentaion. There it says: "By adding "amsmath" to myst_enable_extensions (in the sphinx conf.py configuration file), you can enable direct parsing of amsmath LaTeX equations." I am not sure exactly how to do this. Anyway, even without adding the amsmath the latex "gather" enviornment worked. so, is the mathjax enough?
     - Mathjax is enough. 
     - I think mathjax is in Sphinx and works with any parser
     - The amsmath this is specific to myst-parser, and changes how it parses things.  So that it directly parses LaTeX, instead of needing to wrap it in the generic directives.
         - but how can we add the amsmath? like: myst_enable_extensions = ["amsmath"] ? so adding this line in conf file below the extensions = []...
         - Yes, I think like that in `conf.py`.  I haven't done this myself before.
             - Seems to work. but I removed the mathjax extension. Correction: I think i need both, mathjax and amsmath...

116. The numbered lists with `#.` is not working; instead, one should use, e.g., `1.` for every numbered item (the ones are on purpose, `markdown` automatically uses the correct numbering):
     ```
     1. item 1
     1. item 2
     1. item 3
     ``` 
     - I guess that is left over from ReStructured text, myst-parser is different.  thanks for pointing it out!
     - thanks for pointing this out, it is now an issue on the lesson: https://github.com/coderefinery/documentation/issues/224

117. My code blocks don't have the handy copy-button on the top right that the lesson materials have?
     - It's a separate Sphinx extension: https://pypi.org/project/sphinx-copybutton/, https://sphinx-copybutton.readthedocs.io/en/latest/
     - There are many, many other extensions that do all sorts of things.

---
#### Exercises until xx:28
https://coderefinery.org/documentation/sphinx/
Exercise Sphinx-2

118. I did not quite understand the instruction after point 3, Experiment with the following Markdown syntax: (Thanks to hackMD, I can ask these kind of questions). What should we do at this step?
     - Try adding the lines below to your documentation pages and see what happens.
     - Note 

119. I can't get the table to work - are there any important indents or something here that is not evident from the exercise text?
     - no indent should be needed but trying this also on my side
     - you have an empty line before and after, right?
     - The empty line was what was important
       - ah good 
     - also make sure you try the table in the md file (this is markdown formatting)

120. I get "WARNING: toctree contains reference to nonexisting document 'feature-a.md'"
     - have you created that file? `feature-a.md`?
         - Yes, I did. 
             - is it on the same level/directory as `index.rst
                - Yes, it is.
                   - interesting ... hmm ...
                   - maybe a 
                   - typo in the filename?
                       - Mmhh.. nope.
                       - very interesting... maybe try by renaming the file and also the filename in toctree in index.rst (sorry I really do not know what could be the issue here)

121. Sphinx is based in Python but is it effective to write documentation about other programming languages? what about Java for example? 
     - yes it can be used for any project. it historically comes from python and has good support for docstrings but we use it to create these lessons and to document Fortran/C/whatever projects.

122. For adding links (Sphinx-2 exercise), is the "!" sign missing in the documentation?
     - the exclamation mark is for image links in markdown. "normal" links work like this: `[example](https://example.org)`
         - Oks. It is not working for me... 
            - and this is inside a md file?
                - Yes. It finally worked: without the "!", as you suggested. Thank you. I had a typo before the "http:/...". When I built (sphinx-build) with the typo inside the md file and without the "!" --> I got error messages. // Adding the "!" inside the md file --> error messages desapeared but the link was not working in webpage. Everything fixed now! Typo removed and "!" removed. 

123. Can we link to our private repository (github)?
     - sorry, in which context? in Read the Docs? or from where would you like to link?
       - i dont want to share my code, but just want people to know that there is somehing like this software which is paid service. 
         - one thing that can be done is to have the documentation on a git branch and put that on a public git repository and to keep rest of the code in a private git repository 

124. Can Sphinx interprete a mixture of markdown and html? Some tools do this and I find it convenient.
     - You can insert raw html, but Sphinx isn't a HTML generator.  It can generate PDF, epub, text files, etc.  So the philosophy is to avoid that, not tie yourself too much to one thing.  And I think this is where a lot of the pwore comes form.
         - yes, exactly. And it is also about keeping up-to-date while keeping legacy files

125. I like the customized prompts in general; which tools do I use to do that?
     - This is a big topic, search the web and you can find plenty (or join our chat and find a particular instructor to ask)
     - Some general info on what we do: https://coderefinery.org/manuals/instructor-tech-setup/ (but it hasn't been updated in a while)


---
### Feedback

Today was:
- too fast: oo
- too slow: oo
- just right: ooooooo
- too advanced: o
- too basic: o


#### One good thing about today:
- Very interesting topics today! +1
- Sphinx part was really nice! +3
- Samantha's pace was perfect and sphynx will be VERY useful. Thank you!+1
- Well paced +5
- Speed
- interesting, useful topics: Will be of great use.+1
- Good speed and range of topics to cover
- Great to build our own documentation as an exercise +2
- HackMd :) +1 and quick responses.
- Good Sphynx :+1:
- Sharing exercises for breakout rooms ahead of time- thank you!
- That the installations/preparations were instructed to do beforehand
- git diff through jupyterlab was very nice to learn.
- having the exercise plan at the top of the hackmd was very nice
- I really liked Samantha's style of type-along (pace, showing commands that were used, explaining what she is doing , typing instead of pasting). :+1:+2
- More Samantha! +1

#### One thing to be improved
- Emphasize when to use the tools and perhaps how projects might progress from simple readme to a mature documented code base  with sphinx for example. That evolution and process can be very relevant to see.
- In the first part the pace was too fast
- May be make it clear if it is a type-along or watch. But it is understandable that you might not remember to mention everytime. 
- Would have been nice to make it to collaborative documentation
- Maybe too many topics for the time? The pacing was good so maybe spreading it out more like Git last week.
- I would have liked to have the time for an exercise about using Git/GitHub with Jupyter +1
- The README file example in breakout room works well only if all the attendees have experience with the same tool or are all used to python and can quickly read the given code. In our case none of these assumptions was verified, so it became a vague discussion mostly repeating what had been already stated in the main stream.
- just as you had the exercise plan on top, maybe also write when breaks are planned?
- How to publish the documentation, i.e. how to put the stuff generated by Sphinx into a real accessible website
   - We had to skip this for time, but see https://coderefinery.org/documentation/gh_workflow/
   - EDIT: Thanks, I'll check that 
- As mentioned above , say when type-along and when it is a demonstration. In fact, I would avoid demonstrations - we learn more if we do it too ( I appreaciate the time factor, but it is worth it to have less material but do it all in the type-along mode)
- I can only speak for my group, but I would suggest revising the timing of the exercises (20 min for Jupyter notebook was too long; 10-15min for everything else was right/ could be longer )


#### Any other comments:
- Please avoid highly customized prompts as they make it very difficult for users to see the analogy between their terminal and the one of the instructor. For example, Thor's prompt is very cool, indeed, but it increases the flow of information as well as the demands of interpretations for learners.+1

- In the exercise https://coderefinery.org/documentation/gh_workflow/#exercise-deploy-sphinx-documentation-to-github-pages, there's a mistake in this step: "That’s it! Your site should now be live on `https://github.com/<myuser>/word-count/settings/pages` (replace username).". The link should be username.github.io/word-count/ 
     - Thanks!


