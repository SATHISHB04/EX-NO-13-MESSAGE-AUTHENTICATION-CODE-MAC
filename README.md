# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

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
