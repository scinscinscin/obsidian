# Alphabets

An alphabet is a finite non-empty set of symbols, usually denoted by sigma sign.
 - Latin 
 - Lowercase greek alphabet
 - Special symbols

A string over an alphabet is a finite sequence of symbols from the alphabet. The length of a string is the number of symbols, including duplication of a string. It is denoted with |w| where w is the string.

A string may sometimes be delimited by single or double quotes, which are not a part of the string. The empty string is a string that contains no symbols and has a length of zero. A substring of a string is a consecutive subsequence of a string. A string A is a prefix of a string B if A is a substring of B and A begins B. The same rules apply for a suffixes but in the opposite direction.

An alphabetical ordering of an alphabet is a fixed ordering of its symbols. The alphabetical ordering of strings over an alphabet is a linear sequencing of all such strings. String a comes before string B if the first symbol of a is alphabetically before the first symbol of B. 

The lexicographical ordering of strings over an alphabet is the linear sequencing of all such strings where short strings come first. When two strings have equal length, the ordering is alphabetical. `ba` comes before `aaa`

The reversal of a string w is the sequence of the symbols for w but in reverse order. If the string is equal to its reverse, then a string is a palindrome.

The concatenation of strings means linking strings in sequence. The concatenation of strings s and t is denoted using `s*t`, or simply st. The concatenation operation is not commutative but it is associative.

The n'th power of a string w is the concatenation of n w's.

# Language

A language is a set of strings over an alphabet. The size of the language is the size of the set. It may be finite or infinite. The empty language is the language that contains no strings. 

**Operations on languages**

Languages are sets, thus any set operation can be performed on a language.

The concatenation of two languages is the set of all strings which are concatenations of a string in language 1 and a string in language 2. A language L to the n'th power is the set of all concatenations of n strings from L. Similarly, the alphabet can be raised to the n'th power, where sigma ^ n is the set of all strings over sigma that is of length n.

The kleene-star or kleene-closure of the alphabet sigma is the union of all the powers of E. Sigma* is the set of all strings of all lengths over sigma. The positive closure E+ of E is the set of all non-empty strings over E. E+ = E* - { empty string }.

The kleene-star of a language is the union or all powers of L. The complement of a language L over alphabet sigma is E* - L. E* and the empty language are complements of each other. Remember that E* the empty string, which is still a string that is part of the language. An empty language contains no strings *at all*.

The reversal of a language L is the set of all reversals of strings in L..