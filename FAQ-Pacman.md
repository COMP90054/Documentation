# FAQ - Pacman Projects - AI Planning for Autonomy

* [GENERAL](#general)
   * [In a code assignment/project, how do I make sure I do not go against academic integrity?](#in-a-code-assignmentproject-how-do-i-make-sure-i-do-not-go-against-academic-integrity)
   * [How do I submit my project solution in my GIT repository?](#how-do-i-submit-my-project-solution-in-my-git-repository)
   * [How do I change the submission tag if I have already tagged one commit for submission?](#how-do-i-change-the-submission-tag-if-i-have-already-tagged-one-commit-for-submission)
   * [How do I zip files in folder X without including the folder X itself?](#how-do-i-zip-files-in-folder-x-without-including-the-folder-x-itself)
   * [I submitted wrongly (e.g., didn't tag correctly) and is now after the due date, can you consider my submission?](#i-submitted-wrongly-eg-didnt-tag-correctly-and-is-now-after-the-due-date-can-you-consider-my-submission)
   * [Project specification says "You should code your implementation only at the locations ...." . Does this mean that we can't create our custom classes outside the provided functions?](#project-specification-says-you-should-code-your-implementation-only-at-the-locations---does-this-mean-that-we-cant-create-our-custom-classes-outside-the-provided-functions)
* [PACMAN SETUP](#pacman-setup)
   * [What is the best way to develop my solutions for the Pacman project?](#what-is-the-best-way-to-develop-my-solutions-for-the-pacman-project)
   * [What version of Python should I use?](#what-version-of-python-should-i-use)
   * [How do I setup a system in Windows with Python 3.6?](#how-do-i-setup-a-system-in-windows-with-python-36)
* [TROUBLESHOOTING](#troubleshooting)
   * [Can I use problem._visited?](#can-i-use-problem_visited)
   * [I get "I get "_tkinter.TclError: no display name and no $DISPLAY environment variable" error when running in WSL or ssh](#i-get-i-get-_tkintertclerror-no-display-name-and-no-display-environment-variable-error-when-running-in-wsl-or-ssh)
   * [Cannot run Pacman due to problems with Tkinter: "ImportError: No module named Tkinter"](#cannot-run-pacman-due-to-problems-with-tkinter-importerror-no-module-named-tkinter)
   * [How do I know the type of a variable in Python?](#how-do-i-know-the-type-of-a-variable-in-python)
   * [Error module 'cgi' has no attribute 'escape' when running autograder.pt](#error-module-cgi-has-no-attribute-escape-when-running-autograderpt)
* [CAPTURE THE FLAG](#capture-the-flag)
   * [How to load my additional files beyond myTeam.py?](#how-to-load-my-additional-files-beyond-myteampy)
   * [Do you provide library X (e.g., tensorflow)?](#do-you-provide-library-x-eg-tensorflow)
   * [Games go too fast! What should I do?](#games-go-too-fast-what-should-i-do)
   * [How do I replay a game?](#how-do-i-replay-a-game)
   * [How does one check if a given agent is currently scared? Is the only option to check the number of capsules in previous states?](#how-does-one-check-if-a-given-agent-is-currently-scared-is-the-only-option-to-check-the-number-of-capsules-in-previous-states)       
   * [It looks like the distance calculator is performing calculations in the background of our turns, can we replace it with our own version that does more?](#it-looks-like-the-distance-calculator-is-performing-calculations-in-the-background-of-our-turns-can-we-replace-it-with-our-own-version-that-does-more)
   * [How to call a planner (or another external tool)?](#how-to-call-a-planner-or-another-external-tool)
   * [Binary file for Metric-FF](#binary-file-for-metric-ff)
   * [What does it mean that we must use 2/3 AI techniques? Do they all need to be part of the final submission?](#what-does-it-mean-that-we-must-use-23-ai-techniques-do-they-all-need-to-be-part-of-the-final-submission)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)

----------------------

## GENERAL

### In a code assignment/project, how do I make sure I do not go against academic integrity?

Check the answer to this key question here. [TECHNICAL](https://docs.google.com/document/d/14giB_eIkWeBwMsBWY0-Tjd6itDV2BBOvwEqcSDyYRZ0/edit?usp=sharing)

### How do I submit my project solution in my GIT repository?

You submit by **tagging** the exact commit that you want to submit with the name given in the assignment specification. Note tagging is NOT the same as a branch, a tag is a specific point in the repository history, the point you want to be used for marking. A branch is a whole history, so it does not specify a commit version to use for marking.

- For basic information on tagging, check [here](https://git-scm.com/book/en/v2/Git-Basics-Tagging). 
- To create, push, and view tags in GitHub Desktop, check [here](https://docs.github.com/en/desktop/contributing-to-projects/managing-tags). 
- To tag via command line or via GitHub web interface, check [here](https://stackoverflow.com/questions/18216991/create-a-tag-in-a-github-repository). 

Note that the timestamp of the commit is the submission date.

See next questions to change the submission tag you have already done (i.e., you want to update your submission to another point in the repo history, usually a more recent one).

### How do I change the submission tag if I have already tagged one commit for submission?

This will happen when you realize you have a better version to submit than the one you submitted/tagged before. To do that, you need to delete the tag (from your local repo and from the server:

- First delete it from the GIT server by running: `git push --delete origin <tagname>`
- Second, delete the local tag in your repo by running: `git tag --delete tagname`

More information on how to delete git tags [here](https://devconnected.com/how-to-delete-local-and-remote-tags-on-git/).

### How do I zip files in folder X without including the folder X itself?

Use the `-j` option, for example:

```
zip -r -j myAgent.zip project-2/MySolution/ 
```

However, this is OK if you don&rsquo;t need ANY folder at all in the zip, everything in the root. If you just don&rsquo;t want the root folder included but you do want all the folders after that to be included:

```
rm -f myAgent.zip ; cd project-2/MySolution; zip -r -j ../../myAgent.zip * ; cd ..
```
### I submitted wrongly (e.g., didn't tag correctly) and is now after the due date, can you consider my submission?

We will not fix any submission and it is your responsability to do it correctly.

However, the nice thing about git-based projects/assessments is that we can rely on commits. If you have submitted your tag incorrectly (did not tag it at all, tagged with different name or different capital letters), then please fix your submission by tagging the specific commit you want me to mark. I will use the timestamp of the commit itself, not of when it was tagged. This means that if the commit was done before the deadline, then all good!! Isn't this cool?


### Project specification says "You should code your implementation only at the locations ...." . Does this mean that we can't create our custom classes outside the provided functions?

Yes, you can create some help functions or classes, but **always** in the allowed files. Any other change in any other file will be totally ignored.

If you want to create custom classes and functions, you can also nest them inside the location where you read `***YOUR CODE HERE***`. See [this link](https://www.datacamp.com/community/tutorials/inner-classes-python) and [this link](https://www.programiz.com/python-programming/closure#:~:text=A%20function%20defined%20inside%20another,in%20order%20to%20modify%20them) for more info.

## PACMAN SETUP

### What is the best way to develop my solutions for the Pacman project?

We highly recommend developing your solutions in your local machine (e.g., your laptop). Even more, if you are running Linux locally, 99.99% sure your code will ran in another Linux install. If you are using Windows, you may want to consider installing a Linux virtual machine with Virtualbox.

Running it locally will make the development much faster. I also suggest using a version control system, like git or mercurial. This is best practice and should be something normal at this stage of the program. Remember though NOT to make your solutions public and this will violate the course plagiarism code AND also break the will of the creators of this wonderful project. SO if you use bitbucket for example, make sure your repository is private.

### What version of Python should I use?

**All projects run on Python 3.6, so your code must be written for such version**. Please note the original project from UC runs in Python 2.7. 

__*Note: Some Linux distributions come with both python2 and python3 installed but default to python2 for the python command. In this case, you should use the python3 command in place of python to explicitly use version 3.x.

Additionally, in order to render the game, the homework projects require the Python module tkinter to be installed. You can follow the [official docs](https://tkdocs.com/tutorial/install.html) to get tkinter on your platform if it is not installed already. If you are using Linux, many distributions have packaged tkinter for easy install and you should use the package manager to install it. The package name is python3-tk for Debian/Ubuntu, python3-tkinter for RHEL/Fedora and tk for Manjaro/Arch.

There is no problem **having more than one Python version installed in your machine**, you just need to be careful your code is using the right one. You need to use Python Package and Environment Managers.


One good option is to use **Miniconda**, a minimalist version of Anaconda virtual environment variable to have both installations coexist in your machine (here are others these days, like pipenv)

The download page is [here](https://conda.io/miniconda.html) (install either the version for Python 2 or 3, it only affects the default environment, you can still install others).

After you install Miniconda, you can create new environments via 

```
$ conda create --name <env-name> python=3.6
```

For example, you can do:

```
$ conda create --name ai20 python=3.6
```

At that point, to active your ai20 environment:

```
$ source activate ai20
```

(on Windows; instructions for other OSs [here](https://conda.io/docs/using/envs.html#change-environments-activate-deactivate))

These commands will make your calls to `python` or `pip` run the correct version.

Example run (on Debian Linux, so the activation command is slightly different):

```
marco@w8103259:~$ source activate py27
discarding /home/marco/miniconda3/bin from PATH
prepending /home/marco/miniconda3/envs/py27/bin to PATH

(py27)marco@w8103259:~$ python --version
Python 2.7.12 :: Continuum Analytics, Inc.

(py27)marco@w8103259:~$ source activate py36
discarding /home/marco/miniconda3/envs/py27/bin from PATH
prepending /home/marco/miniconda3/envs/py36/bin to PATH

(py36)marco@w8103259:~$ python --version
Python 3.6.0 :: Anaconda 4.3.0 (64-bit)
```

As you can see, I have python 2.7 and 3.6 coexisting peacefully in my OS."

### How do I setup a system in Windows with Python 3.6?

Although we will assume you are able to install and get Python running in your machine, there are plenty of videos on that on the web. For example: 

[![Alt text](https://img.youtube.com/vi/oHOiqFs_x8Y/0.jpg)](https://www.youtube.com/watch?v=oHOiqFs_x8Y)

## TROUBLESHOOTING

### Can I use problem._visited?

Under Python convention, single underscore before a name (e.g., `_visited`) denotes private data, and hence it is good practice not to rely on such data. Check [this post](https://shahriar.svbtle.com/underscores-in-python) for example. Note that such private data can change without notice, it may not be available anymore, it may not be available under other interfaces, etc. So.... 

### I get "I get "_tkinter.TclError: no display name and no $DISPLAY environment variable" error when running in WSL or ssh

If you do not care about the graphics (e.g., for grading), then try using --textGraphics or even --quietTextGraphics. 

If you do want the display, then you need to do X forwarding when you connect via ssh. If you are in Linux/Unix this is easy, just do -X and -Y when you ssh (e.g., ssh -X -Y server).

If you use Windows, then you need an X server running and set your ssh client (e.g., Putty) with X forwarding. For example, check this page:

https://superuser.com/questions/119792/how-to-use-x11-forwarding-with-putty

Check this video for example: https://youtu.be/vwZXhTykSis

Said so, for development, **we strongly suggest** to clone your repo locally on your machine and work there (e.g., using PyCharm, Visual Code Studio).

### Cannot run Pacman due to problems with Tkinter: "ImportError: No module named Tkinter"

Install Tkinter:

```
$ conda install tk
```

Now it should be installed, so you should not get this error. But please try the code below, it should not trigger any error:

```
[e62439@foo~]$ scl enable rh-python36 bash
[e62439@foo~]$ python
Python 3.6.9 (default, Sep 11 2019, 16:40:19) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-16)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
>>> 
>>> 
[e62439@foo~]$ 
```

### How do I know the type of a variable in Python?

Check [this video](https://www.youtube.com/watch?v=iROZLaQGy4s&feature=youtu.be&t=1490) to know how to print the type of a variable in Python.

### Error module 'cgi' has no attribute 'escape' when running autograder.pt

You are probably not using Python 3.6 but a higher version.

## CAPTURE THE FLAG

### How to load my additional files beyond myTeam.py?

Your code will be copied into a directory called teams/<your_teamname>/ in the contest package. Remember, your code will be run by the following command:

```
python3 capture.py -r teams/<team1>/myTeam.py -b teams/<team2>/myTeam.py
```

This means that if you import from other files outside `myTeam.py` they will not be found unless you tell Python to look in your team dir. You can do so by having the following code on top of your `myTeam.py`:

```
import sys
sys.path.append(&rsquo;teams/<your team>/&rsquo;)
```

Now, the best way is to automatically obtain the folder where your file myTeam.py is located when playing the game, and then use that folder. You can do that using:

```
cd = os.path.dirname(os.path.abspath(__file__))
```

Now you can use variable cd itself, that is where your `myTeam.py` is located. Check [this post](https://stackoverflow.com/questions/9271464/what-does-the-file-variable-mean-do?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa) for more info and ideas.



### Do you provide library X (e.g., tensorflow)?

If it is a "standard" or very "common" library, most probably yes. Just send me an email and we will work out to make sure it is available in the cluster.

### Games go too fast! What should I do?

Use the `--delay-step` option. Note that option is NOT available in the standard UC-Berkeley distribution; I have added it.

### How do I replay a game?

You can play a game and use the `--record` option, you will be left with the game history to a file named by the time the game was played. You can replay these files using the `--replay` option and specifying the file to replay. You can use the `--replay-delay` to change the speed of the replay (see this is a feature in our distribution, not in the UC-Berkeley distribution). For example:

```
python capture.py --replay BBC_vs_It_depends_contest18Capture.replay --delay-step=0.1
```

All matches played in the preliminary contests are automatically recorded and the most recent ones can be viewed on the contest site. You are also able to download the history associated with each replay.


### How does one check if a given agent is currently scared? Is the only option to check the number of capsules in previous states?

```
GetAgentState(self.index).scaredTimer
```


###  It looks like the distance calculator is performing calculations in the background of our turns, can we replace it with our own version that does more?

The short answer is **no**, you cannot replace or change that code, but you can create your own version that you use instead. For the long answer, keep reading.

The premise to this question is a little off, the distancer is not doing any calculations on "your turns", it only calculates things _during the initialisation phase_. To be precise, that work is done during the `self.distancer.getMazeDistances()` call on line `105` of `captureAgents.py`, in the `registerInitialState` method of `CaptureAgent`. This will be called by all of your agents as you are subclassing `CaptureAgent`.
 
This shouldn't be an issue, as it will only take less than 1 second of your 15 second initialisation time (and even then only 1 second for the first agent). 
 After that, all the distances are cached, so you can get distances essentially for free in your code by calling `self.distancer.getDistance(p1, p2)`.




### How to call a planner (or another external tool)?

Suppose you have [`ff` planner](https://fai.cs.uni-saarland.de/hoffmann/ff.html) up and running in your machine. How do I call it from my Python code and extract the plan from its solution?

First, whatever external call is used, it **cannot be done** in another concurrent thread: your agent must _block and wait_ for the external code to finish. Remember that it is against the rules of the game to spawn concurrent threads. You can ran external commands (and wait for them to return) using [`os.system(command)`](https://docs.python.org/3/library/os.html#os.system) or the more preferred one [`subprocess.run(command)`](https://docs.python.org/3/library/subprocess.html#subprocess.run). We will explain the latter here, as it is now a more preferred approach as per Python doc.

**NOTE:** Please do not use `popen`. This is a non-blocking command which might leave things running on the server after your turn has finished, which will lead to your disqualification!

Suppose your code generates the specific `domain.pddl` and `problem.pddl` files that you want to use the planner on.  We are assuming these files are all in the same folder as `myTeam.py`, and the `ff` executable is available systemwide. We make sure that `ff` is available by running this command `sudo cp ff /usr/local/bin/.`, you can install it in your system as well with the same command This will let you run `ff` without the need to use the prefix `./`.

Here is a template using `subprocess.run()`:

```python
import os
import subprocess

def call_ff(domain, problem):
    cd = os.path.dirname(os.path.abspath(__file__))
    cmd = ["ff", "-o", f"{cd}/{domain}", "-f", f"{cd}/{problem}"] 
    # If you run ff in your local folder, change the first string "ff"-> f"{cd}/ff"

    result = subprocess.run(cmd, stdout=subprocess.PIPE, stderr=subprocess.PIPE, universal_newlines=True)

    return result.stdout.splitlines() if result.returncode == 0 else None
```

This will return a list of lines representing the output of `ff,` which can in turn be processed to extract the plan. For example:

```python
output = call_ff('domain.pddl', `problem.pddl')
plan = parse_ff_output(output)

if plan is not None:
    print(plan)
    if plan:
        print(extract_loc(plan[0]))
else:
    print('No plan!')
```


This is the function I use to extract the plan from `ff`'s output:

```python
def parse_ff_output(lines):
    plan = []
    for line in lines:
        search_action = re.search(r'\d: (.*)$', line)
        if search_action:
            plan.append(search_action.group(1))

        # Empty Plan
        if line.find("ff: goal can be simplified to TRUE.") != -1:
            return []
        # No Plan
        if line.find("ff: goal can be simplified to FALSE.") != -1:
            return None

    if len(plan) > 0:
        return plan
    else:
        print('should never have ocurred!')
        return None
```

If there is no plan, a null object will be returned. If a plan was found, a list of actions will be given; for example:

```
['GO P_1_9 P_1_10', 'GO P_1_10 P_1_11', 'GO P_1_11 P_1_12', 'GO P_1_12 P_1_13', 'GO P_1_13 P_1_14', 'GO P_1_14 P_2_14', 'GO P_2_14 P_3_14', 'GO P_3_14 P_3_13', 'GO P_3_13 P_3_12', 'GO P_3_12 P_3_11', 'GO P_3_11 P_3_10', 'GO P_3_10 P_4_10', 'GO P_4_10 P_4_9', 'GO P_4_9 P_4_8', 'GO P_4_8 P_4_7', 'GO P_4_7 P_5_7', 'GO P_5_7 P_5_6', 'GO P_5_6 P_5_5', 'GO P_5_5 P_6_5', 'GO P_6_5 P_7_5', 'GO P_7_5 P_7_6', 'GO P_7_6 P_8_6', 'GO P_8_6 P_9_6', 'GO P_9_6 P_10_6', 'GO P_10_6 P_11_6', 'GO P_11_6 P_12_6', 'GO P_12_6 P_13_6', 'GO P_13_6 P_13_7', 'GO P_13_7 P_14_7', 'GO P_14_7 P_15_7', 'GO P_15_7 P_16_7', 'GO P_16_7 P_17_7', 'GO P_17_7 P_17_6', 'GO P_17_6 P_17_7', 'GO P_17_7 P_18_7', 'GO P_18_7 P_19_7', 'GO P_19_7 P_19_8', 'GO P_19_8 P_19_9', 'GO P_19_9 P_20_9', 'GO P_20_9 P_21_9', 'GO P_21_9 P_22_9', 'GO P_22_9 P_23_9', 'GO P_23_9 P_24_9', 'GO P_24_9 P_24_10', 'GO P_24_10 P_25_10']
``` 

This corresponds to an output containing these lines:

```
ff: found legal plan as follows

step    0: GO P_1_9 P_1_10
        1: GO P_1_10 P_1_11
        2: GO P_1_11 P_1_12
        3: GO P_1_12 P_1_13
        4: GO P_1_13 P_1_14
        5: GO P_1_14 P_2_14
        6: GO P_2_14 P_3_14
        7: GO P_3_14 P_3_13
        8: GO P_3_13 P_3_12
        9: GO P_3_12 P_3_11
       10: GO P_3_11 P_3_10
...
```

Of course, all the above can be adapted to run other planners or even other external tools.

### Binary file for Metric-FF

You can [download](https://github.com/AI4EDUC/pacman-contest-cluster/blob/master/planners/ff) a compiled binary file that works for Linux. Once you download it, remember to run `chmod +x ff` to make sure the binary has executable rights. You can run `./ff` and you should see the command line options.


### What does it mean that we must use 2/3 AI techniques? Do they all need to be part of the final submission?

Your final submission should have >= 1 techniques, and your repo & experiments should have the code & analysis of all the techniques you tried. Which should be at least 2 or 3 depending on the size of the team.

It's expected that some techniques that you try will not work well, so you can just report about them in your analysis. In terms of final submission, if you want to perform well, most likely you'll end up mixing a few techniques. 
