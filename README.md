# Common Commit Guidance

This repository documents a standard commit message and continuous release practice for all Wayfind Entertainment and Graphic Art Quest code projects. This specification is inspired by and supersedes the [Angular Commit Message](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit). Feel free to copy or modify this guidance in your own projects, or link back here as a common resource.

- [Commits](#commits)
    - [Commit Header Format](#commit-header-format)
        - [Types](#types)
        - [Scopes](#scopes)
    - [Commit Body Format](#commit-body-format)
    - [Commit Footer Format](#commit-footer-format)
    - [Referencing Issues Without Closing](#referencing-issues-without-closing)
- [Versioning Triggers](#versioning-triggers)
- [Example Commit Messages](#example-commit-messages)
    - [Patch Version Change](#patch-version-change)
    - [Minor Version Change](#minor-version-change)
    - [Major Version Change](#major-version-change)
    - [No Change](#no-change)
- [License and Development](#license-and-development)
- [Contact](#contact)

# Commits

If possible, make [atomic commits](https://en.wikipedia.org/wiki/Atomic_commit), which means:

-   a commit should contain exactly one self-contained functional change
-   a functional change should be contained in exactly one commit
-   a commit should not create an inconsistent state (such as test errors, linting errors, partial fix, feature with documentation etc...)

A complex feature can be broken down into multiple commits as long as each one maintains a consistent state and consists of a self-contained change.

This project uses very precise rules over how Git commit messages must be formatted. This leads to **easier to read commit history**.

Each commit message consists of a **header**, a **body**, and a **footer**.

```bash
<header>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The `header` is mandatory and must conform to the [Commit Message Header](#commit-header-format) format.

The `body` is mandatory for all commits except for those of type "docs".
When the body is present it must be at least 20 characters long and must conform to the [Commit Message Body](#commit-body-format) format.

The `footer` is optional unless resolving issues. The [Commit Message Footer](#commit-footer-format) format describes what the footer is used for and the structure it must have.

## Commit Header Format

The header contains succinct description of the change:

-   use the imperative, present tense: "change" not "changed", nor "changes"
-   do not capitalize first letter
-   no period (`.`) at the end
-   if the commit is of type `revert`, include `reverts commit <hash>`, where the hash is the SHA of the commit being reverted

```
<type>(<scope>): <short summary>
│ │ │
│ │ └─⫸ Summary in present tense. Not capitalized. No period at the end.
│ │
│ └─⫸ Commit Scope: <custom>|api|contributing|license|readme|security
│
└─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|revert|test
```

### Types

Required. Must be one of the following:

|Type|Description|
|:--|:--|
|`api`|Non-functional changes to code API documentation that help other developers understand how to use a tool or feature (i.e. intellisense)|
|`build`|Changes that affect the build system configuration, package scripts, or developer dependencies (i.e. adds/remove/modify/update)|
|`ci`| Changes to CI configuration files and scripts (e.g. release configs, YAML scripts)
|`docs`|Documentation only changes for the project, excluding API documentation|
|`feat`|Adds a new or enhances an existing feature|
|`fix`| Fixes a bug in an existing feature or updates to non-developer dependencies|
|`perf`|A code change that improves performance|
|`refactor`|A code change that neither fixes a bug nor adds a feature|
|`revert`|Revert to a previous commit|
|`test`|Add missing tests or correct existing tests|

### Scopes

Optional. If used, must be one of the following supported scopes:

|Scope|Description|
|:--|:--|
|`<custom>`|Used for extending these settings with individual projects' unique requirements|
|`contributing`|Contributions to the project's `CONTRIBUTING.md` or `CODE_OF_CONDUCT.md` files|
|`license`|Changes to terms or copyright status within the project's license.<br>***Any change in license type or further restricting terms MUST include a BREAKING CHANGE***
|`readme`|Contributions to a project's main `README.md` file|
|`security`|Changes that address code related security issues or security policies|

## Commit Body Format

Provide a plain text description of _why_ you made this change. This is the place for you to explain your thought process, developer to developer. If helpful, include a comparison of the previous behavior with the new behavior to illustrate the change's impact.

If there are breaking changes, start the body with

    `BREAKING CHANGE: <breaking change summary>.`

## Commit Footer Format

The footer identifies which issues this commit fixes. If none, leave it blank. Otherwise, use the format:

    Resolves: #<issue number>

If more than one issue is resolved, repeat for each one: 

    Resolves: #1, Resolves: #2, Resolves: #3

## Referencing Issues Without Closing

Typing `#<number>` anywhere within the commit text without the `Resolves` flag will cause Github to make a reference to the issue without closing it:

    docs(readme): update `foo` section

    The previous change in #4 made the readme guidance unclear.
    
    Makes preparations for changes coming in #9.

    Resolves: #8


# Versioning Triggers

All Wayfind Entertainment and Graphic Art Quest projects use [Semantic Versioning](https://semver.org/). Pushes to the `main` branches trigger updates either manually or automatically (if a continuous integration process has been enabled) based on the specific types used in the commit messages

|Trigger|Commit Type|
|:--|:--|
|Patch|`api`<br>`fix`<br>`perf`|
|Version|`feat`|
|Major|`BREAKING CHANGE`|

# Example Commit Messages

## Patch Version Change:

```
api: update the docstring comments in the `foo` function for parameter clarity
```

```
perf: change `foo` implementation to the faster xyz algorithm
```

```
fix(index): add function `foo`

This function adds the key functionality to the project.

Resolves: #1
```

## Minor Version Change:

```
feat(index): add function `foo`

This function adds the key functionality to the project.

Resolves: #2
```

## Major Version Change:

```
feat(index): add function `foobar`

BREAKING CHANGE: This function does some new useful things.
Due to additional refactoring in the `foo` function, it no longer does baz.

This change required additional description in a second body paragraph.

Resolves: #3, Resolves: #4
```

## No Change:

```
docs(readme): update readme to document new changes to `foo`
```

```
refactor(foo): reorganize the `foo` code for readability
```

```
build: updated the `bar` dev dependency
```


# License and Development

These standards, configurations, and all other files in this repository are distributed as free and open-source software under the [MIT License](./LICENSE), © 2023 [Wayfind Entertainment LLC](https://www.GraphicArtQuest.com).

Contributions welcome. If you have a question for how to use any of this guidance, [open an issue for assistance][questions].

# Contact

Maintained by [M. Scott Lassiter][maintainer].

[![Subscribe to the Graphic Art Quest YouTube channel](https://img.shields.io/badge/Subscribe%20to%20Graphic%20Art%20Quest-FF0000?style=plastic&logo=youtube&logoColor=white)][subscribe]

[questions]: https://github.com/WayfindEntertainment/Common-Commit-Guidance/issues/new?assignees=m-scott-lassiter&labels=question&template=assistance_requested.yml
[maintainer]: https://graphicartquest.com/author/scott-lassiter/
[subscribe]: https://www.youtube.com/channel/UCFYKeFMbQnY5CdzFH62PAhg?sub_confirmation=1
