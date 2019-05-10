## Description

A type of [PRNG state compromise extension
attack](PRNG_state_compromise_extension_attack "wikilink") in which an
attacker compromises the state of the PRNG at some arbitrary time t.
From t, all future and past states of the PRNG become vulnerable to
attack [1](http://www.schneier.com/paper-prngs.pdf).

## Examples

In 1999, Reliable Software Technologies was able to crack the card
shuffling algorithm used in an online Texas Hold 'Em card game (using
software developed by ASF Software Inc.). By identifying the seed value
used by ASF's PRNG algorithm, Reliable was able to identify how the
cards would be shuffled and, hence, the contents of the deck
[2](http://www.developer.com/tech/article.php/10923_616221_1?o=0).

-----