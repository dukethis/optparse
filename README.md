# optparse
<h3>Bash Options Parser</h3>

Attribution with conditions & description of options and flags

Requirements:
  - BAsh interpreter

No installation:
  - Let the source file be in the PATH environment variable

Usage:

Here is a quick script <i>opt_demo</i> to introduce <b>optparse</b>:
<pre>
#!/bin/bash

# opts array declaration
# "option:option_description [[ option_condition ]]"
opts=(
"n:a number between 5 and 10 [[ n -lt 10 && n -gt 5 ]]"
"x:[[ x =~ ^[a-z]+$ ]]"
)

flags=("v")

source optparse
</pre>
