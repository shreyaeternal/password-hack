# password-hack
# hack password using python

import hashlib

pass_hash = input("Enter md5 hash: ")
wordlist = input("File name: ")

try:
    pass_file = open(wordlist, "r")
except FileNotFoundError:
    print("No file found")
    quit()

flag = 0

for word in pass_file:
    enc_wrd = word.encode('utf-8')
    digest = hashlib.md5(enc_wrd.strip()).hexdigest()

    if digest == pass_hash:
        print("Password found")
        print("Password is: " + word)
        flag = 1
        break

if flag == 0:
    print("Password is not found in the list")

pass_file.close()

