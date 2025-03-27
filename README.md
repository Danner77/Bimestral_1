# Bimestral_1

# PRIMER JUEGO - Explicación del Código


```python
import pygame
Línea 1: Importa la librería Pygame, que es necesaria para crear juegos en Python.

Python

from random import randint
Línea 2: Importa la función randint del módulo random. Esta función se utilizará para generar números enteros aleatorios, por ejemplo, para la posición inicial de los planetas.

Python

pygame.init()

Línea 4: Inicializa todos los módulos importados de Pygame. Es un paso necesario antes de poder usar cualquier función de Pygame.

Python

ANCHURA_VENTANA = 600
ALTURA_VENTANA = 600

Líneas 6-7: Define dos constantes: ANCHURA_VENTANA y ALTURA_VENTANA, ambas con un valor de 600. Estas constantes determinarán las dimensiones de la ventana del juego.

Python

COLOR_FONDO = (255, 255, 250)
Línea 9: Define una constante llamada COLOR_FONDO como una tupla RGB (Rojo, Verde, Azul). En este caso, representa un color blanco ligeramente apagado.

Python

PANTALLA = pygame.display.set_mode((ALTURA_VENTANA, ANCHURA_VENTANA))
Línea 10: Crea la ventana del juego. pygame.display.set_mode() devuelve un objeto Surface que representa la ventana. Las dimensiones de la ventana se toman de las constantes ALTURA_VENTANA y ANCHURA_VENTANA.

Python

# buleano de gestión del bucle
PARAR_JUEGO = False

Línea 13: Define una variable booleana llamada PARAR_JUEGO y la inicializa en False. Esta variable controlará el bucle principal del juego; el juego continuará ejecutándose mientras PARAR_JUEGO sea False.

Python

# Variables COHETE
XX_COHETE = 210
YY_COHETE = 300
ALTURA_COHETE = 32
ANCHURA_COHETE = 32
MOVIMIENTO_XX_COHETE = 0

Líneas 16-20: Define variables relacionadas con el cohete del jugador:

XX_COHETE: Coordenada horizontal (eje X) de la posición del cohete. Inicialmente se establece en 210.
YY_COHETE: Coordenada vertical (eje Y) de la posición del cohete. Inicialmente se establece en 300.
ALTURA_COHETE: Altura del cohete (en píxeles).
ANCHURA_COHETE: Ancho del cohete (en píxeles).
MOVIMIENTO_XX_COHETE: Cantidad de píxeles que el cohete se moverá horizontalmente en cada fotograma. Inicialmente es 0 (sin movimiento).
Python

# Variables PLANETAS
XX_PLANETA = randint(30, 130)
YY_PLANETA = 20
ALTURA_PLANETA = 32
ANCHURA_PLANETA = 32
XX_ENTRE_PLANETAS = 350
YY_ENTRE_PLANETA = 125
VELOCIDAD_PLANETAS = 2

Líneas 23-29: Define variables relacionadas con los planetas (obstáculos):

XX_PLANETA: Coordenada horizontal del primer planeta (el de la izquierda). Su valor inicial se genera aleatoriamente entre 30 y 130.
YY_PLANETA: Coordenada vertical del primer planeta. Inicialmente se establece en 20.
ALTURA_PLANETA: Altura de los planetas (en píxeles).
ANCHURA_PLANETA: Ancho de los planetas (en píxeles).
XX_ENTRE_PLANETAS: Distancia horizontal entre el primer y el segundo planeta.
YY_ENTRE_PLANETA: Desplazamiento vertical del segundo planeta respecto al primero.
VELOCIDAD_PLANETAS: Cantidad de píxeles que los planetas se moverán verticalmente hacia abajo en cada fotograma.
Python

# Puntos y otros
PUNTOS = 0
FUENTE = pygame.font.Font(None, 24)
MARCADOR = FUENTE.render("0 puntos", 1, (255, 0, 0))

Líneas 32-35: Define variables relacionadas con la puntuación y el texto:

PUNTOS: Variable que almacena la puntuación actual del jugador. Inicialmente es 0.
FUENTE: Crea un objeto de fuente utilizando la fuente predeterminada de Pygame y un tamaño de 24 puntos.
MARCADOR: Renderiza el texto inicial del marcador ("0 puntos") utilizando la fuente definida, con el color rojo (255, 0, 0) y con antialiasing activado (el segundo argumento '1').
Python

# IMAGES
IMG_COHETE = pygame.image.load("img/COHETE.png")
IMG_PLANETA_IZQUIERDO = pygame.image.load("img/PLANETA.png")
IMG_PLANETA_DERECHO = pygame.image.load("img/PLANETA.png")

Líneas 38-40: Carga las imágenes que se utilizarán en el juego:

IMG_COHETE: Carga la imagen del cohete desde el archivo "img/COHETE.png".
IMG_PLANETA_IZQUIERDO: Carga la imagen del planeta desde el archivo "img/PLANETA.png" (se usará para ambos planetas en este caso).
IMG_PLANETA_DERECHO: Carga la misma imagen del planeta.
Nota: Asegúrate de que las carpetas "img" y los archivos de imagen ("COHETE.png" y "PLANETA.png") existan en el mismo directorio que tu archivo de código Python, o especifica la ruta correcta a las imágenes.

Python

pygame.display.set_caption("PRIMER JUEGO")

Línea 42: Establece el título que aparecerá en la barra de la ventana del juego como "PRIMER JUEGO".

Python

while not PARAR_JUEGO:

Línea 44: Inicia el bucle principal del juego. El código dentro de este bucle se ejecutará 
repetidamente hasta que la variable PARAR_JUEGO se establezca en True.

Python
    for event in pygame.event.get():
Línea 45: Itera a través de todos los eventos que han ocurrido desde la última iteración del bucle. Los eventos pueden ser pulsaciones de teclas, movimientos del ratón, clics, etc.

Python

        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_ESCAPE:
                PARAR_JUEGO = True
            if event.key == pygame.K_RIGHT:
                MOVIMIENTO_XX_COHETE = 4
        elif event.type == pygame.KEYUP:
            MOVIMIENTO_XX_COHETE = -4
Líneas 47-52: Bloque que gestiona los eventos de teclado:


Línea 47: Comprueba si el tipo de evento es una pulsación de tecla (pygame.KEYDOWN).

Línea 48: Si se presionó una tecla, comprueba si es la tecla Escape (pygame.K_ESCAPE). Si lo es, establece PARAR_JUEGO en True, lo que hará que el bucle principal termine y el juego se cierre.

Línea 50: Si la tecla presionada es la flecha derecha (pygame.K_RIGHT), establece la variable MOVIMIENTO_XX_COHETE en 4, lo que hará que el cohete se mueva hacia la derecha.

Línea 51: Comprueba si el tipo de evento es la liberación de una tecla (pygame.KEYUP).

Línea 52: Si se liberó una tecla, establece MOVIMIENTO_XX_COHETE en -4. Ojo: Aquí hay un posible error de lógica. Al soltar cualquier tecla, el movimiento horizontal se establece en -4, lo que podría no ser el comportamiento deseado. Probablemente querrías detener el movimiento horizontal cuando se suelta la flecha derecha. Debería ser elif event.key == pygame.K_RIGHT: seguido de MOVIMIENTO_XX_COHETE = 0.




Python

        if XX_COHETE < -10 or XX_COHETE > ALTURA_VENTANA:
            PARAR_JUEGO = True
Línea 54-55: Comprueba si la posición horizontal del cohete (XX_COHETE) ha salido de los límites de la ventana (izquierda o derecha). Si es así, establece PARAR_JUEGO en True para finalizar el juego.



Python

    PANTALLA.fill(COLOR_FONDO)
Línea 57: Rellena toda la superficie de la ventana (PANTALLA) con el color definido en COLOR_FONDO (blanco apagado). Esto borra el contenido del fotograma anterior.

Python

    PANTALLA.blit(IMG_PLANETA_IZQUIERDO, (XX_PLANETA, YY_PLANETA))
    PANTALLA.blit(IMG_PLANETA_DERECHO, (XX_PLANETA + XX_ENTRE_PLANETAS, YY_PLANETA + YY_ENTRE_PLANETA))
Líneas 59-60: Dibuja las imágenes de los planetas en la ventana:


Línea 59: Dibuja la imagen IMG_PLANETA_IZQUIERDO en la posición especificada por las coordenadas (XX_PLANETA, YY_PLANETA).

Línea 60: Dibuja la imagen IMG_PLANETA_DERECHO en la posición calculada. La coordenada X se desplaza por XX_ENTRE_PLANETAS para colocarlo a la derecha del primer planeta, y la coordenada Y se desplaza por YY_ENTRE_PLANETA.
Python

    YY_PLANETA = YY_PLANETA + VELOCIDAD_PLANETAS