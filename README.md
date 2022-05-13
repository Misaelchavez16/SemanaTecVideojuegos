# SemanaTecVideojuegos

En este espacio se mostrará los resultados del trabajo realizado en cada uno de los ejercicios que se realizaron durante esta semana.

Juego de Paint:
En este juego se realizaron las funciones para colocar un triángulo, un rectángulo y un circulo

Para la función del triángulo se marca la distancia de uno de sus lados y este girara en 120° para crear el otro lado, repetirá este proceso hasta haber creado un triángulo, el triángulo que se crea es un triángulo equilátero, por lo que todos los lados tendrán un ángulo interno de 60° y sus lados medirán exactamente lo mismo, la siguiente imagen muestra el triángulo creado y la función que se implementó para su creación.

![image](https://user-images.githubusercontent.com/75141227/168392596-35da1d58-8424-4496-847c-5a0e8d305984.png)

    #funcion para crear un triangulo equilatero
    def triangle(start, end):
        """Draw triangle from start to end."""
        up()
        goto(start.x, start.y)
        down()
        begin_fill()

        for count in range(3):
            forward(end.x - start.x)
            left(120)

        end_fill()

Para la siguiente función que es la función para la creación de un rectángulo, para esta función solo se marca la longitud de este o la base, después este dibujara un rectángulo con una altura igual a la mitad de la distancia de la base de este, para el cambio de dirección se hizo que tuviera una rotación de 90° grados para dibujar el siguiente lado de este, las siguientes imágenes muestran el resultado de este junto con la función creada.

![image](https://user-images.githubusercontent.com/75141227/168393248-d1e34f5d-ade9-452a-9744-433351c1f233.png)

    #Se crea un ciruclo con la altura igual a la mitad de su longitud
    def rectangle(start, end):
        """Draw rectangle from start to end."""
        up()
        goto(start.x, start.y)
        down()
        begin_fill()


        forward(end.x - start.x)
        left(90)
        forward(end.x - (start.x/2))
        left(90)
        forward(end.x - start.x)
        left(90)
        forward(end.x - (start.x/2))


        end_fill()

Juego de la serpiente:
Para este juego se realizaron un par de mejoras, como ejemplo de esto tenemos que a lo largo de la partida de manera aleatoria la comida se mueva un lugar a cualquiera de las 4 direcciones, además de una función para cambiar el color de la serpiente y la comida cada que una nueva partida comience con uno de los 6 colores que se crearon.

Para la primera función que es el cambio de color de la serpiente y la comida, se crearon variables con el HEX de un color en formato de Sting, después se agregaron cada una de estas variables a una lista y atreves de la función de randrange se escoge cada vez que se corre el código uno de estos colores de manera aleatoriamente y se les asigna a una variable la cual se les da a la función para que el color sea el escogido de manera aleatoria, a continuación se muestran tanto el código como una imagen ejemplificando esto.

![image](https://user-images.githubusercontent.com/75141227/168395058-a5ab37cd-0cd0-4d2a-b667-f806a7b3758d.png)

La siguiente parte del código muestra la creacion de la lista con los colores y la asignacion aleatoria atravez de la función de Randrange de la libreria de random.

#Variables con el hexadecimal de 6 colores diferentes
cyan = '#00FFFF'
ladrillo = '#FF4D00'
rosa = '#FFB0D8'
amarilo = '#FFDF00'
morado = '#B700FF'
botella = '#007974'

#lista de los colores y asignacion aleatoria de estos a la comida y serpiente
randomcolor = [botella,cyan,ladrillo,rosa,amarilo,morado]
snakecolor = randomcolor[randrange(0, 6)]
foodcolor = randomcolor[randrange(0, 6)]

Modificacion de las funciones dentro del código para cambiar el color.

"""Se cambio el color predeterminado de la serpiente por el aleatoria que se cambio arriba,
    se hace algo de manera similar con la comida"""

    for body in snake:
        square(body.x, body.y, 9, snakecolor)
    

    square(food.x, food.y, 9, foodcolor)
    update()
    ontimer(move, 100)
    
Para la siguiente funcion que es para que la comida se mueva, se realizo una serie de condiciones para que la comida se mueva, para empesar durante cada segundo del juego se esta escoguiendo un numero aleatoreo en un rango del 1 al 40, si el numero resulta ser 10, 20, 30 o 40 se movera en alguna dirección, la unica condicion para evitar que la comida se salga del cuadro es que si esta se encuentra cerca de un lado, este no se acercara más a este y se movera a otro lado, para este caso no se mostrara una imagne por la dificultad pero si el código.

#sumar a ta x de food 10 pixeles
    #Se mueve la comida 10 pixeles, en caso de estar cerca de una de las paredes no se movera hacia esa diraccion
    if (food.x == -150):
        if head != food:
            movefood = randrange(1, 41)
            if movefood == 10:
                food.x += 10
            elif movefood == 20:
                food.y += 10
            elif movefood == 30:
                food.x -= 10
            else:
                food.x = food.x
    elif (food.x == 141):
        if head != food:
            movefood = randrange(1, 41)
            if movefood == 10:
                food.y += 10
            elif movefood == 30:
                food.y -=10
            elif movefood == 20:
                food.x -= 10
            else:
                food.x = food.x
    elif (food.y == -150):
        if head != food:
            movefood = randrange(1, 41) 
            if movefood == 10:
                food.x += 10
            elif movefood == 20:
                food.y += 10
            elif movefood == 30:
                food.x -= 10
            else:
                food.x = food.x
    elif (food.y == 141):
        if head != food:
            movefood = randrange(1, 41)
            if movefood == 10:
                food.x += 10
            elif movefood == 20:
                food.y -= 10
            elif movefood == 30:
                food.x -= 10
            else:
                food.x = food.x
    else:
        if head != food:
            movefood = randrange(1, 41)
            if movefood == 10:
                food.x += 10
            elif movefood == 20:
                food.y -= 10
            elif movefood == 39:
                food.y += 10
            elif movefood == 30:
                food.x -= 10
            else:
                food.x = food.x

Juego de memoria:
Para el juego de la memoria se nos pedía implementar 3 cosas, la primera cambiar los numero de la lista por otra cosa, nosotros escogimos símbolos para ello, además también se implementó un contador de taps y un mensaje de "You Win" cuando se haya ganado.

Para el primer cambio simplemente se remplazó la lista que tenía con otra nueva de esta manera los símbolos que se mostraban en vez de ser números serán la lista que teníamos anteriormente, este es el ejemplo, de igual manera se implementó una función para centrar el símbolo en la casilla, alterando su posición en el eje X:

tiles = ["☺", '☻','♥','♦','♣','♠','•','○','◙','♂','♀','♪','♫','☼','►','◄','↕','‼','¶','§','@','↨','↑','↓','→','←','∟','↔','▲','▼','©']*2

![image](https://user-images.githubusercontent.com/75141227/168400516-783a466f-7b17-473f-a025-5c04eeab486e.png)

Para los otros 2, simplemente se implementó el contador de Taps, cada vez que das un toque a este se aumenta en uno el contador y se muestra en el juego, además se creó otro contador, pero este solo se sumara 1 cuando se revelen 2 imágenes, es decir, cuando juntemos una pareja, de esta manera juntando las 32 parejas aparecerá el mensaje de "You Win" en la pantalla junto con los taps que realizamos, también como función extra se agregó una función de Game over, que tras llegar a cierta cantidad de Taps, el juego se termina, aquí el código con algunas imágenes muestra.

![image](https://user-images.githubusercontent.com/75141227/168400907-bb1a242f-4727-4822-8e14-758bc1ee4236.png)

#Variables para las funciones futuras.
writer = Turtle(visible=True)
finish = Turtle(visible=True)
Taps = {'taps': 0}
GameOver = {'YouWin' : 0, 'Message': 'YOU WIN', 'stop': 'YOU LOSE'}

def tap(x, y):
    """Update mark and hidden tiles based on tap."""
    spot = index(x, y)
    mark = state['mark']
    writer.undo()
    writer.write(Taps['taps'])
    
    #Se tiene el contador de "taps" para detectar cuantas veces a presionado el mouse, y se mostrara el contador.
    #Se tiene la funcion de GameOver para cuando no se completo antes de los 128 taps. (Se puede quitar o modificar el limite)
    if Taps['taps'] == 256:
        finish.goto(0, 210)
        finish.color("black")
        finish.undo()
        finish.write(GameOver['stop'], font=('Arial', 55, 'normal'))
        Break
    elif mark is None or mark == spot or tiles[mark] != tiles[spot]:
        state['mark'] = spot
        Taps['taps'] += 1
        writer.goto(220, 170)
        writer.color('black')
        writer.write(Taps['taps'], font=('Arial', 30, 'normal'))
    else:
        GameOver['YouWin'] += 1         
        hide[spot] = False
        hide[mark] = False
        state['mark'] = None
        Taps['taps'] += 1
        writer.goto(220, 170)
        writer.color('black')
        writer.write(Taps['taps'], font=('Arial', 30, 'normal'))

    #Tras tener las 64 casillas liberadas se soltara el mensaje
    if GameOver['YouWin'] == 32:
        finish.goto(0, 210)
        finish.color("black")
        finish.undo()
        finish.write(GameOver['Message'], font=('Arial', 55, 'normal'))
        
Juego del cañon:
Para este juego simplemente se nos pidio aumentar la velocidad de los proyectiles y que el juego no se terminara una vez que los objetivos llegaran al lado izquierdo de la pantalla

Para aumentar la velocidad del proyectil, se modificó el atributo “speed”, en el que se tenía un valor de 200, y al aumentar ese valor a 300, la velocidad tanto horizontal como vertical de esta aumentó. 

Para aumentar la velocidad de los targets, se modificó su velocidad horizontal, pues la vertical es constante. Para esto, el atributo “target.x”, es decir su posición, se modificó de 0.5 a 1. Esto debido a que el for en el que se encuentra hace que en cada ciclo, se modifique la posición hacia la izquierda. Entonces al aumentar la posición desplazada, se simula una velocidad mayor.

def move():
    """Move ball and targets."""
    if randrange(40) == 0:
        y = randrange(-150, 150)
        target = vector(200, y)
        targets.append(target)
# la posición se duplicó de 0.5 a 1 para que se desplacen más rápido
    for target in targets:
        target.x -= 1

    if inside(ball):
        speed.y -= 0.35
        ball.move(speed)

    dupe = targets.copy()
    targets.clear()
    
Con la función comentada, se hacía un ciclo en el que si un target salía del límite definido, el juego se detenía. Al comentarlo, si un target llega al límite y lo pasa, simplemente desaparece y el juego continúa creando nuevos targets.

    #Comentamos esta funcion para que el juego continue aunque el 
    # target se pase del limite

    # for target in targets:
    #     if not inside(target):
    #         return
    
Juego del Pacman:

Para este juego, se nos pidio aumentar la velocidad de los fantasmas y tambien la de pacman, hacer a los fantasmas un poco más inteligente y crear un nuevo mapa para este juego.

Para crear un algoritmo que le diera “inteligencia” a los fantasmas, se usaron condicionales, mediante las cuáles se le darían opciones de movimiento determinadas a los fantasmas, dependiendo de la posición de Pacman con respecto a ellos. Si Pacman se encuentra a la derecha de un fantasma, por ejemplo, se abren tres nuevas opciones: si está arriba a la derecha, abajo a la derecha, o directamente sobre un mismo carril a la derecha. Y según estas posibilidades, el fantasma sólo puede ir una dirección definida (a la derecha, y dependiendo de la posición vertical arriba, abajo o sin movimiento vertical). Si este movimiento no está permitido, se mantendrá en el ciclo.

for point, course in ghosts:
        if valid(point + course):
            point.move(course)
        else:
            if (pacman.x - point.x > 0):
                if (pacman.y - point.y > 0):
                    options = [
                    vector(10, 0),
                    vector(0, 10),
                    ]
                    
                elif (pacman.y - point.y < 0):
                    options = [
                    vector(10, 0),
                    vector(0, -10),
                    ]
                elif (pacman.y - point.y == 0):
                    options = [
                    vector(10, 0)
                    ]
                plan = choice(options)
                course.x = plan.x
                course.y = plan.y
            elif (pacman.x - point.x < 0):
                if (pacman.y - point.y > 0):
                    options = [
                    vector(-10, 0),
                    vector(0, 10),
                    ]
                   
                elif (pacman.y - point.y < 0):
                    options = [
                    vector(-10, 0),
                    vector(0, -10),
                    ]
                elif (pacman.y - point.y == 0):
                    options = [
                    vector(-10, 0)
                    ]
                plan = choice(options)
                course.x = plan.x
                course.y = plan.y
            elif (pacman.x - point.x == 0):
                if (pacman.y - point.y < 0):
                    options = [
                    vector(0, -10)
                    ]
                elif (pacman.y - point.y > 0):
                    options = [
                    vector(0, 10)
                    ]
                plan = choice(options)
                course.x = plan.x
                course.y = plan.y
            else:
                options = [
                    vector(10, 0),
                    vector(0, 10),
                    vector(-10, 0),
                    vector(0, -10),
                    ]
                plan = choice(options)
                course.x = plan.x
                course.y = plan.y
            
        up()
        goto(point.x + 10, point.y + 10)
        dot(20, 'red')
        
        
Para crear un nuevo tablero, se reescribió a mano usando 1 y 0, significando cuadros en los que se puede mover (azules) y zonas no permitidas (negras). No se usó una función random porque esto podría ocasionar que hubiera zonas cerradas.

Lista con el nuevo tablero:

 tiles = [
    0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
    0, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 0, 0,
    0, 1, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 0, 0, 1, 0, 0, 1, 0, 0,
    0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0, 0, 1, 0, 0,
    0, 1, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1, 1, 1, 1, 0, 0, 1, 0, 0,
    0, 1, 0, 1, 1, 1, 1, 1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0,
    0, 1, 0, 1, 0, 1, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0,
    0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 0, 1, 0,
    0, 1, 1, 1, 0, 1, 1, 1, 1, 1, 1, 0, 0, 1, 0, 0, 0, 0, 1, 0,
    0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 1, 0,
    0, 1, 1, 1, 1, 0, 1, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 1, 1, 0,
    0, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 1, 0, 0,
    0, 1, 0, 0, 1, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0, 0, 0, 1, 1, 0,
    0, 1, 1, 1, 1, 0, 0, 1, 1, 1, 1, 1, 0, 1, 0, 0, 0, 0, 1, 0,
    0, 1, 1, 1, 1, 1, 1, 1, 0, 1, 0, 1, 1, 1, 0, 0, 1, 1, 1, 0,
    0, 1, 0, 1, 0, 0, 0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 0,
    0, 1, 0, 1, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0,
    0, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0,
    0, 1, 1, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0,
    0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
]

Para aumentar la velocidad d ellos fantasmas, se modificaron los valores de sus vectores de movimiento (líneas 20-23), así como en el algoritmo que otorgaba las opciones de movimiento de tipo “inteligencia”. Para mejorar la jugabilidad, además se cambió también la velocidad de Pacman (líneas 254-257) siguiendo la misma lógica. Se debe mencionar que se debía aumentar en múltiplos de 5 porque así está diseñado el tablero.

ghosts = [
    [vector(-180, 160), vector(10, 0)],
    [vector(-180, -160), vector(0, 10)],
    [vector(100, 160), vector(0, -10)],
    [vector(100, -160), vector(-10, 0)],
]

![image](https://user-images.githubusercontent.com/75141227/168401586-6d275bd1-e90f-42e9-a120-2f485a1676f6.png)

Imagenes con Links a los repositorios de los GitHubs de cada uno de los juegos:
![image](https://user-images.githubusercontent.com/75141227/168401740-8086af89-9d83-4ace-97b9-2aa02ba775de.png)
![image](https://user-images.githubusercontent.com/75141227/168401726-503f4be4-49c3-4af5-92df-aa2250220c91.png)
![image](https://user-images.githubusercontent.com/75141227/168401753-95dcd4e3-1315-43be-8ac8-eadcc5563a24.png)
![image](https://user-images.githubusercontent.com/75141227/168401758-d583be4b-7429-454b-af31-b68630102e34.png)
![image](https://user-images.githubusercontent.com/75141227/168401777-4284385a-5ec8-47f7-b216-f9c4a7d39d57.png)

Link repositorio Memoria: https://github.com/RodrigoGE9772/MemoryGameSemanaTec.git

Link repositorio serpiente: https://github.com/RodrigoGE9772/SnakeGameSemanTec.git
Link repositorio Cannon: https://github.com/RodrigoGE9772/PacManGameSemanaTec.git
Link repositorio Pacman: https://github.com/RodrigoGE9772/PacManGameSemanaTec.git
Link repositorio Paint: https://github.com/Misaelchavez16/SemanaTecVideojuegos.git

