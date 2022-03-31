+++
template = "page-with-toc.html"
+++

# Questions and notes from workshop day 6

--- 
## Icebreaker questions
### Feelings on CodeRefinery:
- excited: ooooooooooooooo
- exhausted: ooo
- want more: ooo
- all of the above: oooo

### Have you ever experienced:
- "it worked before": ooooooooooooooooOooo
- "it works on my computer": oooooooooooooooo
- "it worked before I added X": ooooooooooooooooo
- "It worked when I first submitted": o

### What can go wrong when coding:
- float value truncates to int without noticing anyone.from pytest import approx
- change a variable name which affects something further down.
- changing the location of a dataset and not updating it on the code
- different conventions on priority for different OS ("a" vs "A")
- dependencies
- rewriting modules names
- Dependency management!!! Why is this so complicated??? :P 
- side effects which I did not know about
- upstream changes
- Making assumptions about how a function etc of a package works and then it does something you did not anticipate
- writing and executing code by myself and it working fine, then if I have to execute a code live on zoom or in a meeting it suddenly stops working. R smells fear.
- inheritance (is it supposed to be parent or child???)
- Somehow I am always able to trigger the edge cases that seemed not worth it to code a workaround

### How can you prevent this?:
- run the code every time you change something.
- containers?
- automated testing + git
- testing on different platforms
- be organized 
    - That does not really help against code "no longer working" (except if you consider CI system as part of being organizzed)
    - I think well organized code definitly helps preventing "no longer working code"
- code maintenance is part of code development (however it rarely gives academic credit) :+1:
- I do a quick powercry and then I solve the problem +1
- reading the documentation
- commit all changes atomically -> git bisect 
- unit testing. Once implemented, gives so much confidence while exprimenting with your code 
    - :+1: also, I'm still surprised by how many bugs I find in my own code once I finally get around to write unit tests ;-)



## General Q&A
1. If 'clean room design' can't be claimed for anything, why would one participate in brainstroming session or give suggestions?
   - It can be.  It's just very context-dependent, and when it has a really high-value people start fighting about it.

---
## 1. Software testing
https://coderefinery.github.io/testing/

### 1.1 Motivation
https://coderefinery.org/testing/motivation/

2. There is a wonderful homepage on bugs in softwares (unfortunately only in german): https://www5.in.tum.de/persons/huckle/bugs.html 
   Probably Google-Translate helps

3. Do we *have* to include a test function for every function we write? If not, how to choose which ones to test?
    - What Jan has shown with this C/F dgrees example is actually  the calculation of a residual (put your solution back in the equation and see whether it is verified). Any time you could do this is a window of opportunity to ensure the correctness of your formulas.
    - That's why there is art and creativity here... it's some balance of effort and benefit.
    - Side note. You do not have to test each and every time: you can nest them in an if block. Of course you have to code it.
        - what does this mean ?
    - I would add test for a function before rewriting it. Or right after I solved a difficult bug in it to make sure it does not come back.

4. C++ code at https://coderefinery.org/testing/motivation/, what is there a specific reason to `return EXIT_SUCCESS;` instead of `return 0;` in `main()`?
    - I think just clarity. `EXIT_SUCCESS` is `0`, but if the reader does not know the convention they can still guess `EXIT_SUCCESS` means
    - Possibly on some system the success code is not 0?

5. I anonymously disgree that testing is an art. It is coding and computing. Art is another thing at all.
    - I don't interpret art here as "we'd have to put it in a museum and all look at it", but there is a certain skill and fingerspitzengefühl to it
        - Then it's a craft
        - I would not test based on intuition.
            - That's not what I mean. But they did just say that when to test and when not to test is up to you as a coder right, so it does take some intuition to decide that still
                - I would call this responsibility and accountability
                    - So it's down to semantics then ;)
                        - No this is the same escape as invoking 'art'. You need to make choices and explain them. This does not happen with art and intution. They can be bywords for laziness.
                            - Yes so you and I define art differently. Hence semantics
                                - No again. I would not put a piece of code in a museum (although some may have done it). So I do not see a disagreement on the term art.
                                    - depends on the code. some definitely belongs in a museum! (e.g. https://en.wikipedia.org/wiki/Duff%27s_device)
                                        - has that been tested?
                                    - This is starting to feel a lot like this: https://xkcd.com/386/ +1
                                        - :D
                                    - Just throwing this out there: https://www.youtube.com/watch?v=6avJHaC3C2U
    -  Im sure there are some basic rules that you must follow, but I think the point given above is that you require some creativity to do it optimally
        -  Creativity or judgement?
            -  Both maybe
    - It is the art of "state-of-the-art".
    - Wow, what an unproductive comment... (sincerely, anonymous learner)
        - Some people may reflect and learn from it though, while disagreeing of course
    - what is art?
        - Now this: https://www.youtube.com/watch?v=HEXWRTEbj1I is stuck in my head (I know this is a useless comment, but the roomba in my mind works in mysterious ways, I can't always control it lol)

6. What if the test function has a bug as well? 
    - Then you have a problem :) Hopefully other tests will catch this. But this is significantly less likely than having just one problem.
    - Some people have tests for tests, after all who watches the watchmen? But how can you be sure you don't have a test in the test for the bug
    - Then hopefully correct code will find the incorrect test.  If both are wrong in the same way... too bad, I did as well I could with reasonable effort.
        - :+1: 
        - If you publish the code and have other users, hopefully they will complain about the bug sooner or later.

7. Does the assert function in python just does the same procedure as the one in fortran(explicit if statements)?
    - The assert throws an error if false. I will check what explicit if means.
        - Update, I did not quickly find what explicit if means. 
            - Thanks, by explicit if I just meant that the test in fortran is being done by having this condition statements, and then giving either pass or fail
                - OK, then it's rougly the same, but see the answer below
    - `assert` in python within tests (pytest) is great. pytest has special handling for it. its main difference to "normal" exceptions is that it gets optimized away with `python -O` (so in production code, it can be good for checking argument invariances, but you should not rely on it for checking user input)

8. Fun fact about constants. It happened to me to find a bug due to a constant being re-defined locally in different routines with different values!
    - Oh, so a constant was overwritten in a function? This is a common problem that languages try to fix with scoping rules.
        - no, different variables meant to contain the same value (the constant) were initialized locally with different values. E.g., pi=3.14 vs pi2=3.1415
           - it can be useful to have a single file to hold all "magic constants" in one place. conventions e.g. ALLCAPS for constants (so you don't accidentally assign to them within a function)
           - OK, so this is an issue the languages introduce with the scoping rules :smile: 
           - We will later talk about pure functions. This means essentially that all input is in arguments and no global constants are used. This would solve the problem, or at least make it more visible.


----
### 1.2 Concepts
https://coderefinery.org/testing/concepts/#concepts

9. If I want to test a function that gets as input a dataset, to test it I will have to have a whole test dataset?
    - for this it's good to have very small toy/testset datasets, yes! depends on whether you're talking about a data loading function (from disk; e.g. can it handle special cases? one-entry datasets? zero-entry?), or just a function that gets data (e.g. a numpy array)

10. Do you place the scripts for the tests together with the function (same folder) or do you place them in a sperate 'test'-folder +1
     - There are different conventions, but I personally usually have a "tests" folder on top level of the repository.
     - I add end-to-end tests into a separate folder but I like to add unit tests close to the actual code since I use them as documentation. Also when changing them I can do that in the same file and don't have to jump from folder to folder.
     - I really think this question is relevant, maybe the speakers could discuss it later? Show some folder structures/examples.

11. How do you manage testing when you write your own code while relying on external libraries (eg. numpy, scipy, ...)?
     - Very often I rely that the external libraries are tested by somebody else and I don't test them as such but I focus on testing my code. And I start with an end-to-end test and later maybe add tests for individual functions.
     - external libraries _can_ contain bugs! came across one in scipy.optimize some time ago...

---
### 1.3 Testing locally 
https://coderefinery.org/testing/pytest/


12. Is pytest something from the developers of python or an external library?
    - it is a separate library and other test libraries exist in Python but it's perhaps the most popular and simplest
    - https://docs.pytest.org

13. Should we code along? 
    - Not needed to code along, you will get time in exercise session to practice this.
    - But thanks for asking since it was not clear.

14. Does pytest execute `python 2` or `3`? Can it be specified?
    - It exists in either. Your `Python2` and `Python3` installations would have different versions of the library, installed separately.
        - If you installed in a conda container, you have Python3 by default in the container. So pytest is also Python3.
        - If you have both Python3 and 2 installed, you need to specify which to use, for example `python2 -m pip install pytest` will install it for python2 and `python2 -m pytest` will run it for Python2.
            - OK, and just from shell the "pytest" refers to python3?
            - Usually yes. Depends on what your system default is. Almost always Python3 these days. 
                - with default you mean first one in path variable?

15. Please, remind that this excercice should be done in the coderefinery environment.
    - thanks. relaying ...

16. Is there a way to avoid having the test functions in the same file as the actual code? I tried now putting it in a separate file and import it to the main file, but this made pytest not work. Now it works, I just imported it wrongly.
    - they can be anywhere and many projects put them into a separate `test` or `tests` folder 
    - You can crete a file called test_filename.py and import the main code from there
    - Usually I would actually have my tests in a separate folder and import the entire package I'm testing the same way a user would import it.

---
#### Exercise until xx:49
Exercise Local-1
https://coderefinery.org/testing/pytest/#exercise-pytest

17. What's the purpose of having multiple assert, does order matter?
    - Great question. It will fail on the first failing one. And maybe it would be better to not package multiple asserts into the same test so that we can see all failures and not only the first one.
    - Sometimes you have larger omputations and want to test multiple results that originate from the same function. Rerunning the tests for all individual asserts might lead to long computation times that you want to avoid so you simply assert multiple facets of your output. Yes, if multiple of those would fail, only the first is displayed and probably the others show up after that got fixed, but under "normal" circumstances you would assume that modifying a function will only affect one outcome, so it will fail "at the right place"
        - This almost sounds like a feature request to have something which acts like assert, but will not stop on the first fail
            - Julia's tests work like that:)
        - I would recommend having tests be as small as possible (with few, close to 1) assert statements. Then they're also easier to understand. If they have common "setup" code you can put that into its own utility functions, or if it's expensive & you don't want to reuse it can use pytest fixtures

18. What's the "approx" doing?
    - It compares floating point numbers with a tolerance and the tolerance can be adjusted. this is important to consider for any floating point comparison. integers can be compared precisely but floating point numbers (numbers with a comma/point and digits after) cannot
        - Yeah, I did the second example with a tolerance, but in the solution it is mentioned that thetolerance has to be adjusted. so I am wondering if approx has a fixed tolerance? machine precision is somehwat like 1e-16, but what is approx using?
           - It has a default tolerance that can be adjusted. default relative tolerance is 1e-6 but can be changed: https://docs.pytest.org/en/latest/reference/reference.html#pytest-approx
               - OK! Thanks

19. What does the exclamation mark mean in `!pytest -v example.py` for IPython and Spyder? (Exercise 1, point 3, bottom). In standard Python ! is the negation, right?
    - Here it is not negation but to tell `ipython` or `spyder` to run a shell command "outside". same convention is in `vi/vim` editor to run shell/terminal commands from the editor without the need to go outside, run it, and come back.
        - Thx
    - `!` isn't part of standard python

20. So for the testing a file we put done the test by ourself and it is based on our knowledge of the code at the moment. but our knowledge would change specially in field such as data science. How many test is enough and how to make sure your are covering almost all the grounds?
    - You can probably always add more tests. If you specify the expected inputs to a function exactly, you can in principle test all possible ways of running it, but in practice you just test the most common cases.
    - One great heuristic is to add a test every time you find a bug and make sure that that bug never happens again. +1+1
    - Also what can help: Calculating code coverage of the tests , i.e. checking which parts of the code were executed by the all tests. This way you can have a good approximation of whether you test sufficiently (well at least if your functions are not intended for use with multiple different types of inputs). If you get a 100% coverage that means that you even tested all places, where you expect things to go wrong.
        - thank you! that is so helpful.
        - high code coverage is helpful, but not sufficient (it's easy to write tests that give 100% coverage without testing anything!)

21. I saw that the python keywords "def, return" are shown in different color when the instructor demo the example. How to setting the editor (vim, or nano) to identify special keywords?
    - Have a look here:
      https://askubuntu.com/questions/90013/how-do-i-enable-syntax-highlighting-in-nano
      - thanks!
      - in `vim`, I believe adding `syntax on` to your `~/.vimrc` could work.

22. My understanding is that `pyTest` is tool for debugging python script. What if I want to debug script written in other languagues, e.g., `C++?`
    - There is a list of tools in the course material at https://coderefinery.org/testing/quick-reference/
    - If your language is not on the list, search the web for "unit testing framework" + language. Or write functions that run a function, check the output and error if it's wrong.

23. How do you test, for example, data filtering functions? Or other more complex functions which you don't always know the results of? 
    - Store some data for the tests. This way you always know what the output should be. 
    - If you have a function, where for example, you don't care about the order of outputs in a return value but you want to ensure that certain elements are in, and no others, you could run a for loop that asserts that all elemens you expect to be in are in the result, and check that the length is exactly what you expect (no additional elements).
    - Maybe you know some statitically true things about the function (in the MonteCarlo example earlier, we know the result should be close to pi), you can run it many times and check the average.
    - Also, if you have an optimisation function, you might e.g. want to set an limit instead of a fixed value for the result, as you don't necessarily know that what you got out is the optimal (at least if it's a bit more complex inputs), but you know a boundary and improving the function should be allowed.
        - Interesting... Can you explain this a bit more? What do you mean by setting a limit?

24. Funny that `assert add(2.1, 3.0) == 5.1` is verified while `assert add(0.1, 0.2) == 0.3` doesn't.
    - Floating point arithmetic, that's why you often need tolerances (`approx`) for these kind of tests.
        - Even if you do 0.2 and 0.3 the test is passed! :+1:
    - 0.1 + 0.2 is a bit of an edge case, see <https://betterprogramming.pub/why-is-0-1-0-2-not-equal-to-0-3-in-most-programming-languages-99432310d476> for example

25. Is there a function like Julia's `big` in Python?
    - This works but there is probably something better: `"%.50f" % 0.1` 
    - (I would think it is `repr` but it rounds)
    - `repr` works sometimes: `repr(1.4 * 1.5)`
    - I have found this: there is a module called **decimal**. See https://zetcode.com/python/decimal/

26. What hapeend for big(PI) or big (1/3)?
    - In Julia, `pi` is a special constant, so that `big(pi)` will return the closest big float (with set precision) number closest to the true pi. For `big(1/3)`, `1/3` is not exactly one-third, so it will convert that floating point number to a big float.  

27. Would storing the test in `result` cause the small digits to change?
    - In Python, no. In a strongly typed language, it might, depending on the type of `result`.

28. How many assert statements would you recommend to have in a single test function?
    - See question 17 as well.
    - That depends a lot on what you test. If it's a simple function that gets inputs and returns a single output: probably one assert. If the output is a list/dictionary or something: a few asserts for the values/length/size in the list/dict. If it's modifying a complex object: Checkks if all expected modifications of the object were done etc. It's a bit: try to separate tests as much as possible and test one functionality at a time, but if that functionality does muliple things you should check all of them.
        - Thanks, indeed separate tests on functionality and make use of pytest's feature to have tests failing and still be able to run other tests. If all tests are in a single function, it might fail on the first assert statement and not run the remaining ones.
            - Yes, definitely separate tests for different functionalities. You can have tests where you use multiple functions (because some might depend on each other), but the each functionality should have its own test and not rely on being implicitly tested somewhere. 

29. Do you have to write all the tests in the same file, or can you organise it so that all the tests come in a separate test-file?
    - You can have multiple test files (at least in Pytest and in all the testing tools I know of.)
    - Commonly you create something like one test-file per source file, where the test file tests the functionality of that source file.
    - I like to have a `src` folder with source code and a `test` folder for tests and have roughly the same structure in the two folders

30. Nice thing to see: `print("0.3 with approx", approx(0.3))`it prints 0.3+- 2.0e-07
    - haha, yeah that's great! +1
    - to me it prints `0.3 ± 3.0e-07` Is it reproducible across platforms?
    - yes sorry, typo, `0.3 ± 3.0e-07` is what it prints :relieved:
    - Q: where did you place that command? in the script?
        - yes, but when running with `pytest` you need to add the `-s` option: `pytest -v example.py -s`, or use it as a regular python command outside pytest.
            - Thx `-s` is good to know.
        
31. What would be recommended workflow to include tests in jupyter notebook analysis?  
    - You can use [doctest](https://docs.python.org/3.6/library/doctest.html) or [unittest](https://docs.python.org/3.6/library/unittest.html) in notebooks.
    - In general, though, if something is complicated enough to need unit tests, I would recommend moving it to an importable library. That way you can reuse it in all your notebooks.

#### Break until xx:12

---
### 1.4 Automated testing
https://coderefinery.org/testing/continuous-integration/#automated-testing

32. Sorry, "follow the screen" == "type-along" or not? +1
    - `assert("follow the screen" == "type-along")` what is the answer? The webpage says "Type-along exercise".
    - Johan says please watch only.

32. Aaah, where did he press???
-  https://coderefinery.org/testing/continuous-integration/#step-3-enable-automated-testing
    - It somehow looks different in my github. i dont see the button
        - Could it be because you resized the brower's window?
            - No, there are several suggested options below, but not the button he had
                - I think i found the right one. I have to "create test python application"
            - Perhaps is that within the three-dot button? `...`
            - In the screenshots it looks OK ( multiple options to choose)?

33. What resources are being used for running the test? I guess this can be done only for very small test before providing resources to run tests. Is it so?

34. How do you trigger it again? [relay from twitch]
    - Actions trigger automatically on every push, Github looks for `.github/workflows/*.yml` and runs them.
        - I generally do `git commit --allow-empty -m "retrigger worflow"`, the `--allow-empty` allows a dummy commit which does nothing (no changes)
        - You can also navigate to `Actions -> [Action name] > Re-run jobs` to manually trigger a run

35. What are the limitations with a free Github account regarding running tests? I saw a limit on CI/CD, is that related?
    - https://docs.github.com/en/actions/learn-github-actions/usage-limits-billing-and-administration#usage-limits

36. Johan uncommented a line that should not be uncommented +1


37. I made the modification on a feature branch, but the test didn't run when I pushed it to github. In Actions, it shows that the workflow is for the main branch. How to make it run on every branch?
    - The workflow file (.yml file in .github/worflows) there are two lines with `branches: [ main ]`. You can either add branches here, or remove these two lines to run on all branches

38. It was difficult for me to see Johans screen when he opened a file in emacs, too dark.

39. How do we exit emacs? :)))))
    - `CTRL-x-c`


40. How did github realize that his branch was connected to his issue?
    - was the issue number referenced in the commit message or pull request? (I was distracted so did not see this closely)
        - he jsut wrote fixes #1. is this the "standard" message that has to be used?
         - Yes. the #1 is interpreted by github. You can either put that in the comment of the PR or directly into the commit message. There are a bunch of keywords you can use (see link below)
    - GitHub (and GitLab) automatically understands keywords like fix, fixes, close, closes: https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue
    -  Github workflow is configured so that it trggers the tests when a pull request takes place. The idea of a pull request is that you can connect them to tests and make do some checks automatically next to reviewing the code. 

41. Wait what, why a pull request? I thought he was in his own repo.
    - I guess to keep it general
    - This way one can see the test result before merging/modifying the main branch
        - Huh. I didn't even know you could send yourself a pull request.
           - It can  also be good if you know about a problem and don't have time, then open issue. later once you have time, you can then refer to the issue in a pull request in own repository and you have a bit of a trace for your work.
           - It can also be good if you want to get a review from someone else before merging.

42. Would be nice to see the .yaml file again I think.
    - You can see the default at https://coderefinery.org/testing/continuous-integration/
    - Thanks!
    - So you have to update it with the names of the branches that you gradually create, right? And then update it again when the branches are deleted?
        - The yaml has 
          ```yaml
          on:
            pull_request:
              branches: [ main ]
          ```
          which matches all PRs that are made against the `main` branch
             - Thank you. Indeed, what I was asking is how to have the test running on multiple branches. So I was wondering if I have to update this manually or not. But I guess the wildcards mentioned below are the way to go!
    - You can use wildcards (that's what I do at least).

43. Observation: Since GitHub and GitLab use these continuous integration, it would be nice to explain a bit how they work, since containers have been introduced before. This is a very concrete use case for containers, GitHub actually builds containers behind the scenes where an environment is generated and dependencies are installed to test the code on the cloud. (This can be good as a follow up read, not within the lesson).
    - We never have quite enough time for all the interesting things.

44. Will we get to do an exercise on this GitHub testing? (I hope so)
    - We don't have any more exercises planned, unfortunately. You can try following the instructions in the materials and ask here if you have problems.
    - Thanks, I will :) (might have worked just as well as an exercise without much introduction as a "watch the screen" session maybe, but that's rather input for another time)

45. How can we make Github automatically create new issue when test fails?
    - See question #68.

---
### 1.5 Test design
https://coderefinery.org/testing/test-design/

**Demo only, just watch and enjoy**

This uses Julia as an example language but applies to any language.  You should be able to read and understand.

46. Empty question.

47. Question for last topic: is it possible to setup a local machine and tell github to execute the tests there? If more resources are needed...
    - or is this the idea of setting up a local gitlab on my own machine/server?

48. factorial test addition: does it work for non-integers (ie. the gamma function)?

49. Factorial test: make sure that factorial(n) = n * factorial(n-1) for any value of n. Question: how to choose good values of n? Just pick them at random?
    - Test it with something that is larger than 2 probably, and also test it with edge cases like 1.
    
50. Factorial test: what if you enter a number with decimals?
    - Optimally your function should throw an error that indicates that this is not a valid input (e.g. initially testing for int), and that is something you could test (i.e. if the raised error is correct).
    
51. Is there a (jargon) difference between testing for correctness and testing for errors? So to be more clear, asserting for positive numbers test for correctness and testing for negative numbers check for correct input. Are both called testing?
    - both are called testing, and both can be equally important. E.g. you want to make sure, that your code does not give invalid results when someone puts in something unexpected. 
    
52. I don't understand why it says both "Test passed" and "Thrown: DomainError"in the example now +1
     - It was expecting for a DomainError and since it received one, the test passed.
     - It's because the factorial with the DomainError was called without a ";". So its output shows on the screen. Its output is an error message. No, wait. I think a testset returns the last message if there's no ";" after the end of the testset.

53. One could test if n! < ((n+1)/2)^n for n>1

54. Should tests also test validations? For instance, type of arguments. 
    - Yes, you should usually also test for these. The exception is when you want the function to work with unexpected inputs.


---
#### Pathfinding 
The fizzbuzz exercise is at https://coderefinery.org/testing/test-design/#test-driven-development

55. Use the modulus function (for dividing by 3 or 5). ;)

56. Why use test_broken and not just fizzbuzz(3) != "fizz"?
    - Answered in stream.
    - It just marks that we know it's broken, in case someone else looks at it. And if the test succeeds, the test framework will notify us.

57. You missed an `=`
    - Thanks

58. Is `number` in the argument meant as variable type or name?
    - name

59. Still unsure whether the test is case sensitive?
    - I think it is, it's comparing strings and they are usually different if the case is different.
    - OK, answered in stream. They are case sensitive.

60. Mixing up Julia now is too much cognitive overload. These examples should have been done in Python, which is what we have been using all along the workshop. I'd also recommend to do not deviate from the written lesson. Improvisation leads to disaster! :-) :+1:
    - Language consistency: +2
    - Improvisation: +2
    - Improvisation is especially problematic if someone falls behind and there are no notes of what has been done in the stream

61. Why are the right results associated to `@test_broken`? Are my wires crossed perhaps?
    - When we wrote the tests, we did not think they would succeed. Since they are no longer broken, we get a warning about them.
        - This is terribly confusing! You knew/declared you wanted to play a fizzbuzz game. If you want to play with true positives and false negatives, you should mention in advance  that this how we intend to stress-test the code, IMHO. Sensemaking along the way is draining. I am not even sure that I framing this right.
        - Perhaps, we should have mentioned the workflow of test-driven development.

62. Shouldn't use lowercase? fizz instead of Fizz
    - I guess this was answered in stream. Yes, they should.

63. So `broken` is a keyword recognized by Julia? It is not any random string like @test_blabla
    - It's recognized by the testing system.
    - `@test_broken` is a macro, which is kind of like a function. So `broken` is part of that name. 

64. Please leave the vim window open

65. So, I can officially say that I totally got lost... :( 
    - sorry :frowning: 
    - Would it be easier to follow if it was Python? (or consistently one language?) 
        - Yes +1, and stating more clearly what we are going to do. +1 never heard of a fizzbuzz game... Still don't know what has happend
        - Oh, good to know. The fizzbuzz-game is a common example in programming courses, but we should not assume you know it.
            - Probably there is a different name for it in my mother tongue. But I had a looot of programming lessons and never heard of it +1. Maybe my previous teachers were not so good :D
            - It's just one possible example. 
            - You explained what it was but did  not make it clear how you have used it to play around with the test functions (question 61). So I had to follow the actions and guess their intention in once and at once, which was heavy (and got me lost)

66. I saw something about that before, but... How do you test optimization routines? 
    - I generally have a simple function that I want to optimize and check that the returned maximum/minimum is approximately the same of the expected one (which I compute by pen and paper)
    - Use predefined test functions, where you know the result
    - If it's something more sofisticated there are special functions just to test optimization (https://en.wikipedia.org/wiki/Test_functions_for_optimization) +1

67. I found Luca's follow-along to be quite nice and easy to follow. Thank you.
    - Thanks :smile:
        - I like how when I type `:sm` the first suggestions is :small_airplane: 
            - :laughing: :+1:

68. Repeat 45. How can we make GitHub automatically create new issue when test fails?
    - I don't know of a way to do this. The failing test is quite visible, though.
    - There is a workflow that does this here: https://github.com/JasonEtco/create-an-issue. It could be modified to do this, but it would take some work.
    - I think for security reasons it's probably a little tricky to create

69. Hey, I recieve this error :---------------------------------------------------------------------------
    ```
    AssertionError                            Traceback (most recent call last)
    ~\AppData\Local\Temp/ipykernel_18924/4262281447.py in <module>
    ----> 1 test_fiz_buz()

    ~\AppData\Local\Temp/ipykernel_18924/2098323396.py in test_fiz_buz()
      1 import pytest
      2 def test_fiz_buz():
    ----> 3     assert fiz_buz(5)=='Buzz'
      4     assert fiz_buz(12)=='Fizz'
      5     assert fiz_buz(15)=='FizzBuzz'
      ```
    and this is the fuction i made in jupyter nb 
    ```
    def fiz_buz(say):
        if not isinstance(say, int):
            raise TypeError
        if say < 1:
            raise ValueError
        for i in range(1,say):
            if i%3==0 and i%5==0:
                print("FizzBuzz")
            elif i%5==0:
                print("Buzz")
            elif i%3==0:
                print("Fizz")
            else: None
    ```
     - The test expect the function to return a string, insted of printing. So `return "FizzBuzz"` insted of `print("FizzBuzz")`
     - The for loop is not needed (for the standard fizzbuzz exercise, you might be doing a different one).
     Alrighty! Thank you for your help.

    
#### Break until xx:10


---
##  2. Modular code development
https://coderefinery.org/modular-type-along/

### 2.1 Starting questions
https://coderefinery.org/modular-type-along/questions/

#### **What does “modular code development” mean for you?**
- Organising your code, such that similar functionality is grouped and that individual parts can be used without the necessity to load everything. +1
- not spaghetti
- I can take a piece (a module) originally developed for some context (e.g., calculate total sum of money) and I can use it in another contect that needs to solve a similar problem (calculate total number of sheeps).
- Create functions for tasks that are repeatedly needed
- Haven't heard of it before!
- Code developed in smaller modules can be tested in modules in order to more easily isolate problems.
- ...
- not heard of it before (but it's starting to sound like exactly what I'm missing in my programming practice!)
- avoid repetitive codes and define a function corresponding any task
- Isolate dependiencies between software components.
- reusable code in different applications -> more people use it -> you meet new people -> build community and network

#### **What best practices can you recommend to arrive at well structured, modular code in your favourite programming language?**
- [python] Use OOP (object oriented programming)
- each function should do just _one_ job (heuristic: fit on a single screen) +1
- separate "pure" functions (stateless, same input = same output, easy to test) from IO/user input/...
- object oriented programming
- bottom-up or top-down design depends upon the problem
    - don't use too much OOP :P it has its uses, but it's dangerous if "you just have a hammer and then everything looks like a nail" 
        - Funny analogy :smile: 
    - Python also does a lot of OOP out of the box, for instance modules are instances of objects with methods and properties, everything in python is an object. 
- .[python] `if __main_pytest example.py_`...+4 (found out about this just recently, it's so good!!)
- don't repeat yourself ([DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)); if you spot the same pattern three times, see if you can separate it out to avoid the code duplication
    - language features you can use for this (e.g. in Python): OOP & inheritance, writing smaller sub-functions, [context managers](https://book.pythontips.com/en/latest/context_managers.html)
- Inline documentation / function description to help if one uses the funtion for a new application and the functionality is not immediately clear
- For pipelines and workflows I like better function oriented programming and functions I can call from the terminal.  I think OOP and functional programming(FP) have their own benefits for different contexts, we shouldnt overrate OOP (at least with python), as it comes from a context and is also very related to languages.
    - :+1: 

#### **What do you know now about programming that you wish somebody told you earlier?**
- That everyone is still googling stuff continuously and you don't need to know everything +4
- There are many things I would rather have never heard...
- All tought in this course :smile:
- Everything in this workshop......:+1:
- write unit tests! (I already know, and still wish someone kept reminding me) :+1: :+1:
- check every function to be sure that it does what is expected
- [stackoverflow](https://stackoverflow.com) +2
- Start small, with tiny bits of easy syntax. For example, "Hello world", then slightly bigger, etc.
- IDE are there to help
- The power of `vim` / that I don't need to learn an IDE. This isn't a plug, but the real, under-the-hood power. (eg. `gd` in normal mode jumps to a function definition) +1
    - (you beat me to it)
    - I'm almost exclusively using vim, so something for myself: also don't underestimate the power of a proper IDE for debugging (breakpoints, values of local variables, etc)
    - I am not suret sure about this. i quite recently switched from emacs to vscode. There are still things I am missing, but the overall experience is really good
- which courses are helpful for me to advance, because there are sooo many programming courses. I didn't know there were programming courses targeted at researchers who don't know much about coding (such as this one)
- make it readable +1
- Remember that you forget you logic faster than you think! document and simplify the code so that you still understand it 4 months after
- "code patterns", especially Liskov Substitution Principle (cryptic name, but would have helped me avoid so many mistakes-in-hindsight in writing "modular" but not modular-enough code)
    - dependency injection is another one that's probably taking a while to learn, but makes for much more modular code
- if you don't know why your code works, change it +1 (or rewrite)
- 
- learning about one language deeply rather than having superficial knowledge about several programming languages
- comment your code extensively — it's a love-letter to your future "__ self __". <3 +1
    - aim for self-documenting code, sensible variable names, etc. (comments can go out of date)

70. when I tried the Design-3 exercise, the test fail because the process doesn't have permission to access the file. What should I do?
     - Which file? if "reactor", the exercise is to solve this problem :smile_cat: See the monkeypatch library. 
     - the temporary file created by the test function. What is 'reactor'?
        - In the code we import "reactor". 
            - Sorry I mean design-3
     - Do you mean Design-3?
     - Can you clarify, so you create a file using `tempfile.mkstemp()` and then you cannot write to it? Or is there an error at line 5?
     - Error message:
     ```
     ================================== FAILURES ===================================
     _____________________ test_count_word_occurrence_in_file ______________________

        def test_count_word_occurrence_in_file():
             # create a temporary file for the test
             _, temporary_file_name = tempfile.mkstemp()
             with open(temporary_file_name, 'w') as f:
                 f.write("one two one two three four")
             f.close()
             count = count_word_occurrence_in_file(temporary_file_name, "one")
             assert count == 2
     >       os.remove(temporary_file_name)
     E       PermissionError: [WinError 32] The process cannot access the file because it is being used by another process: 'C:\\Users\\xxx\\AppData\\Local\\Temp\\tmpxft7d2sj'
     
     wordinfile.py:26: PermissionError
     =========================== short test summary info ===========================
     FAILED wordinfile.py::test_count_word_occurrence_in_file - PermissionError: [...
     ============================== 1 failed in 0.12s ==============================
    ```
      - OK, so it cannot remove the file. It looks like Python did not properly close the file. But it should, the `with open(...` syntax should take care of it.
          - You could just remove the line with `os.remove`. It's a temporary file, so it should get removed automatically later.
          - There is something going on that I don't understand here.

71. If you make typos, we give you typs instead of tips 
    :laughing: 
    - :heart_decoration: love this!! I am going to steal it :)
        - No stealing: it's licensed alongside the course material

---
### 2.2 Learning topics
https://coderefinery.org/modular-type-along/learning-outcomes/

---
### 2.3 Our task
https://coderefinery.org/modular-type-along/lesson/

72. Shitty weather in helsinki. If it snows one more time I am starting to cry
    - Are the palms on the beach shivering out of the cold?
    - It's even supposed to snow in the Netherlands today...
    - It's just a matter of personal taste. As a person from country with not really significant amount of snow, I quite love it.
        - haha, yes that's true

73. is there any platform that we can recieve one on one, or live help for our coding studies? +1
    - I want to add to that that it is much less scary to ask a question to one single person rather than posting it in a forum for the world to read.

74. Radovan: "HackMD-along."  <-- Nice expression. :+1:

75. One place where I often find myself in need to move out of Jupyter: when I need interactive plots (i.e., click on plot to get something happen) and do not get it to work in Jupyter.
    - You should try the magic-settings in Jupyter! I's not as good as the figure-display in MAtlab, but it's ok (write e.g. %matplotlib notebook before the figure you want to be interactive)
        - done that, but I get some interactivity, not all interactivity :(
        - Hm, yes I agree it's not perfect... If someone else has better tips I'm also super interested in this. But so where do you "move to" when you say that you move away from jupyter?
            - I made a script with essentially the same code and I run it from command line.
        - jupyter is not reactive, that's the bottleneck why you won't have perfect interactivity in it :(

76. Can someone tell me in a short sentence what pandas is doing?
    - Is like spreadsheet in python (with lots more of functionalities of course)
    - It's uploading the data in a dataframe to be sorted, filtered, processed, ... as distinct for example from numpy which is more focussed on number crunching.
        -  If you type `type(data)` you will see it is an instance of a special class provided by Pandas
    - I believe `pandas` uses `numpy` under the hood, by the way.

77. Note: `wget` is not working? Try `curl`.

78. Oppinion: Name the axes in the plots! +1
    - ~~I think pandas makes it a default action~~ 

79. https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.clf.html explains why `plt.clf()` removed the figure
    - Thanks for the explanation!

80. To answer Radovan: Create a function that has as parameter the number of measures +1

    - find out how much data you have in the file, then plot it all (or a subset)
    - Better to load the dataset first and then let the function work on the loaded dataset


81. Generally you shouldn't include imports in a function, correct? But what if you have a modular function you want to use somewhere, but the imports are not included. Is there a nice way to solve that? Would you assert if an import is included?
    - If will naturally fail (with clear message) if not imported, so no need for extra testing
    - Usually people import at the top, it either becomes obvious (or more likely, your editor will warn you about the problem).

82. No, > pre-processing function: (eg. count entries, etc.)

83. I read somewhere that a function should not have more that 6 parameters (as a good programming practice)
    - Seems like a useful rule of thumb (but as always it depends on the context).

84. Should we use a global constant which stores the current maximum number of loaded data and just reload the data if we want to acces more lines?
     - Probably a bad idea in python3... hm not sure
     - Instead of a global number, you could add this to the function or create an object with the dataframe and the number. These leave the function pure and make testing easier.
         - Good point. I am just wondering if he is going to reload the whole dataframe 3 times

85. Book recommendation: Timeless Laws of Software Development. Jerry Fitzpatrick.
    - Is it beginner-friendly or does it assume you are proficient in one language?
        - I would consider it beginner-friendly. It has examples written in C but the important are the concepts discussed in the book. It's easy to read and follow and it has only 172 pages.
            - Thanks

86. Instead of the hard code the directory address and the file name give them as the input so different people can use them on their own computers withouth going through the finding where to change and change the part of the code.
    - Yes, hard-coding paths is a common issue. It's convenient at first, but if you ever reuse the script, you should remove them.

87. **Tip** @radovan pass the `num_measurements` variable to `read_data`; and also the column name `Air Temperature (degC)`+1

88. What about moving function call into another cell then function definition?


89. Do you need an input variable for temperature in the plot_data function?
    - Yes, I think that is coming up

90. would it be tidier as well to use the full path of the file? To make it easier to use in another project
    - Yes, that helps. IF you use in another project, you probably want to make the path into an argument.

91. I think you need to restart the kernel to clear global variables before rerunning. Otherwise, the test if it still works does not apply.
    - Yes (being discussed on stream)

92. Are there any performance issues in placing thing inside functions as opposed to just a sequential script?
    - In Python, I don't think so. In other languages it might be faster if the string is in the function or is an argument to the function.

93. Empty question.

94. One issue long term you might get is with the mean variable name, you could name it differently and that it wouldn't be defined in the plotting function. I would put an argument for the mean. plot_data(figure_name, mean):...
    - Yes.

95. It works because num_measurements is a global variable; the function is just not portable. 
    - Restart the kernel or the variable is still in the memory (like Matlab...) +1

96. Is it possible/sensible to write tests for "Why is it working when it shouldn't be"?+1+:smile:
    - **Very much so**. This condition is called 'unexpected pass' and is indicated with XPASS. In a mirrored fashion, XFAIL means 'expected fail'.  
These are  conditions that you definitely may want to design and implement in your code to make it robust. Have a look at this: https://www.gnu.org/software/dejagnu/manual/Output-States.html. 
This is even a standard for the output of test frameworks: find a bit more in https://www.gnu.org/software/dejagnu/manual/A-POSIX-Conforming-Test-Framework.html

97. For `compute_stats`, would it not be better to divide by `len(temperatures)` instead of passing `num_measurements` as an input variable? +1
    - I agree.

98. What do you think is a good place to know more about how to get different (sub-)projects to work together with GitHub/GitLab via e.g. git submodules or git subtrees?
    - For your actual question, the only place I know is https://git-scm.com/book/en/v2/Git-Tools-Submodules
    - If possible, make them easy to install (for python, release and list on PyPI, or install from a public git repository). Then include them in the requirements of the other project.
        - For Python, add a `setup.py` in each git repository, so that they can be installed with pip.
        - For the main project (that depends on the others), include the other packages in requirements.
        - Now you can `import` the other libraries without needing submodules. They can also be used in you other projects and other people can use them.
        - Check the PyPI tutorial on packaging python projects at https://packaging.python.org/en/latest/tutorials/packaging-projects/
    - This is just my opinion, but I think it's better to keep the different repositories separate and usable by the others.
        - Thanks for the python part of our projects we already do something like this, however I was more wondering, of that would work best for some C API that is somewhat build around singular submodules that are designed to be patched together, but I guess thats a bit out of scope here :smile:
            - See https://git-scm.com/book/en/v2/Git-Tools-Submodules about submodules
            - Personally I would still make them separately installable (for C I would use CMake) and add use installation dependencies insted of submodules. You can add public repositories as dependencies in CMake.
                    - Have to admit I didnt know,that was possible in CMake, will defenitly look into it, thanks! :+1: 


99. In function compute stats, one can just put len(temperatures) instead of another variable num_measurements
    - good catch
100. The name '25.png' looks bad to me. It does not say what is in the file. IMO e.g. 'temperatures_25pts.png' or sth like that.
     - that's a valid point, and yes in production code this should not be the output file.
101. you can do `ctrl`+`shift`+`minus` to split a cell
     - AMAZING! Thanks!
     - Control shift minus!
     - "Activate command palette" available in JupyterLab from the menu View or with Ctrl + Shift + C; then you can search the command you like (and find it with a bit of luck)

102. Is there a way to create a cell out of a selection in Jupyter?

103. Does anybody have experience with jupyterlab-vim? I tried, but the native jupyterlab commands conflict with vim commands.. Where could you redefine jupyter-lab commands per default?

104. **Tip** make sure that you call `plt.figure()` beforehand! And `plt.show()` at the end of the function! +2

105. you should add plt.show() to plot 3 graphs

106. This is super nice! Getting some input on standards and "how to code nicely and increase readability". 
     - I told you it would be amazing

107. Is it really a good idea to reload the WHOLE dataset everytime? +1
     - Yeah, needs improvement if the dataset became large.
     - Pandas helps you select the parts of the datasets you want (even though we don't go into this now...)

108. I also wonder if prototyping in jupyter is not a great idea after all (because values of variables are saved in the kernel, which can make debugging extra challenging).
     - I think it's fine if you make it part of your routine to restart the kernel and run all cells again before you commit your changes
 
#### Break until xx:03

109. May be it is good to show how to use the defined functions in another python script, i.e., a different file. ++++1
     - could it be possible to use functions stored in different files in the jupiter notebook? If so, how?
     - great suggestion. we will try that
     - wouldn't it then be better to store the function in its own .py file and import it at the top (alongside numpy, pandas etc)?

110. Also now perhaps make use of the jupyter notebook and add some comments on what you have done in the different sections. That sometimes also help spotting things to improve.

111. Tip. Cell 4 now. Could get the plot labels from the names in `data`? 


112. How to write test for functions that create plots?
     - Not really answer, just thinking aloud: what is your baseline for a right/wrong result to base the test on?
         - For instance, checking that the axis have the labels, or all the layers are there, etc.
             - If you can translate your idea of 'checking' into an algorithmic form, it should be possible. I am afraid through that you refer to the visual outcome, and this is diffult to parametrize. In terms of coding, you know that there will labels because you placed a command in the function (and that's why functions are for!)
     - Tests for visualisation are inherently difficult. But if it is save to assume, that the plotting function does, what it is supposed to do (wrt to creating the plot), you can test the inputs, OR, you could try to export the plot to a file and potentially have a original file that you compare against.
     - wrong answer: train an AI to recongnize the picture and use it to test the picture produced by the function? ;)
         - Could be a solution to generate the picture as SVG and then test the output SVG file?

113. use `jupyter nbconvert --to python`
    - Good idea!

114. indent! (the comment). ok still works :D but for readability it should be a comment from the function...
    - +1 for the readibility

115. Shouldn't `compute_stats(data)` be rather `compute_mean(data)`?
    - Good suggestion!

116. Nice way to split the file into separate files: `split -p "def" inputfile.py`
    - Cool! Thanks for sharing.

117. If this was a real project, would you now want to make a test for the compute_mean function?
    - probably, when in doubt, test it :D
    - possible tests: 
        - the mean of an array with a single value is that value; try with [0, 0, 0] and with [1, 1, 1]; 
        - with the ones only, if you muliply the average by the number of elements n, you get n (the sum of n ones)
        - test against sign errors [-1, 0, 1]
        - test against error in ordering [-1, 1, 0]
        - ....

118. if this module is in a different directory can you call it with something like import ../folder.statistics
     - You can import from the parent folder with `from ... import statistics`
     - But, even better would be to use an absolute path
       ```
       from importlib.machinery import SourceFileLoader

       statistics = SourceFileLoader("statistics", "/path/to/file.py").load_module()
       statistics.MyClass()
       ```
     - And even better:
         - add a minimal "setup.py" file. This turns the folder into a python package you can install with `pip`. see https://packaging.python.org/en/latest/tutorials/packaging-projects/.
        - then go to the folder and run `pip install -e .`
        - now you can `import statistics`
            - Yeah, but if you update your files later don't forget the --upgrade in the pip install command. This took me some time....


119. Could you please do the command line interface? It seems very usefull+4
    - Would be really helpful to have a short video on this later on.

120. I wouldn't use a hyphen in the filename!
     - It's a question of your convences. "Do it whatever you like, but be consistent". But you're probably correct that some standards might tell naming convention for this.
         - If you want to load this as a Python module, it will be hard if it has a non-valid character in the filename!
         - Ahh, ok, thanks... Didn't know hyphens are non-valid character (considering that there is even "kebab-case" convention -- probably not for python then...)
     - life is too short to worry about style issues :D
    
121. It is very helpful to have tests in separate files; that way, the tests can be run independently of the source code.
     - That is a nice solution as well. Do what is most helpful for you and your collaborators.

122. Is it good to have the test in the script? This implies that your package depends now on pytest. I personally like the idea, but I was wondering what implications it has as I normally come across a separate tests directory. +1
      - A separate tests directory, or separate test files, indeed means you don't need to depend on pytest.
      - Depending on pytest means you have to mind the version you depend on, and this could clash with your other dependencies.

123. In there any IDE for python that would see that `approx` needs to be imported and suggests to add the import statement?
     - I don't know for sure, but I would be very surprised if VScode doesn't have an extension for that (especially when talking about python)

124. Is there going to be an after-workshop? :smile: :smiley_cat: 
     - I think we'll hang around for a bit after the outro. And we have the community call on Monday 14:00 CEST when we'll discus the workshop even more. - joint discussion instructors, ELs, and everyone elese interested.
    

125. Can you post the link to the command line interface instructor note?
     - https://coderefinery.org/modular-type-along/instructor-guide/#command-line-interface
     - Thank you!

126. Is it possible to provide another course focusing on tn the materials of the second week with more details? like coderefinary.v2. covering more test, reproducibility and collaborative coding. another 6 sessions. +1 +1 +1

127. when I have multiple repositories depend on modules from other repository, should I make a package? or there is other solutions? (instead of copying the modules to every repository)
     - Turning the repositories into packages is probably the best option. See https://packaging.python.org/en/latest/tutorials/packaging-projects/ for instructions, but note that the page describes a bit more than a minimal setup.
         - Copying modules means you need to develop the same code in multiple places, where a package is in one place.
     - also (a bit advanced and needs care) one can have dependent git repositories.
         - wow! is there a tutorial?

128. What is the link of the outro page Richard is reading?
     - https://github.com/coderefinery/workshop-outro/blob/master/README.md

### Extras
[Nordic-RSE](https://nordic-rse.org/)

---
## Feedback on today's lessons

### Today was (multi-choice):

- too fast: oo
- too slow: ooooo
- just right: ooο ooooooooooooooo
- too advanced: 
- too basic: ooooo

### One good thing about today:
- automatic testing (really cool!)+5 :+2: 
- The live coding is a good way to educate +1
- Very informative! Learned so many things! Thanks!+1
- I have learned a lot about different aspects of modern software development +1
- all materials had very good flow!
- Quite easy to follow along. 
- pytest +1 +1
- really great learning, especially with testing today.
- GitHub CI +1
- Both testing and seeing the workflow was super useful! 
- It has been amazing learning sessions!
- Met my goal: now I'm comfortable getting stuck into a team that already uses all these tools
- Seeing a live, walk-through of using these various software development tools in a (pseudo-)end-to-end process.
- I think the last session today was really useful - I want to improve my code-style for better readability and better structure, and this is hard to achieve when you're not a programmer, but rather use programming in the science you do! This session helped on that. I just wish there had been more time for this. 

### One thing to be improved:
- maybe, show testing also in more difficult cases (but it requires more time and common ground to do...)
- more exercises (automated testing?)! +2
- Would have liked to work on continuous integration as an exercise +4
- Do you have material on python packaging?
    - https://aaltoscicomp.github.io/python-for-scicomp/packaging/
- more exercises. This is the reason for having a live workshop. If I wanted to just watch a video, there would be tons of videos in youtube for that. So every time you say "just watch and relax" I feel some time could be better invested. +1
- There should be a feedback session for the morning and one for the afternoon when there is a change of content and/or instructors. I tend to forget the feedback for the morning
- Give participants a small piece of code and tell them how many tests would be good to run, then let them figure out which those tests are.
- python has been the main stram for the workshop. The change to Julia was a "disturbance in the force" that could have been avoided since the goal was not learning Julia.+1+1+1+1+1+1
- I hated HackMD going up and down while I was writing +1. Isn't a googleDoc document much simpler for the same purposes?
    - Google Docs would be even more unstable for this number of participants, from our experience. But I do find it annoying too when it's jumping.
- I wish I could join through zoom. Though I participated and did the exercises via twitch, it would be nice to take part through zoom.
- I wish there had been an exercise on testing with git/automated testing. For me at least this session would have been better as an exercise rather than a watch-session. +1
- More time for the final topic on how to improve code structure. 

### Any other comments:
- What is the link of the outro page Richard is reading? https://github.com/coderefinery/workshop-outro/blob/master/README.md

---
## Feedback on the CodeRefinery workshop as a whole

### One good thing about the CodeRefinery workshop style:
- Relaxed, open, flexible style +1 +1
- I really toooooohink that Twitch+Zoom+HackMD really works nicely!+3++3+100+1
- Portrait mode stream +7
- Live HackMD with huge amounts of questions/feedback +2 +1 +1 +1 +1
- Excellent course notes +1+1+1
- A great course to get started in git, shared work and improving your general workflow. +1
- The course was really helpful in understanding the concept. As a beginner in software development, this has really enlightened me of the practices. +1+1+1 +1
- The format of this course was really well done. A few people presenting and another person answering questions on the HackMD is great because it gives viewers the ability to ask questions while listening, but without interuppting the flow of the workshop. +1+1+1
- Availability of more instructors
- Great audio quality +1
- The course material will be an amazing dictionary for later use! Everything we've gone through these days we'll find answers to in the course notes. It's hopeless to remember everything, but just knowing where to look for answers is just as good.
- Good thing to have two instructors interacting.


### One thing to improve about CodeRefinery workshop style:
- More coding Homeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeomeome sessions! :+1: +2222222222222222222222+1
- Maybe exercises in the afternoon for who wants to (at different levels, specially for institutions and groups).
- This might be a bit complicated, but maybe breakdown the info in terms of beginner-beginner/ somewhat beginner with some experience/ intermediate ... Maybe there should be some pre-reading to get acquainted with some of the language? +3
- Actually, the breakout sessions were less useful; I much prefer the live-stream 'channel'.
- More exercises! Less sit back and "relax". I find it very hard to stay focused on watching someone else press buttons on GitHub or run commands in the terminal. I think less time on introduction or the exercise and more time for trying yourself would have been good. The exeption I think was the very last session - this worked well as a "sit and watch". 
- Stick sctrictly to the lesson materials for the type-along parts. Deviating from it makes it impossible to retake if you get lost even just a bit.

### What did you enjoy most about the workshop or found most helpful?
- Live coding was nice! :smile: +1+1 +1
- Coding with python! :satisfied:   +1
- Learning how to use git properly +2+1 +1
- Having all of the teaching materials available publicly+1+1+1+1+1+1+1+1+1+1+1+1 so I could catch up when I missed something +1+1+1+1
- Being able to follow and type along the presenters - helps because it allows me to commit the tools to memory faster. +1++1+1+1
- Home work excercise
- Getting familiar with all these useful tools! There are so many tools to use, it's hard to know whats actually benefitial to get into. This course helped navigate and figure out what would be worth learning and adapting into my daily work. 
- The documentation is excellent and allows you to retake later or refert to it. 

### General thanks
- I really appreciated all the time you devoted to running this workshop - thank you so much!  I learnt lots. +1+1+1+1+1+1+1
- All the presenters were really patient with everyone's needs. That was really nice, thank you
- Just thank you!
- Thanks for preparing the general documentation. It is well done! 
    - omg yes thank you so much for the documentation :100: +1
- Thanks to all behind the workshop! :) 
- Thank you so much. All of you did a lot of work helping many people to improve their coding habilities. Thank you for this opportunity and great job. I enjoy it a lot
- Thanks for the workshop, learned a lot. Really solid teaching approach
- I wish I would have known about this course earlier, it helped me a lot. Both in terms of knowledge and in getting more comfortable / confident with coding. Thanks for this! +1
- Many thanks to the organizers 
- Thank you soo much for everything!! I've learned so much
- Thank you! Really appreciate. I learnt so many new things.
- Thank you very much! CodeRefinery workshops are always very useful!
- Thank you so much! This is really useful . I have finally learnt how and why to use GitHub :D
- This workshop was better and more useful than many others I've been to, thanks! +1+1
- Thanks a lot! It was very useful!
- Thank you again, it is very amazing to learn how you teach and function as a community, very inspiring and moving :) +1
- Thanks a lot for all the work and really nice to have these resources for later use as well. Very well constructed!
- Thanks for the course! Interesting and I have learnt a lot
- I'm super impressed with how good you are at keeping up to speed on the hackmd! Answers come in quickly AND you manage to incorporate what is going on in the hackmd in the stream. 
- Thanks for all the effort put. Excellent job!
