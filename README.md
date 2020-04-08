# BUC-Iceberg-Cube
An implementation of the Bottom-Up Computation (BUC) algorithm for computing Iceberg cubes.

## Execute:
`python3 BUC.py`

## More Info:
1. The program needs to be executed in the same directory that has the dataset
named `Product_Sales_Data_Set.csv`.

2. The generated output file is called `Iceberg-Cube-Results.txt`

3. Absence of data points is represented by *

4. Given example has `minimum_support = 11`


## 5.11 Answers :
    a) La implementación de BUC se realizó en Python, ejecutándose sobre un CSV encontrado en Internet sobre venta de 
    productos; el programa realiza el cálculo de la agregación (suma) en unidades de venta sobre los distintos valores
    encontrados por dimensión. En este caso se acotó a tres dimensiones: items, location y years.
    El programa pide como parámetro de entrada el soporte mínimo, lee los datos del csv e imprime el resumen del cubo de datos
    mediante un arreglo con tuplas de la forma (dim i: agregación); imprimiendo sólo aquellos cuya agregación es mayor igual
    al soporte mínimo definido por el usuario.
    El programa muestra un buen desempeño, ya que el conjunto de datos no es grande; y al al aumentar el soporte mínimo la 
    cantidad podada es bastante significativa y ayuda a evitar obtener datos no representativos.

    b) i) El tamaño del cuboide aumenta exponencialmente con el número de dimensiones; por lo que se requiere de mayor
    cantidad de memoria así como de tiempo necesario para calcular el cuboide.
       ii) Un cubo iceberg, al eliminar celdas con agregaciones pequeñas y reducir por tanto el costo computacional. 
       Los beneficios pueden ser mayores si el dataset es disperso, más no cuando tiene sesgo. Esto se debe a que existen 
       poca posibilidad que las celdas se colapsen en la misma celda agregada, excepto en cuboides con pocas dimensiones. 
       Por tanto, muchas celdas pueden tener valores menores al soporte mínimo y serán omitidas.
       iii) Considerar una base de datos de 100 dimensiones. Sea a,ij el jésimo valor de la dimensión i. Asumiendo 10 
       celdas en el cuboide base, todas agregadas a la celda (a1,1, a2,1,...,a99,1, *). Siendo el soporte mínimo 10, 
       2^99-1 celdas agregadas de esta celda satisfacen el límite. En este caso no habría algún beneficio por podamiento.
    c) BUC puede modificarse para generar un shell cube de alguna combinación de cantidad de dimensiones específica, 
    ya que parte del apex hacia abajo, y mientras lo hace se puede validar que corresponda a los valores deseados y
    deteniéndolo cuando alcance el máximo número de dimensiones.
