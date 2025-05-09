# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- Bump `@metamask/base-controller` from ^8.0.0 to ^8.0.1 ([#5722](https://github.com/MetaMask/core/pull/5722))

## [7.0.3]

### Changed

- Bump `@metamask/base-controller` from `^7.0.2` to `^8.0.0` ([#5079](https://github.com/MetaMask/core/pull/5079)), ([#5135](https://github.com/MetaMask/core/pull/5135)), ([#5305](https://github.com/MetaMask/core/pull/5305))

## [7.0.2]

### Changed

- Bump `@metamask/base-controller` from `^7.0.1` to `^7.0.2` ([#4862](https://github.com/MetaMask/core/pull/4862))

## [7.0.1]

### Changed

- Bump TypeScript from `~4.9.5` to `~5.2.2` and set `moduleResolution` option to `Node16` ([#3645](https://github.com/MetaMask/core/pull/3645), [#4576](https://github.com/MetaMask/core/pull/4576), [#4584](https://github.com/MetaMask/core/pull/4584))

### Fixed

- Produce and export ESM-compatible TypeScript type declaration files in addition to CommonJS-compatible declaration files ([#4648](https://github.com/MetaMask/core/pull/4648))
  - Previously, this package shipped with only one variant of type declaration
    files, and these files were only CommonJS-compatible, and the `exports`
    field in `package.json` linked to these files. This is an anti-pattern and
    was rightfully flagged by the
    ["Are the Types Wrong?"](https://arethetypeswrong.github.io/) tool as
    ["masquerading as CJS"](https://github.com/arethetypeswrong/arethetypeswrong.github.io/blob/main/docs/problems/FalseCJS.md).
    All of the ATTW checks now pass.
- Remove chunk files ([#4648](https://github.com/MetaMask/core/pull/4648)).
  - Previously, the build tool we used to generate JavaScript files extracted
    common code to "chunk" files. While this was intended to make this package
    more tree-shakeable, it also made debugging more difficult for our
    development teams. These chunk files are no longer present.

## [7.0.0]

### Changed

- **BREAKING:** Bump minimum Node version to 18.18 ([#3611](https://github.com/MetaMask/core/pull/3611))
- Bump `@metamask/base-controller` to `^6.0.0` ([#4352](https://github.com/MetaMask/core/pull/4352))

## [6.1.1]

### Changed

- Bump `@metamask/base-controller` to `^5.0.2` ([#4232](https://github.com/MetaMask/core/pull/4232))

## [6.1.0]

### Added

- Add `resetViewed` method to `AnnouncementController` to reset the `isShown` status for all announcements ([#4088](https://github.com/MetaMask/core/pull/4088))

## [6.0.1]

### Fixed

- Fix `types` field in `package.json` ([#4047](https://github.com/MetaMask/core/pull/4047))

## [6.0.0]

### Added

- **BREAKING**: Add ESM build ([#3998](https://github.com/MetaMask/core/pull/3998))
  - It's no longer possible to import files from `./dist` directly.

### Changed

- **BREAKING:** Bump `@metamask/base-controller` to `^5.0.0` ([#4039](https://github.com/MetaMask/core/pull/4039))
  - This version has a number of breaking changes. See the changelog for more.

## [5.0.2]

### Changed

- Bump `@metamask/base-controller` to `^4.1.1` ([#3760](https://github.com/MetaMask/core/pull/3760), [#3821](https://github.com/MetaMask/core/pull/3821))

## [5.0.1]

### Changed

- Bump `@metamask/base-controller` to `^4.0.1` ([#3695](https://github.com/MetaMask/core/pull/3695))

## [5.0.0]

### Changed

- **BREAKING:** Bump `@metamask/base-controller` to ^4.0.0 ([#2063](https://github.com/MetaMask/core/pull/2063))
  - This is breaking because the type of the `messenger` has backward-incompatible changes. See the changelog for this package for more.

## [4.0.3]

### Changed

- Bump dependency on `@metamask/base-controller` to ^3.2.3 ([#1747](https://github.com/MetaMask/core/pull/1747))

## [4.0.2]

### Changed

- Update TypeScript to v4.8.x ([#1718](https://github.com/MetaMask/core/pull/1718))

## [4.0.1]

### Changed

- Bump dependency on `@metamask/base-controller` to ^3.2.1

## [4.0.0]

### Changed

- **BREAKING:** Bump to Node 16 ([#1262](https://github.com/MetaMask/core/pull/1262))

## [3.0.0]

### Removed

- **BREAKING:** Remove `isomorphic-fetch` ([#1106](https://github.com/MetaMask/controllers/pull/1106))
  - Consumers must now import `isomorphic-fetch` or another polyfill themselves if they are running in an environment without `fetch`

## [2.0.1]

### Changed

- Rename this repository to `core` ([#1031](https://github.com/MetaMask/controllers/pull/1031))
- Update `@metamask/controller-utils` package ([#1041](https://github.com/MetaMask/controllers/pull/1041))

## [2.0.0]

### Changed

- **BREAKING:** Migrate to BaseControllerV2 ([#959](https://github.com/MetaMask/controllers/pull/959))
  - The announcement controller now extends `BaseControllerV2` rather than `BaseController`, which includes the following changes:
    - The constructor now accepts a single "args" object rather than positional parameters.
    - A restricted controller messenger instance must be passed into the constructor.
    - The controller configuration has been replaced by an `allAnnouncements` constructor parameter.
    - The following properties previously inherited from `BaseController` are no longer present:
      - `defaultConfig`
      - `defaultState`
      - `disabled`
      - `config`
      - `state`
    - The following methods previously inherited from `BaseController` are no longer present:
      - `configure`
      - `notify`
      - `subscribe`
      - `unsubscribe`
      - `update`
    - The `name` property is now readonly.

## [1.0.1]

### Changed

- Relax dependency on `@metamask/base-controller` (use `^` instead of `~`) ([#998](https://github.com/MetaMask/core/pull/998))

## [1.0.0]

### Added

- Initial release

  - As a result of converting our shared controllers repo into a monorepo ([#831](https://github.com/MetaMask/core/pull/831)), we've created this package from select parts of [`@metamask/controllers` v33.0.0](https://github.com/MetaMask/core/tree/v33.0.0), namely:

    - Everything in `src/announcement`

    All changes listed after this point were applied to this package following the monorepo conversion.

[Unreleased]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@7.0.3...HEAD
[7.0.3]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@7.0.2...@metamask/announcement-controller@7.0.3
[7.0.2]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@7.0.1...@metamask/announcement-controller@7.0.2
[7.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@7.0.0...@metamask/announcement-controller@7.0.1
[7.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@6.1.1...@metamask/announcement-controller@7.0.0
[6.1.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@6.1.0...@metamask/announcement-controller@6.1.1
[6.1.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@6.0.1...@metamask/announcement-controller@6.1.0
[6.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@6.0.0...@metamask/announcement-controller@6.0.1
[6.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@5.0.2...@metamask/announcement-controller@6.0.0
[5.0.2]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@5.0.1...@metamask/announcement-controller@5.0.2
[5.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@5.0.0...@metamask/announcement-controller@5.0.1
[5.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@4.0.3...@metamask/announcement-controller@5.0.0
[4.0.3]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@4.0.2...@metamask/announcement-controller@4.0.3
[4.0.2]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@4.0.1...@metamask/announcement-controller@4.0.2
[4.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@4.0.0...@metamask/announcement-controller@4.0.1
[4.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@3.0.0...@metamask/announcement-controller@4.0.0
[3.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@2.0.1...@metamask/announcement-controller@3.0.0
[2.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@2.0.0...@metamask/announcement-controller@2.0.1
[2.0.0]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@1.0.1...@metamask/announcement-controller@2.0.0
[1.0.1]: https://github.com/MetaMask/core/compare/@metamask/announcement-controller@1.0.0...@metamask/announcement-controller@1.0.1
[1.0.0]: https://github.com/MetaMask/core/releases/tag/@metamask/announcement-controller@1.0.0
