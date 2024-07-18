# Tarea-2_VLSI

En la tarea, además de resolver el problema de diseño de circuitos electrónicos y comparar soluciones en términos de retardo y consumo de potencia, se requiere realizar el diseño de layout para ambos circuitos. Esto implica trazar el diseño físico de las compuertas y conexiones en un chip o sustrato, asegurándose de que todas las compuertas tengan el mismo alto y minimizando las capacitancias parásitas entre nodos. El layout debe seguir un trazado optimizado que tenga en cuenta las relaciones de tamaño obtenidas previamente, con un alto máximo definido de 4.48 micrómetros. Además, se deben realizar simulaciones post-trazado con parásitas incluidas para comparar y comentar los resultados obtenidos.
## Parte 1.
A continuación, se presentarán los estimados de retardo y consumo promedio de potencia aproximado para las dos posibles soluciones al problema 9.4 de [1]. Se evaluará y contrastará ambas soluciones utilizando la teoría de Esfuerzo Lógico, considerando la velocidad y el consumo de potencia dinámica aproximados de cada una.
Para implementar esta lógica, se utilizaron dos enfoques diferentes. En uno de ellos, se emplearon únicamente compuertas simples, mientras que en el otro se utilizó una compuerta compleja junto con un inversor. 
La implementacion realizada con compuertas simple quedó de la siguiente manera: 
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/bc585a32-ba6d-4422-b534-9c71cbfdbb13" width="500"/>
</p>
A continuación se exponen los resultados del análisis realizado utilizando la compuerta mencionada anteriormente, dando como resultado:

$$D = 17.6 \tau$$ 
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/e0fc2c18-4124-45b8-811f-d78d810d38d3" width="500"/>
</p>
Analizando los resultados de la capacitancia para la primera compuerta NOR, se utilizarán transistores con una relación de 2:1, resultando en un tamaño de 6 para el transistor N y 24 para el transistor P, esto debido a las características inherentes de la compuerta. Para la segunda compuerta NOR, los tamaños de los transistores quedaron en 98 para el transistor P y 24 para el transistor N.

Para determinar la potencia se realizaron diferentes iteraciones mediante el uso de un deck, en el cual se fueron variando las entradas, dando como mayor consumo, en un periodo de 10ns, el siguiente resultado:
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/b6262c16-9198-432a-ba3c-664a647fe14c" width="500"/>
</p>


Ahora bien, para la compuerta compuesta con el inversor, se puede análizar utilizando el siguiente esquematico.
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/9a7aaa88-cd45-4575-936c-58a93a860ba8" width="500"/>
</p>

A esta compuerta se le realizan los cálculos presentes en la sigueinte imagen, dando como resultado: 

$$D = 16.54 \tau$$ 

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/7632fd30-2667-4a1d-88e8-a36c6a9e1e75" width="500"/>
</p>

Por lo que se obtiene como resultado que los tamaños de los transistores de entrada tienen que sumar 30 lamda, dada una relación 2:1 se decide que los transistores N sean de tamaño 6 y los P de 24. Con respecto al inversor, los dos transistores deben de sumar 86 lamda, por lo que se decide que los P sean de tamaño 8 y los N de 4.

Para determinar la potencia consumida por la compuerta compuesta se realizó el mismo análisis, variando las entradas y en un periodo de tiempo de 10ns, dando el siguiente resultado:

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/3343c1e0-a316-438c-a3b2-ecf739491113" width="500"/>
</p>


Al tener las dos soluciones propuestas mediante el uso de la teoría del esfuerzo lógico, se concluye que la compuerta compuesta es más rápida, exactamente por 1.06 tau. Por otra parte, con respecto a la potencia se puede observar que la compuerta compuesta, aunque presenta una lógica más compleja, presenta un menor consumo, de 2.81u menos comparado a la compuesta con lógica más simple.

## Parte 2.
Con respecto a los tiempos de propagación y contaminación, se realizaron tanto los cálculos para la compuerta compuesta como para las etapas más pequeñas en el que se estudia el mejor y el peor caso tomando las capacitancias que se deban cargar o descargar en cada caso.

### Compuerta compuesta e inversor 
Con respecto al tiempo de propagación de bajada (tpdf) de la compuerta compuesta se realizaron los siguientes cálculos, donde el caso de estudio será cuando solo dos transistores N esten activos, dejando un retardo de 16RC, donde 
$$RC_{N} = \tau = 17.3 ps$$ 
$$RC_{P} = \tau = 25.48 ps$$ 
De aquí en adelante se asumirá el valor de tau anterior tanto para los transistores N como los P respectivamente.
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/923565bc-24c1-407c-b4af-da3a99a3ff13" width="500"/>
</p>


Para el caso del tiempo de propagación de subida (tpdr), se estudia el caso en el que exite un transitor N activo, por lo que su capacitancia deberá ser cargada. Para este caso el resultado es de: $$20 \tau = 349ps$$ 

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/6c5f8b46-0377-487c-8ced-2f862fb0a312" width="500"/>
</p>

Para los casos de contaminación, se tienen los siguientes casos de estudio.
Para el tcdf, existen por lo menos 3 transistore N activos, reduciendo así la resistencia presente en el camino. Esto da como resultado:

$$ \frac{47}{4} * \tau = 203.23ps$$ 

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/8e8c6f78-3bf7-4754-bb51-7576debb0674" width="500"/>
</p>


El caso del tcdr, no existen transistores N activos, nuevamente reduciendo la resistencia del camino y aparte de esto las capacitancias a cargar, esto deja como resultado: 

$$\frac{17}{2} * \tau = 146.2 ps$$ 

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/8cbf4cc0-ad32-4ca1-9c22-d667a243aa7e" width="500"/>
</p>

Seguidamente, se necesitan estudiar los tiempos de propagación y contaminación del inversor. Las capacitancias y resistencias presentes se puede observar en la siguiente figura:
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/884bd672-171c-4989-9816-79f61ea25e4f" width="500"/>
</p>

Teniendo esta información, se pueden calcular los tiempos de subida como de bajada, pero en este caso no existe un peor o mejor caso, ya que si el transistores P está activo el N no lo está y viceversa. Esto da un resultado, y tomando en cuenta la capacitancia de carga presente, los tiempos de subida y bajada son los siguientes respectivamente:

$$76.44 ps$$

$$51.6 ps$$ 

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/36b06cba-7659-42f4-89a4-7e525c197012" width="500"/>
</p>

Ya obteniendo tanto los tiempos de la compuerta compuesta como los del inversor, se puede hacer una estimación del tiempo de retardo que se puede obtener tanto de subida y bajada en los mejores y peores casos, estos resultados son los siguientes:

$$tpdf = 276.8 ps $$

$$tcdf = 349 ps $$

$$tpdr = 203.23 $$

$$tcdr = 146.2 $$

### Compuertas simples
Al analizar las compuertas simples, podemos determinar los tiempos de propagación y de contaminación tanto en la subida como en la bajada de la señal para la primera compuerta NOR.

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/9ba7a8b6-aaab-4631-84e8-16eaa4d2bc4e" width="500"/>
</p>

Debido a que está compuesto de 3 NOR, este análisis es el mismo para la compuerta que tiene como entrada C y D.

Sin embargo, para la última NOR determinar estos tiempos es diferente, ya que vamos a depender de las dos compuertas anteriores, si se desea determinar los tiempos pero para la salida se debe de realizar de la siguiente manera. Suponiendo que A y B prima son las salidas de las primera dos compuertas.

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/9ceb8edb-0a8f-4b3d-ac50-f0ea1f6fe432" width="500"/>
</p>

Al determinar el los tiempos de la ultima compuerta se puede analizar lo siguiente:

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/f58a16dd-08fe-4395-9f0a-ddab12dbd317" width="500"/>
</p>
Para un total de:

$$435.04 ps $$

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/882970ca-baf4-4d0b-b77d-c3bf775c9f7c" width="500"/>
</p>
Sumando estos valores da:

$$383.14 ps $$

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/04f0d9b2-c636-446d-a908-9555ab663a16" width="500"/>
</p>
Lo cual su suma da:

$$298.96 ps $$

<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/7b9be5c0-2892-49c3-b164-1072187cfede" width="500"/>
</p>
Dando como resultado:

$$394.11 ps $$

## Parte 3.
Para verificar la funcionalidad eléctrica y lógica de los esquemáticos propuestos como solución, se montaron los circuitos a nivel de transistores siguiendo los diseños proporcionados a nivel de compuertas. 
Se realizaron mediciones de los tiempos para la compuerta compuesta y las simples una vez armados los circuitos. Antes de las mediciones, se verificó la correcta conexión de los componentes y se aseguró un suministro de energía adecuado. Dando como resultado los siguientes tiempos.
<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/31cd64a2-3e5e-4547-941f-83252ba0ee81" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/a3026f4f-7a8c-4dea-b6ef-8decaf3e95a9" width="400" /><br>
    <em>Tiempos de propagación de la compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/5c2bdae2-096f-4d4a-aae8-8462133ff132" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/0b43a312-e2c5-48ca-8b68-da0d755e30b1" width="400" /><br>
    <em>Tiempos de contaminación de la compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/c39b46da-6a98-491f-b0a4-98da1df38584" width="500"  /><br>
     <em>Tiempos de propagación y contaminación de la compuerta simple</em>
</p>

Comparando los tiempos medidos con los de Elmore, nos podemos dar cuenta que tienen un porcentaje de error aceptable. En la siguiente tabla se pueden observar las comparaciones.
| Tiempo | Elmore | Simulado |
|--------------|--------------|------------|
| C. tpdf      | 276.8 ps     | 215 ps     |
| C. tcdf      | 203.23 ps    | 212 p      |
| C. tpdr      | 349 ps       | 269 p      |
| C. tcdr      | 146.2 ps     | 164 p      |
| S. tpdf      | 331.24 ps    | 316 ps     |
| S. tcdf      | 95.15 ps     | 76.2 ps    |
| S. tpdf      | 190.3 ps     | 176 ps     |

Dados estos resultados y los tiempos de retardo obtenidos con la teoría del esfuerzo lógico, no se puede caracterizar por completo el comportamiento de las compuertas, ya que los tiempos de retardo dependen totalmente de las entradas y de las capacitancias parásitas presentes. Esto llega a variar los tiempos dando un mejor y peor caso, por lo que se puede decir que la teoría del esfuerzo lógico es una buena aproximación, siendo más optimista y Elmore una aproximación más pesimista.   

## Parte 4.
Utilizando los caminos de Euler se determino que la mejor manera de realizar el diagrama de palitos para la compuesta queda de la siguiente manera:

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/38b8e662-bd3a-4278-8faa-18c39fa64ea0" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/700acf2d-a541-490d-aaed-427095f0041b" width="270" /><br>
</p>

Ahora bien, para la NOR como se sabe que las 3 compuertas van a ser relativamente iguales se determinó la mejor manera, dando como resultado: 
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/b2bf00b5-8b88-4d3c-9430-292c6a9db2cf" width="200"/>
</p>

## Parte 5.
El proceso de diseño del layout de las soluciones comenzó con un análisis del diagrama de palitos y del esquemático a nivel de transistores. Esta etapa inicial fue crucial para obtener una visión clara de cómo podrían ser acomodados en el diseño final.

Como podemos observar en las siguientes figuras, después de la creación de las compuertas, se procedió a realizar tres verificaciones cruciales: DRC (Design Rule Check), LVS (Layout vs. Schematic) y LPE (Layout Parasitic Extraction). 

Una vez que las soluciones pasaron estas verificaciones sin errores, se crearon las compuertas finales, incluyendo las capacitancias parasitarias de cada transistor, entre otras consideraciones importantes. 

Adicionalmente se agregaron las imagenes de las simulaciones de las compuertas, con sus tiempos respectivos.
<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/4c7133d2-bca8-4f9a-a59f-befafdd3b4c4" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/edd113d4-0a30-43da-84f0-7c1c08c015c9" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/c0ae6b6e-0136-4dac-840e-6f78e1d1771d" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/0542c41a-9182-4b4b-9a28-8bef00380e99" width="250" /><br>
    <em>Esquemático y post-trazado con parásitas del inversor</em>
</p>

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/01592264-cc0d-40bf-aca1-25c9ca2710a5" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/cebc9ac9-f850-4dc6-8f69-93b3c7ed8d9c" width="400" /><br>
    <em>Tiempos de propagación con capacitancias parásitas </em>
</p>

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/111e8102-8fd5-46d7-a299-cd6166221da8" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/2f57dc8b-b307-42ec-bc15-c616337b858b" width="400" /><br>
    <em>Tiempos de contaminación con capacitancias parásitas</em>
</p>

Ahora bien, editando el deck se realizó una medición del consumo de la compuerta compuesta, dando como resultado:
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/a3a52c46-df25-4613-b900-05a5c1b5c72d" width="500"/>
</p>

### Simple

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/1a12e0e8-600c-4fd6-94c1-2b3bae498846" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/fe5095bc-6fbd-40f6-b232-f93f95b2b663" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta NOR</em>
</p>   

<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/4975ae96-460b-45cb-8c8a-c85c4c4f1459" width="400" />
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/d5f82842-1560-4cf7-8a8c-46ff292ac707" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta NOR de salida</em>
</p> 


<p float="center">
  <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110353604/975ba088-b4d8-4b97-accc-1d23bc4ce1b4" width="450"  /><br>
     <em>Tiempos de propagación y contaminación de la compuerta simple con capacitancias parásitas</em>
</p>

Realiazando nuevamente una modificación en el deck se determinó la potencia consumida por la compuerta simple.
<p align="center">
    <img src="https://github.com/Rmarino25/Tarea-2_VLSI/assets/110320407/90399cca-15ed-4f4a-9685-35de695b29c4" width="500"/>
</p>

Comparando los tiempos simulados con los esquematicos vs los tiempos de las compuertas con las capacitancias parásitas, lo podemos observar en la siguiente tabla.

| Tiempo    | Esquematico       | Post-trazado    |
|------------|--------------|-----------|
| C. tpdf    | 215 ps       | 275 ps  |           
| C. tcdf    | 212 ps       | 250 ps |           
| C. tpdr    | 269 ps       | 365 ps    |           
| C. tcdr    | 164 ps       | 197 ps  |           
| S. tpdf    | 316 ps       | 358 ps |           
| S. tcdf    | 76.2 ps      | 87 ps  |           
| S. tpdf    | 176 ps       | 192 ps  |           

Analizando los datos podemos ver como el timepo aumentó considerablemente debido a las capacitancias parásitas de las compuertas.

## Parte 6 (Opcional).
Con respecto a la potencia, la aproximación utilizada en el punto anterior no caracteriza del todo la potencia consumida por ambos circuitos, esto debido a que se suponen unos valores de entrada fijos. Para realmente calcular la potencia consumida por estas compuertas, es necesario verificar la probabilidad de que estas entradas estén en "alto". Dado que cada entrada es independiente de las otras, se pueden tomar como equiprobables, por lo que la probablidad de cada entrada está dada por: 

$$P_{entrada} = \frac{1}{4}$$

Ya con la probabalidad de cada entrada, se puede calcular el factor de actividad y utilizando la mayor frecuencia posible, la potencia consumida por cada compuerta, esto mediante la siguiente ecuacuión:

$$P_{s} = \alpha * C * Vdd^2 * f = \alpha * (C_{área} * Area_{chip}) * Vdd^2 * f  $$

Para este caso de estudio en específico, se utiliza un pitch de 4.48 nm y el largo calculado para cada compuertra. Con respecto a la capacitancia por áre se utiliza la siguiente: 

$$450 pF/mm^2$$ 

Por lo tanto, para la compuertas simples se tiene el siguiente cálculo:

$$\frac{63}{256} \times (450 pF/mm^2 \times (4.48 um \times 29 um )) \times (1.8^2) \times 2.23 \times 10^9 = 103.22 uW$$

Y para la compuerta compleja se tiene la siguiente potencia:

$$\frac{63}{256} \times (450 pF/mm^2 \times (4.48 um \times 20 um )) \times (1.8^2) \times 2.37 \times 10^9 = 76.19 uW$$

Dados los resultados anteriores, se observa que la compuerta compleja presenta un menor consumo de potencia aunque esta pueda funcionar a una mayor frecuencia, esto es debido al área total utilizada en las dos propuestas, ya que las compuertas simples ocupan 9 um más que la compuerta compleja, dando así una diferencia de 27.03 uW. 
