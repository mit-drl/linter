# linter

This repo contains a (C++, python (experimental)) linter and auto formatter package that can be included into your repository as a submodule. It provides the following git hooks:
 * **General**
   * Prevent commits to master.
 * **C++** files:
   * **clang-format** Formats your code based on your .clang-format preferences.
   * **cpplint** Checks your C++ code for style errors and warnings.
   
 * **Python** files:

      * **yapf** Formats your python code.
      * **pylint** Checks your Python code for style errors and warnings.
     

## Dependencies

 * **yapf**
   * Ubuntu / macOS: `pip install yapf`
 * **clang-format**
   * Ubuntu: `sudo apt install clang-format-3.8`
   * macOS: 
     ```
     brew install clang-format
     ln -s /usr/local/share/clang/clang-format-diff.py /usr/local/bin/clang-format-diff-3.8
     ```


## Installation

```bash
cd $YOUR_REPO
git submodule add git@github.com:ethz-asl/linter.git
./linter/init-git-hooks.py
```

You can also add the linter submodule in a subfolder of your repo, e.g.:
```bash
mkdir $YOUR_REPO/dev_tools
git submodule add git@github.com:ethz-asl/linter.git dev_tools/linter
./dev_tools/linter/init-git-hooks.py
```

Define the project-specific C++ format by adding a file `.clang-format` to your projects root folder. Example:

```
---
Language: Cpp
BasedOnStyle: Google
DerivePointerAlignment: false
PointerAlignment: Left
ColumnLimit: 80
AllowShortFunctionsOnASingleLine: Empty
AllowShortIfStatementsOnASingleLine: false
AllowShortLoopsOnASingleLine: false
AlignAfterOpenBracket: AlwaysBreak
IncludeCategories:
  - Regex:           '^<.*'
    Priority:        1
  - Regex:           '.*'
    Priority:        2
...
```

#### ASCII-Art Sources

 * [www.retrojunkie.com (accessed through web.archive.org)](https://web.archive.org/web/20150831003349/http://www.retrojunkie.com:80/asciiart/)
