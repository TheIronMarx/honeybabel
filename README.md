# HoneyBabel

A honeywords generation algorithm for legacy-UI passwords.

## Terminology
**Honeywords** - The algorithm introduced by Jules and Rivest wherein false passwords, which are meant to fool an adversary, are stored in a set with a user's genuine password on an authorization system.

**sweetword** - Strings stored with the password that are not the password. This project generates these.

**sugarword** - A user's genuine password.

**honeyword** - Either a sweetword or the sugarword.

**legacy-UI** - Traditional password schema with no restrictions (intentionally) designed to improve sweetword generation.

**modern-UI** - A password schema wherein a user is forced to abide by a password schema which allows for superior chaffing strategies for sweetword generation.

**chaff** - An alteration of the original. It may either be the characters which have changed, or it may refer to words which include (the first definition of) chaff.

**chaffing strategy** - A function in which chaff is produced using a single, specific algorithm such as chaffing by numbers.

## Abstract

The 2013 paper written by Ari Juels and Ronald L. Rivest, found  [here](http://people.csail.mit.edu/rivest/honeywords/paper.pdf), introduces a fascinating way of detecting offline brute-force password-cracking and masquerading. In a similar style to honeypots, honeywords are stored with the user's password. Should the username/password files be compromised, an adversary is presented with honeywords in addition to a user's genuine password. If this false password is entered into the authentication system with the username, a flag is raised indicating that someone has compromised the files and is attempting to masquerade as the user.

Despite being a clever scheme, several problems of Juels and Rivest's Honeywords still remain before an implementation can be successfully deployed. The most pertinent of these problems is the honeywords generation. Given a password, this algorithm attempts to create a set of similar-yet-different honeywords of which the adversary will be forced to guess the genuine password. Modern-UI, which forces users to adhere to a more strict standard of creating passwords as per the paper, successfully eliminates the need for this algorithm. However, the logistics and stigma behind forcing users to adhere to a particular pattern of passwords can be infeasable or undesirable. Therefore, this algorithm will attempt to accept *any* given password and produce a set of corresponding honeywords designed to appear as feasible passwords.

## Roadmap
Eventually, somebody's going to come along and implement honeywords as a serverside software. Maybe it will be me, maybe not. Either way, it won't be long before they realize the difficulty of the sweetwords generation problem. Hopefully, they will search for it and, hopefully, this repository will be the first result. My goal for this HoneyBabel algorithm is to be the de facto, first, last, and best means of generating sweetwords.

### Done

### Doing

### Will Do

### Won't Do
* Encryption. Returned words are not encrypted. This is the job of the Honeywords developer. This is not authentication software, this is a tool for a tool which will augment authentication software.

## How Can You Help?
A project like this needs tight management. If you're interested in the project, that's great! Contact me first. Tell me what you're all about and we can discuss what you'd like to work on. Sound too formal? Sorry about that! It won't be. This is a passion project of mine and I want to have fun (with others!) doing it. That being said, due to the nature and importance of the project, I can't let any aspect of this escape my review or criticism. I hope you feel the same way as well.

## Why HoneyBabel?

# Gratuity
A tremendous **"THANK YOU!"** is in order to everyone who has aided in the HoneyBabel project over the months! Which is, so far, not many.

Thanks, jtan189!

# The Algorithm
The general flow of the algorithm is

1. Receive string input of password

2. Determine category or categories of string

3. Choose number of buckets

4. Place password in bucket and produce chaff to fill bucket

5. Fill remaining buckets with respective strategy's chaff

6. Shuffle set of honeywords and locate password

7. Return set of honeywords and index of sugarword

## A Diagram
