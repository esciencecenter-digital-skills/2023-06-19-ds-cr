![](screenshots/iywjz8s.png)


# Day 3 - 2023-06-19-ds-cr

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

[TOC]


## 👮Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.

## 🎓 Certificate of attendance

If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, raise your hand in zoom. Click on the icon labeled "Reactions" in the toolbar on the bottom center of your screen,
then click the button 'Raise Hand ✋'. For urgent questions, just unmute and speak up!

You can also ask questions or type 'I need help' in the chat window and helpers will try to help you.
Please note it is not necessary to monitor the chat - the helpers will make sure that relevant questions are addressed in a plenary way.
(By the way, off-topic questions will still be answered in the chat)

## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2023-06-19-ds-cr/)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2023-06-19-ds-cr#setup)

## 👩‍🏫👩‍💻🎓 Instructors

Barbara Vreede, Dani Bodor

## 🧑‍🙋 Helpers

Candace Makeda Moore, Ewan Cahen

## 🗓️ Agenda
|  Time | Topic                  |
| -----:|:---------------------- |
|  9:00 | Welcome and icebreaker |
|  9:15 | Writing modular code   |
| 10:15 | Coffee break           |
| 10:30 | Writing modular code   |
| 11:00 | Documentation          |
| 11:30 | Coffee break           |
| 11:45 | Documentation          |
| 12:45 | Wrap-up                |
| 13:00 | END                    |

## If you do not have a repository yet:
1. Open a browser and navigate to github.com.
2. In the top right corner, click the "+" and then "New repository".
3. Give your repository the name `temperature_conversion`
4. Make it Public, and **don't let GitHub automatically add anything else.**
6. Run these lines of code in the command line. Be sure to replace `yourusername` by your own github username.
```bash
git clone git@github.com:DaniBodor/temperature_conversion.git
git remote set-url origin git@github.com:yourusername/temperature_conversion.git
git push -u origin main
```

## Check installations before today's workshop
```bash
conda --version
conda activate coderefinery
python -c "import sys; assert sys.version_info.major>=3"
pytest --version
sphinx-build --version
conda deactivate
```
[more details here](https://esciencecenter-digital-skills.github.io/2023-06-19-ds-cr/#setup)



## 🔧 Exercises


Look at the following (terrible) code.

Extract functions from it without changing its functionality.

What functions did you create?
What strategies did you use to identify them?

Share your answers in the collaborative document

```python=
def convert_temperature(temperature, unit):
    if unit == "F":
        # Convert Fahrenheit to Celsius
        celsius = (temperature - 32) * (5 / 9)
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = celsius + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                fahrenheit = (celsius * (9 / 5)) + 32
                if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                    return "Invalid temperature"
                else:
                    return celsius, kelvin
    elif unit == "C":
        # Convert Celsius to Fahrenheit
        fahrenheit = (temperature * (9 / 5)) + 32
        if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = temperature + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return fahrenheit, kelvin
    elif unit == "K":
        # Convert Kelvin to Celsius
        celsius = temperature - 273.15
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Fahrenheit
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, fahrenheit
    else:
        return "Invalid unit"

```

Awnsers/outcomes:

Main room:
```python=
def celsius_to_fahrenheit(celsius):
    return (celsius * (9 / 5)) + 32

def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * (5 / 9)

def celsius_to_kelvin(celsius):
    return celsius + 273.15

def kelvin_to_celsius(kelvin):
    return kelvin - 273.15

def check_temperature_validity(temperature, unit):
    abs_zero = {"C": -273.15,
                "F": -459.67,
                "K": 0}
    if temperature < abs_zero[unit]:
        return False
    return True

def check_unit_validity(unit):
    if not unit in ["C", "F", "K"]:
        return False
    return True

def convert_temperature(temperature, unit):
    if not check_unit_validity(unit):
        return "Invalid unit"
    if not check_temperature_validity(temperature, unit):
        return "Invalid temperature"
    if unit == "F":
        celsius = fahrenheit_to_celsius(temperature)
        kelvin = celsius_to_kelvin(celsius)
        return celsius, kelvin
    elif unit == "C":
        fahrenheit = celsius_to_fahrenheit(temperature)
        kelvin = celsius_to_kelvin(temperature)
        return fahrenheit, kelvin
    elif unit == "K":
        celsius = kelvin_to_celsius(temperature)
        fahrenheit = celsius_to_fahrenheit(celsius)
        return celsius, fahrenheit


if __name__ == "__main__":
    print(convert_temperature(0, "C"))
    print(convert_temperature(0, "F"))
    print(convert_temperature(0, "K"))
    print(convert_temperature(-500, "K"))
    print(convert_temperature(-500, "C"))
    print(convert_temperature(-500, "F"))
    print(convert_temperature(0, "X"))
```

Breakout rooms:
```python=
def fahrenheit__(temp_in_F):
    temperature = temp_in_F
    # Convert Fahrenheit to Celsius
    celsius = (temperature - 32) * (5 / 9)
    if celsius < -273.15:
            # Invalid temperature, below absolute zero
        return "Invalid temperature"
    else:
        # Convert Celsius to Kelvin
        kelvin = celsius + 273.15
        if kelvin < 0:
                # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, kelvin, fahrenheit

def celsius__(temp_in_celsius):
    temperature = temp_in_celsius
    # Convert Celsius to Fahrenheit
    fahrenheit = (temperature * (9 / 5)) + 32
    if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
        return "Invalid temperature"
    else:
        # Convert Celsius to Kelvin
        kelvin = temperature + 273.15
        if kelvin < 0:
                # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            return temperature, kelvin, fahrenheit

def kelvin__(temp_in_kelvin):
    temperature = temp_in_kelvin
    # Convert Kelvin to Celsius
    celsius = temperature - 273.15
    if celsius < -273.15:
        # Invalid temperature, below absolute zero
        return "Invalid temperature"
    else:
        # Convert Celsius to Fahrenheit
        fahrenheit = (celsius * (9 / 5)) + 32
        if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            return celsius, temperature, fahrenheit


def convert_temperature(temperature, unit):
    if unit == "F":
        celsius, kelvin, fahrenheit = fahrenheit__(temperature)
        return celsius, kelvin, fahrenheit
    elif unit == "C":
        celsius, kelvin, fahrenheit = celsius__(temperature)
        return celsius, kelvin, fahrenheit
    elif unit == "K":
        celsius, kelvin, fahrenheit = kelvin__(temperature)
        return celsius, kelvin, fahrenheit
    else:
        return "Invalid unit"



if __name__ == "__main__":
    result=convert_temperature(14, 'F')
    print("Results for 14 F:\t",result)
    result=convert_temperature(-10, 'C')
    print("Results for -10 C:\t",result)
    result=convert_temperature(263.15, 'K')
    print("Results for 263.15 K:\t",result)
```

```python=
def fahrenheit_to_celsius(fahrenheit):
    return (fahrenheit - 32) * (5 / 9)

def fahrenheit_to_kelvin(fahrenheit):
    celsius = fahrenheit_to_celsius(fahrenheit)
    return celsius_to_kelvin(celsius)

def celsius_to_kelvin(celsius):
    return celsius + 273.15

def celsius_to_fahrenheit(celsius):
    return (celsius * (9 / 5)) + 32

def kelvin_to_celsius(kelvin):
    return kelvin - 273.15

def kelvin_to_fahrenheit(kelvin):
    celsius = kelvin_to_celsius(kelvin)
    return celsius_to_fahrenheit(celsius)

def isTemperatureValid(temperature, unit):
    isValid = True
    if unit == "F":
        if temperature < -459.67:
            isValid = False
    elif unit == "C":
        if temperature < -273.15:
            isValid = False
    elif unit == "K":
        if temperature < 0:
            isValid = False
    else:
        print("Invalid unit")
        isValid = False
    return isValid

def isUnitValid(unit):
    if unit == "F" or unit == "C" or unit == "K":
        return True
    else:
        print("Invalid unit.")
        return False

def convert_temperature(temperature, unit):
    if isUnitValid(unit):
        if isTemperatureValid(temperature, unit):
            if unit == "F":
                print("C = " + str(fahrenheit_to_celsius(temperature)) + " K = " + str(fahrenheit_to_kelvin(temperature)))
                return fahrenheit_to_celsius(temperature), fahrenheit_to_kelvin(temperature)
            elif unit == "C":
                print("F = " + str(celsius_to_fahrenheit(temperature)) + " K = " + str(celsius_to_kelvin(temperature)))
                return celsius_to_fahrenheit(temperature), celsius_to_kelvin(temperature)
            elif unit == "K":
                print("C = " + str(kelvin_to_fahrenheit(temperature)) + " K = " + str(kelvin_to_celsius(temperature)))
                return kelvin_to_fahrenheit(temperature), kelvin_to_celsius(temperature)
        else:
            return "Invalid temperature"
    else:
        return "Invalid unit"


convert_temperature(20,"K")
```

```python=
def convert_temperature(temperature, unit):
    if unit == "F":
        # Convert Fahrenheit to Celsius
        celsius = (temperature - 32) * (5 / 9)
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = celsius + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                fahrenheit = (celsius * (9 / 5)) + 32
                if fahrenheit < -459.67:
                    # Invalid temperature, below absolute zero
                    return "Invalid temperature"
                else:
                    return celsius, kelvin
    elif unit == "C":
        # Convert Celsius to Fahrenheit
        fahrenheit = (temperature * (9 / 5)) + 32
        if fahrenheit < -459.67:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Kelvin
            kelvin = temperature + 273.15
            if kelvin < 0:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return fahrenheit, kelvin
    elif unit == "K":
        # Convert Kelvin to Celsius
        celsius = temperature - 273.15
        if celsius < -273.15:
            # Invalid temperature, below absolute zero
            return "Invalid temperature"
        else:
            # Convert Celsius to Fahrenheit
            fahrenheit = (celsius * (9 / 5)) + 32
            if fahrenheit < -459.67:
                # Invalid temperature, below absolute zero
                return "Invalid temperature"
            else:
                return celsius, fahrenheit
    else:
        return "Invalid unit"

def validate_temperature(temp, unit):
    if unit == 'C':
        if temp < -273.15:
            # Invalid temperature, below absolute zero
            return False
        else:
            return True
    elif unit == 'F':
        if temp < -459.67:
            # Invalid temperature, below absolute zero
            return False
        else:
            return True
    elif unit == 'K':
         if temp < 0:
            # Invalid temperature, below absolute zero
            return False
        else:
            return True
    else:
         return False

def celsius_to_fahrenheit(celsius):
    return celsius/5*9 + 32

def celsius_to_kelvin(celsius):
    return celsius + 273.15

def kelvin_to_fahrenheit(kelvin):
    celsius = kelvin - 273.15
    return celsius_to_fahrenheit(celsius)

def conv_temp(temp, unit):
    if validate_temperature(temp, unit):
        if unit == 'C':
            return celsius_to_fahrenheit(temp), celsius_to_kelvin(temp)
        if unit == 'F':
            #return
        if unit == 'K':
            #return
    else:
        return "Error"

if __name__ == "__main__":
    print('--- Output of the original function:')
    temp = convert_temperature(0, 'C')
    print('Celsius: ', temp)
    temp = convert_temperature(0, 'F')
    print('Fahrenheit: ', temp)
    temp = convert_temperature(0, 'K')
    print('Kelvin: ', temp)
    print('--- Output of the modular code:')
    temp = conv_temp(0, 'C')
    print('Celsius: ', temp)

```




## 🧠 Collaborative Notes

| Activity                        | Location          |
|:------------------------------- |:----------------- |
| Initialize Git repo             | local             |
| Create new repository on remote | GitHub            |
| Code review                     | GitHub            |
| Write new code                  | Local             |
| Write Markdown/README           | GitHub/Local      |
| Edit documentation              | Local             |
| Render documentation            | Local/CI (GitHub) |
| Write tests                     | local             |
| Run tests                       | Local/CI (GitHub) |
|                                 |                   |
|                                 |                   |





Colaborative notes:
-------------------
Welcome: Please check installation, and environment check at line 88.

The table above covers forthcoming material. Local means local IDE. Some of these things are based on your preference e.g. edits can be made in an IDE or on Github.


### Modular code:
-----------------

Today we discuss modular coding and documentation. We will generate documentation for our project.


Developing modular code: What is modularity? Buidling software from smaller pieces. We build individual parts of code that are self contained and independent, deals with one specific task. From these components we can build complex behaviour. Small untis usually work better than one complex big thing. What are the elemts? Functions. Classes. One scripts. Libraries, packages and programs. From all of these you build up modular code. This increases robustnesses, and ease of testing. This ensures we stay big-free, and keeps working as we add complexity, and more modules. It is more readable. It makes your code more reusable. It allows you to scale up. It allows for innovation because you can re-arrange modules to do different things. For truly short projects that you never need later, than it will not help. But if you have a project for a week even it is already useful to build it up in the right way, which includes being written in a modular fashion.

A good module performs a limkited, clearly definied task. It has a proper name and is readable. Readability is not the same as being as short as possible. By just using a function with a clear name, you make things more readable. A good module is 'pure', it does not have a state. This means it does not interact with the outside world except input and output. A stateful function interacts with outside world, and may lead to unforseen functions, and interact with other functions. One way to think of this is that a stateless function has no memory a stateful function interacts with outside world.

"Code smell" is a polite way to say readability stinks, but code will be read. If code is easily readable, it is understandable for you (later) and others.

You should not be repeating code. Anything that is repeated should be in a function instead. The naming of functions often goes by action. Functions should be named to make the action obvious. If you see nested code, e.g. loops within loops, that is often a hint the code can be rewritten in a better way.

We will cover tests later, but each module should have a test. Tests help you identify places code can be improved. If the test is very complex, it may be an indicator that code can be improved. If you can not test something at all, this may be an indication that the function probably can be re-written in a better way.

Questions:
When is it worth rewriting already working code? It depends, but often it is worthwhile. Think about robustness, data size. Rewriting also can make sure you have no mistakes.

How to describe the difference between module, function and a class? A function does something. A class creates an object which can have built in functions, which in Python are called methods. But a class doesn't have to do anything. A module is usually a file with possibly both.



Lessons learned from exercise:
Don't add functionality. The process of rewriting the same code is called refactoring. Refactoring made zombie code (code that does nothing or something unintended) apparent.
Different approaches: rewrite it from scratch versus slowly fixing from the inside. If you refactor slowly you can watch if output changes. You can do with fewer comments if your function names are readable and clear. There is more than one way to skin a cat, improvements can be different but all better. Version control is very helpful to understand what is going on based on your changes.


### Documentation:
------------------

Make sure documentation is appropriate for your project.

Documentation can be as good as it matches the needs of the user. What kinds of documentation do we have?
Readme files, documentation  via comments in the code,  API documentation (inside the code as docstrings), tutorials, data documentation, papers, lectures, youtube tutorials, and more. Documentation should fit the needs of the users.

Readme files: the first thing a user or collaborator sees. What should be there? Something covering parts or files of the project. Author and contact info. Installation guide. The overall purpose of the project and context. Citation, lisence, usage. Some things can be in a readme or in additional files, but readme is a good entry point e.g. changelog, license.

In code documentation: This helps for collaborators/co-developers. There can be many reasons to not write much in terms of comments.
Comments should never be used to replace version control.When you commit you should remove zombie code.
Docstrings are good to add, they have a sepcific syntax. They use three qoutes i.e. """. You can later type help for function, and it will pull teh docstring.

We will use sphinx in this lesson. It is independant of programming languages We will combine sphinx with our Python and Github. Your documentation depends on purpose and state of project.

An API is an application programming interface. API documentation can be done in docstrings.

Type/click along:
1. Go on github to a repo with a file with a function (you can use one we made)
2. Use github interface, add a .gitignore file (choose Python template from Github interface) to your repo (which should have a function on a file). Commit this to your repo, and should be on main branch. Now your repo contains two files (python script and gitignore).

Example function:


```python=
def celsius_to_fahrenheit(celsius):
    return celsius/5*9 + 32
```
3. On local repository (terminal): run `git pull`
4. Check that your IDE shows that you have pulled the new file.
5. You can check(in terminal) `ls -la` (flag a makes hidden files show, l lists)
6. Terminal: `git switch -c documentation`
7. Activate your environment i.e.terminal: `conda activate coderefinery`
8. (starting to setup documentation) from documentation branch with environment activated, we will use sphinx. We will now make a folder (from terminal):
    `mkdir docs`

9. Go into freshly made folder `cd docs`
10. From inside the docs folder run `sphinx-quickstart`
11. Awnser questions that appear. In square bracket you have default awnser. No is n. Project name: temperature conversion. Author name, project release -> 0.1.0, project language -> English
12. Examine what sphin created from inside VS code.
13. Delete unnecesary lines in documentation if you want. Add information to project by making files inside the docs folder (adding then to index.rst file). Name for file = project-intro.md (align to same line indentation)
Note: by adding specific files into the list we can populate documentation with additional files.
15. Before we can parse the markdown file, we need to check extensions. Go into conf.py file and check extensions to include `extensions =['myst_parser']` and `source_suffix = ['.rst', '.md']`
16. Push it up to Github
17. From the terminal run `sphinx-build . _build`
18. Run `ls` to check that there is now a _build folder
19. To rebuild when you made changes again, from terminal: `sphinx-build . _build`
20. Open and see
For different kinds of users (ways to open):
($ just signifies terminal)

Linux users type:

`$ xdg-open _build/index.html`
macOS users type:

`$ open _build/index.html`
Windows users type:

`$ start _build/index.html`
Others:

enter file:///home/user/doc-example/_build/index.html in your browser (adapting the path to your case).


Type-along in main room exercise:
make api.rst file:
API-documentation

On index you can add the file.

in extensions (conf.py) add sphinx.ext.autodoc

`sphinx-build . _build`

The documentation will be pushed so you can reference it online. Note indentations, and exact names matter.

Optional code-along:

(building documentation online)

1. Make a new file  (yaml file) from / at .github/workflows/documentation.yaml

2. Now we add `git add .github/workflows/documentation.yaml` then commit `git commit -m "your message"`
3. Push `git push` and check online in actions how it runs

4. If the error message tells you something is missing, push up what is missing. Action will be run by pushing again.

5. Deployment step: should only be done on a main.

Upcoming tommorow: tests as part of actions/workflow. When someone adds code, if your workflows are set up to, all the tests will run.

As soon as actions run, triggered by pull request sometimes, many things can run.

Pages build and deployment: This can be an action triggered.

The advantage of github actions: you don't deal with files produced by sphinx. The outcome is automated. In action, there is link to documentation website.




## 📚 Resources

- markdown syntax: https://www.markdownguide.org/basic-syntax/
- Documentation example repository: https://github.com/DaniBodor/temperature_conversion
