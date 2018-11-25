---
layout: post
title:  "8 Best Practices for Git"
date:   2016-07-10
categories: code
excerpt: >
  Become a master at Git with these 8 best practices: Set-up, commit messages,
  git workflow, tags, and shortcuts.
---

{{ page.excerpt }}

1. [Set up Git](#1-set-up-git)
1. [Associate your text editor with Git](#2-associate-your-text-editor-with-git)
1. [Work on one issue at a time](#3-work-on-one-issue-at-a-time)
1. [Write clear commit messages](#4-write-clear-commit-messages)
1. [Provide placeholders for files ignored by .gitignore](#5-provide-placeholders-for-files-ignored-by-gitignore)
1. [Find your Git workflow](#6-find-your-git-workflow)
1. [Use version tags](#7-use-version-tags)
1. [Become a Git master](#8-become-a-git-master)

> *Never used Git before? Get your hands dirty with this super newby-friendly
Git tutorial: [https://try.github.io](https://try.github.io)*

# 1. Set up Git

1. Set your username  
  Set with `git config --global user.name "YOUR NAME"`  
  Verify with `git config --global user.name`  
  [Source: Set your username in Git](https://help.github.com/articles/setting-your-username-in-git/)
2. Set your email address  
  Set with `git config --global user.email "your_email@example.com"`  
  Verify with `git config --global user.email`  
  [Source: Set your email in Git](https://help.github.com/articles/setting-your-email-in-git/)
3. Make sure that line endings are configured correctly  
  Set `git config --global core.autocrlf input` (Linux, OS X)  
  Set `git config --global core.autocrlf true` (on Windows)  
  [Source: Handle line endings in Git](https://help.github.com/articles/dealing-with-line-endings/)


# 2. Associate your text editor with Git

If you are using Atom, you can quickly tell Git to use Atom for commit messages.

~~~ shell
$ git config --global core.editor "atom --wait"
~~~

For other editors and more info, see [associating text editors with Git](https://help.github.com/articles/associating-text-editors-with-git/).

# 3. Work on one issue at a time

Each change, addition, or removal you make to your code (adding a controller,
  modifying a model) should go into its own commit with its own clear commit
  message. The only exception is if two pieces of code are very closely related
  and updating both at the same is the only thing that makes sense. For example,
  if your code would otherwise break.

Working (and committing) one issue at a time will make it possible for others
  to understand what is going on. And make it much easier to fix bugs later.

With Git, it's easy to explicitly review what you are about to commit:

1. `git add --patch` to add changes to the index
2. `git diff --cached` to do a review of what you are about to commit
3. `git commit` to execute the commit (this will open your editor for you to
  write a clear commit message!)
4. Repeat from step 1 until you have committed everything (or the remaining
  uncommitted changes need further work).

[Source](https://www.lullabot.com/articles/git-best-practices-workflow-guidelines)

# 4. Write clear commit messages

1. Every commit message should consist of a subject line and a body
1. Line 1: Subject line
  1. Use imperative tense for the subject line: "Fix bug", not "Fixed bug"
  1. Limit to 50 characters
  1. Capitalize the first word
  1. No full stop at the end
1. Line 2: Blank line
1. Line 3+: Body
  1. Use imperative, present tense: "Change", not "Changed" or "Changes"
  1. Limit each line to 72 characters
  1. Include motivation for the change and contrast its implementation to the
     previous behavior (what and why, rather than how)


Here is an example from chris.beams.io](http://chris.beams.io/posts/git-commit/)

~~~
    Summarize changes in around 50 characters or less

    More detailed explanatory text, if necessary. Wrap it to about 72
    characters or so. In some contexts, the first line is treated as the
    subject of the commit and the rest of the text as the body. The
    blank line separating the summary from the body is critical (unless
    you omit the body entirely); various tools like ``log``, ``shortlog`` and
    ``rebase`` can get confused if you run the two together.

    Explain the problem that this commit is solving. Focus on why you
    are making this change as opposed to how (the code explains that).
    Are there side effects or other unintuitive consequences of this
    change? Here's the place to explain them.

    Further paragraphs come after blank lines.

    - Bullet points are okay, too

    - Typically a hyphen or asterisk is used for the bullet, preceded
    by a single space, with blank lines in between, but conventions
    vary here

    If you use an issue tracker, put references to them at the bottom,
    like this:

    Resolves: #123
    See also: #456, #789`
~~~

**Why use the imperative tense?** Because when someone is about to apply your
commits to their code, it will tell them what your commits will do rather than
telling them what they did. Moreover, it also matches Git-generated messages
such as 'Merge' and 'Rebase'.

**Why add a short, descriptive subject line?** Because it will allow people to
skim through your commits using `git log --oneline` and quickly find the
commit that they are searching for.

Pro Tip 1: Sometimes subject-only commit messages are sufficient. In those
  cases you can use `git commit -m "Your 50-character commit message"` to
  write a commit without using any text editor.

Pro Tip 2: You can amend an unpublished commit message by typing
  `git commit --amend` (more on that [here](https://help.github.com/articles/changing-a-commit-message/))

# 5. Provide placeholders for files ignored by .gitignore

This allows the user to get started with your project more quickly. They can
  just rename or reconfigure a few sample placeholder files, rather than
  manually digging through your code to see what files and variables they need.

If, for example, you are using the Rails Dotenv gem, you may want to provide
  a default `.env.example` that is checked into source control. This should list
  all the environment variables that can be defined and provides explanations
  for each.

**Minimize ignored files crucial for operation.** Try to keep the count of
  ignored files, that a user will need to execute your project locally, to a
  minimum.

# 6. Find your Git workflow

There is no one way to use Git for your project. Your usage will depend on
whether you are developing on your own, in a small team, or in a large open
source project.

**Generally, it is agreed that the master branch should always be ready for
deployment. That means that development does not happen on that branch
itself.**

Instead, create a branch called `development` that reflects the new code being
worked on: `git checkout -b development`

Even now, committing directly to the development branch should be avoided.
Instead, **create a new branch from the development branch** for new features
and bug fixed. Assign them a name that clearly summarizes the feature or bug fix
that you are working on. Examples are `email-notifications`, `user-avatars`, or
`single-sign-on`.

~~~ shell
$ git checkout development
$ git branch email-notifications
$ git checkout email-notifications
~~~

## Workflow: Merging

When we merge a new feature into our development branch, there are two
scenarios to consider:

1. We have only made minor modifications, so we do not need to keep a separate
history of the branch (scenario #1)

2. We have developed a full new feature, so we do want to keep a history of this
branch in its entirety (scenario #2)

### Scenario #1: Fast forward

Minor modifications are bug fix, spelling mistakes, and other changes affecting
just a few lines of codes. There is no change in functionality or design.

The `--ff-only` option forces a fast forward, so that your new branch won't
clutter the git history. But in order for the fast forward to succeed, you first
need to rebase your branch to point to the most recent version of the
development branch.

~~~ shell
$ git rebase development YOUR_BRANCH_NAME
$ git checkout development
$ git merge YOUR_BRANCH_NAME --ff-only
~~~

### Scenario #2: True Merge

New features are substantial changes that introduce new functionality,
capabilities, or design to a project.

The `--no-ff` option forces a true merge, retaining the separate branch history.

~~~ shell
$ git checkout development
$ git merge YOUR_BRANCH_NAME --no-ff
~~~

## Workflow: Additional Resources

1. I am working on two new blog posts: One on Solo Git Workflow and one on Team Git Workflow. Stay tuned!
1. Read more [about Git workflow on Github](https://guides.github.com/introduction/flow/).
1. Here is an [absolutely excellent article on Git workflow](http://nvie.com/posts/a-successful-git-branching-model/)
using master, development, release, hotfix, and feature branches.
1. See this [great article by Christophe Porteneuve](https://medium.com/@porteneuve/getting-solid-at-git-rebase-vs-merge-4fa1a48c53aa)
on when to merge and when to rebase.

# 7. Use version tags

Tags are mostly used to specify version numbers that go along with your code.

To add a basic tag to your last commit, do this:

~~~ shell
$ git tag v1.4.3
# Tags the last commit with 'v1.4.3'
~~~

You can also create an annotated tag using:

~~~ shell
$ git tag -a v1.4.3
# Opens the editor to allow you to create a message to go with your tag
~~~

To tag a past commit, specify the commit checksum:

~~~ shell
$ git log --oneline
# c6798fe Add Projects to Blog (PR #11)
# ccf9022 Add projects layout file, Green Naropa project, and images
# d39c2f6 Add collection of type 'project'
# ece9068 Exclude canonical tag from HTML Proofer
# 97655a4 Update site's url to www.finnwoelm.com
# ...
$ git tag v1.2.0 c6798fe
# Adds tag v1.2.0 to commit c6798fe (Add Projects to Blog (PR #11))
~~~

Tags are **not** automatically pushed to Github. To push tags, do `git push
--tags`.

To list all tags, do `git tag` or filter tags with
`git tag -l some_search_query`.


## Renaming tags

Accidentally added the wrong tag?

Rename a tag using:

~~~ shell
$ git tag new_tag tags/old_tag
# Creates a new tag for the same commit as old tag
$ git tag -d tags/old
# Deletes the old tag
~~~

If you already pushed the old tag to Github, no problem. Use these commands to
remove the old tag and push the new one:

~~~ shell
$ git push origin :old_tag
# Removes the old tag from Github
$ git push --tags
# Pushes the new tag to Github
~~~

# 8. Become a Git master

Github has a handy two-page cheat sheet with the most common Git commands:
  [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

Here are some additional commands:

1. `git log branch_a...branch_b`: lists all commits since branch_b split off
branch_a. For example: `git log master...development`. If branch_b is omitted,
simply show all commits since branch_a.
2. `git log --oneline`: lists a log of past commits, showing only their first
lines
3. `git log -some_number`: limit the log to some number of past commits. For
example: `git log -2` will only show the log for the last two commits.
4. `git log -p`: Go through the past commits and show changes made.
5. Learn more formatting options for [viewing the Git commit history](https://www.git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History).
How about `git log --pretty=format:"%h - %an, %ar : %s"` to show date and author
name of each commit?

---

*Featured Image Credits: Git Logo by Jason Long is licensed under the Creative Commons Attribution 3.0 Unported License.*
