# About commit-based release notes generation

## Overview
 
This script functions by cross-referencing Jira issues with the commits on a specified release branch. By comparing data from Jira to a branch comparison captured using `git`, the script automates the process of identifying which Jira tickets are referenced in commit history for a release.

This script ensures that the tickets included in the release notes draft actually have code commits for that release.


### Output

This script produces two outputs: a draft of the release notes (main output) and an exceptions file. Ranger evaluates tickets against specific criteria to organize them into the appropriate sections.

In addition to Ranger's general categorization logic, this script identifies **cherry-picked** issues (included in the release notes draft output) and **exceptions** (placed in an additional exceptions file). The following logic is used to sort these issues:

#### Release notes draft

| Section | Description / Criteria |
|---|---|
| Cherry-picked issues | Commits that appear in the release branch before the current release tag in the branch history. The script identifies the issue as a cherry-pick by using Git tags to compare commit IDs. |

#### Exceptions file

| Section | Description / Criteria 
|---|---|
| Empty or invalid Fix Version field | Jira tickets linked to a commit that have no or incorrect `fixVersion` field value.
| No Jira key in commit | Commits found in the release build cannot be linked to a Jira ticket, usually due to improper naming conventions.
| Jira tickets not in ADO release | Jira tickets that have the queried `fixVersion` value but are not linked to any commit in the release candidate.


## Running commit-based script

The script can be manually run to generate a Markdown draft of release notes for a given release candidate. You can run the script within the Ranger repository.

See [How to run commit-based release notes generation](how-to-run-script.md) for steps on running the script.