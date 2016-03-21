# Miscellaneous links and references

## Setting up SSH keys
```
$ ssh-keygen -t rsa -b 4096 -C "blah@blah.com"
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
```

## Convert plist files to xml
`plutil -convert xml1 -o blah.xml blah.plist`


## Find all files of particular types within current directory and gzip then
e.g, for all json and csv files:
`find . -type f -iname '*.json' -o -iname '*.csv' -exec gzip "{}" \;`

## Github
* [Cheatsheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
* [Github Markdown reference](https://help.github.com/articles/markdown-basics/)
* [More github markdown](https://guides.github.com/features/mastering-markdown/)
* [Git-scm](https://git-scm.com/)

## Latex installation
* Download BasicTex from [here](https://www.tug.org/mactex/) and follow installation instructions.
* Download and install latest release of the Tex Live Utility from [here](https://github.com/amaxwell/tlutility/releases).
* Use the Tex Live utility to install [latexmk](http://users.phys.psu.edu/~collins/software/latexmk-jcc/)
* (Optional): Install TexShop from [here](http://pages.uoregon.edu/koch/texshop/obtaining.html)
* Build PDF using `latexmk blah.tex` or `latexmk -xelatex blah.tex` (the latter if using `microtype` or `fontspec` packages)

## Probability
* [Chen and Blitzstein's cheatsheet](https://github.com/wzchen/probability_cheatsheet/raw/master/probability_cheatsheet.pdf). Github repo for the PDF found [here](https://github.com/wzchen/probability_cheatsheet).
* [common probabily distributtions](https://blog.cloudera.com/blog/2015/12/common-probability-distributions-the-data-scientists-crib-sheet/)

## Scala
* [Scala school](https://twitter.github.io/scala_school/)
* [SBT](http://www.scala-sbt.org/release/tutorial/)

## ML, etc
* [Michael Nielsen book](http://neuralnetworksanddeeplearning.com/)
* [Deep learning book](https://goodfeli.github.io/dlbook/)

## Start postgres on localhost
```
$ postgres -D /usr/local/var/postgres > logfile 2>&1
```

## Setting up PostgreSQL
* Install via homebrew `$ brew install postgresql`
* Make a postgres directory `$ sudo mkdir -p /usr/local/var/postgres`
* Change permissions for current user `$ sudo chown ${USER}:admin /usr/local/var/postgres/`
* Start the server `pg_ctl -D /usr/local/var/postgres/data -l /usr/local/var/postgres/data/server.log start`
* (optional) Make postgres launch on startup `cp /usr/local/Cellar/postgresql/<VERSION NUMBER>/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/`

## Fixing obnoxious vim/zsh errors (e.g._ _arguments:451: _vim_files: function definition file not found_)
* Remove all .zcompdump files
`rm -f ~/.zcompdump`
* Restart shell
`exec zsh`


## Get n-degree connectedness in postgres
```
WITH RECURSIVE transitive_closure AS
  (SELECT a, b, 1 AS degree, a || '.' || b || '.' AS path
	FROM edges

	UNION ALL
	SELECT tc.a, e.b, tc.degree + 1, tc.path || e.b || '.' AS path
	FROM edges AS e
	JOIN transitive_closure AS tc ON e.a = tc.b
	WHERE tc.path NOT LIKE '%' || e.b || '.%'
)

SELECT a, b, degree, path
FROM transitive_closure
WHERE 
	degree = 2 --change or remove altogether for other degrees
	AND a || b NOT IN (SELECT a || b FROM edges)
ORDER BY a, b, degree;
```
