# Contributing to onbaordMD

The following is a set of guidelines for contributing to onboardMD and its packages,
which are hosted in the Wearedragonfly organization on GitHub. These are mostly
guidelines, not rules. Use your best judgment, and feel free to propose changes
to this document in a pull request.

#### Table Of Contents

[What should I know before I get started?](#what-should-i-know-before-i-get-started)

[How can I contribute?](#how-can-i-contribute)

[Styleguides](#styleguides)

- [JavaScript styleguide](#javascript-styleguide)

- [TypeScript styleguide](#typescript-styleguide)

- [Specs styleguide](#specs-styleguide)

- [Documentation styleguide](#documentation-styleguide)

- [Issue and pull request templates](#issue-and-pull-request-templates)

[Additional notes](#additional-notes)

- [Issue and pull request labels](#issue-and-pull-request-labels)

- [Code reviews](#code-reviews)

## What should I know before I get started?

onboardMD is a software platform developed for MD Financial. It is a platform
aimed at helping aspiring doctors reach their goals. Every decision should be in
service to this objective.

All code is required to go through static analysis and code reviews before being
comitted. Static analysis is performed using [SonarLint](https://www.sonarlint.org/)
connected to the repository's [SonarCloud](https://sonarcloud.io) project.

All code reviews follow the guidelines outlined in the [Code reviews](#code-reviews) section.

## How can I contribute?

TBD

## Styleguides

### JavaScript styleguide

TBD

### TypeScript styleguide

TBD

### Specs styleguide

- Include thoughtfully-worded, well-structured Mocha specs alongside the module
  under test.

- Unit tests should be distinguished between integration tests by file suffix.

- Unit tests do not require other services for the the test to be executed

- Integration tests require other services such as DB connections, the file system,
  or other microservices for the test to be executed

- Unit test file names should end with `*.test.(js|ts)`

- Integration test file names should end with `*.int.(js|ts)`

- Treat `describe` as a noun or situation.

- Treat `it` as a statement about state or how an operation changes state.

Example

```js
describe('A user repository', function () {
  it('can create a user', function () {
    // spec here
  })

  describe('When the repo is destroyed', function () {
    it('throws an error', function () {
      // spec here
    })
  })

  describe("When the repo's connection is closed", function () {
    it('throws an error', function () {
      // spec here
    })
  })
})
```

### Documenatation styleguide

Use [JSDoc](https://jsdoc.app/), specifically the tags supported by [TypeScript](https://www.typescriptlang.org/docs/handbook/type-checking-javascript-files.html).

Use [Markdown](https://daringfireball.net/projects/markdown).

Reference methods and classes in Markdown with [{@link}](https://jsdoc.app/tags-inline-link.html).

JavaScript example
```js
/**
 * Disable the package with the given name.
 *
 * @param {string} name The name of the package to disable
 * @param {Object} [options] The {@link Object} with disable options (default: {})
 * @param {boolean} options.trackTime Determines if the amount of time taken should be tracked
 * @param {boolean} options.ignoreErrors Determines if errors should be caught and ignored
 * @param {(error?: Error) => void} [callback] The function to call after the package has been disabled
 * @return {void}
 */
function disablePackage (name, options = {}, callback = null) {}
```

TypeScript example
```ts
type DisablePackageOptions = {
  /**
   * Determines if the amount of time taken should be tracked
   */
  trackTime?: boolean
  /**
   * Determines if errors should be caught and ignored
   */
  ignoreErrors?: boolean
}
/**
 * Disable the package with the given name.
 *
 * @param name The name of the package to disable
 * @param [options] The {@link DisablePackageOptions} with disable options
 * @param [callback] The function to call after the package has been disabled
 */
function disablePackage (name: string, options?: DisablePackageOptions, callback?: (error?: Error) => void) {}
```

### Issue and pull request templates

When creating issues there are templates in place for bugs, features and tasks.
When filling out the template please remove sections that are not applicable.

- **bugs** should be preferred for creating issues pertaining to a divergence in
  accepted program behaviour.

- **features** should be preferred for creating issues pertaining to new ideas,
  new behaviour requests, or changes to existing behaviour.

- **tasks** should be preferred for creating issues pertaining to tasks that
  are either tangentially related to product being developed or not suitable
  to be classified as a bug or a feature.

When creating a pull request use the template that is provided, filling in details
where applicable and removing anything that is not applicable.

Generally, all templates are a guide. If you feel the need to add or change a
section to better suit the issue/pull request being created, please do so. The
overall idea behind the templates is that sufficient context is provided for
the stakeholders and/or code reviewers.

## Additional notes

### Issue and pull request labels

TBD

### Code reviews

TBD
