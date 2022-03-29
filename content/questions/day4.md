+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 4

![](https://github.com/coderefinery/2022-03-22-workshop/raw/main/map/CR_participantmap_2022-03-15.png)

## 0. Intro 

- Join us:
  - Twitter hastag: #CodeRefinery22
  - [Everyone welcome to the community call next Monday 14 CEST](https://coderefinery.org/organization/meetings/)


### 0.1 Icebreaker question

Computer programs are expected to produce the same output for the same inputs. Is that always true for research software? Can you give some examples?

#### Answers from the audience

- Solving chaotic differential equations: rounding errors produce different input -> output gives a different solution
- Bug in the compiler (because the code is always correct ;)...)
- (true for:) circuit simulation (SPICE)
-  (yes) if I run my simulations, I expect the same results for the same inputs (geometry, material, loading)
- Ideally it's true, but one must verify and validate the software if changes have been made.
- It depends.
- Calculations based on random number generator (or some random initial guess) would have always some numerical differences
- But Monte Carlo calculations that are based on random number generation gives solutions that converge to the "real" value. For example we can use Monte Carlo to calculate Pi. +1
- Different versions of a software package can produce different results, even if the program is identical.
- Interpreter version has changed.
- Uncertain which version of software used.
- Which set of data was actually used.
- Perhaps compilers and libraries can change versions.
- I have had different results with different versions of computational tools (bioinformatics)
- Sometimes, I have heard, in GPU programming you need to state explicitly that the memory transfers between CPU and GPU or inside the GPU have to be done exactly in the same way, otherwise there will be small differences in the results. This could be linked to how arrays of memory addresses are split into batches.
- Yes, even stochastic simulations (pseudo-random, that is) should be reproducible in some set up (e.g., by-passing parallelization issues). Otherwise it is impossible to debug and test.
- Summarizing: I think one needs to specify what is meant with **"same output"**
- Different results with release and debug builds.
- If software version/code and data is clear, the same input should give the same output each time.
- Regarding random seed: you should run it with _multiple_ random seeds. A lot of ML results are "lucky random seeds"... Random seed isn't enough. You also need to specify the RNG type itself. E.g. Julia changed the default algorithm multiple times ...
- I use fixed random seed. I am making UMAPs with data from 10000s cells (bioinformatics, R). So without using random seeds my figure will be different everytime.
- Ideally it's true, though in my experience if there is a longer time between runs you often run into dependency issues.

#### Questions from the audience

1. Should we report a random seed in a publication?
    - If you are reporting code or an algorithm, I would like to see the seed (and any other parameters) if I was peer-reviewing. But I'm weird, I teach in this workshop :smile:
        - More likely, provide a link to the code and include a test with a specific seed.
    - Your code could accept "seed" as one of the (probably many) configuration parameters. Then you could/should publish it together with all other settings you've used. Random seed by itself is useless without being tied to a *specific* version of code (e.g. just changing line order can change effect with multiple random() calls).

2. Are (paid) programming languages like MATLAB more difficult to share with the community? (generally speaking). Thanks for all the answers :-)
   - I guess you mean beyond the obvious "not everyone can get access to them".
   - Somehow, I have a feeling that open ones are better designed for plugging into other workflows, but it depends on how you use them.
    - I think it's not necessarily that they are "paid", just that often they are bad languages. Maybe because less community around building the language itself (feeding back what works and what doesn't)? Matlab code for example I often find completely incomprehensible.
        - I find javascript incomprehensible, that isn't necessarily a result of the language being paid, just of your experience with it.
            - Oh yeah! Plenty of bad code out there. My thought was more that it might be relatively worse for languages that don't have a community around _building the language_.
                - yet, many communities are writing tons of bad languages...  ;-)
                    - :+1: 
                - There is bad code in all programming languages. I used both Matlab and Python a lot and I don't feel like there's a big difference tbh. But that is just 1 person's opinion of course, I don't know any wide spread research or results about this.
    - Everyone can still open matlab code in notepad and see what the code does, so that way you can still "share" it.
    - The code that you build is shareable like any other code. But as mentioned, if it depends on any built-in libraries, it is not necessarily usable. Also: You get into more trouble with building e.g. a CI system, since you need to run Matlab on the CI system.

---
## 1. Reproducible research and FAIR data

https://coderefinery.github.io/reproducible-research/

### 1.1 Motivation
https://coderefinery.github.io/reproducible-research/motivation/

3. I could not spot the instructions to download and install Snakemake. Can you please direct to those?
     - it is part of the Conda environment (https://coderefinery.org/installation/conda-environment/) so if you have installed that one, then you have snakemake
         -  working with conda 4.12.0
 and snakemake is not listed in `conda list` alas
     - we will later also discuss what Conda environments are but if you want to see what is inside the one we provide: https://github.com/coderefinery/software/blob/main/environment.yml


4. Like anything in research: it depends ;) (should software and data be reproducible and are they?)
    - yes, and it is such a spectrum of what can be done and it can be difficult to decide how far to go.


5. Tip, not really a question. Open-access article on the terminology behind reproducibility and replicability: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5778115/
which is not quite uniform as we may wish...
    - thanks for sharing!
    - :+1: 

#### **Open conversation:**

**Computer programs are expected to produce the same output for the same inputs**

#### a. Is that true for research software?

#### b. Can you give some examples? 

#### c. What can we do about it?


- Not always. Different compiler versions and optimization flags may lead to different results even for the same input. Very important to keep in mind if you need high accuracy. It is always a good idea to track the compiler versions and `Makefile` used.
- Numerical issues for unstable systems can lead to different results on different machines (Happened quite frequently for me during my work with Linear/Integer programming). 

---
### 1.2 Organizing your projects

6. (curiosity) About folders and directory structures. How does this couples with the growing generation of users that do not have a strong concept of "folder"?
    - It needs to be explained to them. Mainly because there needs to be some kind of structure for a more complex project than just "throw everything in one place"

7. What would be the best way to incorporate jupyter notebooks in the project directory?
    - if possible close to the data and close to figures. it could be a separate folder if it helps having the overview ("notebooks"?). Later we will also see how we can make notebooks available to others via GitHub/Binder. but definitely good idea to keep also notebooks under version control and to back them up on GitHub/GitLab.

8. [This paper](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510) has another example of **project organization**:  and there is a nice template that someone made based on it [here](https://github.com/bvreede/good-enough-project)
    - The first author of the article is the founder of the Carpentries, remarkably
    - Thanks for sharing
    - Note: by template I meant that it lets you create the project structure in a new project, but it's not a GitHub template that lets you copy the repository.

9. Are you recommending to use an IDE (Spyder, Vscode), or should we work also with `nano`?
   - We only use `nano` here since it's simple and can work for everyone.  Usually you would want something more fancy.
       - Would you recommend then to use an IDE after the workshop?
           - there are many editors and some people prefer a tool that is "only" an editor (me for instance) but many people like to have more integrations and tools like vscode, spyder, ... offer very nice features such as git integration and also it will mark typos on the fly. so yes: I would recommend to have a look at a number of editors and choose one that you like best. since we all often spend quite a bit of time editing files and code it pays off to invest some time learning an editor and choosing the one that you like best. +1

10. How to deal with using software from other people/libraries alongside your own data or code?
    - the best you can... it can be hard, I wish I had better ideas
    - (at Aalto, you could ask the RSEs for help rather than struggle yourself)

11. What is meant by consistent and informative directory structure? Could you give some examples maybe?
    - Informative refers to giving useful names to the directories and files. Consistent in this context means same across multiple of your projects, same in the group.  Directories used for what they are meant for, not mixing up too much.


12. (comment) Git tag (or at least commit) for before/after review etc. is super valuable!
    - yes! then if you want to find out what changes were made later, you can diff with respect to the tag and create a list of changes.
        - I totally agree tags are so useful. One should just keep in mind that the only unique identifier is the hash of the commit. Tags can change, although that is very bad practice for shared repositories.

13. Could you elaborate on a Google Docs workflow. (asking in case there are features Im not aware)
    - Google docs can be used to collaborate on a document. Multiple people can make changes and it tracks changes in time.
        - Compared to Git and text files, Google Docs lacks branches. Everyone is editing the same version
        - Google docs has comments and suggestions, instead. You can make your edits into suggestions. Someone else can then accept those suggestions. (So similar to code review.)

14. This lecture provides sugguestions which is based on git and version control. What if I don't need to share my project on GitHub, but internally within the organization or across two organizations?  
    - One option is your organization setting up an internal GitLab service. Another option are private GitHub repositories that you share only with your collaborators (within or outside of your organisation). At least for academic users organisations can have private repos for free, this might not be true for industry. And at least once you publish your research, the code should be made publicly available, and github is a good place to do this. 
    
#### **Open conversation**

##### a: How do you collaborate on writing academic papers?
- git/latex/overleaf
- Depends on the co-authors. But Overleaf is one example for Latex and it has version control integrated. Google docs too, although it's not my favourite.
- I am old fashioned, and use word and mail back and forth with co-authors.
- HackMD
- GitLab
- Forced to use Microsoft Teams :( 
- I use Overleaf, but never tried the version control function
- LaTeX (sans Overleaf due to it being slow to recompile when iterating quickly)
- Overleaf (I would be happy to use git also, but the other authors are not keen on this)

###### b: Are you using version control?
- absolutely yes :-) :+3:
- Yes!
- Yes, for many years (and I still find myself looking back at my (recent) past self wishing I had made _more_ use of it, committed more often, thought more about what to put into a single commit...)

###### c: How do you handle collaborative issues?
- coordination still over email and sometimes running Git only on my side to synchronize if my collaborators don't like git
- using comments in overlaf
- Communication (via issues or sometimes emails or meetings) and a good set of guidelines.

##### d: How would you like it to work if you could decide?
- hackmd in very early stage and later git and pull requests/ merge requests for improving the draft

15. Perhaps it's worth mentioning Slack for collaboration in teams?
    - yes many chat solutions exist to simplify communication within a team/project
    - Slack/Zulip/... a lot of them, and somewhat too many if you have collaborators on all of them... 
    
16. What is the difference between a template and repo in Github.
    - A repo in Github can be a template (that is, a template is a repo)
    - Marking a repo as a template allows others to copy it automatically, without the copy becoming a fork.
    - I like to think of a GitHub template like a "cookie cutter" form or a blueprint. It can be useful if you would like to create similar repositories with a predefined structure from a template.

---
### 1.3 [Dependencies](https://coderefinery.github.io/reproducible-research/dependencies/)

17.  If we add dependencies later in the project, when the project is ongoing, does it affect our results? For eg we might not know all the dependencies at the beginning of our project. 
        - Yes, using a different version of the dependencies may affect the results.
        - How do we do this if needed?   
            - One way is to contact the code author and ask to add a list of dependencies to the repo.
            - I mean not for other's project, but when starting my own project. 
                - Start by tracking the version of the compiler and the libraries or other dependencies you're using. If you're programming in Python for example, working in an enviornment "forces" you to work with a limited number of dependencies which are easier to track and adjust.

18. Do dependency packages "disappear" from the web after a certain time?
    - It's always something to consider!  (also when picking your dependencies)
    - In general they should not, this would be a bad thing :smile: Of course some times the maintainer of a library stops maintaining it, and might even take it down.
    - This also depends on the programming language and dependency management system: for example, something on a personal webpage will disappear, something on the Python Package Index probably won't. They can use different licenses and rules about keeping copies of old versions.

19. In practice how do we handle the fact that having many conda environments take up a lot of space, is the solution to just delete them when we are not done?
    - Yeah, mananging them that way is important.  If you have the requirements/environment file you can recreate later
    - Also disk space is much cheaper than time spent solving problems later, so this hopefully doesn't happen too often in practice.

20. I am very uncertain how to best organise my environments. I.e., how should I treat my base-environment? What happens when I need to use several of my own-written packages in the same project? Will we discuss some best practicses here?
    - I'm not really using my base environment at all and essentially build specific environments for current projects. And if you use mamba instead of conda to build them, it doesn't take ages to recreate :)
    - What about updating packages within a project environment? If I spend several months on one project, I don't want to risk breaking anything by updating all pacakges in my environment. But I also want the most up-to-date packages?
        - That's where you want to set versions in the environment.yml file. If you want to start with the "latest" version, you can leave the version unspecified initially but once you have set it up, freeze it, so that it doesn't change. And if you want to update: update the requirements file and rebuild, test, whether it works, and if it does: all good. IF it doesn't stay with the old. But yes, if you need to update because you have some new feature that needs an updated version of something, than you need to handle the conflicts.

21. Should we be aware of the fact that environments can take  lot of memory because they copy special versions of many packages separately? Once I saw a conda environment take up 4GB on its own...
    - Yes, aware: definitely. 
    - Normally memory is not an issue these days but maybe you are working with partitions or in a cluster with a limited memory quota (possibly managed by a strict, stubborn and insensitive administrator)
        - The only suggestion I would have for this situation: Ask for some place, where you can store larger amounts of data, and put your conda environments and packages there.


22. Should we create a new environment.yml everytime we need to use different versions of dependencies?
    - I would recommend a separate `environment.yml` for each project since different projects can have different dependencies. Bonus: you document the dependencies at the same time.
        - If it's the same project, good practice is to version control it, this way you will also be able to check the `environment.yml` at different stages of the project.


24. Is the commit hash in example C a good idea? I.e. if someone does `git rebase`, it might be lost. Or have I misunderstood the `rebase`? 
    - You understand correctly.  You'd want to be careful, but something on a main branch is probably safe.
    - If you want to be absolutely certain: Fork the repository and refer to your own fork.

25. Why are there two equalsigns in the requirements file (==)?
    - To specify the _exact_ version. If you say `numpy==1.20.4` then it _has_ to be this version. In principle, you _should_ get equivalent results with numpy 1.21.3 (backwards compatibility), but that's not guaranteed. When you write _libraries_, you should aim to provide "lower bounds" (e.g. `numpy>=1.20.4`) only, so other people can use your code in different environments. When writing _"end" code_ (e.g. for paper experiments), you should specify all versions exactly.
    - Does one equal sign even work at all?  I think two is required.
        - :+1:

26. Is D really the safest option? If another user than 'someuser' has a 'someproject' with version 1.2.3, you still don't know which project to use?
    - These are references to central indexes (conda, Python Package Index, etc.), where the names are unique.
        - Aaah option D does not refer to the same repo's as option C. I thought the two were interchangeable ways to point to the same things.
        - But in this case yo;u 
    - not sure I fully understood the question but D assumes that there is one well defined place that holds packages (such as Conda or PyPI) so the versions refer to the same project. perhaps I misunderstood the question?

    - The way I see it, D assumes that 'someuser' is the only person with a 'someproject' repo, so if other people have the same repo, the github link would be the only way to differentiate.

27. the git hash has higher resolution than the version number, sometimes. For example, vertion x.y.z is the result of a number of commits. So "D" sounds safer than "C".
    - The last two lines in "C" do point to specific commits. "C" is a safe option.

28. Just to confirm, option D assumes that someone has put those packages online right?
    - yes, right


29. Should you have a seperate environment for every project?
    - I recommend it. This way you avoid version clashes and you also keep things documented. I like doing it this way because if I mess up something, it does not affect my whole system but only one folder.

30. Can `pip freeze > requirements.txt` give all the requirements that are installed using the conda install command?
    - then I would use the conda equivant of this. But yes, conda can also export into requirements.txt. I just need to find the command for this (I don't do this often enough). I often go the opposite way: I first add the package to environment.yml or requirements.txt and install from that. Then it's already documented and also it contains only the packages that I actively installed and not their dependencies.

31. What's the difference between pip and pip3 and why is pip3 sometimes the only thing that works (using Mac?)
    - It's related to how Python is installed.
    - `type pip` and `type pip3` might give hints about which is which.  I often run these commands to verify it is what I expect

32. The hackmd window is going up and down wildly as I type, up to the point I loose the cursor, I dont remember this happening in the previous days.
    - hmmm. ah there it happened to me too. let's see what we do about it.
    - I tried to reduce size, let's see if it gets better...
        - there was someones browser resending data. Not sure how that happens though, but it changes the document and hackMD tries to adapt. 
        
33. If I activate a specific environment, and then do the pip freeze > requirements.txt, will all the packages in just this spesific environment be written to the .txt?
     - yes
         - Nice!

34. What is the difference between pip and pipy?
    - pip: thing that installs packakges.  A software.
    - PyPI: default place to find packages to install (pypi.org).  A platform.

35. What is a .yml file? (as opposed to a requirements.txt)
    - environment.yml is to Conda what requirements.txt is to virtual environment. Same idea. Conda can use both but more often uses the yml file. Python virtual environments use the requirements.txt. But same idea.


36. Difference between Conda, miniconda, anaconda, please?
    - Anaconda comes with more than 150 different packages, while miniconda only comes with a handful. Both Anaconda and Miniconda use Conda as the package manager to find and install packages.

37. I've had massive troubles with getting conda environments to work across different machines. I've had to use a --no-build tag, and even then I've had troubles coming back after several weeks to install it again.
    - Yeah, unfortunately it's more complicated than you think!
    - I think it partly is because of versions avaliable on each particular platform (e.g. windows build won't install on mac).
    - I would recommend looking at the requirements and then narrowing down to what is really needed.  Unfortunately this is annoying.


37. Where do we find the .yml file we should create our new CodeRefinery environment from?+1
     - Follow https://coderefinery.org/installation/conda-environment/
     - The file itself is actually here: https://github.com/coderefinery/software/blob/main/environment.yml

38. Can we activate an environment without deactivating before or do we have to deactivate, then activate?+1
    - I think it could work without deactivating first.  But I wouldn't recommend it.
    - And it's even wors when they are different kinds of enviroments: load module then activate conda.  or activate conda then activate virtualenv.
    - So better to assume it does *not* work and always start from scatch.

39. Where do you normaly store your environment, centrally or locally in the project's folder? Any advantages and disadvantages on the two options?


### Exercises until xx:05, then break.
### [Dependencies-2](https://coderefinery.org/reproducible-research/dependencies/#exercise-exploring-conda-environments)

Explore most commands there, if you can't finish it all there is no problem

I am:
done: oooooooooo
need more time: ooooooo
not trying: oo

39. Why after doing [this step](https://coderefinery.org/installation/conda/#setting-conda-path), I cannot find my Anaconda Prompt anymore? And after some time, I have to do it again because git bash does not recognize 'conda' anymore. What could be the reason?
    - I'm not sure, we would need to look.  Can we look later, or find someone local/in Zoom/etc to as''k?
    - I am not sure whats your problem exactly, but I realized that one has to be careful with the "conda init" command. it modifies the .bashrc file and comments the line with the export path command. Also, for some reason the conda activate command did not work for me (although `PATH` was set up correctly) and I needed to go to the env folder and use "source activate ...."

39. `conda env export > environment.yml` In this step, what if there is already one `environment.yml` file? Will it create another for next version?
    - I'd use a different name to export to a different file.


41. how do i compare the `.yml` file format to the `.txt` file format?
    - For now, open them both in editors and look
    - The `diff` program would be used in general, but the yml and txt are probably too different to be diffed easily.
    - You can use "vim -O <one.file> <other.file>"


42. At first I was under the impression that the .txt files would be cross-compatible between pip and conda, but the requirements.txt file from conda has extra =pyxxxx at the end, what does this mean, and does it mean i cannot use pip install -r requirements.txt (just tried pip install -r requirements.txt and it does not work).
    * the last extra =pypi*** / =py*** / =hc** tells about the build of the package, ie what platform it was originally built for, these might be different between pypi and conda; might be that you need to remove the last '=xx' part from the requirements.txt to use it with pip, BUT not all conda packages are also available in pip
    * in conda environment.yml files pip can also be installed and then further packages can be installed with pip within a conda environment
  

43. How to delete (uninstall, not deactivate) conda environment after the course?
    * see last point in the exercise: `conda env remove -r myenv`

44. Ref question 36: what are your experiences using ```conda env export --from-history```and ```conda env export --no-build```to resolve any issues across different platforms?
    - I would try that, yes
    - It's a balance between "exact versions" and "enough flexibility to work on different OSs".  Yes, it's hard!  I try to lean towards flexibility a bit.
        - We just had some problems with the CodeRefinery environment on Mac M1 processors, for example!
    - uhm, reproducibility that fights portability?
        - Great quote, good description of the problem.  Things have to be carefully designed to be reproducible *and* portable :+1:
    - Example: `python=3.9.7=h12debd9_1` includes the build ID (`h12deb9_1`) that won't work on other OSs.

45. I get`access denied` when trying `conda list --export > requirements.txt`.Any idea why? 
    - Are you in a directory where yo uhave permissions to write?
    - I though I was, but I wasn't. Sorry, my bad.

46. Worth pointing out that the coderefinery environment.yml file doesn't work on an M1 Mac if running ARM compiled conda (currently I'm only aware of Miniforge3 providing this). I just installed all the packages without version specifications, so hope that will be okay...
    - It's probably OK, we give the versions to avoid problems, not because exact ones are needed
        - ... good example of solving problems making new problems.
    - We found this and hopefully will be fixed soon.  This is a good learning experience!

47. HOw to quit vim? :q did not work. I need to have !, but where?
    - ESC : q   or   ESC : q!
    - After exiting insert mode (you can exit insert mode by pressing "esc") you have to type :q!, but it force quits and does not save your work. If you save your work first with :w then you can quit with just :q. Or you can save and quit with one command which is :x.

### Break until xx:17

47. After running... 
   - question was never completed


----
### 1.4 [Recording computational steps](https://coderefinery.github.io/reproducible-research/workflow-management/)

48. Is this a type-along exercise?
    - yes, type-along with us now

49. What is 'Gitpod' button?
    - it seems this is an integration that the instructor activated for https://www.gitpod.io/ where one can have containerized environments in the cloud (? I have never used it myself so I am not 100% sure how it works)

50. Why are we not cloning directly from their page?
    - We might be using it as our own upstream for later exercises (not sure though).
    - We modify the repository later. In the documentation section, we will use some GitHub features with your accounts.

51. Where are the questions of this morning until 13?
    - "archive HackMD", link should be at the top
        - https://hackmd.io/@coderefinery/archive-workshop-2022-march
    - motivation why we move older questions to the archive is that if this document gets too long, it may get slow/stuck

52. Missed that whole last bit as I was trying to exit Vim. What's going on and am I supposed to follow along?
    - You should create a word-count repository from the template here: https://github.com//coderefinery/word-count
    - Then clone it to your computer (git clone ...) 

53. Please, could you do this a bit more slowly. It is too fast
    - Even though there will be an exercise, too fast now will not help then either

54. I am getting the error ```/word-count/source/wordcount.py", line 37, in load_word_counts
	counts.append((fields[0], int(fields[1]), float(fields[2])))
    ValueError: invalid literal for int() with base 10: 'JOURNEY'```
    - I am looking into this ... trying to reproduce/understand this on my side first.
    - Could you copy/paste the command you used?
    - Yes: `python source/plotcount.py data/isles.txt processed_data/isles.png` I am using Ubuntu 20.04 if that is of any help. Miniconda with the coderefinery environment installed as instructed (python 3.10.2).
        - I can confirm this error on my system. 
    - It should have been this instead: `python source/plotcount.py processed_data/isles.txt results/isles.png` . In other words, that script expects two arguments: the processed data and the output image file name. The script got confused since it got the raw data as input instead of the processed data.
        - It worked, thanks!

55. This is so fast. Even if we are going to do this later we need to understand what is happening.
    - If you have cloned the repository, don't worry.
    - No, I haven't. I lost the track there.
        - Go to https://github.com//coderefinery/word-count. Use the green "Use this template" button to create a repository. Then clone the new repository.
        - steps also at https://coderefinery.org/reproducible-research/workflow-management/, in the Exercise preparation section

> HPC: High Performance Computing 

56. What happens when you run the workflow many times and you want to save some results? How do you do if you want to persist results and still use the clean subcommand to rerun the workflow again? Can you also add an operation to store data in a database with snakemake? Or is this mainly designed to be used in the context of HPC?
    - The first thing that comes to my mind is storing them in a separate folder.

57. Snakemake is a "meta script"? The script that rules them all!
    - Snakemake is a software that runs rules in the Snakefile.  But yeah, the one tool to rule your whole workflow.

58. Is Snakemake like an advance bashscript?
    - More advanced than a single script, in that it knows of different steps and can re-order them and only run the necessary parts.


60. What's the advantage of snakemake as opposed to a top-level python script that runs all the other scripts in approriate sequence? I also didn't quite get how snakemake is not 'imperative' and in that case what is the advantage of not being 'imperative'.
    - advantage of workflow tools like snakemake is that it will not run all steps every time if not all need to be rerun. it will only rerun steps where the "input" is newer than the "output"
    - declarative: meaning that we describe dependencies but not the order and the order is inferred from dependencies

61. Is snakemake as portable or moreportable than bash (or any other shell)?
    - I would describe it as equally portable. Maybe even slightly more portable since snakemake can run on Windows but bash may or may not be available on Windows (the latter requires Git Bash or WSL)
    - but the competitive edge of snakemake is perhaps not the portability but the fact that it does not need to run all steps every time, see also question 60 above.

62. If I interrupt snakemake half-way does it catch up where it was interruped?
    - In practice, yes: It will use any files that were already generated. If you interupt it during a step, it will have to redo that step.

63. I don't really understand the advantages of snakemake compared to a shell script, so it only prevents you from running and overriding other results. But in a shell script, for example, you can specify arguments that also can fulfill the same no?
    - Everything can be done some other way.  Sometimes it's convenient to have a tool that already works - all depends on the person and what you do.
    - Sure it could be done with a script, but IMO specifying the dependencies would essentially lead to something similar like `(Snake)make` or a complete mess. If you have to compile 1000 source files where 1 depend on others, can you imagine the for loops over dependencies...
    - if everything takes few seconds or minutes, go for a script. but if you have many steps and some steps may take a long time, you will not want to rerun everything every time and then you can benefit from a workflow management tool such as snakemake

64. If we add one more book in the input folder, will it just run for that one book and ignore the rest?
    - Snakemake will realize there is a new book and run all steps for that one book. (Unless you remove the existing results)

65. When trying to run snakemake, I get the following message: bash: snakemake: command not found. Do I miss anything?
    - It shoul de in your conda coderefinery environment. Did you activate it?
    - Works now! Thanks!
    

66. Does changing the Python code rerun all computations?
    - If not, you can make it do so (I don't remember exactly how this one is set up)

67. Is declarative style better than imperative style?
    - Depends on the situation. It allows the computer (or the program you are giving isntructions to,) to optimize the workflow more. It is also less predictable, you have less control.

68. I feel like too many new tools are interesting, e.g., snakemake, and it is impossible to learn new tools all the time. Can you do it with e.g. bashsript instead of snakemake?
    - similar questions above. bash script can be perfectly reproducible also and if the whole run takes few seconds or minutes, it might be the simpler tool and perfectly fine. but look also at 60 and 61.

69. Does Snakemake also throws errors somewhere? I ran the command but it stopped immediately without saying why (it is installed in the environment that I am using though).
    - Maybe if everything is already done, it does this?
    - I don't think so, it is the first time that I am using this

70. For the declerative style the actual data files are not listed (snakemake searches a directory). But if the contents of that directory changes would that make the workflow less reproducible.
    - Yeah.  You then need to track the inputs.

71. The project direcotry structure looks useful. I think we have freedom to change slightly according to our needs. Right? The structure is especially useful when you are writting paper in latex. I feel less useful when writing paper in word. The figures are still copy-pasted into the word document not knowing where they come from. Is it right?
    - Yeah, everything is flexible depending on what you actually do.
    - Correct on "pasting figures without being able to track their source" - you need to be careful in other ways.

72. Am i correct to assume `snakemake --delete-all-output -j 1` , deletes all previous generated by snakemake? it is not explicitly mentioned what it exactly it does.
    - Yes.  So you get a "clean up" operation for free.

73. Before learning of Snakemake, I would in all cases have chosen to do this kind of processing in a dedicated Jupyter Notebook. Are there any reasons that this would be a very bad idea? It seems to me to be a clearer way to document a particular workflow, especially to someone who is not as up to date with new technologies (i.e. my soon-to-retire supervisor)
    - Jupyter can easily run top-to-bottom.  What happens when some need skipping, run them in a certain order, one thing changes and others don't need to be re-run?  This can't be tracked
    - If your workflow is short, it doesn't matter: jupyter is fine
    - Snakemake and similar tools really shine when you might be running on tens or hundreds of inputs and it takes hours or more to run.  (and once you know it, it's easy for small things, too)
    - Thanks, great answers

### Exercise until xx:00
[Exercise Workflow-1](https://coderefinery.github.io/reproducible-research/workflow-management/#exercise-using-snakemake)

#### Poll
I am:
- done: ooooooo
- need more time: ooo
- not trying: oooo


74. Is this expected or am I doing something wrong? P.S I don't use python.
    `source/wordcount.py`
    i got this:
    `source/wordcount.py: line 1: import: command not found`
    - are you running `python source/wordcount.py` ?
    - No only `source/wordcount.py`
    - Also with `python source/wordcount.py`, I get this:
    `line 125, in <module>`
    `input_file = sys.argv[1]`
    `IndexError: list index out of range`
    - Then it needs more arguments for the input file.


75. Any pitfalls to consider when needing to process larger datasets stored elsewhere, e.g. external harddrive, server, on NIRD etc? I've had issues using Git from remote storage spaces before for example. Typically my need is to pre-process some larger raw files, and will then do actual analysis on the smaller, easier to store locally, output-files.
    - Data management is a big issue, and yes, you need a way to track and manage these files.  What you use is up to you (we don't go into more detail here), there are different options per field.
    - [name=rkdarst] really likes something called git-annex, but it is not easy to learn so maybe can't be recommended easily.
    
76. I totally lost the part of the Snakemake as I was busy with the previous parts. This part was too fast. but anyway, now my question is should we make our own snakemake? how we can make it? I totally lost the whole explaination of the snakemake file and should rewatch the recording for that.
    - Snakefile defines steps for your work.  If you have a project that need this automation, you would make a Snakefile and then your workflow is automated.

77. Advantage of `snakemake -j 1 --archive ` over `tar -cpzvf`
    - see below

78. What does it mean to "archive a workflow
    - It makes a .zip / .tar.gz with all dependencs and scripts needed, for you to run somewhere else.

79. snakemake not considering 'make_plot' as multiple thread option?
    - you mean why it doesn't have `threads`?  I wonder if that is just an example, I doubt any of these are actually multi-threaded.
 
80. I am getting error once running "snakemake -j 1 --dag | dot -Tpng > dag.png". the error is `"Error: <stdin>: syntax error in line 1 near 'Error'".`
    - try first to run the part before the "pipe" (the | symbol) as probably that part gave an error and then the second part of the command (the one after the pipe) got something unexpected
    - it has been fixed
      - good :-) 


---
### 1.5 [Recording environments](https://coderefinery.github.io/reproducible-research/environments/)

81. So docker solves the problem of having to send sensitive information over the internet, it's secure. But does it have an advantage over ssh remote desktop? The only difference I can  think of is the fact that it still runs on your local machine, if the place with the sensitive information doesn't have computing servers.
    - You mean: "you can use a ssh remote desktop to install things.  Or docker locally"?
    - Two different options.  docker is more shareable, it's like the whole operating system in a file.
        - So docker is just an extreme version of a .yml file, in a sense?
           - yes it records not only the software environment but the entire operating system

82. Will the data be public in docker? or could we have data in private mode?
    - If I understand right: the image with code is public.  Usually the container wouldn't have the data in it, it would be mounted in when it is running (tracked separately on your computer)


83. Why I have "'conda' is not recognized as an internal or external command" error when running "snakemake --use-conda --conda-frontend conda -j 1" eventhough I can run "conda" in bash?
    - Good qusetion, I think we will have to look later.

84. Can I have a container with a previous version of the *operating system*? Say I want to use some software that was supported only in old OS versions, for example Ubuntu 16 when the current version is Ubuntu 20. So I want a container with Ubuntu 16 and that obsolete software.
    - Yes, that is a common use case.
        - Glad this is a common case. Where can I find directions as for to implement this use case?
        - We don't go over it in this course, but you would: create a new container image.  Derive from the older operating system base image.  It should become more clear once you see how to make the image.


85. Problems I've had with Docker. Default memory limits make it really difficult to get something running as smooth as originally expected.
    - It does require more consideration for how to run things.  Things such as memory and CPU limits can be adjusted.

86. I needed to run `docker pull` as root, otherwise I got `permission denied`...
    - You can give permission to your user to do this (to be discussed later).  All these permission problems are one reason we don't have an exercise about this!
    - [Run Docker when not root](https://docs.docker.com/engine/security/rootless/)
	- For more Docker material, see also [extra lesson](https://coderefinery.org/reproducible-research/docker/)


---
### 1.6 Sharing code and data
https://coderefinery.github.io/reproducible-research/sharing/


87. How dangerous can it be to allow these platforms (Zonodo, or Github history that we used last week) to access our repositories? I think you have to grant (maybe read-only) access to all of what is connected to your profile, right? Maybe there is something that is not just mine and potentially private
    - In general this is always a good question to ask.  You need to check permissions, reputation of the sites, and what you are doing
    - Thank you. So, for the particular case of Zenodo, can we just go on without problems of any sort?
    - We trust Zenodo enough for this exercise, at least.

88. The concept of FAIR is based on the suitation that all the older versions of an open-source software are available. I mean if a very old version of piece of open-source code do not exit after a long time, e.g., five year. Then it is impossible for other people to reproduce the data that was made before.
    - It is correct that keeping things available is hard.  That's why we try things like zenodo/using good platforms is important.
    - So much more could be said about this.
    - Agree; on the other hand - if it's hosted in GitHub or similar platform, it should exist there "forever", shouldn't it?

### Exercise until xx:25
[Sharing-1](https://coderefinery.org/reproducible-research/sharing/#exercise-connecting-repositories-to-zenodo)
Do what you can, no problem if you can't/run out of time.


89. I get the error: "You are being blocked. Please contact us at: info@zenodo.org". +2
    - Good question!  No idea.
    - Copy pasting the link manually onto incognito worked. (Might be related to the fact that many people are clicking the link on the exercise web page and they might think its spam since there is ?next=https%3A%2F%2Fcoderefinery.org%2F at the end from using the link straight from the coderefinery webpage)
    - It also happened to me. It was the first time in Zenodo. I received an email few seconds/minuts latter from Zenodo. They wanted to confirm the email. After the confirmation was done I was able to work properly.
    - Could also be related to using a VPN

90. The repo must be public?? Yes, i seems so. otherwise zenodo does not see it
    - I guess so, I would have to check the docs to see.
    - yes. if you practice this make sure you are on the sandbox one.

91. I don't understand how to publish a release. Any link to a step by step instruction?
    - right side of a github repository. [example](https://github.com/coderefinery/installation) (see on right side "Releases" and click on it)
    - yes i understand that but beyond the first click. what next?
      - then green button "Create a new release", then "Choose a tag" and give it e.g. "1.0". "Create new tag on publish"

92. Did you say this `sandbox.zenodo.org` way does NOT create a real DOI? Could I make a real DOI using Zenodo?
    - The real zenodo *does* make real DOIs.
       - but use this only for real projects and not for exercise since DOIs can't be revoked easily
           - I see, thank you!

93. Seconding question 87 on granting crossed access to repositories, how do we actually ascertain whether the choice is safe? Where do we expect to find the relevant information for an informed decision?  
(My point is that information that cannot be found easily is like information that discourages granting access )
    - Websites of the things.  Organizationly who controls it.
    - If you are worried, you can do the same things without giving Zenodo access: download and upload to Zenodo yourself.  It is very reasonable to be worried about this.


94. In Zenodo, you only get the Zenodo link *after* you've given the GitHub tag. But then adding the Zenodo link to the GitHub repository won't appear in that tagged version. I guess that's OK, though: the link just goes back to the tagged version.
    - good point. yes. what you can do for future releases is that on zenodo you can get a DOI that resolves to latest release and then you can use that one in the github readme.

95. Should we redo the authorization to zenodo after this? It feels a bit sketchy to have the authorization there when it's not needed (and maybe later give access again)
    - you had to authenticate twice?
    - no, undo is what I meant. So withdraw the authorization
    - (sorry for these counterquestions) and you mean now revoking the "switch" to watch a repository or to get rid of the zenodo account which you may have logged into via github account?
    - I really just mean delete the connection between github and zenodo since I don't have use for this right now (but set it up for the sake of the exercise)
    - https://github.com/settings/applications I can remove the connection here

96. Can I remove the data shared on Zenodo? (proper Zenodo, not the sandbox)
    - it is possible by contacting their support but normally data published on zenodo is never removed as this is the point of this service. but if a severe mistake happens you can contact their support. :+1:
        - asking because I see the "permanence" of data as a good advantage over github (or other) repo only.
           - yes exactly. great point. github itself is often not enough since nothing prevents me from deleting things there.

97. Does GitHub generate a DOI as well?
    - You have to use zenodo, or other acrchiving platform: https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content

98. GitHub release done, Zenodo Synced, but no DOI generated (it has been already > 10 mins). Any recommendations? +1
    - Check that the switch in the repository list is on. Reload the page and check again, just in case. I've seen some errors with this.
    - You should see it in https://sandbox.zenodo.org/account/settings/github/ under the list of enabled repositories, after reload.
    - Are you sure the release was published? I did not put a tag name initially and Github did not show any errors so it looked like the release may have been published while it was not
    - You may check the GotHub releases at https://github.com/username/repository/releases. Click the pencil to edit if needed.

### Break until xx:35
Then social coding

---
## 2. [Social coding](https://coderefinery.github.io/social-coding/)

### 2.1 [Social coding in general](https://coderefinery.org/social-coding/social_coding/)


### Discussion: basics of sharing

Did you ever share your code?  If so, what motivated you?  What reasons did you have for sharing?
- Yes. on Zenodo as been suggusted by a previous course by codeRefnery. Maximize the impact, citation, reusing and prefered by the funding agency.
- Improve the work with others; i.e. collaborating to further improve.
- Collaborative project with people I only knew through discord
- getting independent credit for work done: independently on my Boss's opinion.
- I made code, but someone else was using it. Without using proper sharing platform, I wouldn't be able to get feedback. 
- As a supplement of a submitted paper
- Shared my Master's Thesis code on public GitLab repo such that it would be accessible by later members of the group or for later publication. +1
- Yes, it was a requirement of the Atmospheric Chemistry and Physics journal
- Credit
- Nice to do something meaningful
- my work has a positive imapct on the world...
- help colleagues=-
- help collegues and get help from collegues. It goes both ways, if you share, they might also find a bug you missed
- feeling more useful
- Working with collegue on same project, Also creating code together to have visual representation of our data for non-coding people. +1
- Help a collegue out.
- Not so much code, but data from the data collections for other to use for, e.g., metaanalysis.


What reasons are there to not share?
- No proper citation by those using it+1.
    - Licensing might help here, i.e. a proper open source license and a friendly reminder
- NDA's
- Fear of being scooped/plagiarism.
    - Using your work before you can publish it. +1
    - You can always make things available once you publish/submit, also you have evidence of having the idea earlier, when you do have it on a public repository.
- Really badly written, afraid of people judging. Also extremely unefficient and wasting cpu time, for sure +3+1+1              
    - By the way, this workshop makes me less afraid to share my code :-) 
- It's horrible spaghetti +3+1
- Not sure when to share in relation to publications- how do we share during the peer review process? +1 +1
    - Make the repo open once you submit, or, if you are really afraid, provide it initially as a supplement, with the indication in the paper that it will be on github and open once it's accepted.
    - https://anonymous.4open.science/ can anonymize your repo, to preserve double-blind process (hopefully?)
    - https://github.com/jayphelps/git-blame-someone-else ;-)
- It was a private code, sharing is restricted by the policy of our institution. You need a specific permission to publically share any codes or data that belong to the institution.
    - That might actually go against e.g. EU funding requirements. 
- Waiting until my project is fully functional +1+1
- Users ask too many questions while I'm not working on repo. I'm not required to support anyone, but what's the point of sharing if people cannot use it (without my support)?
    - But then: if people can't use it, whats the purpose of publishing it? If its code in development, then sure, not having it open is (imo) perfectly valid, even though having it open from the beginning can be useful.
    - People can use it with my support, which I don't have time for
        - But that would mean (imo), that e.g. Reviewers did not check the tool properly.
        - I think it just means I need to spend more time on documentation and user manual
- You want to avoid someone misusing the code. +1 Basically issue why codes for nuclear engineering are often not open :( :o
    - Of course, it's better to make it such the way it would be useful only for the good purposes. But it might be difficult to assure.
- Code is very system-specific, I don't think it's of general use

- my code is for post-processing my data. Sharing the equations I used is easier for reproducing than sharing my actual code because it is heavily tailored to the specific data formats of my testing machines
    - True, but wouldn't it be nicer to have "preprocessing" scripts, and general purpose code? I.e. have a data format you process and scripts for the actual data that bring it into that format? 
        - That would make it easier for others, sure, but not for me. So I am not very inclined to make something more complex for myself for the sake of sharing.
            - It will also make it easier for you to re-use on other data.
                - All my other data comes from the same machines. I totally get your point though, I just don't agree with it :P
                    - To me: If I have the option of citing someone where I can directly use the code and some paper where I need to reimplement everything or spend lots of time reproducing/debugging/adapting, I will go for the former. So if you want to be cited, chances are a lot better if a useful tool is provided in contrast to just formulas.
                        - "where I can directly use the code" is an important part of your sentence though
- University gets financing only based on articles. So far code publications don't count.
    - Imo that depends on how reviewers see it, i.e. if they want to see the code/won't accept it unless its reproducible (i.e. code available)



99. Do you think modern journals need editorial boards for shared codes also?
    - good suggestion! I think journals will need to adapt to this and some journals (and funding agencies) do not have yet have the resources or expertise to review the quality of the code 
        - The classical reviewing process is already voluntary. I would be happy to review a code. I think it has to be an initiative from journals, resources will come from community.

100. It's not just a problem that people may refuse to share their code if you ask for it; it's also increasingly less likely you will even be able to contact them as time goes by from when they published their paper (due to people changing institutions, emails no longer working...). https://doi.org/10.1016/j.cub.2013.11.014
     - one more reason for code to be put on public (not institutional) repositories

101. Why do you suggest OSS rather than FOSS? 
     - sorry I missed this discussion. in which context was this mentioned?
     - - Sorry it was not discussed but I saw a glimpse of that on the presenters screen

102. "Open Software Licensing – a discussion, 8.3.2022 (Aalto University)" (mentioned by one instructor)
     - recording: https://www.youtube.com/watch?v=BuS0mvlNo08

103. Who is responsible for approving changes proposed to such open source projects like numpy for example? If their is no central authority/control?
     - open source governance is a very good question, each project is difference
     - numpy is large enough there is teh NumFocus foundation that is in charge, day-to-day work delegated to its maintainers.
         - who funds them? What if the funding stops? ------ any ideas on this?!!
            - hopefully too important to not be funded but there are many important projects that nobody funds. there is this xkcd comic about that: https://xkcd.com/2347/


104. When should I cite numpy? If I use it in a software that I develop and then publish a paper from the results of the software, should I cite numpy? +1+1
     - Isnt the package dependency list somehow citing numpy? At list in code this is also a way of citing/crediting ;) also downloads and forks
        - but can be misleading, if a package requiring numpy is listed and numpy is omitted even though it is directly used. +1 
            - pandas depend on numpy as well that would happen in this case.

105. The presence of numpy in an environment or dependencies list should be used as citation. Wouldn't that be great?
     - perhaps any installation of a dependency could leave a "citation token"

106. So do we have to cite the package that contains numpy then? and also what numpy uses, then?
     - the recommendation I follow is to cite the packages and codes which I directly use but not to cite their dependencies and their dependencies (as I hope that they cite those)

107. Regarding "generale knowledge" that is not cited, there is a big difference between fields. I think original work by Sanger is still cited every single time, and is one of the 10 most cited papers. By the way, I just submitted a paper where I cited NumPy :)
     - Nice! Yes, this depends a lot on the field. Citing everything you use would be optimal, but journals usually have a limit on how many things you can cite. And even if there wasn't, you want your citation list to fit on your disk :smile:


108. My code are usually not really long, no more than 100 lines, but I have many different stuff. Is this really worth it to share ?
     - The effort of sharing can be really low, and if no-one ends up using it, at least you have a backup in the internet. And adding an open license means you can always use it.
     - Yes. In particular sharing with your future you. Do it :-) I have lost access to some of my scripts because I accidentally deleted them or for license reasons.

---
### 2.2 [Code reusability](https://coderefinery.org/social-coding/social_coding/#code-reusability)

### Exercise: [Social-2](https://coderefinery.org/social-coding/social_coding/#what-contributes-to-reusability)

[Recipe repository](https://github.com/coderefinery/recipe)

What can be added to our recipe repository to make it more reusable?
- more informative text in the readme file.
- a requirementes.txt / environment.yml to know dependencies and how to install it
- the usage (to avoid misuse)
- how to contribute instructions?
- release or version information
- a license
- tests
- How many persons each recipe feeds?
- Readme.md: separate sections for 'users' and 'developers'.
- see GitHub `Insights/Community standards` -- that's good for beginning IMO

109. Whose names should be in citation if the repo has many contributors (external and internal)?
     - This is similar to the question who should be an author of a paper. There is no exact limit, but hopefully you can draw a line so that no-one feels left out.
     - You can add a separate section in the README where you thank contributors who are not authors (yet).

### 2.3 [Licensing](https://coderefinery.github.io/social-coding/licensing/)

110. But doesn't copyright expire after certain amount of years after their death? Example, classical music of Mozart, Beethoven, etc. are not copyright protected.
     - correct. is it 70 years? same applies (depending on coutry) to software but let's see whether we can still compile and run the code we write today in 70 years. for books this is known territory but for software we are in a new territory here.


### [Exercise: derivative works](https://coderefinery.org/social-coding/licensing/#derivative-work)

1. Download some code from a website and add on to it
2. Download some code and use one of the functions in your code
3. Changing code you got from somewhere
4. Extending code you got from somewhere
5. Completely rewriting code you got from somewhere
6. Rewriting code to a different programming language
7. Linking to libraries (static or dynamic), plug-ins, and drivers
8. Clean room design (somebody explains you the code but you have never seen it)
9. You read a paper, understand algorithm, write own code

#### Answers from the audience

1. o++++++++++++++++++++
2. oo+++++++++
3. oo+++++++++++++++++++
4. oo++++++++++++++++++
5. oo++++--o-+
6. oo++++++++++++o++
7. ooooo+-+
8. oooo+++----
9. oooooooooo++-++-++--


- my code is for post-processing my data. Sharing the equations I used is easier for reproducing than sharing my actual code because it is heavily tailored to the specific data formats of my testing mac


111. Clean room design: so if someone told me about a book they read then I make a movie out of it, it's not derivative?
     - Yeah, it also sounds a bit weird to me (a sort of too 'liberal interpretation' I would say)
     - copyright is about creative expression.  The idea is that with code, the algorithm itself is not the expression so isn't copyrightable: this is different from the movie example.
     - I suppose it is not derivative if is a genre, like how many dark noir detective or war movies are out there?
         - +1

112. How to create a copyright of your code for a mobile application for instance?
     - this question is probably about license and not about copyright (which the software automatically gets attached)
     - also for web applications you have to make a choice between custom (closed), permissive, share-alike, or copyleft. one example for a license for web services is AGPL where derivative work has to be made available even if the software is not distributed since the web service is understood as distributing. but depends what you want to achieve and avoid as software author. this may be good or bad depending on perspective. personal opinion: I like AGPL for my web projects because I want people to change them and reuse them but I also want to be able to reuse their improvements.
     - Thank you for the enlightment!


113. I find this topic quite tricky, what about coding methodologies you learnt in a course, for example?
     - it is tricky but for small examples shared on twitter or stack overflow there is typically no problem. this starts to get tricky when money gets involved and for larger projects. but all large projects started as small projects. sharing copyrighted material may also be fine for educational purposes.
     - I don't have time to type more but: ideas are not protected. Expressions/implementions can be.
     - for ideas credit/attribution/citation is more important and relevant, especially in academic setting

114. Can licenses be changed in future?
     - The copyright holder can (basically original authors or whoever they explicitely gave it to)
     - As projects grow and organizations join the project, it becomes more difficult. So it is good to discuss this early in the project when it is easy to change.
     - Some licenses allow publishing under a different, more restrictive license. This does not change the license of previous versions.

115. What's the cat's name? :heart::+1: +1 +1 +1

116. Comment: Rather than a virus, GPL can be described as a seedling which spreads and grows trees everywhere
     - thanks, I like that analogy a lot better.
     - It is good also to explain the context of GPL and when it appeared. By the time many researchers were used to share code and pass it around. This was a way to protect authorship legally and it was a struggle during its time to keep open source as a legitimate practice, things are different Today, but what we ave Today is a result of those early pioniring licenses in open source.

118. There are many license types, a little bit  confusing for me. What is the difference between Creative Common 4.0 license and the GPL license? They both seem to be very free.
     - GPL is more relevant to code and is a copyleft license. CC is more relevant to text or data or course material or slides. CC has many flavors itself: CC0 (equivalent to public domain), CC-BY (equivalent to MIT or BSD), CC-BY-SA (equivalent to LGPL or MPL or GPL)

119. Why is forcing users of my code to use the same licence against open-source? E.g. I can say "It's open and anything derived has to be open as well"...
     - I don't think this would be against open source but perhaps I missed that comment.
         - I had the same question.

120. what does this mean: distributing closed source versions?
     - you could distribute only compiled binaries but no source distributions. this way people can use them but not inspect them and not change them.
     - This could also be a license that does not allow you to change the code, even if the code is included.

121. When I posted my code to Zenodo, they provide options of CC license, not GPL license. Is this very strange?
     - You can add a GPL license in GitHub.
     - Zenodo was originally designed for data, and CC licenses work better for data. They are not designed for code, though.

122. Can there be multiple copyright holders? How to arrange this kind of situation?
     - If multiple people contribute to a project, they hold copyright to their contributions. Often the contributions overlap so much that it's not possible to say who wrote a given line in a file. In that case both or all contributors hold copyright
     - Your employer might specify that you share copyright with them for any work project.

123. What if the software will be used internally for the research group but not published. For instance, a database management system for a biobank. What would be a suitable license?
     - The license can be given to just the employees. The license can be any of the usual.


124. How is a copyright automatically generated? Once you saved it as jupyter notebook or something else?
     - Whenever you write something, you have copyright to it. It does not need to be published in principle. However to prove that someone has infringed your copyright, you need to show they could have seen your work.

### [Exercises: licensing](https://coderefinery.org/social-coding/licensing/#exercises-licensing)

**Licensing-2: Consider some common licensing situations**

- What is the StackOverflow license for code you copy and paste?
    - In https://stackoverflow.com/legal/terms-of-service#licensing I found the **Subscriber Content**. It starts like this *You agree that any and all content, including without limitation any and all text, graphics, logos, tools, photographs, images, illustrations, software or source code, audio and video, animations, and product feedback (collectively, “Content”) that you provide to the public Network (collectively, “Subscriber Content”), is perpetually and irrevocably licensed to Stack Overflow on a worldwide, royalty-free, non-exclusive basis pursuant to Creative Commons licensing terms (CC BY-SA 4.0)* and goes on three times as wide. **Recommended reading.**
    - That depends. Most of the time in StackOverflow people just copy paste the documentation, or name a function that they know but the asked didn't. 


- A journal requests that you release your software during publication. You have copied a portion of the code from another package, which you have forgotten. Can you satisfy the journal’s request?

- You want to fix a bug in a project someone else has released, but there is no license. What risks are there?

- How would you ask someone to add a license?
    - Open an issue in GitHub or contact the developers via email, for example.

- You incorporate MIT, GPL, and BSD3 licensed code into your project. What possible licenses can you pick for your project?

- You do the same as above but add in another license that looks viral. What possible licenses can you use now?

- Do licenses apply if you don’t distribute your code? Why or why not?

- Which licenses are most/least attractive for companies with proprietary software?


---
### Feedback

#### Today was:
- too fast: oooooooooooooooooooOoooooo
- too slow: oo
- just right: ooooooooo
- too disorganized: oooo
- organized enough: oo
- wanted more exercises: oooooooo
- more demos: ooo
- not enough time for the exercises: ooooo

#### Poll
I would prefer longer days to have longer exercise sessions:
- yes: o
- no, find some other strategy: oooo

 Probably many EL would not have enough time...o

#### One thing that was good about today:

- Reproducibility and learning about Zenodo was super useful +1
- Hard to choose, I enjoyed both lessons a lot. Great clarifying discussion about copyright.
- SNAKEMAKE, AWESOME!!!+7
- snakemake and reprducable work was great but the demo was very fast. We need more time for this important topic. +3
- Good overview of a lot of things. You touched upon them and we can look them up for ourselves later if we're interested.
- The topic on licensing nicely fitted the format you have (discussion like sports commentators) +1
- the agenda was chosen carefully and the presentation did have very good flow and relevance.
- Zenodo and Snakemake

#### One thing to improve for today:

- The sections about the Reproducability and Snakemake, were too quickly +2
- Please let the exercise leaders know which exercises will be in breakout rooms at the start, to help prepare +1+1
- Please consider more time for exercises. +1+1+1
- More time on: how to decide, based on time available, between snakemake and writing your own shell script(s); eg. is it worth investing time to learn this new tool? +1+1
- More about Docker+2
- Should decide either making type along session slower, or no type along at all, beforehand

#### Any other comments:

- I find sometimes the first introduction to a topic quite hard and difficult to relate to (being new to me). However, doing the exercise is very clarifying and useful but it raises more questions (more educated and interesting ones). Altough hackMD is useful in that sense it sometimes lacks the clarity that an oral answer can have. Suggestion: Brief intro about a topic, Exercise (with more time), follow-up based on hackMD questions
- How to create a snakefile for my projet? any recommendations or a good source that can give us the step by step guide? +1
    - see for example https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html#tutorial
- Very useful workshop! Great speakers and answering supports! Great job! At the same time, the workshop is very intensitve, and I was too busy in listening, reading and writing questions. Little time for doing execises. 
- I think it was rather computer/programing science centric. Often there are so much more than code to be able to reproduce; data collection, study design etc. +1
- ...
- Too fast: when allocating time for excercise you need to count the time it takes to explain/clarify things, not just the time to copy paste the commands and obtain the output.
- Why do we have so many standards :(
    - there must be a cartoon by xkcd... [Here](https://xkcd.com/927/)


