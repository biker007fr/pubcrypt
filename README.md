This script will encrypt or decrypt a file or a string using a SSH public and private key pair.  
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
echo "myPassword" | sshpkcrypt -e /path/to/key.pub
```
### To encrypt a file:
```
sshpkcrypt -e /path/to/key.pub < /path/to/cleartext/secret/file.txt
```

## Decrypt
### To decrypt a string:
If your private key is ~/.ssh/id_rsa you do not need to specify it
```
echo "myEncryptedPassword" | sshpkcrypt -d
```
otherwise
```
echo "myEncryptedPassword" | sshpkcrypt -d ~/.ssh/key_rsa
```
### To decrypt a file:
With ~/.ssh/id_rsa as a private key
```
sshpkcrypt -d < /path/to/encrypted/secret/file.txt
```
Otherwise
```
sshpkcrypt -d ~/.ssh/key_rsa < /path/to/encrypted/secret/file.txt
```

# Notes
Do not forget to add sshpkcrypt in your $PATH  
Ex: For /home/myuser/bin/sshpkcrypt  
add the following line to your ~/.profile or ~/.bashrc  
export PATH=$PATH:/home/myuser/bin/sshpkcrypt
