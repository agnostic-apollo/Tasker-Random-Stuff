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


[0.3.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/compare/v1.4.0...v1.5.0
[0.2.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/compare/v1.2.0...v1.3.0
[0.1.0]: https://github.com/agnostic-apollo/Tasker-Random-Stuff/releases
