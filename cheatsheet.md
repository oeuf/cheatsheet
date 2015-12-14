# Setting up SSH keys
```
$ ssh-keygen -t rsa -b 4096 -C "blah@blah.com"
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
```

# Github
* [Cheatsheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
* [Github Markdown reference](https://help.github.com/articles/markdown-basics/)

# Latex installation
* Download BasicTex from [here](https://www.tug.org/mactex/) and follow installation instructions.
* Download and install latest release of the Tex Live Utility from [here](https://github.com/amaxwell/tlutility/releases).
* Use the Tex Live utility to install [latexmk](http://users.phys.psu.edu/~collins/software/latexmk-jcc/)
* (Optional): Install TexShop from [here](http://pages.uoregon.edu/koch/texshop/obtaining.html)
* Build PDF using `latexmk blah.tex` or `latexmk -xelatex blah.tex` (the latter if using `microtype` or `fontspec` packages)
# Probability
* [Chen and Blitzstein's cheatsheet](https://github.com/wzchen/probability_cheatsheet/raw/master/probability_cheatsheet.pdf). Github repo for the PDF found [here](https://github.com/wzchen/probability_cheatsheet).

