---
title: Contribution
source: https://github.com/naomiproject/naomi-docs/blob/master/developer/contributing/contributing.md
meta:
  - property: og:title
    content: "Contribution"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Contributing to the Development of Naomi

## The Repositories

Naomi as a whole is broken into different Repos depending on what it pretains.

* [Naomi Base](https://github.com/naomiproject/naomi): This repo contains the base Naomi program.
* [Naomi Plugins](https://github.com/naomiproject/naomi-plugins): Plugins for Naomi. They cannot be used with a Jasper 1.x instance, since they provide features that the old runtime does not support.
* [Naomi Docs](https://github.com/NaomiProject/naomi-docs): This repository contains the documentation for Naomi | Master branch is updated per stable releases from the Dev branch which is where day to day changes take place!
* [Naomi Website](https://github.com/NaomiProject/naomi-website): This repository contains the final artifacts from which the project website is served.

## Contribution Guidelines

### Pull Requests are Always Welcome

We are always thrilled to receive pull requests, and do our best to
process them as fast as possible. Not sure if that typo is worth a pull
request? Do it! We will appreciate it.

If your pull request is not accepted instantly, don't be
discouraged! If there's a problem with the implementation, hopefully you
received feedback on what to improve.

We're trying very hard to keep Naomi lean and focused. We don't want it
to do everything for everybody. This means that we might decide against
incorporating a new feature. However, there might be a way to implement
that feature *on top of* Naomi.

### Discuss your Design on the Mailing List

We recommend discussing your plans [in the discussion forum](https://community.projectnaomi.com)
before starting to code - especially for more ambitious contributions.
This gives other contributors a chance to point you in the right
direction, give feedback on your concept, and maybe point out if someone
else is working on the same thing.

### Create Issues

Any significant improvement should be documented as a GitHub
issue in the [appropriate repository](#the-repositories) before anybody
starts working on it.

### ...but Check for Existing Issues First

Please take a moment to check that an issue doesn't already exist
documenting your bug report or improvement proposal. If it does, it
never hurts to add a quick "+1" or "I have this problem too". This will
help prioritize the most common problems and requests.

### Conventions

Fork the repo and make changes on your fork in a feature branch:

* If it's a bugfix branch, name it XXX-something where XXX is the number of the
  issue
* If it's a feature branch, create an enhancement issue to announce your
  intentions, and name it XXX-something where XXX is the number of the issue.

Submit unit tests for your changes.  Naomi has a great test framework built in; use
it! Take a look at existing tests for inspiration. Run the full test suite on
your branch before submitting a pull request.

Update the documentation when creating or modifying features. Test
your documentation changes for clarity, concision, and correctness, as
well as a clean documentation build.

Write clean code. Universally formatted code promotes ease of writing, reading,
and maintenance.

Pull requests descriptions should be as clear as possible and include a
reference to all the issues that they address.

Pull requests must not contain commits from other users or branches.

Commit messages must start with a capitalized and short summary (max. 50
chars) written in the imperative, followed by an optional, more detailed
explanatory text which is separated from the summary by an empty line.

Code review comments may be added to your pull request. Discuss, then make the
suggested modifications and push additional commits to your feature branch. Be
sure to post a comment after pushing. The new commits will show up in the pull
request automatically, but the reviewers will not be notified unless you
comment.

Before the pull request is merged, make sure that you squash your commits into
logical units of work using `git rebase -i` and `git push -f`. After every
commit the test suite should be passing. Include documentation changes in the
same commit so that a revert would remove all traces of the feature or fix.

Commits that fix or close an issue should include a reference like `Closes #XXX`
or `Fixes #XXX`, which will automatically close the issue when merged.

### Merge Approval

Naomi maintainers use the [Github review feature](https://help.github.com/articles/about-pull-request-reviews/) to indicate acceptance.

A change requires approval from an absolute majority of the maintainers of each
component affected. For example, if a change affects `plugins/` and `features/`, it
needs an absolute majority from the maintainers of `plugins/` AND, separately, an
absolute majority of the maintainers of `features/`.

### Sign your Work

The repos are setup to ask for a CLA sign-off when creating a pull request for the first time. This certifies that you wrote code or otherwise have the right to
pass code on as an open-source patch.
The rules are pretty simple: if you can certify the below (from
[developercertificate.org](http://developercertificate.org/)):

```text
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
660 York Street, Suite 102,
San Francisco, CA 94110 USA

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.


Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

This is done by clicking the link on the CLAassitants comment on your pull request,
signing in to the site using your github account, and then filling out the form.

You **MUST** your real name (sorry, no pseudonyms or anonymous contributions.) as well as an
e-mail address under which you can be reached (sorry, no github noreply e-mail
addresses (such as username@users.noreply.github.com) or other non-reachable
addresses are allowed).

> Note: If this is not followed your contribution will be rejected.

If your pull request contains code from others as well, each party has to accept the CLA.

### How can I Become a Maintainer

* Step 1: learn the program inside & out
* Step 2: make yourself useful by contributing code, bugfixes, support, etc.
* Step 3: volunteer [in the community](https://community.projectnaomi.com/)

Don't forget: being a maintainer is a time investment. Make sure you will have time to make yourself available.
You don't have to be a maintainer to make a difference on the project!

## Community Guidelines

We want to keep the Naomi community awesome, growing and collaborative. We
need your help to keep it that way. To help with this we've come up with some
general guidelines for the community as a whole:

* Be nice: Be courteous, respectful and polite to fellow community members: no
  regional, racial, gender, or other abuse will be tolerated. We like nice people
  way better than mean ones!

* Encourage diversity and participation: Make everyone in our community
  feel welcome, regardless of their background and the extent of their
  contributions, and do everything possible to encourage participation in
  our community.

* Keep it legal: Basically, don't get us in trouble. Share only content that
  you own, do not share private or sensitive information, and don't break the
  law.

* Stay on topic: Make sure that you are posting to the correct channel
  and avoid off-topic discussions. Remember when you update an issue or
  respond to an email you are potentially sending to a large number of
  people.  Please consider this before you update.  Also remember that
  nobody likes spam.

<DocPreviousVersions/>
<EditPageLink/>
