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
```#include <stdio.h>
#include <string.h>
void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0;

    for (int i = 0; message[i] != '\0'; i++) {
        temp = temp ^ message[i];  
        temp += message[i];        
    }
    
    *hash = temp;
}

int main() {
    char message[256];     
    unsigned char hash;    
    char receivedHash[3];   

    printf("Enter the message: ");
    scanf("%s", message);

    computeSimpleHash(message, &hash);

    printf("Computed Hash (in hex): %02x\n", hash);

    printf("Enter the received hash (in hex): ");
    scanf("%s", receivedHash);
    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue);

    if (hash == receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}
```


## Output:

![WhatsApp Image 2025-05-29 at 19 04 49_25b3bc91](https://github.com/user-attachments/assets/efe4580c-7cbc-40c2-875a-45d5bab3f5db)

## Result:
The program is executed successfully.
