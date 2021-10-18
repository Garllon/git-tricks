# git-tricks
Some git work commands. Keep in mind if you have any question what things are doing you can run 
`man git` for the manual page of `git` and for example `man git-commit` for the manual page of `git commit` command.

## Add changes to the last commit

If you like to add something to the last commit then you can run:
```shell
git add <your changes files>
```

then you can add it with the following command to the last commit:
```shell
git commit --amend --no-edit
```

The `--amend` means that we append the last commit.

The `--no-edit` means that we don't want edit the commit message again.

## Add changes to an already existing commit, which is not the last one

1. Use `git stash` to store the changes you want to add.
2. Use `git rebase -i HEAD~10` (or however many commits back you want to see).
3. Mark the commit for edit by changing the word `pick` at the start of the line into `edit`. Don't delete the other lines as that would delete the commits.
4. Save the rebase file, and git will drop back to the shell and wait for you to fix that commit.
5. Pop the stash by using git stash pop
6. Add your file with `git add <file>`.
7. Amend the commit with `git commit --amend --no-edit`.
8. Do a `git rebase --continue` which will rewrite the rest of your commits against the new one.
9. Repeat from step 2 onwards if you have marked more than one commit for edit.
