# How to run commit-based release notes generation

## Overview

This guide explains how to run Ranger's commit-based script to generate customer-facing release notes.

## Run Ranger script

### 1. Update local repository

Check that all remote branches from the remote repository exist in your local working copy.

To get all remote branches, open a terminal in your repository and use the `git fetch --all` command.

### 2. Run generator script 

Open a new terminal window and run the script from the Ranger repository. Provide a value for each of these arguments:

- `argument`: <redacted\>
- `argument`: <redacted\>
- `argument`: <redacted\>

!!! example "Command examples"
    === "General"
        
        Enter the following with your information:
        ```sh
        <redacted>
        ```

    === "<redacted\>"

        <redacted\>
        ```sh
        <redacted>
        ```

### 3. Process output

After running the script, a Markdown file named `release_notes_v<version>` should appear in your local repository. A file with exceptions, `exceptions_v<version>.md`, will also appear.

Open the release notes Markdown file in a text editor (e.g. Visual Studio Code) to format, revise, and polish the content according to release notes standards. 

Refer to [Additional resources](../guidance.md) for guides on post-processing and document cleanup.

## Troubleshooting

### Script error
If an error arises while running the script for the installed module, call the script file directly.
