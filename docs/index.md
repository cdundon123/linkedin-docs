# Ranger overview

Welcome to Ranger!

Ranger (Release Notes Generator) is an inner source Python tool that streamlines release note creation for Jira projects. This automation saves time, enhances accuracy, and enables clear communication with business partners. 

### Jira project configuration

To use the Ranger script, your project must meet the following requirements:

- Your project must be fully managed in Jira and use standard Jira configuration/workflows.
- All code changes should be associated to either a **Bug** or **Story** with a Release Notes Content field.
- You should follow standard naming conventions for branches and pull requests. Ranger parses PR titles to identify which Jira tickets it should query.

### Script logic

Ranger includes two scripts with distinct behaviors for generating release notes: 

- A [commit-based script](ranger-commit-script/index.md).
- A [version-based script](ranger-version-script/index.md).

## Generated output

For any given release candidate, Ranger organizes pull requests and their release notes content into a standardized format. Running the Ranger script generates a Markdown (.md) draft that adheres to a standard template.

The generated release notes provide a preview of what is included in the build; however, the content in the generated file is raw and may contain gaps or errors depending on the quality of the information provided in Jira.

Ranger populates the release notes with an entry for every Jira issue associated to a PR that is discovered in the build, so you may see entries for tickets that are still in progress, or for tickets that were partially delivered in the previous release candidate. These entries should be manually reviewed and revised for clarity by a subject matter expert.

### Entry categorization logic

For each release notes draft, Ranger evaluates Jira issues against specific criteria to organize them into appropriate sections. The following logic is used:

| Section | Description / Criteria |
|---|---|
| New features | Jira issues where the work type is `New Feature` and issue type is **not** `Bug`. |
| General enhancements   | Jira issues where the work type is **not** `New Feature` and issue type is **not** `Bug`. |
| Fixes | Jira issues where the issue type is `Bug`. |
| All updates  | All issues, grouped by project key (see note) and shown in a table. |

!!! note

    Issues are organized in the `## All updates` section using the Jira key in their PR title. Proper branch and PR naming conventions can be viewed in Confluence

### Additional logic (commit-based)

The **commit-based** release notes script also identifies cherry-picks (included in the release notes Markdown file) and exceptions (placed in a separate file). 

## Ranger installation

### Prerequisites

- **Python**: You have the latest version of Python installed. You can download Python here: [Welcome to Python.org](https://www.python.org/). Mac users can use homebrew to install Python.

- **Jira Personal Access Token**: To generate a Jira PAT, go to [Security - API Tokens](https://id.atlassian.com/manage-profile/security/api-tokens).
- **Text editor**: You have a text editor that can preview and edit Markdown files installed. 
  
  !!! tip
      Install [Visual Studio Code (VSC)](https://code.visualstudio.com/). VSC is free and offers built-in support for [previewing Markdown files](https://code.visualstudio.com/docs/languages/markdown#_markdown-preview).

### 1. Clone repository

Clone the Ranger repository to your device under the `C:/src` directory:

```sh
git clone <redacted>
```

### 2. Install release notes package

Depending on your workstation configurations, you may encounter issues when running the release notes scripts. To mitigate issues, consider using a virtual environment like [venv](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/), which creates lightweight virtual environments on top of an existing Python installation. To check if you have venv installed, run `python -m venv --help`. 

!!! note
    If you get an error that the module is not found, you may need to ensure that Python is properly installed and added to your PATH.

Use the following commands to create a virtual environment and install the release notes package.

 1. Create a virtual environment. The second argument is the location to create the virtual environment. If you're in the Ranger directory, you can just call it `.venv` so you have the same virtual environment associated with the project. venv will create a virtual Python installation in the .venv folder.
    ```shell
    python3 -m venv .venv
    ```
 2. Activate the virtual environment with `<path_to_your_virtual_env>/scripts/activate`:

    ```shell
     .venv/scripts/activate
    ```
 3. Run the command to install the release notes generator package. Since you are running the command in your virtual environment, venv will install the packages in the virtual environment, and put them in your shell's PATH. From the repo root enter the command:
    ```shell
    pip install .
    ```

## Feedback and support

For additional feedback or support, please  contact the Technical Documentation (`@<redacted>`) team in Slack.