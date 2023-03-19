# rock-beat-paper
ROCK PAPER SCISSOR
from tkinter import *
import random

root = Tk()
root.title("rock paper scissors")
paperimg = PhotoImage(file="paper.png")
rockimg = PhotoImage(file="rock.png")
scissorimg = PhotoImage(file="scissors.png")
paperrockimg = PhotoImage(file="paper rock.png")
rockscissorimg = PhotoImage(file="rock scissor.png")
scissorpaperimg = PhotoImage(file="scissor paper.png")
papertieimg = PhotoImage(file="paper paper.png")
rocktieimg = PhotoImage(file="rock rock.png")
scissortieimg = PhotoImage(file="scissor scissor.png")
blankimg = PhotoImage(file="blank.png")
gif = PhotoImage(file="rps.gif")
blank = Label(root,image=blankimg)
blankwin = Label(root,image=blankimg)
wintext = Label(root, text="")

choice = 0
hwin=0
compchoice = 0
cwin=0


def labels():
    humanwin.config(text="wins: " + str(hwin))
    compwin.config(text="comp wins: " + str(cwin))

def rockupdate():
    blank.configure(image=rockimg)

def paperupdate():
    blank.configure(image=paperimg)

def scissorupdate():
    blank.configure(image=scissorimg)


def finalcompimg():
    global compchoice
    compchoice = random.randrange(1,4)
    if compchoice == 1:
        blank.configure(image=rockimg)
    elif compchoice == 2:
        blank.configure(image=paperimg)
    elif compchoice == 3:
        blank.configure(image=scissorimg)
    else:
        blank.configure(image=blankimg)

def win():
    global cwin
    global hwin
    global choice
    global compchoice
    if choice == 3 and compchoice == 3:
        blankwin.configure(image=scissortieimg)
        wintext.configure(text="Tie!")
    elif choice == 2 and compchoice == 2:
        blankwin.configure(image=papertieimg)
        wintext.configure(text="Tie!")
    elif choice == 1 and compchoice == 1:
        blankwin.configure(image=rocktieimg)
        wintext.configure(text="Tie!")
    elif choice == 1 and compchoice == 2:
        blankwin.configure(image=paperrockimg)
        wintext.configure(text="Computer wins!")
        cwin += 1
    elif choice == 1 and compchoice == 3:
        blankwin.configure(image=rockscissorimg)
        wintext.configure(text="You win!")
        hwin += 1
    elif choice == 2 and compchoice == 1:
        blankwin.configure(image=paperrockimg)
        wintext.configure(text="You win!")
        hwin += 1
    elif choice == 2 and compchoice == 3:
        blankwin.configure(image=scissorpaperimg)
        wintext.configure(text="Computer wins!")
        cwin += 1
    elif choice == 3 and compchoice == 1:
        blankwin.configure(image=rockscissorimg)
        wintext.configure(text="Computer wins!")
        cwin += 1
    elif choice == 3 and compchoice == 2:
        blankwin.configure(image=scissorpaperimg)
        wintext.configure(text="You win!")
        hwin += 1
    else:
        blankwin.configure(image=blankimg)
        wintext.configure(text="")


def rock():
    finalcompimg()
    global choice
    choice = 1
    win()
    labels()

def paper():
    finalcompimg()
    global choice
    choice = 2
    win()
    labels()

def scissor():
    finalcompimg()
    global choice
    choice=3
    win()
    labels()

humanwin = Label(root, text="wins: "+ str(hwin))
compwin = Label(root,text="comp wins: "+ str(cwin))
# setting buttons with pictures
rl = Button(root, image=rockimg, command=rock) # rl = rock label
pl = Button(root, image=paperimg, command=paper)
sl = Button(root,image=scissorimg, command=scissor)

humanwin.grid(row=0,column=2)
compwin.grid(row=8,column=2)
rl.grid(row=2,column=1,pady=20,padx=(30,0))
pl.grid(row=2,column=2,padx=10)
sl.grid(row=2,column=3,padx=(0,30))
blank.grid(row=6,column=2,pady=20)
blankwin.grid(row=4,column=2)
wintext.grid(row=4,column=3, sticky=N+E+S+W)

blog = Label(root,text="randomresourceweb.blogspot.com")
blog.grid(row=8,column=3,sticky=SE)
root.mainloop()
