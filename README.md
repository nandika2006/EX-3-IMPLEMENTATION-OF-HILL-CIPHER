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
     #include <ctype.h>
     #define SIZE 3  
    
    
    void multiplyMatrix(int key[SIZE][SIZE], int text[SIZE], int result[SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        result[i] = 0;
        for (int j = 0; j < SIZE; j++) {
            result[i] += key[i][j] * text[j];
        }
        result[i] = result[i] % 26;
    }
    }
    
    int main() {
    
    char plainText[100];
    int key[SIZE][SIZE];
    char cipherText[100] = "";
    int len;
    
    
    printf("Enter the plain text: ");
    fgets(plainText, sizeof(plainText), stdin);
    plainText[strcspn(plainText, "\n")] = '\0';
    
    
    for (int i = 0; plainText[i]; i++) {
        if (isalpha(plainText[i]))
            plainText[i] = toupper(plainText[i]);
    }
    
    
    char temp[100];
    int idx = 0;
    for (int i = 0; plainText[i]; i++) {
        if (isalpha(plainText[i])) {
            temp[idx++] = plainText[i];
        }
    }
    temp[idx] = '\0';
    strcpy(plainText, temp);
    
    
    len = strlen(plainText);
    while (len % 3 != 0) {
        plainText[len++] = 'X';
    }
    plainText[len] = '\0';
    
    
    printf("Enter the 3x3 key matrix (row by row):\n");
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            scanf("%d", &key[i][j]);
        }
    }
    
    
    for (int i = 0; i < len; i += 3) {
        int textVec[SIZE], result[SIZE];
    
    
        for (int j = 0; j < SIZE; j++) {
            textVec[j] = plainText[i + j] - 'A';
        }
    
    
        multiplyMatrix(key, textVec, result);
    
     
        for (int j = 0; j < SIZE; j++) {
            char c = result[j] + 'A';
            strncat(cipherText, &c, 1);
        }
    }
    
    
    printf("Cipher Text: %s\n", cipherText);
    
        return 0;
    }

## OUTPUT:
<img width="1643" height="872" alt="image" src="https://github.com/user-attachments/assets/fe809308-9f6c-4a70-bda8-201594912a96" />

## RESULT:
Thus the execution of Hill cipher text is executed successfully
