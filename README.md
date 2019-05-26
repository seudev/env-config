# Env Config

## What is it?

A shell scripts set for config the work environment.

## Using Env Config

Add execution permision to the desire script using `chmod +x script-file-name`.

Optionaly you can add the script to the path variable, to make the script available in anywhere.
An easy mode to do it is puting the script in some of this folders: `/usr/local/bin/`, `$HOME/bin` or `$HOME/.local/bin`.

*Note: The inline parameters has priority over the environment variables.*

### Git

### set-git-config

Sets the global Git config. The configuration can be defined using environment variable or inline parameters

* Define the environment variables and simply execute the script: `set-git-config`.
* Execute the script passing the parameters inline, by example: `set-git-config "arg1" "arg2" "arg3" ...`.

| **Git config**    | **Environment Variable** | **Inline Position** | **Default Value**   |
|-------------------|--------------------------|---------------------|---------------------|
| user.email        | GIT_USER_EMAIL           | 1                   |                     |
| user.name         | GIT_USER_NAME            | 2                   |                     |
| push.default      | GIT_PUSH_DEFAULT         | 3                   | simple              |
| credential.helper | GIT_CREDENTIAL_HELPER    | 4                   | cache --timeout 300 |

### get-git-target-branch

A simple script that returns target branch of the `CURRENT_BRANCH` environment variable or of the parameter 1.

* Define the environment variables and simply execute the script: `get-git-target-branch`.
* Execute the script passing the inline parameters, by example: `get-git-target-branch "branch-name"`.

| **Input**                  | **Environment Variable** | **Inline Position** | **Default Value**    |
|----------------------------|--------------------------|---------------------|----------------------|
| **current branch**         | CURRENT_BRANCH           | 1                   |                      |
| **develop branch pattern** | DEVELOP_BRANCH           | 2                   | develop              |
| **feature branch pattern** | FEATURE_BRANCH_PATTERN   | 3                   | feature*             |
| **release branch pattern** | RELEASE_BRANCH_PATTERN   | 4                   | release*             |
| **hotfix branch pattern**  | HOTFIX_BRANCH_PATTERN    | 5                   | hotfix*              |
| **production pranch**      | PRODUCTION_BRANCH        | 6                   | master               |

This script is based in feature branch workflow. 

* If the current branch match with the feature branch pattern then returns "develop".
* If the current branch match with the develop, release or hotfix pattern then returns "master".
* otherwise returns the current branch name.

### SSH

### add-ssh-key

Adds and test a given ssh key.

* Define the environment variables and simply execute the script: `add-ssh-key`.
* Execute the script passing the inline parameters, by example: `add-ssh-key "arg1" "arg2" "arg3" ...`.

| **Input**       | **Environment Variable** | **Inline Position** | **Default Value**    |
|-----------------|--------------------------|---------------------|----------------------|
| **public key**  | SSH_PUBLIC_KEY           | 1                   |                      |
| **private key** | SSH_PRIVATE_KEY          | 2                   |                      |
| **host**        | SSH_HOST                 | 3                   |                      |
| **user**        | SSH_USER                 | 4                   |                      |
| **ssh id**      | SSH_ID                   | 5                   | $HOME/.ssh/id_rsa    |
| **config file** | SSH_CONFIG_FILE          | 6                   | $HOME/.ssh/config    |

*Note: If the user is not defined the system user will be used in the test*

## Licensing

**seudev/env-config** is provided and distributed under the [Apache Software License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

Refer to *LICENSE* for more information.
