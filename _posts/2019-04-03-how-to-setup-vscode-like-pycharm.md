---
title: 'How to setup VSCode like PyCharm'
date: 2019-04-03
permalink: /posts/2019/04/how-to-setup-vscode-like-pycharm/
tags:
  - python
  - VSCode
  - PyCharm
---

I have been using PyCharm since writing python. It is a great tool that you don't even need to do much setting. I have multiple projects and customized package going one, so sometimes feels it is easy to switch back and force using some lightweight IDE. Well, I also have to admit that I like to try new things. This is how I started to explore VSCode. 

VSCode is a nice tool, but, you need to do your own settings and manage extensions. After searching around for a few hours, I ended up with the following extensions and settings:

My extensions:
---------------

1. Python
2. GitLens
3. Python Indent
4. Better Comments
5. autoDocstring
6. Sublime Material Theme
7. Markdown All in One

My settings.json:
---------------------
```json
{
    "workbench.colorTheme": "Sublime Material Theme - Dark",
    "files.autoSave": "afterDelay",
    "git.autofetch": true,
    "python.pythonPath": "C:\\xxx\\Anaconda3\\python.exe",
    "python.autoComplete.addBrackets": false,
    "python.autoComplete.showAdvancedMembers": true,
    "python.autoComplete.extraPaths": [
        "C:\\xxx\\Program\\Continuum\\anaconda3\\"
    ],
    "python.formatting.provider":"autopep8",
    "python.formatting.autopep8Args": [
        "--max-line-length", "120", "--experimental"
    ],
    "python.linting.enabled": false,
    "python.linting.pep8Enabled": true,
    "python.linting.pep8Args": [
        "--ignore=E301,E501,E225,E266,E265,E231,W293"
    ],
    "python.linting.pylintEnabled": true,
    "python.linting.pylintArgs": [
    "--enable=W0614"
    ],
    "autoDocstring.docstringFormat":"numpy",
    "files.autoSave":"off",
    "editor.cursorBlinking": "expand",
    "editor.renderWhitespace": "none",
    "editor.formatOnPaste": false,
    "editor.quickSuggestionsDelay": 10,
    "python.jediEnabled": false,
    "python.dataScience.sendSelectionToInteractiveWindow": true

"[markdown]": {
    "editor.quickSuggestions": true,
    "editor.wordBasedSuggestions": true
}
}
```
    
There are still some features lacking in VSCode, like make unused package grey, keep appropriate indent when copying a block of code, etc. But certainly VSCode gives a fresh feeling of writing code and very extendable.
