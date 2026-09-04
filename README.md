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

void encryptRailFence(char *message, int rails, char *encrypted)
{
    int len = strlen(message);
    char rail[rails][len];

    memset(rail, '\n', sizeof(rail));

    int row = 0, direction = 1, k = 0;

    for (int i = 0; i < len; i++)
    {
        rail[row][i] = message[i];

        row += direction;

        if (row == rails - 1 || row == 0)
            direction = -direction;
    }

    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                encrypted[k++] = rail[i][j];

    encrypted[k] = '\0';
}

void decryptRailFence(char *encrypted, int rails, char *decrypted)
{
    int len = strlen(encrypted);
    char rail[rails][len];

    memset(rail, '\n', sizeof(rail));

    int row = 0, direction = 1, k = 0;

    for (int i = 0; i < len; i++)
    {
        rail[row][i] = '*';

        row += direction;

        if (row == rails - 1 || row == 0)
            direction = -direction;
    }

    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] == '*')
                rail[i][j] = encrypted[k++];

    row = 0;
    direction = 1;

    for (int i = 0; i < len; i++)
    {
        decrypted[i] = rail[row][i];

        row += direction;

        if (row == rails - 1 || row == 0)
            direction = -direction;
    }

    decrypted[len] = '\0';
}

int main()
{
    char message[100], encrypted[100], decrypted[100];
    int rails;

    printf("Enter a Secret Message: ");
    scanf("%s", message);

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    encryptRailFence(message, rails, encrypted);

    printf("Encrypted text: %s\n", encrypted);

    decryptRailFence(encrypted, rails, decrypted);

    printf("Decrypted text: %s\n", decrypted);

    return 0;
}
```
# OUTPUT
<img width="1217" height="647" alt="image" src="https://github.com/user-attachments/assets/bc7d6861-d74f-46eb-bf1a-caa94f6f62b7" />


# RESULT

Thus the program was executed successfully.
