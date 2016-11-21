# Get the directory of the current running script

    $(dirname "$(readlink -f "$0")")

# Arithmetic operations in BASH

Use the `bc` command:

    $ echo '2*2' |  bc
    4

and the *scale* special argument for floating point numbers:

    $ echo 'scale=2; 1/3' | bc
    .33

# Round numbers

Use the `printf` command:

    $ printf '%.2f' '0.3333333'
    0.33
