---
layout: post
title: Search and replace in Linux
author: terry
categories: shell
excerpt_separator: <!--more-->
---

This post is about some commands to search and replace strings in Linux.
<!--more-->

## File names

```sh
# find file here
find . -name "*str*"

# find file in path
find ./path -name "*str*"

# find file exclude path
find . -name "*str*" \( -not -path "*exc_path/*" -path "*inc_path/*" \)
find . -name "*str*" \( -not -path "*exc_path_1/*" -not -path "*exc_path_2/*" -or -path "*inc_path_1/*" -or -path "*inc_path_2/*" \)

# find and rename file
for file in $( find . -name "*str_old*" )
do
    mv ${file} ${file/str_old/str_new}
done

# rename file using arguments
if [[ $1 ]] && [[ $2 ]]; then
    echo "Old string: ${1}"
    echo "New string: ${2}"
    echo "Start renaming..."
    for file in $( find . -name "*${1}*" )
    do
        mv ${file} ${file/${1}/${2}}
    done
    echo "Renaming finished."

# to find/replace for upper/lowercase, use
find . -name "*${1^^}*"
find . -name "*${1,,}*"
mv ${file} ${file/${1^^}/${2^^}}
mv ${file} ${file/${1,,}/${2,,}}
```

## File contents

```sh
# find string here
# -r recursively
# -l only show file name
grep -rl . "str"

# find string in path
# -n show line number
# -i ignore case
grep -rni './path/' -e 'pattern'

# find string include folder and exclude file/folder
grep -rl ./inc_path_1/ ./inc_path_2/ "str" --exclude={'*.log','*.rpt'} --exclude-dir={.svn,'report'}

# replace string
grep -rl . "str" | xargs sed -i "s/str_old/str_new/g"

# replace string using arguments
if [[ $1 ]] && [[ $2 ]]; then
    echo "Old string: ${1}"
    echo "New string: ${2}"
    echo "Start replacing..."
    grep -rl . ${1} | xargs sed -i "s/${1}/${2}/g"
    echo "Replacing finished."
```

## Reference

* [Find files in multiple folder names](https://unix.stackexchange.com/questions/60849/find-files-in-multiple-folder-names)
* [exclude directory from find command’s search](https://linuxconfig.org/how-to-explicitly-exclude-directory-from-find-command-s-search)
* [Bash Script; Replacing certain string in filename](https://stackoverflow.com/questions/34986746/bash-script-replacing-certain-string-in-filename-with-another-string-using-find)
* [how to rename multiple files by replacing string in file name?](https://unix.stackexchange.com/questions/175135/how-to-rename-multiple-files-by-replacing-string-in-file-name-this-string-conta)
* [How can I do a recursive find/replace of a string with awk or sed?](https://stackoverflow.com/questions/1583219/how-can-i-do-a-recursive-find-replace-of-a-string-with-awk-or-sed)
* [How do I find all files containing specific text on Linux?](https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux)
