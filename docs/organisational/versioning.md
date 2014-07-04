# Versioning

To have a more readable and understandable versioning we will start to implement a certain structure from release of version `1.0.0.0` on.

This structure will be based on the thoughts illustrated by the example below:

`1` = ARCHITECTURE (Major changes in architecture e.g. external interfaces)

`.0` = MAJOR release (Changes on e.g. internal interfaces, internal component structures)

`.0` = MINOR release (Features including interface enhancements)

`.0` = BUILD number (Bugfixes)

As you can see every digit of the version number has its own meaning of severity related to it.
These severity levels are further defined within our [glossary](glossary.md). There you might check which changes
should increment which digit.

Basically every change related to a certain severity level MUST increment the related version number digit. There are
some exceptions where changes might also increment digits of a *higher* severity.
These exceptions mostly boil down to breaking BACKWARDS COMPATIBILITY which *always* MUST result in changes in either
ARCHITECTURE or MAJOR severity version number digits.

## Some examples

- All applications using external interfaces MUST work within the same ARCHITECTURE release
- All components using internal interfaces MUST work within the same MAJOR release
- New features MUST increment at least (depending on its influence on existing interfaces) the MINOR release number 
- A new build including only bugfixes MUST increment the BUILD number