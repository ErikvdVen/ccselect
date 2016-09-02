# CSSComb on selected rows
I don't always want to run `csscomb` on a complete file, especially not when working in a team of developers working on the same files, in which case `csscomb` can results in a lot of file changes every single commit. This was a reason for me to create a script which is able to run `csscomb` only on a particular selection.

# how it works
```
./ccselect.py --start <start rownumber> --end <end rownumber> --file /path/to/file.scss
```
Note: `.css` files work as well obviously.

# PHPStorm
This is my setup for PHPStorm, so I only have to select the particular code and hit `CTRL + SHIFT + C` to run `csscomb` on that selection.
![External Tools in PHPStorm](/../screenshots/phpstorm_external_tools.png?raw=true "External Tools in PHPStorm")
