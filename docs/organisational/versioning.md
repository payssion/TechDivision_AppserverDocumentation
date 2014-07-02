# Versioning

To have a more readable and understandable versioning we will start to implement a certain structure from release of version `1.0.0.0` on.

This structure will be based on the thoughts illustrated by the example below:

`1` = ARCHITECTURE (Major changes in architecture e.g. external interfaces)

`.0` = MAJOR release (Changes on e.g. internal interfaces, internal component structures)

`.0` = MINOR release (Features including interface enhancements)

`.0` = BUILD number (Bugfixes)

As you can see every digit of the version number has its own meaning of severity related to it.
Every change within the related severity breaking BACKWARDS COMPATIBILITY MUST increment the version.

The mentioned severity levels are also defined within our [glossary](glossary.md).

## Some examples

- All applications using external interfaces MUST work within the same ARCHITECTURE release
- All components using internal interfaces MUST work within the same MAJOR release
- New features MUST increment at least (depending on its influence on existing interfaces) the MINOR release number 
- A new build including only bugfixes MUST increment the BUILD number