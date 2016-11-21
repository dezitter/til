# List changed files of last commit

    git diff-tree --no-commit-id --name-only -r HEAD

# Count the number of commits affecting files

    git log --name-only --pretty=format: | sort | uniq -c | sort -nr
