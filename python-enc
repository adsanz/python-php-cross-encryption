from base64 import b64decode, b64encode
from Crypto.Hash import HMAC, SHA256
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad,pad

key = bytes("", "utf8") #key should be generated securely DON'T do this also pass a string if you use this


def encryptData(plaintext,key):
    cipher = AES.new(key, AES.MODE_CBC)
    ct = cipher.encrypt(pad(bytes(plaintext, "utf8"), AES.block_size))
    iv = cipher.iv
    hmac = HMAC.new(key,ct,digestmod=SHA256)
    return b64encode(iv+hmac.digest()+ct)

def decryptData(ciphertext,key):
    ct = b64decode(ciphertext)
    iv = ct[:16]
    cipher_plain = ct[48:]
    hmac_mac = ct[16:-len(cipher_plain)]
    hmac = HMAC.new(key,cipher_plain,digestmod=SHA256)
    try:
        hmac.verify(hmac_mac)
    except:
        print("MAC verification failed, data has been modified!")
    cipher = AES.new(key, AES.MODE_CBC, iv)
    pt = unpad(cipher.decrypt(cipher_plain), AES.block_size)
    return pt
