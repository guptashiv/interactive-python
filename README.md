interactive-python
==================
import random
import simplegui

secret_num =0
num_range=100
max_guess=7
count =0

def init():
    print 
    print "New Game;;the range is 0 to",num_range
    print " guess remained:" ,max_guess - count
    global secret_num 
    secret_num=random.randrange(0,num_range)
    

def range100():
    global num_range ,count,max_guess
    count=0
    num_range=100
    max_guess=7
    init()
    print
def range1000():
    global secret_num , max_guess,num_range
    num_range=1000
    secret_num=random.randrange(0,1000)
    count=0
    max_guess=10
    init()
    print
 
def input_guess(guess):
    print
    print "your guess is:",guess 
    global count
    count+=1
    print "remaining:",max_guess-count 
    
    g = int(guess)
    if count<=max_guess:
        if  g>secret_num:
            print "make lower guess "
        elif g<secret_num:
            print "make higher guess "
        else:
            print "congratulations!!!"
            print
            range100()
    else:
        print "game over"
        print
        range100()
    
    print        
     
init()
print secret_num
frame=simplegui.create_frame("guess the number", 300,300)
frame.add_button("range is [0,100)",range100,200)
frame.add_button("range is [0,1000)",range1000,200)
frame.add_input("ur guess",input_guess,200)

frame.start()        


            
    
