---
layout: default
title: Inverted Index Compression
---

As mentioned in lecture, we'd like to compress the inverted index for two
reasons:

- smaller! the postings file will be very large
- faster! accessing a fewer number of pages is preferrable

The type of data that our postings file has is all integers; thus, we need some
sort of integer compression method. Besides that, we'd like random access into
the postings file. We definitely don't want to have to decompress the whole
file to get information from a single term!

Due to Zipf's law, many of the integers that we'll be storing are very low
numbers. Most terms only occur a very small number of times. Additionally, in
the inverted lists, we can store the distance between the sequential docIDs
rather than the docIDs themselves. This adds more small numbers to our postings
file. This trick is known as *gap encoding*.

In any event, we'll have a very skewed distribution of integers that we'd like
to compress. We'll talk about three different types of compression that can
achieve this:

- unary encoding
- $\gamma$-encoding
- $\delta$-encoding

With compression, instead of writing out strings representing numbers (like
"1624"), or fixed byte-width chunks (like a 4-byte integer as "00000658"), we
are writing raw binary numbers. When the representation ends, the next number
begins. **There is no fixed width, or length, of the number representations**.

## Unary

Unary encoding is the simplest method. To write the integer $k$, we simply
write $k-1$ zeros followed by a one. The one acts as a delimiter and lets us
know when to stop reading:

$$1\rightarrow 1$$
$$2\rightarrow 01$$
$$3\rightarrow 001$$
$$4\rightarrow 0001$$
$$5\rightarrow 00001$$
$$19\rightarrow 0000000000000000001$$

Note that we can't encode the number zero -- this is true of the other two
compression methods as well.

## Gamma

To encode a number with $\gamma$-encoding, first simply write the number in
binary. Let $k$ be the number of bits in your binary string. Prepend $k-1$ zeros
to the binary number:

$$1\rightarrow 1$$
$$2\rightarrow 010$$
$$3\rightarrow 011$$
$$4\rightarrow 00100$$
$$5\rightarrow 00101$$
$$19\rightarrow 000010011$$
$$47\rightarrow 00000101111$$

To decode, read and count $k$ zeros until you hit a one. Read the one and
additional $k$ bits in binary. Note that all $\gamma$ codes will have an odd
number of bits.

## Delta

In short, $\delta$-encoding is $\gamma$-encoding a number and then
$\gamma$-encoding the unary prefix (including the one):

$$1\rightarrow 1\rightarrow 1$$
$$2\rightarrow 010\rightarrow 0100$$
$$3\rightarrow 011\rightarrow 0101$$
$$4\rightarrow 00100\rightarrow 01100$$
$$5\rightarrow 00101\rightarrow 01101$$
$$19\rightarrow 000010011\rightarrow 001010011$$
$$47\rightarrow 00000101111\rightarrow 0011001111$$

To decode, decode the $\gamma$ code at your start position to get an integer
$k$. Write a one, and then read the next $k+1$ bits in binary (including the
one you wrote).

As you can see, the $\delta$ compression at first starts off to have more bits
than the $\gamma$ encoding, but eventually becomes more efficient as the
numbers get larger. It probably depends on your dataset (the distribution of
integers) as to which compression method would be better.
