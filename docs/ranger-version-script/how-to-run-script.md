# How to run version-based release notes generation

## Overview

This guide explains how to run the version-based script to generate customer-facing release notes for any existing Jira project that has been [properly configured](../index.md#Jira-project-configuration).

## Run Ranger script

### 1. Confirm fix version name

Confirm the name of the fix version assigned to the current release candidate. This name should be consistent across all Jira tickets that will be included in the build.

!!! note

    Unlike the commit-based script, this script **does not** use previous versions to compare against the current build of a project. The script relies upon Jira tickets being assigned to the proper fix version.

### 2. Run generator script 

1. Open a new terminal window and `cd` into the Ranger directory.

2. Run `<redacted>`. Provide a value for each of these arguments:

- `argument`: <redacted\>
- `argument`: <redacted\>
- `argument`: <redacted\>

!!! example "Command examples"
    === "General"

        ```sh
        <redacted>
        ```
    === "<redacted\>"

        <redacted\>

        ```sh
        <redacted>
        ```

### 3. Process output

After running the script, a Markdown file should appear in the designated output location.

Open the Markdown file in a text editor (e.g. Visual Studio Code) to format, revise, and polish the content according to release notes standards. 

Refer to [Additional resources](../guidance.md) for guides on post-processing and document cleanup.

## Troubleshooting

### Wrong directory

Check that you are running the script from the correct directory.

### Dependencies not installed
If an error arises while attempting to run the script, check that you have the following dependencies installed:

- `jira`
- `pytz`
- `jira2markdown`

To install on Windows, use `python -m pip install jira pytz jira2markdown`.

To install on Mac, use `pip install jira pytz jira2markdown`