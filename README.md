<h1>Diceware Passphrase Generator</h1>

An implementation of the [Diceware](https://theworld.com/~reinhold/diceware.html) method for creating passphrases based on [libsodium.js](https://github.com/jedisct1/libsodium.js).

<h2>What Is A Passphrase?</h2>

A passphrase is a memorized secret consisting of a sequence of words or other text that a claimant uses to authenticate their identity. A passphrase is similar to a password in usage, but is generally longer for added security. Randomly-generated passphrases offer a major security upgrade over user-chosen passwords.

<h2>What Is Diceware?</h2>

Diceware is a technique that uses dice to produce random text for passphrases and other uses. The Diceware method provides an easy way to create strong passphrase that are easy to remember.

For each word in the passphrase, five rolls of a six-sided die are required. The numbers from 1 to 6 that come up in the rolls are assembled as a five-digit number. That number is then used to look up a word in a word list. By generating several words in sequence, a lengthy passphrase can be constructed randomly.

<h2>Generating Dice Rolls</h2>

`create_passphrase()` generates an unpredictable random number between 1 and 6 using the `randombytes_uniform()` function from **libsodium.js**.

The `randombytes_uniform()` function returns an unpredictable value between 0 and upper_bound (excluded). Unlike randombytes_random() % upper_bound, it guarantees a uniform distribution of the possible output values even when upper_bound is not a power of 2.

<h2>Diceware Word List</h2>

The script uses a [EFF's Long Wordlist](https://www.eff.org/files/2016/07/18/eff_large_wordlist.txt) (contain 7776 words) that was converted into a JavaScript file (dictionary) for easier lookup.

<h2>Usage (in a web browser)</h2>

```html
  <div id="passphrase"></div>

  <script>

    window.sodium = {
      onload: function (sodium) {
        document.getElementById('passphrase').innerText = create_passphrase(EFF_LARGE_WORDLIST, 10);
      }
    };

  </script>

  <script src="eff_large_wordlist.js"></script>
  <script src="index.js"></script>
  <script src="sodium.js" async></script>
```

<h2>Authors</h2>

* Serhiy Guryev, https://github.com/53rhiy

<h2>Links And References</h2>

* [The Diceware Passphrase Home Page](https://theworld.com/~reinhold/diceware.html)
* [The Diceware Passphrase FAQ](https://theworld.com/~reinhold/dicewarefaq.html)
* [EFF Dice-Generated Passphrases](https://www.eff.org/dice)
* [Deep Dive: EFF's New Wordlists for Random Passphrases](https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases)
* [libsodium.js](https://github.com/jedisct1/libsodium.js): libsodium compiled to Webassembly and pure JavaScript, with convenient wrappers
