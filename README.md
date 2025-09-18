# EX 7 : IMPLEMENTATION OF IMPLEMENTATION OF DES

## AIM:

To implement the working of the Data Encryption Standard (DES) using a simplified XOR-based encryption and decryption method in C programming.

## ALGORITHM:
To Perform Encryption:
1.	Start the program.
2.	Accept the plaintext message and encryption key from the user.
3.	Calculate the length of the message.
4.	For each character in the message:
•	XOR the character with the corresponding character in the key.
•	If the key is shorter than the message, repeat the key using key[i % keyLength].
•	Store the result in the encrypted message array.
5.	Null-terminate the encrypted message string.
6.	Display the encrypted message in hexadecimal format.
To Perform Decryption:
7.	For each character in the encrypted message:
•	XOR it with the same corresponding character from the key.
•	This reverses the XOR operation, retrieving the original character.
8.	Null-terminate the decrypted message string.
9.	Display the decrypted message.
10.	End the program.


## PROGRAM:
```
#include <stdio.h>
 #include <string.h>
 void encrypt(char *message, char *key, char *encryptedMessage, int
 messageLength) {
 int keyLength = strlen(key);
 for (int i = 0; i < messageLength; i++) {
 // Encrypt by XORing message byte with key byte
 encryptedMessage[i] = message[i] ^ key[i % keyLength];
 }
 encryptedMessage[messageLength] = '\0'; 
 }
 // Function to perform decryption (XOR again with the same key)
 void decrypt(char *encryptedMessage, char *key, char *decryptedMessage, int
 messageLength) {
 int keyLength = strlen(key);
 for (int i = 0; i < messageLength; i++) {
 // Decrypt by XORing encrypted byte with key byte
 decryptedMessage[i] = encryptedMessage[i] ^ key[i % keyLength];
 }
 decryptedMessage[messageLength] = '\0'; // Null-terminate the decrypted
 }
 int main() {
 char message[100];
 char key[100];
 printf("\n**Simulation of DES encryption and decryption\n\n");
 // Get user input for the message
 printf("Enter the message to encrypt: ");
 fgets(message, sizeof(message), stdin);
 message[strcspn(message, "\n")] = '\0'; // Remove newline character if present
 // Get user input for the key
 printf("Enter the encryption key: ");
 fgets(key, sizeof(key), stdin);
 key[strcspn(key, "\n")] = '\0'; // Remove newline character if present
 int messageLength = strlen(message);
 // Buffers to hold encrypted and decrypted messages
 char encryptedMessage[100];
 char decryptedMessage[100];
 // Encrypt the message
 encrypt(message, key, encryptedMessage, messageLength);
 printf("Original Message: %s\n", message);
 printf("Encrypted Message: ");
 // Print encrypted message in hex format
 for (int i = 0; i < messageLength; i++) {
 printf("%02X ", (unsigned char)encryptedMessage[i]);
 }
 printf("\n");
 // Decrypt the message
 decrypt(encryptedMessage, key, decryptedMessage, messageLength);
 printf("Decrypted Message: %s\n", decryptedMessage);
 return 0;
 }
```
## OUTPUT:

<img width="919" height="491" alt="image" src="https://github.com/user-attachments/assets/df108630-4a02-43be-8ef0-208611f7fe99" />

## Result:
The program implementing the Data Encryption Standard (DES) for encryption and decryption	has	been	successfully	executed,	and	the	results	have	been	verified.
