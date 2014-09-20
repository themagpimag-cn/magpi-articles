PY ENIGMA
Simulating the Pocket Enigma Cipher Machine in Python

BASIC ENCRYPTION
Simulating mechanical encryption

Pocket Enigma Cipher Machine

The Pocket Enigma Cipher Machine is a superbly designed toy that demonstrates some of the principles of a real Enigma Cipher Machine, as pictured on the cover of this issue. The Enigma Cipher Machine was used during World War two by the German armed forces, to send secrete messages to submarines and solders. I obtained my Pocket version from Bletchley Park [ http://www.bletchleypark.org.uk/ ], but unfortunately it no longer appears to be on sale. I t is made only of plastic and cardboard and is substantially simpler when compared with a real Enigma cipher machine! On the other hand, if you enjoy encryption and ciphers you will get a kick out of the Pocket Enigma. I t is not too difficult to understand either.

The Pocket Enigma Cipher Machine is not even close to an unbreakable cipher ¨C it is a trivial cipher to break but it is fun. Therefore, do not use it to encrypt sensitive information. A full review of the Pocket Enigma Machine, including a detailed description and further reading, can be found at: http://www.savory.de/pocket_enigma.htm

How does it work?

Each plaintext character is replaced with another character called the cipher text character. The cipher text character is chosen according to the connection between characters printed on the wheel, where there are two wheels to choose from.

In more detail, the algorithm follows:
1 . Cipher wheel (1 or 2) is chosen.
2. The key character is chosen.
3. The start character is chosen.
4. The wheel is set to the key character and the start character is encoded.
5. The wheel is moved to the start character and the first message character is encoded.
6. The wheel is incremented by 1 position, and the next message character is encoded.
7. Repeat step 6 until the entire message is encoded.
8. The encoded message is arranged such that the encoded start character is separated from rest of the encoded message, which is arranged in blocks of, typically, five characters.

For the message to be successfully decoded by the recipient, they must already know the wheel number and key character that was used to encrypt the message.

Now for the limitations:
1 . Only upper case characters can be encoded.
2. No punctuation can be encoded, apart from full-stops which are traditionally substituted with X.

With a bit of imagination the encoding algorithm can easily be modified. For example, more wheels could be used, or the increment could be varied or even reversed.

Python Pocket Enigma Cipher Machine

Use a text editor such as nano or emacs to create a new Python file called Py-Enigma. py. Then add:

to the top of the file. In this article each piece of the program is numbered and should be appended to this file, to create the final program. The ord() function returns the numerical value of an ASCI I character. ord(' A' ) returns 65, whereas ord(' B' ) returns 66 etc.. Lower case characters have different numerical values, but since the cipher only has one set of characters, upper case characters are used throughout the program. The selectedWheel variable is used to select which wheel is used, pointerChar is the initial wheel settings and codeStartChar is the starting character. Integer values of these variables are also stored to simplify manipulating the wheels within the functions that follow. The increment is the amount that a wheel is turned after each character is encrypted and blocksize is used to split the encrypted string into pieces that are separated by spaces.

1. Analysis of the wheels

The wheels have no characters on them, just a lot of connections. One position has an arrow, or pointer, and is taken as the starting position (actually position 0). Looking at the pictures on the first page of this article, it is clear that the connections simply connect from one position to another. These connections indicate how one character should be substituted for another. The wheels can be summarised using two Python lists:

Add these two lists to the end of the Python file. Each list has 26 entries, since there are 26 characters around the outside of the wheel. The number in each entry corresponds to the joining line on the wheel, where a negative number implies moving to the left and a positive number implies moving to the right.

The Python version of the algorithm relies on the modulo (%) operator to stay within the A--Z character range. First, the character should be converted to an integer. Then the offset should be applied, using the modulo operator. For example, using ' A' and the first wheel:

If the number is bigger than the 26 character range, then the modulo operator causes the number to become less than 26. This means that adding 1 to the value of ' Z' returns ' A' :

In both of these examples, the chr() function is used to convert an integer value back into the associated ASCII character. I t helped me to visualise the modulo maths by imagining that it turned the alphabet into a circle.

2. Encrypting or decrypting a character

The Pocket Enigma algorithm states that the wheel should be moved 1 position clockwise after each message character is encoded. This means that a repeated character in the message is not encrypted as the same character. Append the code below to the end of the Python file.

This function takes an input character, the selected wheel number and the current pointer position. The pointer represents the position of the wheel and is substracted from the integer value of the character before it is used to find the offset. I f a character that is not within the A--Z range is passed into the function, then it is ignored and no character is returned.

3. Encrypting a string

To encrypt a string, each character should be passed to the transformChar() function. Append the code below to the Python file.

The function takes a string and returns an encrypted string. The pointer starts from the initial value (key character) set using the global variable pointerInt. Then the starting character is encrypted and appended to the encrypted string. The pointer value is reset to the starting character and then each character in the string is encrypted. To retain some punctuation, each ' . ' is replaced with ' X' . The encrypted output is also split into fixed size blocks that are separated by spaces to help further disguise the words.

4. Decrypting a string

The connections on the wheels are bi-directional. Therefore, if a character is encoded as ' F' and the wheel is in the same position, encoding ' F' will return the original character. Consequently, the same encryption routine can be used to decrypt a string. Append the program at the top of the next page to the Python file. This function takes an encrypted string and returns a decrypted string. Notice that punctuation and spaces are not recovered during the encryption. Therefore, the person that receives the encrypted message will need to put those back in by hand.

5. Welcome, menu & input functions

To call the encrypt and decrypt functions, a text menu provides a simple interface. Add the code given below to the end of the Python file.

The first function is used to report the version and build date, whereas second function prints out the menu choices. To read values that correspond to the menu options three simple input functions are needed. Add the functions below to the end of the Python file.

These functions are used to read a value from the keyboard, read an integer value and read a character value, respectively. The functions prevent a string without any characters from being accepted, check the type of the input string and if it is within the allowed range of numbers or characters.

6. Finishing the program

To finish the program, a function is needed to call all of the other pieces of the program. Add the main function at the top of the next page to the end of the Python file. Then save the file and make it executable by typing:

Then run the program by typing:

The program will print the menu and allow changes to the settings to be made. I f the settings are updated, then the menu is printed again with the new values. The input functions are used to make sure that the settings do not go outside of their allowed range. The menu can also be used to encrypt or decrypt strings, where the result is printed on the screen. With the default settings of wheel 1, key character ' D' and start character ' J ' , the message "Attack at dawn. " becomes "M UQXZI MGAZE DKS" . Decoding this returns "ATTACKATDAWNX" .

The main() function starts by declaring the global variables as global. This is necessary to prevent Python from creating a local version of the same variable when a value is assigned. I t is not needed if the values are only used. The welcome message is printed. Then in the whi le loop, the menu is printed. The users choice is read and checked against each of the menu options. Depending on the menu option, the required action is taken.

The Py-Enigma. py program is a Python version 2 program that cannot be used with Python3 without modification. The program was tested on the latest Raspbian image.

What next?

Well that depends... let me know what you think. All/any feedback is appreciated.