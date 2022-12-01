# Classic crypto

The use of encryption has existed since the dawn of history. Classical encryption includes any type of encryption that does not involve computing. (page and pen, steganography, etc.)


There is much evidence of the use of encryption in cultures such as: the ancient Egyptians, in the Bible and Judaism, and in Greece. The most well-known cipher from these periods is: the Caesar cipher


## Examples:

* Caesar cipher - one of the simplest chipers. This is a substitution cipher, in which every letter of the text is replaced with another letter at a fixed offset.
* Vigenère cipher - is a polyalphabetic substitution cipher. Each time a different key will be used to make the exchange. Its weakness: the length of the key. It is exposed to statistical bias, and is therefore cryptographically unsafe to use.
* The enigma - is a machine that enables encryption and decryption of messages. It was used mainly in World War II by the Germans and Italians. Deciphering some of the messages gave the Allies a significant advantage in the war.

> There is only one unbreakable code called the Vernam cypher created during World War II to defeat the Germans. It uses genuinely random information to create an initial key.

### Ceaser code in C language

##### Encryption
```c
#include<stdio.h>

int main()
{
  char message[500], ch;
  int j, key;
  printf("Enter a message to encrypt: ");
  scanf("%s",message);
  printf("Enter the key: ");
  scanf("%d", &key);
  for(j = 0; message[j] != '\0'; ++j){
    ch = message[j];
    if(ch >= 'a' && ch <= 'z'){
      ch = ch + key;
      if(ch > 'z')
        ch = ch - 'z' + 'a' - 1;
      message[j] = ch;
    }
    else if(ch >= 'A' && ch <= 'Z'){
      ch = ch + key;
      if(ch > 'Z')
        ch = ch - 'Z' + 'A' - 1;
      message[j] = ch;
    }
  }
  printf("Encrypted message: %s", message);
  return 0;
}
```
##### Decryption
```c
#include<stdio.h>
int main()
{
  char message[500], ch;
  int j, key;

  printf("Enter a message to decrypt: ");
  scanf("%s",message);
  printf("Enter key: ");
  scanf("%d", &key);

  for(j = 0; message[j] != '\0'; ++j){
    ch = message[j];
    if(ch >= 'a' && ch <= 'z'){
      ch = ch - key;
      if(ch < 'a')
        ch = ch + 'z' - 'a' + 1;
      message[j] = ch;
    }
    else if(ch >= 'A' && ch <= 'Z'){
      ch = ch - key;
      if(ch < 'A')
        ch = ch + 'Z' - 'A' + 1;
      message[j] = ch;
    }
  }
  printf("Decrypted message: %s", message);
  return 0;
}
```