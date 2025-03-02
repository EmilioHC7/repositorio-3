"Proyecto Logica Katas Python."

Este proyecto contiene una serie de consultas o ejercicios para generar funciones o codigo en python por medio de vscode. A continuación, se describe el contenido del archivo `.ipynb` y las consultas que se han realizado.

"Descripción del Archivo SQL"

El archivo `proyecto_logica_katas_python.ipynb` contiene varios ejercicios con su respectivas soluciones o respuestas segun los parametros indicados.

"""Pregunta 1: Contar frecuencia de letras en una cadena"""


def contar_letras(cadena="Aprendiendo Python"):
    """Devuelve un diccionario con la frecuencia de cada letra en la cadena, ignorando espacios."""   
    resultado = {} 

    for letra in cadena:
        if letra != " ":  # Ignorar espacios
            resultado[letra] = resultado.get(letra, 0) + 1
    
    return resultado

print(contar_letras("Aprendiendo Python"))


"""Pregunta 2 Dada una lista de números, obtén una nueva lista con el doble de cada valor. Usa la función map()"""

numeros = [2,30,33,29,7,8]
numeros_al_doble = list(map(lambda x: x*2, numeros))

print("Lista original", numeros)
print("lista con el doble de cada numero", numeros_al_doble)


"""Pregunta 3 Escribe una función que tome una lista de palabras y una palabra objetivo como parámetros. 
La función debe devolver una lista con todas las palabras de la lista original que contengan la palabra objetivo."""

def filtrar_palabras(lista, objetivo):
    return[palabra for palabra in lista if objetivo in palabra]

palabras = ["mover", "volver", "coger", "resolver", "tomar"]
objetivo = "ver"
resultado3 = filtrar_palabras(palabras,objetivo)
print(resultado3)


"""Pregunta 4 Genera una función que calcule la diferencia entre los valores de dos listas. Usa la función map()"""

def diferencia_listas(lista1, lista2):
    return list(map(lambda x, y: x-y, lista1, lista2))

lista1 = [5,10,15,20,25]
lista2 = [1,2,3,4,5]

resultado4 = diferencia_listas(lista1,lista2)
print(resultado4)


"""Pregunta 5 Esribe una función que tome una lista de números como parámetro y un valor opcional nota_aprobado, que por defecto es 5. La función debe calcular la media de los números en la lista y determinar si la media es mayor o igual que nota aprobado. Si es así, el estado será "aprobado", de lo contrario, será "suspenso". La función debe devolver una tupla que contenga la media y el estado."""


notas = [5,7,8,5,7.5]

def nota_estado(notas, nota_aprobado=5):
    """Calcular la media de una lista de numeros y determina si esta aprobada o suspendida

    Args:
        notas (int, float): Lista de numeros(notas)
        nota_aprobado (int, float): Nota minima para aprobar (por defecto es 5)

    Return: Tupla con la media y el estado ("aprobado" o "suspendido")
    """
    media = sum(notas) / len(notas)
    estado = "aprobado" if media >= nota_aprobado else "suspendido"
    return (media, estado)

resultado5 = nota_estado(notas)
print(resultado5)


"""Pregunta 6 Escribe una función que calcule el factorial de un número de manera recursiva."""


numero = 6

def factorial(n):
    """Calcula el factorial de un número de manera recursiva.
    Lanza un ValueError si el número es negativo."""
    if n < 0:
        raise ValueError("Error, el número no puede ser negativo")
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

try:
    print(factorial(6))
except ValueError as resultado:
    print(resultado)


"""Pregunta 7 Genera una función que convierta una lista de tuplas a una lista de strings. Usa la función map()"""


tuplas = [(1, 2), (7, 8, 9), ("Feliz", "Semana")]

def tuplas_a_strings(lista_tuplas):
    return [" ".join(map(str, t)) for t in lista_tuplas]

resultado7 = tuplas_a_strings(tuplas)
print(resultado7)


"""Pregunta 8 Escribe un programa que pida al usuario dos números e intente dividirlos. Si el usuario ingresa un valor no numérico o intenta dividir por cero, maneja esas excepciones de manera adecuada. Asegúrate de mostrar un mensaje indicando si la división fue exitosa o no."""


def dividir():
    try:
        num1 = float(input("ingrese el primer numero: "))
        num2 = float(input("ingrese el segundo numero: "))
        resultado8= num1/num2
    except ValueError:
        print("Error: Debes ingresar valores numericos")
    except ZeroDivisionError:
        print("Error: No se puede dividir por cero")
    else:
        print(f"El resultado es: {resultado8}")
    finally:
        print("Fin del programa")

#como ejemplo puse primer numero 29 y segundo 2
dividir()

"""Pregunta 9 Escribe una función que tome una lista de nombres de mascotas como parámetro y devuelva una nueva lista excluyendo ciertas mascotas prohibidas en España. La lista de mascotas a excluir es ["Mapache", "Tigre", "Serpiente Pitón", "Cocodrilo", "Oso"].Usa la función filter()"""


mascotas = ["Perro,", "Gato", "Conejo", "Mapache", "Tigre", "Canario", "Serpiente Piton", "Cocodrilo", "Oso"]

def filtrar_mascotas_permitidas(lista_mascotas):
    mascotas_prohibidas = {"Mapache", "Tigre", "Serpiente Piton", "Cocodrilo", "Oso"}
    return list(filter(lambda mascota: mascota not in mascotas_prohibidas, lista_mascotas))

resultado9 = filtrar_mascotas_permitidas(mascotas)
print("Mascotas permitidas:", resultado9)


"""Pregunta 10 Escribe una función que reciba una lista de números y calcule su promedio. Si la lista está vacía, lanza una excepción personalizada y maneja el error adecuadamente."""


class ListaVaciaError(Exception):
    """Exception personalizada para listas vacias"""
    pass

def calcular_promedio(numeros):
    if not numeros:
        raise ListaVaciaError("Error: La lista esta vacia, no se puede calcular el promedio")
    return sum(numeros) / len(numeros)
try:
    lista_numeros = [] #Si colocamos numeros dentro de la lista, tendremos el promedio, pero si la dejamos vacia veremos el error.
    resultado10 = calcular_promedio(lista_numeros)
    print(f"El promedio es : {resultado10}")
except ListaVaciaError as i:
    print(i)


"""Pregunta 11 Esribe un programa que pida al usuario que introduzca su edad. Si el usuario ingresa un valor no numérico o un valor fuera del rango esperado (por ejemplo, menor que 0 o mayor que 120), maneja las excepciones adecuadamente."""

def pedir_edad():
    try:
        edad=int(input("Por favor, ingrese su edad"))
        if edad < 0 or edad > 120:
            raise ValueError("Error:la edad debe estar entre 0 y 120")
    except ValueError as e:
        print(f"Entrada no valida. {e}")
    else:
        print(f"Edad valida: {edad}")
    finally:
        print("fin del programa")

pedir_edad()



"""Pregunta 12 Genera una función que al recibir una frase devuelva una lista con la longitud de cada palabra. Usa la función map()"""


frase = ("Estoy aprendiendo Phyton")

def longitud_palabras(frase):
    return list(map(len, frase.split()))
result = longitud_palabras(frase)
result



"""Pregunta 13 Genera una función la cual, para un conjunto de caracteres, devuelva una lista de tuplas con cada letra en mayúsculas y minúsculas. Las letras no pueden estar repetidas .Usa la función map()"""


caracteres = "python"

def mayusculas_minusculas(conjunto):
    return list(map(lambda x: (x.upper(), x.lower()), set(conjunto)))

resultado = mayusculas_minusculas(caracteres)
resultado



"""Pregunta 14 Creaa una función que retorne las palabras de una lista de palabras que comience con una letra en especifico.Usa la función filter()"""


palabras = ["perro", "gato", "gusano", "paloma"]
letra = "p"

def palabras_que_comienzan_con(lista_palabras, letra):
    return list(filter(lambda palabra: palabra.startswith(letra), lista_palabras))

resultado14 = palabras_que_comienzan_con(palabras, letra)
resultado14


#Pregunta 15 - Crea una función lambda que sume 3 a cada número de una lista dada.
numeros = [4,5,7,8,11]

def sumar_tres(lista):
    return list(map(lambda x: x + 3, lista))

resultado = sumar_tres(numeros)
resultado


"""Pregunta 16 Esribe una función que tome una cadena de texto y un número entero n como parámetros y devuelva una lista de todas las palabras que sean más largas que n. Usa la función filter"""


texto = "Este es el ejercicio decimo sexto del proyecto"
n = 4

def palabras_mas_largas(cadena, n):
    return list(filter(lambda palabra: len(palabra) > n, cadena.split()))

resultado = palabras_mas_largas(texto, n)
resultado


"""Pregunta 17 Crea una función que tome una lista de dígitos y devuelva el número correspondiente. 
Por ejemplo, 5,7,2 corresponde al número quinientos setenta y dos 572. Usa la función reduce()
from functools import reduce"""


digitos = [5, 7, 2]

def lista_a_numero(digitos):
    return reduce(lambda x, y: x*10 +y, digitos)

numero = lista_a_numero(digitos)
numero


"""Pregunta 18 Esribe un programa en Python que cree una lista de diccionarios que contenga información de estudiantes (nombre, edad, calificación) y use la función filter para extraer a los estudiantes con una calificación mayor o igual a 90. Usa la función filter()""".


estudiantes = [
    {'nombre': 'Luis', 'edad': 20, 'calificacion': 75},
    {'nombre': 'Maria', 'edad': 25, 'calificacion': 93},
    {'nombre': 'Pepe', 'edad': 34, 'calificacion': 91},
    {'nombre': 'Diana', 'edad': 30, 'calificacion': 86}
]

def estudiantes_calificacion(estudiantes):
    """Devuelve una lista de estudiantes con calificación mayor o igual a 90."""
    return [estudiante for estudiante in estudiantes if estudiante['calificacion'] >= 90]

print(estudiantes_calificacion(estudiantes))


"""Pregunta 19 Crea una función lambda que filtre los números impares de una lista dada."""

numeros = [ 2,3,6,7,8,12,13]

def filtrar_impares(lista):
    return list(filter(lambda x: x%2 != 0, lista))

resultado = filtrar_impares(numeros)
resultado


"""Pregunta 20 Crea una lista con elementos tipo integer y string obtén una nueva lista sólo con los valores int.Usa la función filter()"""

lista = [ 7, "Python", 29, 8, "ejercicios"]

def filtrar_enteros(lista):
    return list(filter(lambda x: isinstance(x, int), lista))


resultado = filtrar_enteros(lista)
resultado


"""Pregunta 21 Creaa una función que calcule el cubo de un número dado mediante una función lambda"""

numero = 7

def numero_al_cubo(numero):
    return (lambda x: x**3)(numero)

resultado = numero_al_cubo(numero)
resultado


"""Pregunta 22 Crea una lista numérica, obtén el producto total de los valores de dicha lista.Usa la función reduce()."""

from functools import reduce
lista = [4,5,6,2,3]

def producto_total(lista):
    return reduce(lambda x,y : x*y, lista)

resultado = producto_total(lista)
resultado


"""Pregunta 23 Concatena una lista de palabras.Usa la función reduce()."""

from functools import reduce

palabras = ["Hola", "me", "llamo", "Emilio"]

def concatenar_palabra(lista):
    return reduce(lambda x, y: x+" "+ y, lista)

resultado = concatenar_palabra(palabras)
resultado



"""Pregunta 24 Calcula la diferencia total en los valores de una lista. Usa la función reduce()."""

from functools import reduce
numeros = [88, 15, 25, 6]

def diferencia_total(lista):
    return reduce(lambda x, y: x-y, lista)

resultado = diferencia_total(numeros)
resultado



"""Pregunta 25 Crea una función que cuente el número de caracteres en una cadena de texto dada."""


texto = "Soy analista de datos"

def contar_caracteres(cadena):
    return len(cadena)

resultado = contar_caracteres(texto)
resultado


"""Pregunta 26 Crea una función lambda que calcule el resto de la división entre dos números dados."""

resto_division = lambda x, y: x % y

resultado = resto_division(28,3)
resultado


"""Pregunta 27 Crea una función que calcule el promedio de una lista de números."""

numeros = [10,20,30,40,50]

def calcular_promedio(lista):
    if len(lista) == 0:
        return None
    if len(lista) > 0:
        return sum(lista) / len(lista)
    
resultado = calcular_promedio(numeros)
resultado



"""Pregunta 28 Crea una función que busque y devuelva el primer elemento duplicado en una lista dada"""

numeros = [ 2,3,4,5,1,2,5,3,8]

def primer_duplicado(lista):
    vistos = set()
    for num in lista:
        if num in vistos:
            return num
        vistos.add(num)
    return None

print(primer_duplicado(numeros))



"""Pregunta 29 Crea una función que convierta una variable en una cadena de texto y enmascare todos los caracteres con el carácter '#', excepto los últimos cuatro."""

texto = "contraseña"

def enmascarar(variable):
    variable_str = str(variable)
    longitud = len(variable_str)
 
    enmascarado = "#" * (longitud -4) + variable_str[-4:]
    return enmascarado

print(enmascarar(texto))



"""Pregunta 30 Crea una función que determine si dos palabras son anagramas, es decir, si están formadas por las mismas letras pero en diferente orden."""


palabra1 = "amor"
palabra2 = "mora"
def son_anagramas(palabra1, palabra2):
    return sorted(palabra1.lower()) == sorted(palabra2.lower())

print(son_anagramas(palabra1, palabra2))



"""Pregunta 31 Crea una función que solicite al usuario ingresar una lista de nombres y luego solicite un nombre para buscar en esa lista. Si el nombre está en la lista, se imprime un mensaje indicando que fue encontrado, de lo contrario, se lanza una excepción"""


def buscar_nombre():
    try: 
        nombres = ["David", "Juan", "Maria", "Lola", "Luis", "Pedro"]
        nombre_buscar = input("Ingrese el nombre que desea buscar").strip()
        if nombre_buscar in nombres:
           print(f"El nombre {nombre_buscar} fue encontrato en la lista")
        else:
           raise ValueError(f"El nombre {nombre_buscar} no esta en la lista")
    except ValueError as e:
        print(f"Error: {e}")

buscar_nombre()



"""Pregunta 32 Crea una función que tome un nombre completo y una lista de empleados, busque el nombre completo en la lista y devuelve el puesto del empleado si está en la lista, de lo contrario, devuelve un mensaje indicando que la persona no trabaja aquí."""

empleados = {"Luis Cid": "Gerente", 
              "Ana Lopez": "Analista de datos",
              "Juan Rodriguez": "Contador",
              "Pedro Gomez": "Desarrollador"}

def buscar_puesto(nombre, empleados):
    if nombre in empleados:
        return (f"{nombre} trabaja como {empleados[nombre]}.")
    else:
        return (f"{nombre} no trabaja aqui.")

print(buscar_puesto("Ana Lopez", empleados))
print(buscar_puesto("Miguel Lopez", empleados))



"""Pregunta 33  Crea una función lambda que sume elementos correspondientes de dos listas dadas."""

lista1 = [2,3,4,5]
lista2 = [4,13,56,32]

sumar_listas = lambda lista1, lista2: list(map(lambda x, y: x+y, lista1, lista2))

resultado = sumar_listas(lista1,lista2)
resultado


"""Pregunta 34 Crea la clase Arbol , define un árbol genérico con un tronco y ramas como atributos. Los métodos disponibles son:crecer_tronco , nueva_rama , crecer_ramas , quitar_rama e info_arbol. El objetivo es implementar estos métodos para manipular la estructura del árbol."""

class Arbol:
    def __init__(self):
        """Inicializa el árbol con un tronco y sin ramas."""
        self.tronco = 1
        self.ramas = []

    def crecer_tronco(self):
        """Incrementa la longitud del tronco."""
        self.tronco += 1

    def nueva_rama(self):
        """Añade una nueva rama con longitud 1."""
        self.ramas.append(1)
        
    def crecer_ramas(self):
        """Incrementa la longitud de cada rama en 1."""
        self.ramas = [rama + 1 for rama in self.ramas]

    def quitar_rama(self, posicion):
        """Elimina una rama en la posición dada si es válida."""
        if 0 <= posicion < len(self.ramas):
            self.ramas.pop(posicion)
        else:
            print("Posición inválida")
    
    def info_arbol(self):
        """Imprime la información del árbol en lugar de retornarla."""
        print(f"Longitud del tronco: {self.tronco}")
        print(f"Número de ramas: {len(self.ramas)}")
        print(f"Longitudes de las ramas: {self.ramas}")


arbol = Arbol()
arbol.crecer_tronco()
arbol.nueva_rama()
arbol.crecer_ramas()
arbol.nueva_rama()
arbol.nueva_rama()
arbol.quitar_rama(2)
arbol.info_arbol()



"""Pregunta 36 Crea la clase UsuarioBanco ,representa a un usuario de un banco con su nombre, saldo y si tiene o no cuenta corriente. Proporciona métodos para realizar operaciones como retirar dinero, transferir dinero desde otro usuario y agregar dinero al saldo."""

class UsuarioBanco:
    def __init__(self, nombre, saldo, cuenta_corriente=True):
        """Inicializa un usuario del banco con nombre, saldo y si tiene cuenta corriente."""
        self.nombre = nombre
        self.saldo = saldo
        self.cuenta_corriente = cuenta_corriente

    def retirar_dinero(self, cantidad):
        """Retira dinero de la cuenta si hay saldo suficiente."""
        if cantidad > self.saldo:
            raise ValueError("Saldo insuficiente para realizar el retiro.")
        self.saldo -= cantidad

    def transferir_dinero(self, otro_usuario, cantidad):
        """Transfiere dinero a otro usuario si hay saldo suficiente."""
        if cantidad > self.saldo:
            raise ValueError("Saldo insuficiente para realizar la transferencia.")
        self.saldo -= cantidad
        otro_usuario.agregar_dinero(cantidad)

    def agregar_dinero(self, cantidad):
        """Agrega dinero al saldo del usuario."""
        self.saldo += cantidad


alicia = UsuarioBanco("Alicia", 100, True)
bob = UsuarioBanco("Bob", 50, True)

bob.agregar_dinero(20)
alicia.retirar_dinero(50)
bob.transferir_dinero(alicia, 80)


print(f"{alicia.nombre}: {alicia.saldo}")
print(f"{bob.nombre}: {bob.saldo}")



"""Pregunta 37 Crea una función llamada procesar_texto que procesa un texto según la opción especificada: contar_palabras, reemplazar_palabras, eliminar_palabra. Estas opciones son otras funciones que tenemos que definir primero y llamar dentro de la función procesar_texto."""


def contar_palabras(texto):
    palabras = texto.split()
    frecuencia = {}
    for palabra in palabras:
        frecuencia[palabra] = frecuencia.get(palabra, 0) + 1
    return frecuencia

def reemplazar_palabras(texto, palabra_original, palabra_nueva):
    return texto.replace(palabra_original, palabra_nueva)

def eliminar_palabra(texto, palabra_eliminar):
    palabras = texto.split()
    palabras_filtradas = [palabra for palabra in palabras if palabra != palabra_eliminar]
    return " ".join(palabras_filtradas)

def procesar_texto(texto, opcion, *args):
    if opcion == "contar":
        return contar_palabras(texto)
    elif opcion ==  "reemplazar" and len(args) == 2:
        return reemplazar_palabras(texto, args[0], args[1])
    elif opcion == "eliminar" and len(args) == 1:
        return eliminar_palabra(texto, args [0])
    else:
        return "Opcion no valida o argumentos incorrectos"
    
texto = "la niña vivia en la casa"
                 
print(procesar_texto(texto, "contar"))
print(procesar_texto(texto, "reemplazar", "niña", "perra"))
print(procesar_texto(texto, "eliminar", "la"))


"""Pregunta 38 Genera un programa que nos diga si es de noche, de día o tarde según la hora proporcionada por el usuario."""

def determinar_momento_dia(hora):
    if 6 <= hora < 12:
       return "Es de dia (mañana)."
    elif 12 <= hora < 18:
        return "Es de tarde."
    elif (18 <= hora <= 23) or (0 <= hora < 6):
        return "Es de noche."
    else:
        return "Hora no valida. Ingresa un numero entre 0 y 23"
    
try:
    hora_usuario = int(input("Ingresa la hora (0-23): "))
    print(determinar_momento_dia(hora_usuario))
except ValueError:
    print("Error: Ingresa un número entero válido.")
    


"""Pregunta 39 Escribe un programa que determine qué calificación en texto tiene un alumno en base a su calificación numérica. Las reglas de calificación son:"""

def determinar_calificacion(nota):
    if 0 <= nota <= 69:
        return "Insuficiente"
    elif 70 <= nota <= 79:
        return "Bien"
    elif 80 <= nota <= 89:
        return " Muy bien"
    elif 90 <= nota <=100:
        return "Excelente"
    else:
        return "Calificacion fuera de rango. Ingrese un numero entre 0 y 100."
    
try:
    calificacion = int(input("Ingresa tu calificacion (0-100):"))
    print(f"Tu calificacion es : {determinar_calificacion(calificacion)}")
except ValueError:
    print("Error: Ingresa un numero entero valido")



"""Pregunta 40 Escribe una función que tome dos parámetros: figura (una cadena que puede ser "rectangulo" , "circulo" o "triangulo") y datos (una tupla con los datos necesarios para calcular el área de la figura)."""

import math

def calcular_area(figura, datos):
    figura = figura.lower()
    if figura == "rectangulo":
        if len(datos) == 2 and all(d > 0 for d in datos):
            base, altura = datos
            return base * altura
        else:
            return "Error: El rectángulo requiere base y altura positivos."
        
    elif figura == "circulo":
        if len(datos) == 1 and datos[0] > 0:
            radio, = datos
            return math.pi * (radio ** 2)
        else:
            return "Error: El círculo requiere un radio positivo."
        
    elif figura == "triangulo":
        if len(datos) == 2 and all(d > 0 for d in datos):
            base, altura = datos
            return (base * altura) / 2
        else:
            return "Error: El triángulo requiere base y altura positivos."
        
    else:
        return "Error: Figura no reconocida. Usa 'rectángulo', 'triángulo' o 'círculo'."

print(calcular_area("circulo", (6,)))
print(calcular_area("triangulo", (4, 8)))
print(calcular_area("rectangulo", (3, 6)))
print(calcular_area("cuadrado", (2, 2)))



"Pregunta 41"

try:
    precio_original = float(input("Ingresa el precio original del articulo: "))
    tiene_cupon = input("¿Tienes un cupon de descuento? (si/no): ").strip().lower()

    if tiene_cupon =="si" or tiene_cupon == "si":
        descuento = float(input("Ingresa el valor del cupon de descuento: "))
        if descuento > 0:
            precio_final = precio_original - descuento
            if precio_final < 0:
                precio_final = 0 
            print(f"Descuento aplicado: {descuento}€")
        else:
            precio_final = precio_original
            print("El valor del cupon no es valido, no se aplicara descuento.")
    else:
        precio_final = precio_original
    print(f"El precio final de la compra es: {precio_final:.2f}€")

except ValueError:
    print("Error: Ingresa valores numeros validos para el precio y el descuento.")

                     
