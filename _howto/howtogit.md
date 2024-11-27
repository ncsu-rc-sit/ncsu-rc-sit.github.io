---
layout: post
title: GitHub HowTos
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---

## Tips for GitHub

1. [Resolving Issues after Two-Factor Authentication](#Two-FactorIssues)
2. [Return to a Previous State in Git](#PreviousState)
3. [How to Uncommit](#Uncommit)
4. [How to Delete a Git Branch](#DeleteBranch)


<a name="Two-FactorIssues"></a>
### Resolving Issues after Two-Factor Authentication
* After enabling a two-factor authentication in my GitHub account, when
I run the Git `git push` command it throws the following error message:
```
$ git push
Username for 'https://github.com': your username
Password for 'https://Username@github.com':
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/username/repository.git/'
```
**Solution**
Creating a GitHub personal access token.
 1. In the upper-right corner of any page, click your profile photo, then click Settings.
 2. In the left sidebar, click Developer settings.
 3. In the left sidebar, click Personal access tokens.
 4. Click Generate new token.
 5. Give your token a descriptive name.
 6. Select the scopes, or permissions, you’d like to grant this token. To use your token to access repositories from the command line, select repo.
 7. Click Generate token.
 8. Copy the token to your clipboard. For security reasons, after you navigate off the page, you will not be able to see the token again.

 Using a token on the command line.

 Once we have a token, we can enter it instead of our password when performing  Git operations over HTTPS. Just inter your token after prompted a password and then watch the magic happen…

 ```
 $ git push origin remote_branch
 Username: your_username
 Password: your_token
 ```
<a name="PreviousState"></a>
### Return to a Previous State in Git
 [How to reset, revert, and return to previous states in Git](https://opensource.com/article/18/6/git-reset-revert-rebase-commands)

<a name="Uncommit"></a>
### How to Uncommit
[How to Uncommit Sensitive Files from Git](https://www.freecodecamp.org/news/how-to-uncommit-sensitive-files-from-git/)

<a name="DeleteBranch"></a>
### How to Delete a Git Branch
[How to Delete a Git Branch both Locally and Remotely](https://www.freecodecamp.org/news/how-to-delete-a-git-branch-both-locally-and-remotely/)