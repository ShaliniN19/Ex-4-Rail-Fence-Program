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

int main()
{
    char s[100], a[10][100], e[100], d[100];
    int r, n, i, j, k = 0;
    int row = 0, dir = 1;

    printf("Enter message: ");
    scanf("%s", s);
    printf("Enter rails: ");
    scanf("%d", &r);

    n = strlen(s);

    for(i = 0; i < r; i++)
    {
        for(j = 0; j < n; j++)
        {
            a[i][j] = ' ';
        }
    }

    for(i = 0; i < n; i++)
    {
        a[row][i] = s[i];
        row = row + dir;

        if(row == r - 1 || row == 0)
        {
            dir = -dir;
        }
    }

    for(i = 0; i < r; i++)
    {
        for(j = 0; j < n; j++)
        {
            if(a[i][j] != ' ')
            {
                e[k] = a[i][j];
                k++;
            }
        }
    }

    e[k] = '\0';
    printf("Encrypted: %s\n", e);

    k = 0;
    row = 0;
    dir = 1;

    for(i = 0; i < n; i++)
    {
        d[i] = a[row][i];
        row = row + dir;

        if(row == r - 1 || row == 0)
        {
            dir = -dir;
        }
    }

    d[n] = '\0';
    printf("Decrypted: %s", d);

    return 0;
}
```
# OUTPUT

<img width="552" height="590" alt="image" src="https://github.com/user-attachments/assets/9559928c-a1ee-4f86-93ff-661dd4d3f740" />



# RESULT

Thus the program was executed successfully.
