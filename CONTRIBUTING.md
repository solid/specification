# Solid Technical Reports Contributing Guide

Thank you for investing your time in contribution to the Solid project!

This repository contains the source code of the work on [Solid Technical
Reports](https://solidproject.org/TR/) (TR) of the [W3C Solid Community
Group](https://www.w3.org/community/solid/) (CG) to meet the needs of the [Solid
Project](https://solidproject.org/).

The TRs include specifications, use cases and requirements, best practices and
guidelines, primers and notes about the Solid ecosystem.


## Code of conduct

Read the [Solid Code of
Conduct](https://github.com/solid/process/blob/main/code-of-conduct.md) and the
[Positive Work Environment at W3C: Code of Ethics and Professional
Conduct](https://www.w3.org/Consortium/cepc/) to keep our community approachable
and respectable.

See [additional
resources](www.w3.org/about/positive-work-environment/#Education) for
education and training to promote a positive work environment.

## Conformance

The key words “MUST” and “MUST NOT” are to be interpreted as described in [BCP
14](https://tools.ietf.org/html/bcp14)
[RFC2119](https://datatracker.ietf.org/doc/html/rfc2119)
[RFC8174](https://datatracker.ietf.org/doc/html/rfc8174) when, and only when,
they appear in all capitals, as shown here.

## Contributions

In order to be a substantive contributor to work items, you MUST be a member of
the CG. It’s easy to [join the CG](https://www.w3.org/community/solid/join) if
you’d like to contribute. People agree to the [W3C Community License Agreement
(CLA)](http://www.w3.org/community/about/agreements/cla/) upon joining the CG.

The works in this repository use the [MIT
license](https://github.com/solid/specification/blob/main/LICENSE.md).

We accept different types of contributions as described below.

To ensure that anyone can follow along a contribution and support
verification, provide citations to significant units of information, e.g.,
references to specific requirements in technical reports, decisions made in a
formal meeting. To promote accountable discourse, request citations when
questioning uncited claims.

### Discussions

If you'd like help troubleshooting a pull request (PR) you're working on, have a
great new idea, or want to share implementation feedback, join us in [Solid
specification chat](https://gitter.im/solid/specification).

### Issues

[Issues](https://docs.github.com/en/github/managing-your-work-on-github/about-issues)
are used to track tasks that contributors can help with. If an issue has a
triage label, we haven't reviewed it yet and so you are not encouraged to
begin work on it.

If you've found something in the content or the website that might need to be
updated, search open issues to see if someone else has reported the same
thing. If it's something new, open an issue. We'll use the issue to have a
conversation about the problem you want to fix.

### Pull requests

A [pull
request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)
is a way to suggest changes in our repository.

### Translations

We aim to have our documents internationalized and available in multiple
languages. The source content in this repository is written in English. We
accept contributions to localize the English content.


## Contributions at source repository

Each CG work item listed at [Solid Technical
Reports](https://solidproject.org/TR/) has its own repository. It is strongly
encouraged that any issues and PRs are made at their source.

The persistent version of technical reports published in this repository (see
[publishing technical reports](#publishing-technical-reports) are intended to
be read-only snapshots of the CG work items.

[Solid
Panels](https://github.com/solid/specification/blob/main/README.md#solid-panels)
focus on certain work streams, with an aim to propose technical reports for
the Solid ecosystem.

A low-barrier way to add concrete suggestions is to submit a [user
story](https://github.com/solid/user-stories). User stories are descriptions of
desired features written in a special way, see the description there for
details. User stories might then be used when formulating use cases and
requirements.


## Creating and solving issues

### Create a new issue

If you spot a problem with the technical reports being worked on in this
repository or would like to request a feature, [search if an issue already
exists](https://docs.github.com/en/github/searching-for-information-on-github/searching-on-github/searching-issues-and-pull-requests#search-by-the-title-body-or-comments).
If a related issue doesn't exist, you can open a new issue. In the issue,
include relevant information that can help others, e.g., links to
specifications, issues, implementations, test suite, discussions.

### Solve an issue

Scan through our [existing
issues](https://github.com/solid/specification/issues/) to find one that
interests you. You can narrow down the search using `labels` as filters. See
[Labels](https://github.com/github/docs/blob/main/contributing/how-to-use-labels.md)
for more information. If you find an issue to work on, you are welcome to open
a PR with a fix.


## Make changes

### Make changes locally

1. Install Git
2. Fork the repository.
3. Create a working branch and start with your changes!


## Commit your update

Commit the changes once you are happy with them. See [Atom's contributing
guide](https://github.com/atom/atom/blob/master/CONTRIBUTING.md#git-commit-messages)
to know how to use emoji for commit messages.

Once your changes are ready, don't forget to [self-review](#self-review) to
speed up the review process:zap:.

### Self-review

You are strongly encouraged to review your own PR first.

For content changes, make sure that you:

* [ ] Confirm that the changes meet the user experience and goals outlined in
  the content design plan (if there is one).
* [ ] Compare your PR's source changes to staging to confirm that the
  output matches the source and that everything is rendering as expected. The
  W3C service to [creating diff between HTML pages](https://services.w3.org/htmldiff)
  can also be used.
* [ ] Review the content for technical accuracy.
* [ ] Review the content using the [translation guide for
  writers](https://github.com/github/docs/blob/main/contributing/translations-for-writers.md)
  and the [W3C Manual of Style](https://www.w3.org/2001/06/manual/) as guides.
* [ ] Review the content to use [inclusive
  language](https://github.com/github/docs/blob/main/contributing/content-style-guide.md#inclusive-language).
  Celebrate people/names from under represented ethnic/cultural backgrounds in
  examples, e.g., [unique forenames in
  Earth](https://forebears.io/earth/forenames), [example person
  names](https://developers.google.com/style/examples#example-person-names).
* [ ] If there are any failing checks in your PR, troubleshoot them until
  they're all passing.
* [ ] Follow the [Publication Rules](#publication-rules)


## Creating a pull request

When you're finished with the changes to documents that are maintained in this
repository, create a PR.

* Include atomic commits, small PRs: "one concern, one PR".
* In the PR comment, provide as much context and evidence to help reviewers
  evaluate the PR. Identify, classify, describes the changes as per W3C
  Process [Correction
  Classes](https://www.w3.org/Consortium/Process/#correction-classes).
* Don't forget to [link PR to
  issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
  if you are solving one.
* We can ask for changes to be made before a PR can be merged, either using
  [suggested
  changes](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/incorporating-feedback-in-your-pull-request)
  or PR comments. You can apply suggested changes directly through the UI. You
  can make any other changes in your fork, then commit them to your branch.
* As you update your PR and apply changes, mark each conversation as
  [resolved](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request#resolving-conversations).
* If you run into any merge issues, checkout this [git
  tutorial](https://lab.github.com/githubtraining/managing-merge-conflicts) to
  help you resolve merge conflicts and other issues.
* You can attribute a commit to more than one author by adding one or more
  `Co-authored-by: NAME <NAME@EXAMPLE.COM>` per line to commit's message
  (after two empty lines). See [github
  tutorial](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors).

### Your PR is merged!

Congratulations :tada: Solid community thanks you :sparkles:.


## Work items

In general, all documents in scope of the group are welcome. Work items can be
documents or software.

### New work item proposal

* Propose new work item as an issue in https://github.com/solid/specification
  and propose it as an agenda topic in a group meeting.
* Include publicly accessible link to abstract or draft.
* List and link to owners (at least 1 person for advancing the work item and 1
  other person).
* Answer the following questions in order to document how you are meeting the
  requirements for a new work item at the W3C Solid Community Group. Please
  note if this work item supports certain programs or another government or
  private sector project.
  1. Explain what you are trying to do, using no jargon or acronyms.
  2. How is it done today, and what are the limits of the current practice?
  3. What is new in your approach, and why do you think it will be successful?
  4. How are you involving participants from multiple skill sets and global
     locations in this work item? (Skill sets: technical, design, product,
     marketing, anthropological, and UX. Global locations: Africa, the
     Americas, APAC, Europe, Middle East, Antarctica.)
  5. What actions are you taking to make this work item accessible to a
     non-technical audience?


## Publishing a technical report

This section describes how to prepare the technical reports and how they'll be
published on the Solid website.

### General guidance

* Content: the full content of the technical report MUST be human-readable with
  HTML alone. It is strongly discouraged that any CSS and JavaScript interferes
  with the accessibility of the content.
* Offline-friendly: there MUST not be any mandatory external dependencies (e.g.,
  a network connection) to retrieve, to render, or to manipulate the content of
  the article.
* Privacy: scripts MUST not be used to identify or track readers.

There are two parts to publishing a technical report that applies to all
reports:

1. PR including the technical report in HTML and all local script and media
   files.
2. Updating the technical report index (if necessary).

Published documents will be publicly accessible under the paths
`https://solidproject.org/TR/` or `https://solidproject.org/ED/`.

### Versioned technical report

The PR for a versioned technical report MUST include two HTML documents:

1. "Latest version" of the TR under the root (`/`) directory.
2. "This version" (also known as the persistent version) of the TR under
   the `/{YYYY}/` (year in 4 digits) directory.

We recommend that the latest version of the technical reports use a
`{shortname}`, e.g., `protocol`, `wac`, and the persistent version of the
technical report follows the following form: `{shortname}-{YYYYMMDD}`.

All files use common file name extensions, e.g., `.html`.

The documents will be published under the path `https://solidproject.org/TR/`.

For example, the *Solid Protocol* is available from the following URLs:
* This version: https://solidproject.org/TR/2022/protocol-20221231
* Latest version: https://solidproject.org/TR/protocol

When a new version of the technical report is made available, we follow the
same process. The updated "latest version" document will then link to the new
latest persistent version. All persistent versions link to the latest version.

Versioned technical reports MUST indicate their version using the [Semantic
Versioning](https://semver.org/) scheme in the document. The first release
of a technical report MUST use `1.0.0` (for `version-core`). Any release can
use a `pre-release` value part of the version indicating the document status
and the publication date, e.g., "Version 1.0.0-CG-DRAFT" indicates a CG Draft.

### Non-versioned technical report

The PR for a non-versioned technical report MUST include one HTML document and
follow the same requirements as in "latest version" (see [versioned technical
report](#versioned-technical-report)).

The documents will be published under the path `https://solidproject.org/TR/`.

### Editor's draft

The PR for a non-versioned technical report MUST include one HTML document and
follow the same requirements as in "latest version" (see [versioned technical
report](#versioned-technical-report)).

The document will be published under the path `https://solidproject.org/ED/`.
For example, the Editor's Draft of the *Solid Protocol* is available from
https://solidproject.org/ED/protocol .

## Technical Report index

When a new technical report is added, information about it is modified, or a
new work item is being worked on by the CG, a follow-up can PR can be made
to update the [Technical
Report index](https://github.com/solid/specification/blob/main/index.html).

## Publication Rules

W3C CG reports are not required to follow the publication requirements as
W3C reports [on the standards track](https://www.w3.org/TR/). However, we
recommend using the [W3C's Publication rules for Recommendation
(“REC”)](https://www.w3.org/pubrules/doc/rules/?profile=REC)
as a guideline. Solid CG's technical reports differ along the lines of document
status, rights, identifiers. To help readers already familiar with W3C
technical reports, it is recommended to maintain the same look and feel.

See also the [W3C Manual of Style](https://www.w3.org/2001/06/manual/)
guide containing best current practice, written for editors and authors of W3C
technical reports.

We also make the following recommendations:

* MUST be a valid HTML5 document (see also the [W3C Markup Validation
  Service](https://validator.w3.org/)).
* MUST include published and modified dates (`YYYY-MM-DD`).
* MUST use the MIT License (with URL: http://purl.org/NET/rdflicense/MIT1.0 ).
* Follow the [Internationalization Best Practices for Spec
  Developers](https://www.w3.org/TR/international-specs/).
* Follow the [Linked Data](https://www.w3.org/DesignIssues/LinkedData) design
  principles. Give all significant units of information, e.g., concepts,
  requirements, an identifier, and provide a description using a concrete RDF
  syntax (see also [Spec Terms](http://www.w3.org/ns/spec)).
* Cite the source resource in which consensus was reached for a given
  statement.
* Changelog from previous published releases (if applicable).
* Considerations section, e.g., [Self-Review Questionnaire: Security and
  Privacy](https://www.w3.org/TR/security-privacy-questionnaire/),
  Accessibility, Internationalization, Societal Impact.
* Conformance Classes section to identify who and/or what will implement the
  specification.
* Document wilful violations.
* Use consistent spelling throughout the document.


## Vocabulary Management

TRs might refer to or make use of namespaces for specific functionality. The
CG handles the management of Solid vocabularies under its responsibility
through the [solid/vocab](https://github.com/solid/vocab) repository.

The policy for the management of Solid vocabularies under the W3C namespace is
described in [Adding to W3C RDF
Namespaces](https://www.w3.org/2016/08/namespaces/).


## Meetings

The CG [Meeting
Guidelines](https://github.com/solid/specification/blob/main/meetings/README.md)
describes how to participate and record meetings. There is a
[minutes
template](https://github.com/solid/specification/blob/main/meetings/template.md)
that can be used by scribes to transcribe the meeting.


## Communication

The opinions of CG members may carry particular weight, whether they are
expressed within our community or elsewhere. As a CG member:
* It is assumed you are speaking as an individual unless you state otherwise.
* If you want to express the opinion of your organisation or a group you are
  affiliated with, make it clear before you state their view.
* Do not use phrases like "on behalf of the CG" or "the CG thinks that" unless
  the group has asked you to do so.
* When communicating CG decisions, provide references to what was decided and
  what was not decided.
