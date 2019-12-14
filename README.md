# Backport Bot

Backport Bot is a [JavaScript GitHub Action](https://help.github.com/en/articles/about-actions#javascript-actions) to backport a pull request by simply adding a label to it.

It can backport [rebased and merged](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-merges#rebase-and-merge-your-pull-request-commits) pull requests with a single commit and [squashed and merged](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-merges#squash-and-merge-your-pull-request-commits) pull requests. It thus integrates well with [Autosquash](https://github.com/marketplace/actions/autosquash).

This version even works on forked repositories. Also, it will open a pull request even if there is a conflict. Happy backporting!

## Usage

1. :electric_plug: Add this [.github/workflows/backport.yml](.github/workflows/backport.yml) to your repository.
2. :guardsman: Create a user for the bot. Set this username in backport.yml
3. :scissors: With this user, fork your repository.
4. :key: Generate a personal access token with this user. Give it permission to write to its repositories.
5. :unlock: Setup this personal access token as BACKPORT_BOT_TOKEN in your repo.
6. :speech_balloon: Let's say you want to backport a pull request on a branch named `production`. Then label it with `backport production`. (See [how to create labels](https://help.github.com/articles/creating-a-label/).)
7. :sparkles: That's it! When the pull request gets merged, another pull request will be opened, backporting the commit to the `production` branch. If the pull request cannot be backported, a comment explaining why will automatically be posted.

_Note:_ multiple backport labels can be added. For example, if a pull request has the labels `backport staging` and `backport production` it will be backported to both branches: `staging` and `production`.
