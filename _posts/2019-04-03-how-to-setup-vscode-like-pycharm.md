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
2. Sublime Material Theme
3. autoDocstring
   Used to highlight #TODO
4. Markdown All in One

My settings.json:
---------------------
```json
{
    "workbench.colorTheme": "Sublime Material Theme - Dark",
    "files.autoSave": "afterDelay",
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
    "git.autofetch": true,
    "python.autoComplete.addBrackets": true,
    "python.autoComplete.showAdvancedMembers": true,
    "python.formatting.provider":"autopep8",
    "python.formatting.autopep8Args": [
        "--max-line-length", "120", "--experimental"
    ],
    "python.linting.pep8Enabled": false,
    "python.linting.pep8Args": [
        "--ignore=E301,E501,E266"
    ],
    "python.linting.pylintEnabled": false,
    "python.linting.pylintArgs": [
    "--enable=W0614"
    ],
    "autoDocstring.docstringFormat":"numpy",
    "editor.cursorBlinking": "expand",
    "editor.renderWhitespace": "none",
    "editor.formatOnSaveTimeout": 1500,
    "editor.formatOnPaste": true,
    "editor.multiCursorModifier": "ctrlCmd",
    "python.pythonPath": "C:\\Users\\joyin\\Anaconda3\\python.exe",
    "python.dataScience.sendSelectionToInteractiveWindow": true,
"[markdown]": {
    "editor.quickSuggestions": true,
    "editor.wordBasedSuggestions": true
}
}
```
    
There are still some features lacking in VSCode, like make unused package grey, keep appropriate indent when copying a block of code, etc. But certainly VSCode gives a fresh feeling of writing code and very extendable.
