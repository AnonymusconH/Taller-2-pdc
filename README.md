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

#Vamos a definir el coseno de Taylor

x= float
n= float
def cos_taylorSwift (x, n):
    coseno_aproximación = 0
    factorial = 1
    for i in range(n):
        coseno_aproximación += ((-1)**i) * (x**(2 * i))/ factorial
        factorial *= (2 * i + 1) * (2 * i + 2)
    return coseno_aproximación

# Ya definido el coseno, ahora vamos a definir el calculo de error

def calcular_error(x, n):
    coseno_aproximación = cos_taylorSwift(x, n) #Despues traemos a math para el calculo del coseno
    coseno = math.cos(x)
    error = abs(coseno - coseno_aproximación)
    return error

# Ya estipulado todo, vamos a calcular el margen de error definiendo si es de 10%, 1% ,0.1% y 0.001%

error = []
margen_error = [0.1, 0.01, 0.001, 0.0001]
for margen_error in margen_error:
    n= 1
    while True:
        x= 1e-10 #Esto es un parametro que damos para determinar desde cuando se puede calcular el error
        error= calcular_error(x, n)
        if error <= margen_error * abs(math.cos(x)):
            error.append((n, margen_error)) #Añadimos este parametro
            break
        n += 1

for i in range (len(error)):
    print ("Se necesita" + str({error[i][0]}) + "terminos de la serie para obtener un error de" +  str({error[i][1] * 100}))

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
