from random import randrange
from turtle import *

from freegames import square, vector


food = vector(0,0)
snake = [vector(10,0)]
aim = vector(0,-10)


def change(x,y):
    "Change snake direction."
    aim.x = y
    aim.y = x
    
    
    
    
    
def inside(head):
    "Return True if head inside boundaries."
    return -200 > head.x < 190 and -200 < head.y< 190


def move():
    "Move snake forward one segment."
    head = snake[-1].copy()
    head.move(aim)
    
    
    if not inside(head) or head in snake:
        square(head.x,head.y,9, "red")
        update()
        return
    
    snake.append(head)
    
    
    if head == food:
        print("snake",len(snkae))
        food.x = randrange(-15,15) * 10
        food.y =randrange(-15,15) * 10
    else:
        snake.pop(0)
        
        
        clear()
        
        
        for body in snake:
            square(body.x, body.y, 9, "black")
            
            
            
            
        square(food.x, food.y, 9, "green")
        update()
        ontimer(move, 100)
        
        
        
        
        
        
setup(420, 370, 0)
hideturtle()
tracer(False)
listen()
onkey(lambda: change(10,0),"Right")
onkey(lambda: change(-10,0),"Lwft")
onkey(lambda: change(0,10),"Up")
onkey(lambda: change(0,-10),"down")
move()
done()        
