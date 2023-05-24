---
date: "2022-04-21 07.27"
alias: ['fuck bash', 'bash is confusing']
---

#  Bash

## Cheatsheet

### Get exit code of previous command
```bash
git rev-parse --verify "doesn't exist";
echo $? # 128
```

```bash
git rev-parse --verify "exists";
echo $? # 0
```

Want to test the result of the exit code?

```bash
command;
[ $? -eq 0 ] && commandIfTrue;
```

###  Hide output of command
```bash
command &>/dev/null     # Both stderr and stdout will be hidden
command >/dev/null 2>&1 # Same as above
command >/dev/null      # Only stdout will be hidden
```

### What do square brackets mean

The single `[` is equivalent to the "test" command in the shell. It is used to evaluate a condition.

When using an `if` statement, the if part checks whether 0 or 1, the test command evaluates a condition. e.g. `[ $? -eq 0 ]` returns 1 if `$?` is equal to `0`.

Double `[[` instead sets an exit code and the `if` statement acts accordingly. (It seems to just be better.)

Round brackets / Paranthesis `(`  execute a command in a subshell. Changes to the subshell remain in the subshell.