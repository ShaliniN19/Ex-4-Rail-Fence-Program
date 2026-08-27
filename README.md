# Ex-5 Rail-Fence-Program
## NAME: SHALINI N
## REG NO: 212224040305
# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

void encryptRailFence(char text[], int key) {
    int len = strlen(text);
    char rail[key][len];

    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';

    int row = 0, col = 0;
    int dir_down = 0;

    for (int i = 0; i < len; i++) {
        if (row == 0 || row == key - 1)
            dir_down = !dir_down;

        rail[row][col++] = text[i];

        if (dir_down)
            row++;
        else
            row--;
    }

    printf("Encrypted Text: ");

    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);

    printf("\n");
}

int main() {
    char text[100];
    int key;

    printf("Enter text: ");
    scanf("%s", text);

    printf("Enter key (number of rails): ");
    scanf("%d", &key);

    encryptRailFence(text, key);

    return 0;
}
```
# OUTPUT

<img width="1310" height="590" alt="image" src="https://github.com/user-attachments/assets/9726e89a-2c4c-4798-abf1-0fc3fa849e17" />

# RESULT

Thus the program was executed successfully.
