# Glossary
To provide a destinct set of language which can be interpreted in one way only we introduce some key words which have a clearly defined meaning in the context they are used for.
These key words are defined below and are bound to their containing context which allows for overriding of meaning based on the given context. 


The use of a specific key word is indicated by all-capital letters.
So does e.g. *SHOULD* translate to its meaning defined here where as *should* would be interpreted as its commonly known meaning.


## General
There are general wordings we use within our documents and means of communication.

**MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, OPTIONAL**

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL are always interpreted as described in [RFC 2119](<http://www.ietf.org/rfc/rfc2119.txt>).

## Versioning
In the context of versioning and changes on the project sources the following key words are used.

**ARCHITECTURE**

ARCHITECTURE changes reflected by versioning might be onw of the following:

- Major changes in architecture such as the introduction or removal of a former core component such as an *container*
- Changes of external interfaces breaking BACKWARDS COMPATIBILITY

**MAJOR**

Changes which have a major influence on internal workflows and structure. These might be:

- Changes of internal interfaces breaking BACKWARDS COMPATIBILITY
- Changes to internal component structures

**MINOR**

The introduction of new features or the change of any interface, both **not** breaking BACKWARDS COMPATIBILITY might be considered a MINOR change.

**BUILD**

Any new recreation of a working instance of the project (build) which **only** contains bugfixes is called BUILD. 

**BACKWARDS COMPATIBILITY, BACKWARDS COMPATIBLE**

Defines that changes do not change the way structures depending on the changed sources interact with it. E.g. a changed interface is BACKWARDS COMPATIBLE if it only adds to, but does not change or remove from its behavioral definition.
