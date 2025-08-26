# About version-based release notes generation

## Overview

This script generates release notes for any given release version by pulling all Jira tickets whose `fixVersion` fields match the version specified in the script input.

The draft will only include Jira issues that contain the specified `fixVersion` value, regardless of whether or not there was an associated code commit.

### Output

This script produces one output: a Markdown draft of release notes. Ranger's [categorization logic](../index.md#entry-categorization-logic) evaluates tickets against specific criteria to organize them into the appropriate sections.

!!! note
    This script omits cherry-pick logic and does not produce an exceptions file.

## Running version-based script for Jira projects
Given a specific fix version used in Jira, this script can be used to generate a Markdown draft of release notes from Jira projects. You can manually run the script within the Ranger repository.

See [How to run version-based release notes generation](how-to-run-script.md) for steps on running the script.

