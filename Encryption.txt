from tkinter import *
from tkinter import font as TkFont
import random 

#Window utama
jendela = Tk()
jendela.title('Enkripsi Caesar Cipher')
jendela.geometry('500x300')

coun18 = TkFont.Font(family='Courier New', size='18')
coun12 = TkFont.Font(family='Courier New', size='12')
coun10 = TkFont.Font(family='Courier New', size='10')

#Fungsi untuk enkripsi
def encrypt(key, message):
    message = message.upper()
    alpha = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    result = ""

    for letter in message:
        if letter in alpha: 
            letter_index = (alpha.find(letter) + key) % len(alpha)

            result = result + alpha[letter_index]
        else:
            result = result + letter

    return result

#Fungsi utama
def main():
    key = int(ent1.get())
    message = ent2.get()
    encrypted = encrypt(key, message)
    ent3.delete(0, END)                  #bisa dirun berkali2
    ent3.insert(END, encrypted)

label = Label(jendela, text="ENKRIPSI CAESAR CIPHER\n", font=coun18)
label.pack()

label0 = Label(jendela, text="Setelah anda masukkan kata dan kunci,\nTekan 'Mulai Enkripsi' untuk memulai enkripsi", font=coun12)
label0.pack()

label1 = Label(jendela, text="Masukkan kata", font=coun12)
label1.pack()

#Tempat input kata
ent2 = Entry(jendela)  
ent2.pack()

label2 = Label(jendela, text="Masukkan kunci", font=coun12)
label2.pack()

#Tempat input kunci
ent1 = Entry(jendela)
ent1.pack()

tombol = Button(jendela, text="Mulai Enkripsi", font=coun10, command = main)
tombol.pack()

label3 = Label(jendela, text="")
label3.pack()

#Tempat Output
ent3 = Entry(jendela)
ent3.pack()

jendela.mainloop()