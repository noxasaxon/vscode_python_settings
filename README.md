# vscode_python_settings
setting up vscode for (opinionated) optimal python development

## Installing python dependencies for the IDE

These will need to be installed in the python environment that vscode will use (you can view/change environments in vscode by clicking it in the bottom bar, or with `CMD + Shift + P` and typing `interpreter`.

```shell
pip install black
pip install flake8
pip install flake8-bugbear
```

## Installing VSCode extensions for python analysis

Pastee the following into your `Extensions` search bar in vscode and install these official Microsoft extensions

- [ ] `ms-python.python`
- [ ] `ms-python.vscode-pylance`

## Setting up your VSCode settings

Open your global `settings.json` by **_either_**:
- type `CMD + Shift + P` to open search, then find `Preferences: Open Settings (JSON)` 
- type `CMD + ,` to open the Settings GUI, then click the icon in top right called `open settings (JSON)`

Once in the global VSCode json settings, paste the following:

```json
    "editor.formatOnSave": true,
    "python.formatting.provider": "black",
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Enabled": true,
    "python.linting.flake8Args": [
        "--select=B,C,E,F,W,T4,B9",
        "--ignore=E203,E266,E265,E501,E401,W503,B950"
    ],
    "python.languageServer": "Pylance",
    "python.analysis.extraPaths": [
        "./common_files"
    ],
    "python.analysis.diagnosticMode": "workspace",
    "python.analysis.typeCheckingMode": "basic",
```

- If you want more stringent type checking, you can change `python.analysis.typeCheckingMode` from `basic` to `strict`
- the `"python.analysis.extraPaths"` setting allows VSCode to find functions in the `./common_files` folder used for SOCless integrations

## Additional (optional) Extensions to aid development accuracy and speed

- `usernamehw.errorlens` : shows error messages without having to highlight the red squiggly line
- `coenraads.bracket-pair-colorizer-2` : uses a different color for each set of nested brackets, curly braces, parentheses, etc
- `oderwat.indent-rainbow` : uses a different color for each set of indentation (useful for python whitespace) 
- `aaron-bond.better-comments` : Will highlight usages of `NOTE:` `FIX:` `TODO:` in your code comments
- `zhuangtongfa.material-theme` : Not all themes make use of ALL the syntax features exposed by PyLance, this is one of the best that makes use of all its features
