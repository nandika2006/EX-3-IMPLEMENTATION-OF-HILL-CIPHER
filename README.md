## EX : 3 IMPLEMENTATION OF HILL CIPHER

## AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

Step 1:

Design of Hill Cipher algorithnm

Step 2:

Implementation using C or pyhton code

Step 3:

1.	Convert each letter of the message to a number (A = 0, B = 1, ..., Z = 25) and divide the message into blocks of size n.
2.	Select an invertible n × n matrix as the cipher key (modulo 26 for the English alphabet).
3.	Multiply each block of n letters by the cipher key matrix (modulo 26) to get the encrypted numbers.
4.	Convert the encrypted numbers back into letters using the reverse of step 1.
5.	Multiply the encrypted blocks by the inverse of the cipher key matrix (modulo 26) to recover the original message.
6.	Ensure the key matrix is invertible (mod 26) for decryption to be possible.


## PROGRAM:

     #include <stdio.h>
     #include <string.h>
     
     int main() 
     {
         unsigned int a[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}}; // Encryption key
         unsigned int b[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};   // Decryption key (inverse of a mod 26)
         int i, j, t;
         unsigned int c[3], d[3];
         char msg[4]; // buffer for exactly 3 characters plus null terminator
     
         printf("Enter plain text (3 letters, A-Z): ");
         scanf("%3s", msg); // ensure input is limited to 3 characters
     
         // Ensure the message has exactly 3 characters
         if (strlen(msg) != 3) {
             printf("Error: The plain text must be exactly 3 letters.\n");
             return 1;
         }
     
         // Convert plain text to numerical values (A=0, B=1, ..., Z=25)
         for (i = 0; i < 3; i++) {
             c[i] = msg[i] - 'A';
             printf("%d ", c[i]); // display numerical representation of characters
         }
     
         // Encrypt the message using matrix 'a'
         for (i = 0; i < 3; i++) {
             t = 0;
             for (j = 0; j < 3; j++) { 
                 t += a[i][j] * c[j];
             }
             d[i] = t % 26; // mod 26 for alphabet range
         }
     
         // Output encrypted cipher text
         printf("\nEncrypted Cipher Text: "); 
         for (i = 0; i < 3; i++) {
             printf("%c", d[i] + 'A');
         }
     
         // Decrypt the message using matrix 'b'
         for (i = 0; i < 3; i++) {
             t = 0;
             for (j = 0; j < 3; j++) { 
                 t += b[i][j] * d[j];
             }
             c[i] = t % 26; // mod 26 for alphabet range
         }
     
         // Output decrypted plain text
         printf("\nDecrypted Plain Text: "); 
         for (i = 0; i < 3; i++) {
             printf("%c", c[i] + 'A');
         }
     
         printf("\n");
     
         return 0;
     }


## OUTPUT:
<img width="1643" height="873" alt="image" src="https://github.com/user-attachments/assets/62afb21f-6e08-4275-bce0-64fcf996e642" />


## RESULT:
Thus the execution of Hill cipher text is executed successfully
