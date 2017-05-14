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

# opts array declaration
# "option:option_description [[ option_condition ]]"
opts=(
"n:a number between 5 and 10 [[ n -lt 10 && n -gt 5 ]]"
"x:[[ x =~ ^[a-z]+$ ]]"
)

# flags declaration (-h is automatic, don't bother)
flags=("v")

source optparse
</pre>

Some outputs:
<pre>
$ opt_demo -h

Usage: /home/duke/bin/opt_demo [options] [flags]

Options:
        -n               a number between 5 and 10 [[ n -lt 10 && n -gt 5 ]]
        -x               [[ x =~ ^[a-z]+$ ]]                     
Flags:
        -h    true                                               
        -v    false 
</pre>

No output, arguments are good to be used:
<pre>
$ opt_demo -x coucou -n 6
</pre>

Help message could be useful:
<pre>
$ opt_demo -x coucou -n 6 -h

Usage: /home/duke/bin/opt_demo [options] [flags]

Options:
        -n    6          a number between 5 and 10 [[ n -lt 10 && n -gt 5 ]]
        -x    coucou     [[ x =~ ^[a-z]+$ ]]                     
Flags:
        -h    true                                               
        -v    false 
</pre>

Description part is a string without empty spaces (the trick to have spaces on the screen is to use AltGr+SpaceBar when you type it).
