
## Goal

The goal of this repository is to provide a consistent customer experience and improve the quality of workshop documentation for AI Tour 26 events. By following the suggested structure and best practices, you can ensure your content is clear, engaging, and easy to follow for all participants.

Welcome to the AI Tour 26 documentation toolkit! This guide will help you create effective, engaging content for your audience.

## Suggested Structure for Labs

This repository provides a recommended structure for your documentation. For lab guides (see `lab-1-open-workshop.md` as a reference), each lab should include:

- **What You'll Learn:** Briefly outline the key skills or concepts participants will gain.
- **Introduction:** Set the context and explain the purpose of the lab.
- **Lab Exercise:** Step-by-step instructions for completing the lab tasks.

Following this format helps ensure consistency and clarity across all workshop materials.

## 1. Understand Your Audience

- **Developers or Data Scientists:** Focus on practical examples, code snippets, and hands-on labs.
- **Technical Decision Makers:** Highlight architecture, business value, and strategic insights.

!!! info
    For content aimed at **Data Scientists**, Jupyter Notebooks are a great way to present interactive code, data analysis, and visualizations.

## 2. KISS Principle

- **Keep It Simple:** Avoid jargon and complex explanations. Assume minimal prior knowledge.
- **Be Clear:** Use concise language and step-by-step instructions.

## 3. Get Started with This Repo

- **Clone this repository:**

  ```sh
  git clone <your-repo-url>
  ```

- **Copy docs:**
  Copy the contents of the `docs` folder from this repo to the `docs` folder in your AI Tour 26 repo.

## 4. Getting Started with MkDocs

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

## 5. Tricks for Sticky Tabs


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

## 6. Splitting Content with 'includes'

You can split out reusable content using the `includes` folder. For example to include a common introduction for self-guided learners:

&#123;% include-markdown "includes/introduction-self-guided.md" %&#125;

This will include the content from `docs/docs/includes/introduction-self-guided.md` into your page.

Explore the `docs/docs/includes` folder for more examples.


## 7. Deploying to GitHub Pages

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
# Content Creators Guide
