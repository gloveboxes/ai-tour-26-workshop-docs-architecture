
## Goal

The goal of this repository is to provide a consistent customer experience and improve the quality of workshop documentation for AI Tour 26 events. By following the suggested structure and best practices, you can ensure your content is clear, engaging, and easy to follow for all participants.

Welcome to the AI Tour 26 documentation toolkit! This guide will help you create effective, engaging content for your audience.

## Suggested Structure for Labs

This repository provides a recommended structure for your documentation. For lab guides (see `lab-1-open-workshop.md` as a reference), each lab should include:

- **What You'll Learn:** Briefly outline the key skills or concepts participants will gain.
- **Introduction:** Set the context and explain the purpose of the lab.
- **Lab Exercise:** Step-by-step instructions for completing the lab tasks.

Following this format helps ensure consistency and clarity across all workshop materials.

## Understand Your Audience

- **Developers or Data Scientists:** Focus on practical examples, code snippets, and hands-on labs.
- **Technical Decision Makers:** Highlight architecture, business value, and strategic insights.

    !!! tip
        For content aimed at **Data Scientists**, Jupyter Notebooks are a great way to present interactive code, data analysis, and visualizations.

## KISS Principle

- **Keep It Simple:** Avoid jargon and complex explanations. Assume minimal prior knowledge.
- **Be Clear:** Use concise language and step-by-step instructions.

## Get Started with This Repo

- **Clone this repository:**

  ```sh
  git clone <your-repo-url>
  ```

- **Copy docs:**
  Copy the contents of the `docs` folder from this repo to the `docs` folder in your AI Tour 26 repo.

## Getting Started with MkDocs

- **Install requirements:**
  The `requirements.txt` file for MkDocs is in the `docs` folder. Install dependencies with:

    ```sh
    pip install -r docs/requirements.txt
    ```

- **Run MkDocs locally:**

    ```sh
    cd docs && mkdocs serve
    ```

Once running, you can live preview your documentation by clicking the link shown in your terminal (usually [http://127.0.0.1:8000](http://127.0.0.1:8000) or similar).

## Don't use Heading level 1

MkDocs automatically generates the main title from the `mkdocs.yml` file, so avoid using Heading level 1 (`#`) in your Markdown files. Use Heading level 2 (`##`) for main sections and Heading level 3 (`###`) for subsections.

## Using MkDocs Admonitions (Tips, Warnings, Info)

You can use MkDocs admonition to highlight important information, tips, warnings, and more in your documentation. Here are some commonly used admonition:

**Raw Markdown:**

```markdown
!!! tip
    This is a tip annotation.

!!! warning
    This is a warning annotation.

!!! info
    This is an info annotation.

!!! note
    This is a note annotation.

!!! danger
    This is a danger annotation.

!!! success
    This is a success annotation.

!!! question
    This is a question annotation.
```

**How it Renders:**

!!! tip
    This is a tip annotation.

!!! warning
    This is a warning annotation.

!!! info
    This is an info annotation.

!!! note
    This is a note annotation.

!!! danger
    This is a danger annotation.

!!! success
    This is a success annotation.

!!! question
    This is a question annotation.

---

## Tricks for Sticky Tabs

Use sticky tabs to show code examples in multiple languages. Example:

**Raw Markdown:**

```markdown
=== "Python"
    ```python
    print("Hello, AI Tour 26!")
    ```

=== "C#"
    ```csharp
    Console.WriteLine("Hello, AI Tour 26!");
    ```
```

**How it Renders:**

=== "Python"
    ```python
    print("Hello, AI Tour 26!")
    ```

=== "C#"
    ```csharp
    Console.WriteLine("Hello, AI Tour 26!");
    ```

## Splitting Content with 'includes'

You can split out reusable content using the `includes` folder. For example to include a common introduction for self-guided learners:

&#123;% include-markdown "includes/introduction-self-guided.md" %&#125;

This will include the content from `docs/docs/includes/introduction-self-guided.md` into your page.

Explore the `docs/docs/includes` folder for more examples.

## Using LLMs to Help with Content Creation

Large Language Models (LLMs) like GitHub Copilot or ChatGPT can be valuable tools for improving your documentation. Here are some example prompts you can use to enhance your content:

**Useful Prompts for Document Content Creators:**

- `Rewrite to be concise and clear.`
- `Summarize this section for a beginner audience.`
- `Suggest a more engaging introduction for this lab.`
- `Check this text for grammar and spelling errors.`
- `Convert this list into a step-by-step guide.`
- `Add a practical example to this explanation.`
- `Rephrase this to be more formal/informal.`
- `Highlight the key takeaways from this section.`
- `Suggest improvements for accessibility and inclusivity.`

Experiment with these prompts to make your documentation more effective and user-friendly.

---

## Deploying to GitHub Pages

You can easily publish your documentation using GitHub Pages. Here are the steps:

### 1. Add a GitHub Actions Workflow

Create a file at `.github/workflows/gh-pages.yml` in your repository with the following content:

```yaml
name: Deploy MkDocs to GitHub Pages
on:
  push:
    branches:
      - main
permissions:
  contents: write
jobs:
  deploy:
    env:
      CONFIG_FILE: docs/mkdocs.yml
      REQUIREMENTS: docs/requirements.txt
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v3
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material mkdocs-glightbox mkdocs-include-markdown-plugin
      - run: mkdocs gh-deploy --force --config-file docs/mkdocs.yml
```

### 2. Enable GitHub Pages

Go to your repository settings, find the **Pages** section, and set the source to `gh-pages` branch. After your workflow runs, your site will be published at the provided URL.

For more details, see the [MkDocs GitHub Pages documentation](https://www.mkdocs.org/user-guide/deploying-your-docs/#github-pages).

## Language Translations

1. From VS VCode and GitHub Copilot, you can use the following prompt to translate your documentation into Spanish:

    ```text
    Translate the workshop documentation in folder `docs/docs/en` from English to Brazilian Portuguese, maintaining the original file structure and formatting. 
    Follow these steps:
    1. Create a new folder using the destination language ISO 639-1 code name to store the translated files.
    2. For each file:
      - **NEVER** wrap the translated files in a markdown code block.
      - Maintain the original file name, structure, and formatting (including Markdown structure, metadata, and code blocks).
      - **IGNORE** any linting or formatting warnings and continue processing all files without interruption.
      - Append a note to the end of each file indicating that it has been translated using GitHub Copilot and GPT-4o.
      - Save the translated files into a new folder.

    Additionally:
    1. Update the mkdocs.yml configuration file by:
    • Adding a new locale entry for Brazilian Portuguese (pt-BR) under the i18n plugin section.
    • Providing appropriate translations for all nav_translations and admonition_translations keys.
    ```

2. Add Context to Copilot

   - mkdocs.yml
   - docs folder

3. The agent will translate the files and update the `mkdocs.yml` file with the new language settings in batches. You'll need to ask the agent to continue until all files are translated.
