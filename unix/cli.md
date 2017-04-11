# Resize an image from command line

    convert -resize 50% original.png resized.jpg

`convert` is part of the ImageMagick package.

# List files and exclude directories

    find . -name '*.js' ! -path '*/vendor/*'

# Search and replace a pattern in all matching files

    git grep -l 'pattern' | xargs sed -i 's/pattern/relacement/g'

# Merge/concat/paste lines separated by a space.

    paste -s -d':'

Useful when the output of one command in on multiple lines, and a single line is wanted.

# Get the last field when using cut

(Without having to count its index)

    grep 'pattern' | rev | cut -d'/' -f 1 | rev

Uses the `rev` command to reverse all characters, select the first field,
then reverse again.

# Repeat the previous command

    $!!

# Repeat the previous command and substitute a string

To repeat the previous command but replace the *first occurence* of "foo" with "bar":

    $ !!:s/foo/bar

For a global substitution:

    $ !!:gs/foo/bar

See **Event designators** in `man bash`.

# Move files without overwritting existing names

`mv` supports a **--backup** option to rename the source file if a destination
of the same name exists.

Example with the tree below:

    src/
    |__ bar
    |__ foo

    dest/
    |__ foo

Running:

```bash
# use 'numbered' backup
$ mv --backup=t src/* dest/
```

results in:

    src/

    dest/
    |__ bar
    |__ foo
    |__ foo.~1~ # original dest/foo

# Re-run a command and subtitute a pattern

    !!:s/foo/bar
