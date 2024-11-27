---
layout: post
title: Globus CLI
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---

The Globus Command Line Interface (CLI) is a Python-based application that need to be installed on the computer systems at both ends of your file transfer. Python version 2.7 or higher, and  the Python "pip" packages are required for the Globus CLI to be installed.

1. [Installation](#install)
2. [Login to Globus](#login)
3. [Using the interface](#interface)
4. [Endpoint Commands](#endpoint)
5. [File and Folder Commands](#files)
6. [Transfer Commands](#transfer)
7. [Task Commands](#task)

<a name="install"></a>
## Installation
The Globus website provides [CLI installation](https://docs.globus.org/cli/installation/) instructions. You will find instructions for installation on Windows, Mac, Linux and for updating or removing the CLI. The CLI will be added to your shell path and will automatically be available when you log in again. <br>

<a name="login"></a>
## Login to Globus
Before you can use the Globus CLI on a given computer, you must log in to Globus using the `globus login` command on the computer.
```yml
globus login
```

<img src="/assets/img/tutorialsimages/globuscli/1.png" >

It will redirect you to the browser and you need to login with your Globus credentials.

<img src="/assets/img/tutorialsimages/globuscli/2.png" >

After successful login you will see a success message in the terminal.

<img src="/assets/img/tutorialsimages/globuscli/3.png" >

You will now be able to issue Globus CLI commands on this computer. You can check your Globus login status at any time with the command `globus whoami`.
```yml
globus whoami
```

<a name="interface"></a>
## Globus CLI Commands
Each CLI command begins with `globus` and the command name, possibly followed by a sub-command name and/or flags and arguments. To see more information about a specific CLI command, pass the `--help` flag to the command.

You can see a list of all Globus CLI commands by issuing the command:

```yml
globus list-commands
```
There are over four dozen commands, many of which are in groups containing a parent command and multiple sub-commands.
If you need more information on any CLI command, Globus provides in-depth [here](https://docs.globus.org/cli/reference/).

<a name="endpoint"></a>
## Endpoint Commands

#### Endpoint IDs and Display Names
Most Globus CLI commands require you to specify one or more endpoints, so it is important to understand how Globus endpoints are identified. Each endpoint has a globally unique 32 character ID as well as a user-friendly and non-unique "display name". It is the ID that must be used in CLI commands.

#### Searching for Endpoints
To acquire the necessary endpoint IDs, users can search using the CLI's `endpoint search` command.
By default, the search will be performed on all endpoints (its scope is "all"). When searching over all endpoints you must add a quoted search term argument to the command. The CLI will search for the term(s) in various endpoint attributes, such as display name, description and organization, but will not attempt to match the owner name.

In this example, we search for all endpoints whose fields contain the text "uncg".

<img src="/assets/img/tutorialsimages/globuscli/4.png" >

Such searches can return up to 100 results; in this example, the search returns over two dozen.

By using the --filter-owner-id option we can limit the results to those where the owner matches an ID we provide.

```yml
globus endpointsearch --filter-owner-id mail_id@test.com "uncg"
```

Results can also be filtered by a scope using the `--filter-scope` option. Several scopes are available, such as endpoints that are owned by you (`my-endpoints`) and endpoints that have been shared with you (`shared-with-me`). Only one such filter can be specified. When filtering in this way you do not have to provide a search term.

<img src="/assets/img/tutorialsimages/globuscli/5.png" >

The [globus endpoint search](https://docs.globus.org/cli/reference/endpoint_search/) reference page contains more information about this command.

<a name="files"></a>
## Files and Folder Commands
For this we assign variable names to two of the endpoints we have.
We can use the below command for assigning variable names to endpoints.
```yml
$[variable name]=<endpoint_id>
```

<img src="/assets/img/tutorialsimages/globuscli/6.png" >

#### globus ls

CLI commands that work with endpoints specify file and folder locations as combinations of the endpoint ID and an optional colon, followed by a path:
```yml
globus ls [options] <endpoint>:<path>
```
<img src="/assets/img/tutorialsimages/globuscli/7.png" >

The `globus ls` command lists the contents of a specified endpoint and optional path. The command's options include `-a, --all` to include hidden files, `-l, --long` to produce long form output and `-r, --recursive` for recursively printing contents of folders.

#### globus mkdir

The `globus mkdir` command creates a new directory at the given endpoint/path combination:
```yml
globus mkdir <endpoint><:path>
```
The command returns 0 on success (as in the example below), 1 if there was an error (including if the path already exists), and 2 if the command was used improperly.

<img src="/assets/img/tutorialsimages/globuscli/8.png" >

#### globus rename

The `globus rename` command renames a file or directory at the first endpoint:path combination to have the name given by the second endpoint/path combination:
```yml
rename <endpoint><:old-path> <endpoint><:new-path>
```
The endpoint must be the same in the "from" and "to" locations, and the new path must not already exist. The command returns 0 on success, 1 if there was an error, and 2 if the command was used improperly.

<img src="/assets/img/tutorialsimages/globuscli/9.png" >

#### globus rm

The `globus rm` command removes a file or directory at the given endpoint/path combination:
```yml
globus rm [options] <endpoint><:path>
```
When the path refers to a directory, you must use the "-r" recursive option. The remove operation is performed asynchronously and its progress can be tracked using the task ID that is returned by the command. The command has numerous options, some of which relate to managing the task. The command returns 0 on success, 1 if there was an error, and 2 if the command was used improperly.

<mark>Note: One should know what he/she is going to delete, Once deleted files cannot be recoverd.</mark>

<a name="transfer"></a>
## Transfer Commands
The `globus transfer` command can take two forms: single target and batch.

#### Single Transfers

To transfer a single file or folder, use the form that takes two endpoint / path parameters and copies the contents of the location specified by the first parameter to the location specified by the second. The "to" file name need not match the name of the "from" file.
```yml
globus transfer [options] <from-endpoint>:<from-path> <to-endpoint>:<to-path>
```

<img src="/assets/img/tutorialsimages/globuscli/10.png" >

#### Batch Transfers

To perform a "batch" transfer of multiple targets, use the `--batch` option and specify only the source and target endpoints in the command.
```yml
globus transfer --batch [options] <from-endpoint> <to-endpoint>
```
Then, individual source files/folders are identified on separate lines of the `stdin` stream until an end-of-file (EOF) is entered. Each line is of the form:
```yml
[--recursive] <from-path> <to-path>
```
The `--recursive` option must be provided when the source path is a folder. Blank lines and lines beginning with a '#' (comments) are ignored.

<img src="/assets/img/tutorialsimages/globuscli/11.png" >

Batch transfer has been completed.

<img src="/assets/img/tutorialsimages/globuscli/12.png" >

<a name="task"></a>
## Task Commands
[Transfer commands](https://gcrnet.github.io/tutorials/globus_cli.html#transfer) are one example of Globus CLI tasks that run in the background. These tasks may result in an email being sent to the initiator upon the task completion, but in order to learn about the task status or interact with it in the shell where it was issued, a user must use one of the globus task commands.

#### globus task list

The `globus task list` command prints a list of the most recent Globus CLI tasks initiated by the current user, including their status. It has the form:
```yml
globus task list [options]
```

#### globus task show

The `globus task show` command displays information about a specific Globus CLI task such as a previously initiated transfer. It has the form:
```yml
globus task status [options] <taskid>
```

<img src="/assets/img/tutorialsimages/globuscli/13.png" >

#### globus task cancel

The `globus task cancel` command cancels an active Globus task such as a previously initiated transfer. This can be useful when the failure of one transfer command implies that a sequence of operations cannot proceed and other active transfers should be aborted. Note that when transfers are not succeeding as expected they are repeatedly retried until successful. For this reason, when there is no longer an expectation that a transfer will succeed, it should be canceled. The command can have one of the following forms:
```yml
globus task cancel [options] <taskid>
```
```yml
globus task cancel --all [options]
```
The command must either include a single taskid argument or the --all option, which will cause all active tasks to be canceled. Both tasks that are pending and currently executing will be canceled.

<img src="/assets/img/tutorialsimages/globuscli/14.png" >
