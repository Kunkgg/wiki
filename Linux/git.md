
# git

## How to Write a Git Commit Message

The seven rules of a great Git commit message:

1.  Separate subject from body with a blank line
1.  Limit the subject line to 50 characters
1.  Capitalize the subject line
1.  Do not end the subject line with a period
1.  Use the imperative mood in the subject line
1.  Wrap the body at 72 characters
1.  Use the body to explain what and why vs. how

For example:

```sh
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

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
See also: #456, #789
```
## Common Tasks

### Clear History

1.  Use rebase merging

2.  Set merge button allow rebase merging

### Delete branch

1.  Delete local branch

    git branch -d <branchname>
    git branch -D <branchname>

2.  Delete remote branch

    git branch -a
    git push origin --delete <branchname>

## Tips

### specify a particular version of the file:

    $ git diff v2.5:Makefile HEAD:Makefile.in

### How to complete a git clone for a big project on an unstable connection?

Use shallow clone

    git clone --depth=1
    git fetch --depth=N or git fetch --unshallow
    git pull --all

[stackoverflow](https://stackoverflow.com/questions/3954852/how-to-complete-a-git-clone-for-a-big-project-on-an-unstable-connection)

## Reference

### man pages

*   gitglossary
*   giteveryday
*   gitworkflows
*   gittutorial[-2]
*   git-format-patch
*   git-am
*   git-bisect
*   git-config

### Guidelines

-   [Pro Git](https://git-scm.com/book/en/v2)
-   [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
-   [gitlab Merge requests workflow](https://docs.gitlab.com/ee/development/contributing/merge_request_workflow.html)
