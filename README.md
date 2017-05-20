# optparse
<h3>Bash Options Parser</h3>

Attribution with conditions & description of options and flags

<h4>Requirements:</h4>
  - BAsh interpreter

<h4>No installation:</h4>
  - Let the source file be in the PATH environment variable

<h4>Usage:</h4>

Here is a quick script <i>opt_demo</i> to introduce <b>optparse</b>:
<pre>
#!/bin/bash

# Mandatory: opts & flags array
opts=(
"n:'number between 5 and 10' [[ n -lt 10 && n -gt 5 ]]"
"x:'low-case string' [[ x =~ ^[a-z]+$ ]]"
)

# -h flag is by default
flags=("A:Affect all options as variables")

# Optional description
function about() {
    echo "Demonstration script"
}

# Let the script do the job
source optparse

# If you want to affect options as variables -A:
[[ "${OPTS[A]}" =~ true ]] && affect_opt
echo "n="$n

# TODO CODE HERE :)

exit 0
</pre>

Some outputs:
<pre>
$ opt_demo -h

Usage: ./opt_demo [options] [flags]

Demonstration script

Options:
        -n               'number between 5 and 10' [[ n -lt 10 && n -gt 5 ]]
        -x               'low-case string' [[ x =~ ^[a-z]+$ ]]   
Flags:
        -A    false      Affect all options as variables     
        -h    true
</pre>

Given conditions are tested at first:
<pre>
$ opt_demo -x coucou -n 3
Condition failed: [[ 3 -lt 10 && 3 -gt 5 ]]
</pre>

No output, arguments are good to be used:
<pre>
$ opt_demo -x coucou -n 6
</pre>

We can affect all options as variables using -A:
<pre>
$ opt_demo -n 6 -A
n=6
</pre>

Description part is a string without empty spaces (the trick to have spaces on the screen is to use AltGr+SpaceBar when you type it).
