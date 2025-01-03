---
layout: post
title: "Setup Dependabot"
date: 2025-01-03 10:00:00 -0500
categories: technology
---

Dependabot is one of the most underrated features on a GitHub repository. It's a
free service that ensures your dependencies are up to date and warns you about
security issues in them. It does this by automatically scanning your
dependencies and creating a pull request for you to approve.

## How to Set Up

To set up Dependabot in your GitHub repository, follow these steps:

1. Navigate to the **Insights** tab in your GitHub repository.
2. Click on the **Dependency graph** on the left.
3. Depending on whether your repo is public or private, you will see a couple of
   tabs. Open the one for **Dependabot**, and click on the **Enable Dependabot**
   button.
4. Finally, click on the **Create config file** button. This will create a
   `dependabot.yml` file in the `.github` folder in your repository.

I like to add a groups node to the config file; the groups node tells Dependabot
to group the updates for the dependencies into two PRs instead of creating a
separate PR for each update.

```yaml
version: 2
updates:
  - package-ecosystem: "npm" # See documentation for possible values
    directory: "/" # Location of package manifests
    schedule:
      interval: "weekly"
    # Add these groups
    groups:
      development-dependencies:
        dependency-type: "development"
      production-dependencies:
        dependency-type: "production"
```

For other options see
[the official Dependabot docs](https://docs.github.com/en/code-security/dependabot).

## What Does a PR Look Like

Dependabot creates two separate PRs, one for production packages and one for
development packages.

![List of Dependabot PRs](/assets/images/dependabot-prs.png)

In the description of each PR, it outlines which packages are updated, with
links to the commits, release notes, and changelog, when available.

![PR description](/assets/images/dependabot-pr-info.png)

After that, the PRs can follow your regular PR approval process of running tests
and getting approvals before merging.
