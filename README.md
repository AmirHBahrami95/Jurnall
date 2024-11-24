# Jurnall - Text Editor with Encryption

Encrypt/Decrypt text files in a session, while only entering password once for each session
Each time you write a text file, it's encrypted using a password String kept in the heap memory

## How it works

When user registers for the first time, after entering his password:

1- The passwd gets hashed (h0)
2- A Salts is generated (salt)
3- __Salt__ + __h0__ are hashed (h2)
4- __h2__ gets saved in a file called hash.h2 (you can check it under ${USER.HOME}/jurnall/${JURNALL_USER}/)
5- The program uses __h0__ (not h2) for encryption of text files

###  Why use h0 for encryption instead of h2 ?

The file which contains __h2__ is stored permanently, whereas __h0__ only exists in your jvm's heap memory as long
as the program is on. If we use __h2__ for encryption, anyone with physical (or remote ftm) access can easily run
a rainbow table/ wordlist/ etc. against the __h2__ and __salt__ in different combinations to decode the text files.

So if we use __h2__ he doesn't even need to run a test, all he has to do is to use __h2__ itself :|

### What algorithm is used for enc/dec?

AES. Big Alphabet boys in US government recommend __AND__ use it for cold storage, so why shouldn't we?
in fact when I searched for it online, I got the idea by visitting some .gov website!

I know, there might be some other techniques and they 'maybe' recommending it only bc they have the technology to break
it... but I dgaf at this point, cuz this text editor is not supposed to be a program in cyber arm-race, it's just an idea

besides, if u have a better solution, just fork this bad boy and redo the __Cryptos__ class

### What's Next?

The current solution of using __h2__ is temporary and in the next versions there's gonna be a different formula for 
a new hash called "__h3__" which is basically just a different combination for salt+password and we will use __h3__
to encrypt text files instead of __h2__ 

This adds a new layer of security as the time for password generation goes higher, bc instead of only one possible
combination u now have 6! And if someone is trying to crack your shit, they're gonna have an absolutely harder time

Also the user will be given the choice to choose how the __h3__ is generated and each time he logs in, he also needs to
remember the combination (ofcourse there's a default option, if u don't want to bother remembering the thing)

### TODO
- [ ] Add h3 support
- [ ] Add user's custom choice for symmetrical key combination of salt+passw

### Contact
If u have any questions or objections, or just wanted to banther, deosn't matter. a letter from a stranger is always welcome. you can reach me out under 
"ezekiel2088@gmail.com"

### CHEERS
