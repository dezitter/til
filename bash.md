# Today I Learned - Bash

## Get the directory of the current running script

    $(dirname "$(readlink -f "$0")")
