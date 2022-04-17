# word_jumble_python
from tkinter import *
from random import choice
from random import shuffle

root = Tk()
root.geometry('500x500')
root.title('word jumble game')
root.configure(bg= 'lemon chiffon')

label = Label(root, text='', font= ('Helvetica',20))
label.pack(pady = 20)


def shuffled() :
    entry_answer.delete(0,END)
    
    ans_label.config(text = '')
    
    word_list = ['cat', 'anaconda', 'bear', 'coyote', 'goose', 'koala', 'duck', 'bird', 'fish', 'chicken', 'octopus']
    
    
    global word 
    word = choice(word_list)
    # print(word)

    sep_word = list(word)
    shuffle(sep_word)
    # print(sep_word)
    
    global shuffled_word
    shuffled_word = ""
    for letter in sep_word : 
        shuffled_word += letter
    # print(shuffled_word)
    
    label.config(text= shuffled_word, font=('Helvetica',28))

def answer() :
    if word == entry_answer.get() :
        ans_label.config(text = 'correct')
    else : 
        ans_label.config(text = 'incorrect')

entry_answer = Entry(root, font=('Helvetica', 28))
entry_answer.pack(pady = 20)

ans_button = Button(root, text= 'check', font=('Helvetica', 12),command= answer)
ans_button.pack(padx=20,pady=5)

next_button = Button(root,text='next', font=('Helvetica', 12),command= shuffled)
next_button.pack(padx = 20, pady = 5)

ans_label = Label(root, text = '', font=('Helvetica', 20))
ans_label.pack(pady= 20)


shuffled()
root.mainloop()
