---
title: "Encrypting Your Grandma's Password Using the Affine Cipher"
date: 2017-12-06T15:18:47-05:00
draft: false

featuredImage: "images/grandmameme.jpg"
categories: ["cryptography"]
tags: ["cryptography", "mathematics"]
author: "Nisarga Patel"
---

One day you noticed your grandma was typing her passwords in a text document and referring to them when trying to log into popular websites. Wanting to teach her about the importance of security you decided to give her a brief introduction to cryptography. The first cipher you decided to teach was the [affine cipher](https://en.wikipedia.org/wiki/Affine_cipher).

## Introduction to the Affine Cipher

The affine cipher is a monoalphabetic substitution cipher, there isn't really all that much to it and anyone can learn it given a few minutes. All one needs is an alphabet of size $m$ (in our case the English alphabet is of length 26) and two keys $a$ and $b$ with the value of $a$ being coprime to the alphabet-size $m$. 

### What makes two numbers coprime?

Two numbers are coprime if the only number that can divide them both is 1. For example, 26 and 3 are coprime because only 1 can divide both of them, but 26 and 4 are not coprime as 2 can divide both 26 and 4.

### How do you encrypt something?

To encrypt a single letter using the affine cipher first you must map the alphabet to indices 0 to $m - 1$ this means 0 corresponds to A, 1 to B and so on. In our case $m - 1 = 25$. We use modular arithmetic to ensure that the result always is between 0 and 25.

The formula to encrypt a character is:
$$
    E(x) = ax + b\;mod\;m
$$

In this case the $x$ variable is the index of the letter you want to encrypt.

**Let's do an example:**

Encrypt the letter $a$ using the affine cipher with $a = 3$, $b = 20$ and $m = 26$

$$
    E(0) = 3*0 + 20\;mod\;26
$$

The answer after solving for $E(0)$ is $20$. The 21st letter of the alphabet is $u$ which corresponds to the 20th index because out alphabet starts at index 0.

### How do you decrypt?

To decrypt, grandma first needs to understand the concept of a modular multiplicative inverse. To decrypt we must first find $a^{-1}$ which is the modular multiplicative inverse of $a$. We already established that $a$ and $m$ are coprime, in this context we must find $a^{-1}$ such that:
$$
   aa^{-1}\;\equiv\;1\;mod\;m
$$

**Let's do an example**:

Find the modular multiplicative inverse $a^{-1}$ given $a = 3$, and $m = 26$.

$$
   3*a^{-1}\;\equiv\;1\;mod\;26
$$

What number multiplied by 3 gives a remainder of 1 when divided 26? We know that $9 * 3 = 27$ and when 27 is divided by 26 the remainder is 1 therefore $a^{-1} = 9$. 

Note this is a very brute force way of finding the modular multiplicative inverse later we will learn about the [Extended Euclidean Algorithm](https://en.wikipedia.org/wiki/Modular_multiplicative_inverse#Extended_Euclidean_algorithm) which is a computational method to get the modular inverse. 

Now that we know what the modular multiplicative inverse we can use the affine formula for decryption which is:

$$
    D(x) = a^{-1} (x - b)\;mod\;m
$$

Given our original example of $a = 3$, $b = 20$ and $m = 26$ and now knowing that the modular multiplicative inverse of 3 is 9. We can decrypt $x = 20$ which corresponds to the letter $u$ back to the letter $a$ which correponds to the index of 0.

$$
    D(0) = 9*(20 - 20)\;mod\;26
$$

After plugging in the correct values we get the correct plaintext of 0.

### Why encrypting your grandma's password using the affine cipher is a bad idea

Although it is definitely better than storing passwords in a text file, the affine cipher is a weak cipher for encrypting confidential data. There are multiple very well documented methods an attacker can use to crack encrypted affine ciphertext some of them include: [frequency analysis](https://en.wikipedia.org/wiki/Frequency_analysis), brute force, as well as guessing. Knowing the plaintext values of just two characters is also enough to crack the code as one can then write a system of equations and solve for the keys $a$ and $b$.

### Conclusion

This is one of a line of many posts regarding cryptography that I will be posting, I hope you enjoyed! If you really want a good way to store passwords I recommend looking into the theory behind hashing and salting passwords, perhaps that will also be covered in a future post.