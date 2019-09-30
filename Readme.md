# Using Git hooks to enforce branch naming policy!

**1-STEP**
Run command **`$ git init`**

**2-STEP**
Run command **` $ git config core.hooksPath .githooks `**

Create folder  **.githooks** in project root folder  **`$ mkdir .githooks`**
In folder  **.githooks** create file **pre-commit** and run command **`$ chmod +x pre-commit`**
Code **pre-commit** git hooks
```bash
#!/usr/bin/env bash
LC_ALL=C

local_branch="$(git rev-parse --abbrev-ref HEAD)"

#valid_branch_regex="^(feature|bugfix|hotfix|bug)\/[A-Z0-9-]*\/[a-zA-Z._-]+$"
valid_branch_regex="^(feature|bugfix|hotfix|bug)\/[CLP0-9-]*\/[a-zA-Z._-]+$" CLP it`s your project from jira

message="There is something wrong with your branch name. Branch names in this project must adhere to this contract: $valid_branch_regex. Your commit will be rejected. You should rename your branch to a valid name and try again."

if [[ ! $local_branch =~ $valid_branch_regex ]]
then
    echo "$message"
    exit 1
fi

exit 0 ```
