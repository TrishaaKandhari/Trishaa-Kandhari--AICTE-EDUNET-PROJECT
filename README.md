# Trishaa-Kandhari--AICTE-EDUNET-PROJECT
Python 3.12.0 (tags/v3.12.0:0fb18b0, Oct  2 2023, 13:03:39) [MSC v.1935 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license()" for more information.

= RESTART: C:\Users\kandh\Downloads\Stenography-main\Stenography-main\stego.py
Enter secret message:Hello
Enter a passcode:1234
Enter passcode for Decryption1234
Decryption message: Hello

=============================== RESTART: C:\Users\kandh\Downloads\Stenography-main\Stenography-main\stego.py =================================
Enter secret message:Hello
Enter a passcode:1234
Enter passcode for Decryption2345
YOU ARE NOT auth
# CODE:
import cv2
import os
import string

img = cv2.imread("mypic.JPG") # Replace with the correct image path

msg = input("Enter secret message:")
password = input("Enter a passcode:")

d = {}
c = {}

for i in range(255):
    d[chr(i)] = i
    c[i] = chr(i)

m = 0
n = 0
z = 0

for i in range(len(msg)):
    img[n, m, z] = d[msg[i]]
    n = n + 1
    m = m + 1
    z = (z + 1) % 3

cv2.imwrite("encryptedImage.jpg", img)
os.system("start encryptedImage.jpg")
# Use 'start' to open the image on Windows

message = ""
n = 0
m = 0
z = 0

pas = input("Enter passcode for Decryption")
if password == pas:
    for i in range(len(msg)):
        message = message + c[img[n, m, z]]
        n = n + 1
        m = m + 1
        z = (z + 1) % 3
    print("Decryption message:", message)
else:
    print("YOU ARE NOT auth")
