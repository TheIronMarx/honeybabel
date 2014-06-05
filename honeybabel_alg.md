This document is mostly initial thoughts on the inner-workings of the algorithm. It's rather informal and certainly tentative, but I'd prefer to keep all of these ideas on the record.

---

# Goals of algorithm
	* Every set of honeywords generated must have the same pattern such that the output of the algorithm does not hint at the characteristics of the password.
	* Sweetwords must be typo-resistant.
	* Minimize or eliminate external libraries dependencies.
	* Language-agnostic -- It would be nice to have pseducode in several different styles, and several different implementations including C, Perl, Java, Python, and R.

# High-level design
	* Given an input password, this algorithm should identify its characteristics and produce chaffing accordingly.
	* For a given k>30 sweetwords to generate, k/n=5 buckets will be created. n-1 buckets will contain 5 sweetwords. 1 bucket will contain the sugarword and 4 sweetwords. Each bucket's honeywords will have a similar pattern through identical chaffing strategies.
		* Perhaps buckets should be jagged based on RNG.
	* In addition to the characteristics, their ratio in respect to the length of the password, and each of their densities throughout the password will matter to the generation.
		* I wish I could remember what the hell I meant here.
	* It would be nice to avoid a dictionary all together, but this may be impossible. Regardless, dictionary should be comprehensive -- only required during honeyword generation, never during authorization.
	* RNG where possible and with several layers of redundancies. Use trusted RNG.

* Characteristic [zero, one, two, three, four, five...]
 This refers to the number of numeric digits in the password.

* Characteristic [A, B, C, D, E...]
	This refers to the number of non-alphanumeric characters in the password.

* Characteristic [alpha, beta, gamma, delta, epsilon, zeta...]
	This refers to the number of words identified in the password.

* Characteristic [red, orange, yellow, green, blue, indigo, violet]
	This refers to the number of alphanumeric characters not identified as a word or "noise."

As a rough example of applying characteristics to a password, the password *dingdongdaddy* has a category of zero-A-delta-red. The password *123fastchthn!!* has a category of three-C-beta-indigo.

Characteristics need to be named in a manner that makes seeing which category a string is easy. Essentially, a string's determined category and chaffing strategy need to be human-readable for testing and verification purposes.

There will probably need to be more characteristics or hierarchical expansion of these characteristics.

---

An order to the characteristic tests may also matter due to a number possibly representing a letter or word in a password. If a user's password is *2cool4school935*, it would be more beneficial to test for identifiable words in the password first (assuming, of course, we can detect 2 as to or too and 4 as for) and then stray numbers at the end in a latter test.

After a password's respective category (collection of characteristics) is calculated, we should be able to choose one of several applicable chaffing strategies and fill a bucket with chaff.

# The Algorithm

1. Input: A password and number of honeywords desired.
	* Number of honeywords should be factor of five for simplicity's sake. At least until somebody can prove to me that static buckets isn't a good idea.
* Generate buckets such that each bucket has five possible honeywords
* Place password in a bucket
* Fill bucket with chaff from appropriate strategy
* Fill other buckets with respective chaffing strategies
* Shuffle final set of honeywords in from all buckets.
* Search for sugarword in set and record index
* Output: A set of honeywords and index of sugarword in the set.
