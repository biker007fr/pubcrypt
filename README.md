This script will encrypt or decrypt a file or a string using a ssh key.  
It is usually used to exchange sensitive information with a specific person that can provide you a public ssh key.
The public key will be used to encrypt a file or a text. Send the encrypted version to this person so he can use his private ssh key to decrypt it

# Requirements
- Openssl binary
- To encrypt it requires a public ssh key
- To decrypt it requires the private ssh key related to the public ssh key used to encrypt

# Usage

## Encrypt
### To encrypt a string:
```
"myPassword" | pubcrypt -e /path/to/key.pub
```
### To encrypt a file:
```
pubcrypt -e /path/to/key.pub < /path/to/cleartext/secret/file.txt
```

## Decrypt
### To decrypt a string:
If your private key is ~/.ssh/id_rsa you do not need to specify it
```
"myEncryptedPassword" | pubcrypt -d
```
otherwise
```
"myEncryptedPassword" | pubcrypt -d ~/.ssh/key_rsa
```
### To decrypt a file:
With ~/.ssh/id_rsa as a private key
```
pubcrypt -d < /path/to/encrypted/secret/file.txt
```
Otherwise
```
pubcrypt -d ~/.ssh/key_rsa < /path/to/encrypted/secret/file.txt
```

# Notes
Do not forget to add pubcrypt in your $PATH  
Ex: For /home/myuser/bin/pubcrypt  
add the following line to your ~/.profile or ~/.bashrc  
export PATH=$PATH:/home/myuser/bin/pubcrypt
