---
layout: post
title: "Using Git and GitHub for Network Administration"
date: 2026-10-07
categories: [networking, git, github, network-plus]
---

Version control is something I originally associated mostly with software development, but after working through the Git and GitHub lessons, it became clear that it is just as useful in networking and IT administration. Network administrators regularly change device configurations, documentation, scripts, diagrams, firewall rules, and troubleshooting notes. Without a version-control system, it can be difficult to know what changed, who changed it, or how to return to a known working version.

Git provides a structured way to solve that problem. GitHub builds on Git by providing remote repositories, collaboration tools, code review, issue tracking, and a way to publish technical work through GitHub Pages.

## Why Version Control Matters in Networking

One of Git's biggest advantages is that it creates a history of changes. Instead of saving files with names such as `router-config-final.txt`, `router-config-final2.txt`, and `router-config-really-final.txt`, Git records meaningful versions as commits.

For a network administrator, Git can be used to track:

- Router and switch configurations
- Firewall and access-control rules
- VLAN documentation
- IP addressing plans
- Network diagrams
- Automation scripts
- Troubleshooting notes
- Standard operating procedures

If a configuration change creates a problem, Git can help identify exactly what changed and make it possible to return to an earlier version. This provides a more reliable process than depending on memory or manually maintained backup copies.

## The Basic Git Workflow

The Microsoft Learn **Introduction to Git** module explains the main ideas behind source control and distributed version control. A basic workflow begins by creating a repository and then recording changes as the project develops.

Some common commands are:

```bash
git init
git status
git add .
git commit -m "Updated VLAN configuration"
git log
```

`git init` turns a directory into a Git repository. `git status` shows files that have changed. `git add` stages changes for the next commit, and `git commit` creates a recorded checkpoint.

Commit messages are important because they become technical documentation. A message such as `Updated VLAN 20 gateway and switch ports` gives useful information about the change. A message such as `changes` does not.

## Branches Make Changes Safer

A branch creates a separate line of work. That means an administrator can experiment with a configuration or documentation change without immediately changing the main version of the project.

For example:

```bash
git switch -c vlan-redesign
```

I could make the proposed VLAN changes on that branch, test them, document the results, and only merge the work into the main branch after I am satisfied with it.

This is similar to making changes in a test environment before touching production. Branching reduces risk and also creates a clearer history of how a change was developed.

## Merging and Merge Conflicts

After work on a branch has been tested, it can be merged back into the main branch.

```bash
git switch main
git merge vlan-redesign
```

Sometimes Git cannot automatically decide how to combine two versions of the same section of a file. This creates a **merge conflict**. Git marks the conflicting sections so the administrator can review both versions and decide what the final file should contain.

Merge conflicts are not necessarily failures. They are a signal that two changes overlap and need human review. In networking, that review can be especially important because an incorrect configuration could affect connectivity or security.

## Undoing Changes and Returning to a Working State

Another major advantage of version control is the ability to recover from mistakes.

Git provides several ways to undo work depending on the situation. An administrator might restore an individual file, reverse a previous commit, or reset a local branch when appropriate.

For shared repositories, `git revert` is often useful because it creates a new commit that reverses an earlier change while preserving the project history.

```bash
git revert <commit-id>
```

The important idea is that Git gives administrators a documented path back instead of forcing them to reconstruct an old configuration from memory.

## Git and GitHub Are Different

Git and GitHub are related, but they are not the same product.

**Git** is the distributed version-control system running locally.

**GitHub** is a platform that hosts Git repositories and adds collaboration features.

A local Git repository can exist without GitHub. GitHub becomes valuable when the repository needs remote storage, collaboration, review, issue tracking, or public presentation.

## Remote Repositories

Once a local repository is connected to GitHub, commits can be pushed to a remote repository.

A normal workflow might look like:

```bash
git add .
git commit -m "Documented switch configuration changes"
git push
```

Another administrator can clone the repository and receive its history:

```bash
git clone <repository-url>
```

This makes it possible for multiple administrators to work from the same controlled source of documentation.

For real network environments, sensitive information must be handled carefully. Passwords, API keys, private keys, authentication tokens, and other secrets should never be committed to a public repository. Network configuration files should be sanitized before publication.

## GitHub Issues and Pull Requests

The Microsoft Learn **Introduction to GitHub** module shows that GitHub is more than a place to store files.

GitHub Issues can be used to track work such as:

- Updating firewall rules
- Replacing network equipment
- Correcting documentation
- Investigating an outage
- Testing a configuration change

Pull requests provide a review process before changes are merged into the main branch. A team member can inspect the changes, leave comments, request corrections, or approve the work.

For network administration, this provides useful accountability. The team can see what was proposed, why it was proposed, which files changed, and whether the change was reviewed.

## GitHub Pages and Jekyll

GitHub Pages turns a GitHub repository into a public website. Jekyll is a static site generator supported by GitHub Pages that can convert Markdown files into webpages.

That makes GitHub Pages a practical way to build a technical portfolio.

Instead of only writing on a resume that I understand subnetting, VLANs, Git, security, or troubleshooting, I can publish examples of the work itself.

Jekyll blog posts are commonly stored in a folder named `_posts` and use a filename that begins with the publication date:

```text
2026-10-07-using-git-and-github-for-network-administration.md
```

The file begins with front matter that defines information such as the layout, title, date, and categories.

This portfolio is itself an example of that process: the article was written in Markdown, committed to a Git repository, pushed to GitHub, and published using GitHub Pages.

## Building a Networking Portfolio

The most useful part of this lesson is that Git and GitHub can become part of my normal networking workflow rather than existing only as another topic to study.

This repository is organized so that future work can be added in separate areas:

```text
networking-portfolio/
├── _posts/
├── labs/
├── documentation/
├── about.md
├── index.md
└── _config.yml
```

The `_posts` directory contains technical blog posts. The `labs` directory can hold hands-on exercises and evidence. The `documentation` directory can contain reference material, configuration examples, and technical notes.

As the portfolio develops, Git will maintain the history behind all of it.

## Final Thoughts

Learning Git and GitHub gives me a better way to manage technical work. The biggest benefit is not simply storing files online. The real value is maintaining a complete change history, testing changes safely, documenting why changes were made, collaborating with other people, and being able to recover when something goes wrong.

Those abilities are directly useful in network administration because reliability, documentation, troubleshooting, and controlled change management are all important parts of operating a network.

By combining Git, GitHub, Jekyll, and GitHub Pages, I can use the same work I complete while learning networking to build a professional portfolio that demonstrates the skills instead of only listing them.

## Resources

- [Microsoft Learn: Introduction to Git](https://learn.microsoft.com/en-us/training/modules/intro-to-git/)
- [Microsoft Learn: Introduction to GitHub](https://learn.microsoft.com/en-us/training/modules/introduction-to-github/)
- [GitHub Docs: Setting up a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
- [GitHub Docs: GitHub Pages](https://docs.github.com/en/pages)
- [YouTube: How to make a personal website with GitHub Pages](https://www.youtube.com/watch?v=qZsgPgGdOzQ)
