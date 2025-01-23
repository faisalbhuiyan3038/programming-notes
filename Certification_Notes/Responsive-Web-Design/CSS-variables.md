# CSS Variables

- Variable declarations begin with two dashes (-) and are given a name and a value like this: `--variable-name: value;`

- To use a variable, put the variable name in parentheses with var in front of them like this: `var(--variable-name)`.

- You should add a fallback value to a variable by putting it as the second value of where you use the variable like this: `var(--variable-name, fallback-value)`.

- That didn't work, because the variables you declared in .bb1 do not cascade to the .bb2 and .bb3 sibling elements. That's just how CSS works. Because of this, variables are often declared in the `:root` selector.

- This is the highest level selector in CSS; putting your variables there will make them usable everywhere.