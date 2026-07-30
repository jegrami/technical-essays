# How Your Computer Verifies Your Identity (Passwords, PINs, and Fingerprints)

Your raw password is not stored on your device or on any server, at least not in a form anyone could read. When you first set a password, the system runs it through a technique called _hashing_. Hashing uses a special kind of algorithm to transform your password into a fixed string of characters. The system saves this string, called a *hash*, and discards the original password. 

Because hashing is designed to work in only one direction, there is no practical way to turn a hash back into the password that created it. This is also why a forgotten password can only be reset, never recovered. The system never kept your original password, and the hash it stored cannot simply be reversed to reveal it.

Every time you log in afterward, your device runs the password you type through the same hashing algorithm and compares the resulting hash with the one it has stored. If the two hashes match, you're in. 

A PIN looks similar to a password but works on a different principle. A four-digit PIN has only ten thousand possible combinations, few enough that a hacker could use a computer to try them all in seconds. A PIN stays secure anyway, because it only gets checked on **the one device it belongs to**. After a handful of wrong guesses, that device locks itself for longer and longer stretches, and eventually demands a full account login or wipes itself. A password protecting an online account does not have that same built-in delay, so it needs to be long and complex enough to resist rapid guessing from anywhere on the internet. A PIN trades length for a lockout, and a password trades a lockout for length.

Fingerprint and face recognition work by comparison too, not by storing a photo. When you first scan your fingerprint or face, the device converts it into a mathematical pattern, a set of measurements describing unique features, such as the arrangement of the "ridges and valleys" in your fingerprint or the distances between key points on your face. Every later scan is converted the same way and checked against that saved pattern. The comparison happens inside a protected part of the device itself, which is why it still works with no internet connection.

Many accounts today are cloud-linked. When you log into a Windows PC with a Microsoft account, a Mac with an Apple ID, or a phone with a Google account, the device checks your login against that company's servers. This is what lets your settings and files follow you to a new device. Most devices still keep a local copy of your login so you can get in while offline, but full verification needs a connection now and then.

