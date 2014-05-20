# HoneyBabel

A honeywords generation algorithm for legacy-UI passwords.

## Terminology
**Honeywords** - The algorithm introduced by Jules and Rivest wherein false passwords, which are meant to fool an adversary, are stored in a set with a user's genuine password on an authorization system.

**Sweetword** - Strings stored with the password that are not the password. This project generates these.

**Sugarword** - A user's genuine password.

**Honeyword** - Either a sweetword or the sugarword.

**Legacy-UI** - Traditional password schema with no restrictions (intentionally) designed to improve sweetword generation.

**Modern-UI** - A password schema wherein a user is forced to abide by a password schema which allows for superior chaffing strategies for sweetword generation.

## Abstract

The 2013 paper written by Ari Juels and Ronald L. Rivest, found  [here](http://people.csail.mit.edu/rivest/honeywords/paper.pdf), introduces a fascinating way of detecting offline brute-force password-cracking and masquerading. In a similar style to honeypots, honeywords are stored with the user's password. Should the username/password files be compromised, an adversary is presented with honeywords in addition to a user's genuine password. If this false password is entered into the authentication system with the username, a flag is raised indicating that someone has compromised the files and is attempting to masquerade as the user.

Despite being a clever scheme, several problems still remain before an implementation can be successfully deployed. The most pertinent of these problems is the honeywords generation. Given a password, this algorithm attempts to create a set of similar-yet-different honeywords of which the adversary will be forced to guess the genuine password. Modern-UI, which forces users to adhere to a more strict standard of creating passwords as per the paper, successfully eliminates the need for this algorithm. However, the logistics and stigma behind forcing users to adhere to a particular pattern of passwords can be infeasable or undesirable. Therefore, this algorithm will attempt to accept *any* given password and produce a set of corresponding honeywords designed to appear as feasible passwords.

## Roadmap
Eventually, somebody's going to come along and implement honeywords as a serverside software. Maybe it will be me, maybe not. Either way, it won't be long before they realize the difficulty of the sweetwords generation problem. Hopefully, they will search for it and, hopefully, this repository will be the first result. My goal for this algorithm is to be the de facto, first, last, and best means of generating sweetwords.
