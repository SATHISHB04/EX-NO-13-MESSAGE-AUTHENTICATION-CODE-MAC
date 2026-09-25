# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:
Enter the secret key and message from the user.
Find the length of the key and message using strlen().
Generate the MAC by performing XOR between key and message characters repeatedly for 32 bytes.
Display the generated MAC in hexadecimal format.
Enter the received MAC and compare it with the computed MAC using memcmp().
Display the result as “MAC verification successful” if both MACs match; otherwise, display “MAC verification failed.”

## Program:
```
#include <stdio.h>
#include <string.h>

int main() {
    char key[50], msg[100], mac[33], rmac[33];
    int i, k, m;

    printf("Enter key: ");
    scanf("%s", key);

    printf("Enter message: ");
    scanf("%s", msg);

    k = strlen(key);
    m = strlen(msg);

    for (i = 0; i < 32; i++)
        mac[i] = key[i % k] ^ msg[i % m];

    printf("Computed MAC: ");
    for (i = 0; i < 32; i++)
        printf("%02x", (unsigned char)mac[i]);

    printf("\nEnter received MAC: ");
    for (i = 0; i < 32; i++)
        scanf("%2hhx", &rmac[i]);

    if (!memcmp(mac, rmac, 32))
        printf("MAC verification successful.");
    else
        printf("MAC verification failed.");

    return 0;
}
```


## Output:
<img width="658" height="247" alt="Screenshot 2026-03-09 102101" src="https://github.com/user-attachments/assets/264f3c86-1d01-47e9-a7f1-58c1795335f4" />


## Result:
The program is executed successfully.
