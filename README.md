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

         #include <stdio.h>
         #include <string.h>
         
         int main()
         {
             char message[100], key[100];
             int i, mac = 0;
         
             printf("MESSAGE AUTHENTICATION CODE (MAC)\n");
         
             printf("Enter the message: ");
             scanf("%s", message);
         
             printf("Enter the secret key: ");
             scanf("%s", key);
         
             for(i = 0; i < strlen(message); i++)
             {
                 mac = mac + message[i];
             }
         
             for(i = 0; i < strlen(key); i++)
             {
                 mac = mac + key[i];
             }
         
             mac = mac % 256;
         
             printf("\nGenerated MAC: %d\n", mac);
         
             int verifyMac = 0;
         
             for(i = 0; i < strlen(message); i++)
             {
                 verifyMac = verifyMac + message[i];
             }
         
             for(i = 0; i < strlen(key); i++)
             {
                 verifyMac = verifyMac + key[i];
             }
         
             verifyMac = verifyMac % 256;
         
             if(mac == verifyMac)
             {
                 printf("Message is Authentic\n");
             }
             else
             {
                 printf("Message is Not Authentic\n");
             }
         
             return 0;
         }

## Output:

<img width="1919" height="989" alt="Screenshot 2026-05-21 113103" src="https://github.com/user-attachments/assets/7394b436-3408-4169-af37-60f7e67bfb64" />


## Result:
The program is executed successfully.
