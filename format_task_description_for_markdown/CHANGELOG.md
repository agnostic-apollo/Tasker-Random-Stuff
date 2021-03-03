# Changelog

All notable changes to this project will be documented in this file.

**Version Number Format:** `major.minor.patch`  
**Release Date Format:** `yyyy-mm-dd`  

**Types of Changes:**
- **Added** for new features.
- **Changed** for changes in existing functionality.
- **Deprecated** for soon-to-be removed features.
- **Removed** for now removed features.
- **Fixed** for any bug fixes.
- **Security** in case of vulnerabilities.
##


## [0.4.0] - 2021-03-04

### Added
- Added support for splitting of action parameters on multiple lines for Tasker `v5.12.3-beta`.
- Added support for splitting of `Plugin` action parameters.
- Added the `Format Task Description For Markdown On Clipboard Copy` profile which can be imported to automatically format description when user exports a task or profile description to clipboard.
- Added future support for [Instant Profiles](https://tasker.joaoapps.com/userguide/en/faqs/faq-other.html#instant) description which have two entry tasks instead of an entry and exit task. The Tasker `v5.12.3-beta` currently still has the bug where it labels the second entry task with `Exit` instead of `Enter`, which will hopefully be fixed in future so that both tasks are labeled with `Enter`, which will require this update to work.

### Removed
- Removed dependency on internal tasker `TCUJV_CM_TaskerUtils_GetIndexOfStringInArray` java function.

### Fixed
- Fixed bug where task parameters received via `%par1` were not being parsed properly due to a typo in a `Variable Set` action.
- Fixed bug for task properties likely not handled properly because of forgetting to enable `Do Maths` toggle for a `Variable Set` action.
- Fixed bug where `Continue Task After Error` action parameter was not being split, since its not part of action parameters.


## [0.3.0] - 2020-09-15

### Added
- Added support for formatting exported profile description.
- Added support to allow force splitting of actions even if parameter name is repeated in the action description, like for the multiple `Param` parameters of `Java Function` actions.

### Changed
- Changed `Java Function` actions to use dynamic class and method names using tasker variables for easier fixes in future in case the task no longer remains compatible with the latest tasker version.

### Fixed
- Fixed bug where last action of task was not being split on multiple lines.
- Fixed bug where actions were not being split on multiple lines if a parameter had regex special characters in their name.


## [0.2.0] - 2020-04-15

### Added
- Added support to split action parameters on multiple lines.


## [0.1.0] - 2020-04-13

`-`
##


[0.4.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/compare/v1.5.0...v1.6.0
[0.3.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/compare/v1.4.0...v1.5.0
[0.2.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/compare/v1.2.0...v1.3.0
[0.1.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases
