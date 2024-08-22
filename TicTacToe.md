from turtle import *

from freegames import line


def grid():   #tabuleiro
    """Draw tic-tac-toe grid."""
    line(-67, 200, -67, -200)
    line(67, 200, 67, -200)
    line(-200, -67, 200, -67)
    line(-200, 67, 200, 67)


def drawx(x, y):    #desenhar X
    """Draw X player."""
    pencolor("red")
    line(x + 35, y + 25, x + 105, y + 110)
    line(x + 35, y + 110, x + 105, y + 25)
  #Mudamos o tamanho a posição do X e adicionamos uma cor para ele.


def drawo(x, y):     #desenhar O
    """Draw O player."""
    pencolor("blue")
    up()
    goto(x + 68, y + 15)
    down()
    circle(45) 
  #Mudamos o tamanho a posição do circulo e mudamos sua cor.


def floor(value):
    """Round value down to grid with square size 133."""
    return ((value + 200) // 133) * 133 - 200


state = {'player': 0}
players = [drawx, drawo]


def tap(x, y):
    """Draw X or O in tapped square."""
    x = floor(x)
    y = floor(y)
    player = state['player']
    draw = players[player]
    draw(x, y)
    update()
    state['player'] = not player


setup(420, 420, 420, 420)
hideturtle()
tracer(True)
grid()
update()
onscreenclick(tap)
done()
