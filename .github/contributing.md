# Contributing to onbaordMD

The following is a set of guidelines for contributing to onboardMD and its packages,
which are hosted in the Wearedragonfly organization on GitHub. These are mostly
guidelines, not rules. Use your best judgment, and feel free to propose changes
to this document in a pull request.

#### Table Of Contents

[What should I know before I get started?](#what-should-i-know-before-i-get-started)

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
connected to the repository's [SonarCloud](https://sonarcloud.io) project. Read
the [SonarCloud integration documentation](https://3.basecamp.com/4107684/buckets/9378454/documents/1874399417)
to get your workstation setup.

All code reviews follow the guidelines outlined in the [Code reviews](#code-reviews) section.

## Styleguides

### JavaScript styleguide

All JavaScript must adhere to [JavaScript Standard Style](https://standardjs.com/).

See the [JavaScript template repo](TBD) for example setup.

- Use the following naming convention:
  - All modules should use kebob casing (such as `my-profile`)
  - All classes should use pascal casing (such as `MyProfile`)
  - All factory functions should use pascal casing (such as `Authorize` as a middleware factory function)
  - All namespaces should use pascal casing (such as `import * as Path from 'path'`)

- Prefer the object spread operator `({...anotherObj})` to `Object.assign()`

- Prefer named exports over `default` exports unless there is a good reason
```js
// Use this:
export class MyClass {}

// Instead of:
export default class MyClass {}
```

- Inline exports with expressions whenever possible
```js
// Use this:
export class ClassName {

}

// Instead of:
class ClassName {

}
export ClassName
```

- Place requires in the following order:
  - Built in Node modules (such as `path`)
  - Third part modules (such as `lodash`, `express`)
  - LaunchFort modules (such as `@launchfort/std`, `@launchfort/xprss`)
  - Local modules (using relative paths)

- Place class properties in the following order:
  - Class methods and properties (methods and properties starting with `static`)
  - Constructor
  - Instance methods and properties

### TypeScript styleguide

All TyoeScript must adhere to [JavaScript Standard Style](https://standardjs.com/)
as well as the [TypeScript ESLint recommended](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin#usage) ruleset.

See the [TypeScript template repo](TBD) for example setup.

- Use the following naming convention:
  - All modules should use kebob casing (such as `my-profile`)
  - All classes should use pascal casing (such as `MyProfile`)
  - All factory functions should use pascal casing (such as `Authorize` as a middleware factory function)
  - All namespaces should use pascal casing (such as `import * as Path from 'path'`)

- Prefer the object spread operator `({...anotherObj})` to `Object.assign()`

- Prefer named exports over `default` exports unless there is a good reason
```js
// Use this:
export class MyClass {}

// Instead of:
export default class MyClass {}
```

- Inline exports with expressions whenever possible
```js
// Use this:
export class ClassName {

}

// Instead of:
class ClassName {

}
export ClassName
```

- Place requires in the following order:
  - Built in Node modules (such as `path`)
  - Third part modules (such as `lodash`, `express`)
  - LaunchFort modules (such as `@launchfort/std`, `@launchfort/xprss`)
  - Local modules (using relative paths)

- Place class properties in the following order:
  - Class methods and properties (methods and properties starting with `static`)
  - Constructor
  - Instance methods and properties

- Do not prefix interfaces with `I` unless necessary to improve clarity
```ts
// Use this:
export interface UserDto {}

// Instead of:
export interface IUserDto {}
```

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

### Documentation styleguide

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

When reviewing code keep these guidelines in mind:

- Keep an eye out for [naming conventions](#javascript-styleguide)

- Keep an eye out for code smells
  - abstraction leakage
  - functions too large
  - code that can't be well read or understood)

- Keep an eye out for best practices
  - returning proper HTTP status codes
  - wrapping promise-based Express middleware
  - promise chains missing a `.catch(...)`