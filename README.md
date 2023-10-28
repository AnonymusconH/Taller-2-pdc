# Taller-2-pdc

### Punto 3

Desarrollar un programa que permita ingresar dos números enteros y determinar si se tratan de números espejos, definiendo números espejos como dos números a y b tales que a se lee de izquierda a derecha igual que se lee b de derecha a izquierda, y viceversa.

```
# Aqui vamos a dar el parametro general que permita identificar números iguales, ya despues le daremos el criterio de espejo
def num_espejo(num1, num2):
    return str(num1) == str(num2)

def numeros_analizar():
    num1 = int(input("Ingresa un primer número: "))
    num2 = int(input("Ingresa ahora un segundo número: "))
    return num1, num2

# Aqui se da el criterio de espejo
def main():
    num1, num2 = numeros_analizar()
    if num_espejo(num1, num2):
        print("Los números"  + str(num1) +  " y"  + str(num2) + "son números espejo ")
    else:
        print("Los números" + str(num1) + " y " + str(num2) + "no son números espejo")

if __name__ == "__main__":
    main()

````


### Punto 4

Diseñar una función que permita calcular una aproximación de la función coseno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Taylor. nota: use math para traer la función coseno y mostrar la diferencia entre el valor real y la aproximación. Calcule con cuántos términos de la serie (i.e: cuáles valores de n), se tienen errores del 10%, 1%, 0.1% y 0.001%.

```
import math

def cos_approx_TaylorSwift(x, n):
    # Variable para almacenar el resultado
    resultado = 0

    # Sumamos los términos de la serie de Taylor
    for i in range(n):
        resultado += ((-1) ** i) * (x ** (2 * i)) / math.factorial(2 * i)

    # Devolvemos el resultado
    return resultado


x = float(input("Ingrese el valor de x: "))
n = int(input("Ingrese el número de términos de la serie: "))

# Calculamos la aproximación y mostramos la diferencia entre el valor real y la aproximación
cos_x = math.cos(x)
cos_approx = cos_approx_TaylorSwift(x, n)
print(f"El valor real de cos({x}) es: {cos_x}")
print(f"La aproximación de cos({x}) usando {n} términos de la serie es: {cos_approx}")
print(f"La diferencia entre el valor real y la aproximación es: {abs(cos_x - cos_approx)}")

```



### Punto 5

Desarrollar un programa que permita determinar el Minimo Comun Multiplo de dos numeros enteros. Abordar el problema desde una perpectiva tanto iterativa como recursiva. Pista: Puede ser de utilidad chequear el Algoritmo de Euclides para el cálculo del Máximo Común Divisor, y revisar cómo se relaciona este último con el Mínimo Común Múltiplo.


```
El algortimo de euclides para encontrar un Mínimo Común Multiplo es un algoritmo que permite sistematizar mediante la busquedad de un Máximo Común Divisior la solución a esta.

Hay que tener presente antes de, el máximo común divisor (MCD) de dos enteros A y B es el entero más grande que divide tanto a A como a B. y con esto e l algoritmo de Euclides es una técnica para encontrar rápidamente el MCD de dos enteros.

El algortitmo:

El algoritmo de Euclides para encontrar MCD(A,B) es como sigue:
Si A = 0 entonces MCD(A,B)=B, ya que el MCD(0,B)=B, y podemos detenernos.  
Si B = 0 entonces MCD(A,B)=A, ya que el MCD(A,0)=A, y podemos detenernos.  
Escribe A en la forma cociente y residuo (A = B ⋅Q + R).
Encuentra MCD(B,R) al usar el algoritmo de Euclides, ya que MCD(A,B) = MCD(B,R).

Trasladado a codigo quedaria asi:

```
```
a = int(input("Ingresa un numero: "))
b = int(input("Ingresa ahora otro número: "))
def MCD(a, b):
    if b == 0:
        return a
    else:
        return MCD(b, a % b)

def MCM(a, b):
    return a * b // MCD(a, b)


print(f"El mínimo común multiplo de {a} y {b} es: {MCM(a, b)}")

```

### Punto 6 

Desarrollar un programa que determine si en una lista existen o no elementos repetidos. Pista: Maneje valores booleanos y utilice el operador in.

```
numeros = (input("Coloca una lista de número y separalos con una coma: "))

# Variable booleana para indicar si hay elementos repetidos
tiene_repetidos = False

# Bucle for para recorrer cada elemento de la lista
for i in range(len(numeros)):
    # Estructura condicional if para verificar si el elemento actual de la lista está presente en la lista entera
    if numeros[i] in numeros[i] + numeros[i+1]:
        tiene_repetidos = True
        break

# Verificar el valor de la variable booleana "tiene_repetidos"
if tiene_repetidos:
    print("Existen elementos repetidos en la lista.")
else:
    print("No existen elementos repetidos en la lista.")

```

### Punto 9 

Resolver el punto 7 del taller 1 usando operaciones con vectores.

Escriba un programa que pida 5 números reales y calcule las siguientes operaciones:

- El promedio
- La mediana
- El promedio multiplicativo (multilplica todos y luego calcula la raíz de la cantidad de operandos)
- Ordenar los números de forma ascendente
- Ordenar los números de forma descendente
- La potencia del mayor número elevado al menor número
- La raíz cúbica del menor número


### El promedio de 5 numeros reales con vectores

```

import math

def obtener_numeros():
    numeros = []
    for i in range(5): # Definimos cuantos elementos tiene la lista
        numero = float(input(f"Ingrese el número {i+1}: ")) #Aui es donde se le pedira al usuario que coloque sus 5 números
        numeros.append(numero)
    return numeros


def calcular_promedio(numeros): # Definimos la operacion para calcular promedios
    suma = sum(numeros)
    total_elementos = len(numeros)
    promedio = suma / total_elementos
    return promedio

def main():
    numeros = obtener_numeros()
    promedio = calcular_promedio(numeros)
    print(f"El promedio de los números ingresados es: {promedio}")

if __name__ == "__main__":
    main()

```



### La mediana de 5 numeros reales con vectores

Importando #"tatistics" y estableciendo la respectiva lista de 5 numeros que se le pedira al usuario, junto con la accion de "median" dentro de la lista. Sale facilito

```
import statistics

numeros = []
for i in range(5): # Definimos cuantos elementos tiene la lista
    Num_usuario = float(input(f"Ingrese el número {i+1}: ")) #Aqui es donde se le pedira al usuario que coloque sus 5 números
    numeros.append(numeros)

mediana = statistics.median(numeros)

print("La mediana de los números es:" + str(mediana))

```



### El promedio multiplicativo de 5 numeros(multilplica todos y luego calcula la raíz de la cantidad de operandos) con vectores

```
import math

def promedio_multi(lista):
    if not lista:
        return None
    product = math.prod(lista)
    raiz = math.sqrt(len(lista))
    return product ** (1 / raiz)

lista = []
for i in range(5):
    number = float(input(f"Ingrese el número {i+1}: "))
    lista.append(number)
    print(promedio_multi(lista))

```

### Ordenar los números de forma ascendente usando vectores de 5 numeros


```

def orden(lista, pos1, pos2):
    lista[pos1], lista[pos2] = lista[pos2], lista[pos1]

#Todo esto sera las instrucciones que definan su ascendencia
def lista_numeros(lista):
    n = len(lista)
    for i in range(n):
        for j in range(0, n-i-1):
            if lista[j] > lista[j+1]:
                orden(lista, j, j+1)


def main():
    lista = []
    for i in range(5):
        numeros = float(input(f"Ingrese el número {i+1}: "))
        vector.append(numeros)

    lista_numeros(vector)
    print("Los números ordenados ascendentemente son:")
    for numeros in vector:
        print(numeros)

if __name__ == "__main__":
    main()

```




### Ordena los numeros de forma descedente usando vectores de 5 numeros

Aqui vamos a importar buildings por parte de input y print, y a parte usaremos bubble_sort que se encargara de ahorrarnos trabajo para hacer el ordenamiento de forma descedente siempre y cuando se establezcan los parametros necesarios

```
from builtins import input, print

def orden(lista, pos1, pos2):
    lista[pos1], lista[pos2] = lista[pos2], lista[pos1]

def bubble_sort(lista):
    n = len(lista)
    for i in range(n):
        for j in range(0, n-i-1):
            if lista[j] < lista[j+1]:
                orden(lista, j, j+1)

def main():
    lista = []
    for i in range(5):
        numeros = float(input(f"Ingrese el número {i+1}: "))
        lista.append(numeros)

    bubble_sort(lista)
    print("Los números ordenados descendientemente son:")
    for numeros in lista:
        print(numeros)

if __name__ == "__main__":
    main()

```





### La potencia del mayor número elevado al menor número de 5 numeros usando vectores

Para esto usamos map para permitir colocar los 5 numeros. Sin embargo lo mas escencial va a ser utilizar el max y el min, parametros que nos permitiran hallar la solucion a este ejercicio

```
numeros = list(map(int, input("Ingrese 5 números separados por espacios: ").split()))

# Aqui es donde estipularemos la condicion clave para hallar la respectiva potendia entre el mayor y menor numero
max_num = max(numeros)
min_num = min(numeros)
resultado = max_num ** min_num

# Mostrar el resultado
print("La potencia del mayor número elevado al menor número es: ", resultado)

```




### Hallar la raiz cubica del menor numero entre 5 numeros que ingrese un usuario usando vectores

Para ello, es indispensable usar el map y el min para poder hallar nuestros numero inferior y asi darle ese parametro de sacarse su raiz cubica

```

numeros = list(map(int, input("Ingrese 5 números separados por espacios: ").split()))

# Aqui se coloca el parametro para calcular la raíz cúbica del menor número
menor_numero = min(numeros)
raiz_cubica = menor_numero ** (1/3)


print("La raíz cúbica del menor número es: ", raiz_cubica)

```

