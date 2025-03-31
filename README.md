# Tarea-2_VLSI

En la tarea, además de resolver el problema de diseño de circuitos electrónicos y comparar soluciones en términos de retardo y consumo de potencia, se requiere realizar el diseño de layout para ambos circuitos. Esto implica trazar el diseño físico de las compuertas y conexiones en un chip o sustrato, asegurándose de que todas las compuertas tengan el mismo alto y minimizando las capacitancias parásitas entre nodos. El layout debe seguir un trazado optimizado que tenga en cuenta las relaciones de tamaño obtenidas previamente, con un alto máximo definido de 4.48 micrómetros. Además, se deben realizar simulaciones post-trazado con parásitas incluidas para comparar y comentar los resultados obtenidos.
## Parte 1.
A continuación, se presentarán los estimados de retardo y consumo promedio de potencia aproximado para las dos posibles soluciones al problema 9.4 de [1]. Se evaluará y contrastará ambas soluciones utilizando la teoría de Esfuerzo Lógico, considerando la velocidad y el consumo de potencia dinámica aproximados de cada una.
Para implementar esta lógica, se utilizaron dos enfoques diferentes. En uno de ellos, se emplearon únicamente compuertas simples, mientras que en el otro se utilizó una compuerta compleja junto con un inversor. 
La implementacion realizada con compuertas simple quedó de la siguiente manera: 
<p align="center">
    <img src="https://github.com/user-attachments/assets/ab7c24bc-7d95-4cd6-aa5a-26a5c51381e2" width="500"/>
</p>
A continuación se exponen los resultados del análisis realizado utilizando la compuerta mencionada anteriormente, dando como resultado:

$$D = 17.6 \tau$$ 
<p align="center">
    <img src="https://github.com/user-attachments/assets/1ff51bdb-49c0-48f7-8d29-ececc76902b2" width="500"/>
</p>
Analizando los resultados de la capacitancia para la primera compuerta NOR, se utilizarán transistores con una relación de 2:1, resultando en un tamaño de 6 para el transistor N y 24 para el transistor P, esto debido a las características inherentes de la compuerta. Para la segunda compuerta NOR, los tamaños de los transistores quedaron en 98 para el transistor P y 24 para el transistor N.

Para determinar la potencia se realizaron diferentes iteraciones mediante el uso de un deck, en el cual se fueron variando las entradas, dando como mayor consumo, en un periodo de 10ns, el siguiente resultado:
<p align="center">
    <img src="https://github.com/user-attachments/assets/f2a05046-db41-4ea3-868e-594aad6b7fc2" width="500"/>
</p>


Ahora bien, para la compuerta compuesta con el inversor, se puede análizar utilizando el siguiente esquematico.
<p align="center">
    <img src="https://github.com/user-attachments/assets/994fcbe7-86ca-4c63-a6db-652f1591f74a" width="500"/>
</p>

A esta compuerta se le realizan los cálculos presentes en la sigueinte imagen, dando como resultado: 

$$D = 16.54 \tau$$ 

<p align="center">
    <img src="https://github.com/user-attachments/assets/b48206d8-ab6d-4c53-85b1-4deb3ede779c" width="500"/>
</p>

Por lo que se obtiene como resultado que los tamaños de los transistores de entrada tienen que sumar 30 lamda, dada una relación 2:1 se decide que los transistores N sean de tamaño 6 y los P de 24. Con respecto al inversor, los dos transistores deben de sumar 86 lamda, por lo que se decide que los P sean de tamaño 8 y los N de 4.

Para determinar la potencia consumida por la compuerta compuesta se realizó el mismo análisis, variando las entradas y en un periodo de tiempo de 10ns, dando el siguiente resultado:

<p align="center">
    <img src="https://github.com/user-attachments/assets/0546cb60-f514-405c-8e9e-58460b07ac8b" width="500"/>
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
    <img src="https://github.com/user-attachments/assets/cc33d02f-a413-41a1-88ff-a5adbaee1bdf" width="500"/>
</p>


Para el caso del tiempo de propagación de subida (tpdr), se estudia el caso en el que exite un transitor N activo, por lo que su capacitancia deberá ser cargada. Para este caso el resultado es de: $$20 \tau = 349ps$$ 

<p align="center">
    <img src="https://github.com/user-attachments/assets/ade220c4-c152-4193-99af-838def5075e9" width="500"/>
</p>

Para los casos de contaminación, se tienen los siguientes casos de estudio.
Para el tcdf, existen por lo menos 3 transistore N activos, reduciendo así la resistencia presente en el camino. Esto da como resultado:

$$ \frac{47}{4} * \tau = 203.23ps$$ 

<p align="center">
    <img src="https://github.com/user-attachments/assets/3d0687bf-deff-4bf4-bb52-aa5ae97d5581" width="500"/>
</p>


El caso del tcdr, no existen transistores N activos, nuevamente reduciendo la resistencia del camino y aparte de esto las capacitancias a cargar, esto deja como resultado: 

$$\frac{17}{2} * \tau = 146.2 ps$$ 

<p align="center">
    <img src="https://github.com/user-attachments/assets/ee88f419-2f5b-49ed-bd28-c158198f7bf7" width="500"/>
</p>

Seguidamente, se necesitan estudiar los tiempos de propagación y contaminación del inversor. Las capacitancias y resistencias presentes se puede observar en la siguiente figura:
<p align="center">
    <img src="https://github.com/user-attachments/assets/68bfb5be-7e5a-4d12-82f1-bc0ec536c415" width="500"/>
</p>

Teniendo esta información, se pueden calcular los tiempos de subida como de bajada, pero en este caso no existe un peor o mejor caso, ya que si el transistores P está activo el N no lo está y viceversa. Esto da un resultado, y tomando en cuenta la capacitancia de carga presente, los tiempos de subida y bajada son los siguientes respectivamente:

$$76.44 ps$$

$$51.6 ps$$ 

<p align="center">
    <img src="https://github.com/user-attachments/assets/e3d2b0ee-42a4-4547-bdcd-f69cb27c59fb" width="500"/>
</p>

Ya obteniendo tanto los tiempos de la compuerta compuesta como los del inversor, se puede hacer una estimación del tiempo de retardo que se puede obtener tanto de subida y bajada en los mejores y peores casos, estos resultados son los siguientes:

$$tpdf = 276.8 ps $$

$$tcdf = 349 ps $$

$$tpdr = 203.23 $$

$$tcdr = 146.2 $$

### Compuertas simples
Al analizar las compuertas simples, podemos determinar los tiempos de propagación y de contaminación tanto en la subida como en la bajada de la señal para la primera compuerta NOR.

<p align="center">
    <img src="https://github.com/user-attachments/assets/e32a5360-613e-4b73-a1b0-12198448453f" width="500"/>
</p>

Debido a que está compuesto de 3 NOR, este análisis es el mismo para la compuerta que tiene como entrada C y D.

Sin embargo, para la última NOR determinar estos tiempos es diferente, ya que vamos a depender de las dos compuertas anteriores, si se desea determinar los tiempos pero para la salida se debe de realizar de la siguiente manera. Suponiendo que A y B prima son las salidas de las primera dos compuertas.

<p align="center">
    <img src="https://github.com/user-attachments/assets/491f8855-2e6a-4cfd-85ef-b45f7b751bfb" width="500"/>
</p>

Al determinar el los tiempos de la ultima compuerta se puede analizar lo siguiente:

<p align="center">
    <img src="https://github.com/user-attachments/assets/1bc61b86-daca-4efd-a99c-ae40320fd148" width="500"/>
</p>
Para un total de:

$$435.04 ps $$

<p align="center">
    <img src="https://github.com/user-attachments/assets/e3e26512-16c4-4633-ae52-f7a6b408534f" width="500"/>
</p>
Sumando estos valores da:

$$383.14 ps $$

<p align="center">
    <img src="https://github.com/user-attachments/assets/b5a097a3-fe05-4361-b7e9-b4733f40cd66" width="500"/>
</p>
Lo cual su suma da:

$$298.96 ps $$

<p align="center">
    <img src="https://github.com/user-attachments/assets/3b5eaca6-a2fa-487a-820a-0e3c46ee05c5" width="500"/>
</p>
Dando como resultado:

$$394.11 ps $$

## Parte 3.
Para verificar la funcionalidad eléctrica y lógica de los esquemáticos propuestos como solución, se montaron los circuitos a nivel de transistores siguiendo los diseños proporcionados a nivel de compuertas. 
Se realizaron mediciones de los tiempos para la compuerta compuesta y las simples una vez armados los circuitos. Antes de las mediciones, se verificó la correcta conexión de los componentes y se aseguró un suministro de energía adecuado. Dando como resultado los siguientes tiempos.
<p float="center">
  <img src="https://github.com/user-attachments/assets/2456b8e4-bf74-4fad-a007-ba92966d01dd" width="400" />
  <img src="https://github.com/user-attachments/assets/2803d318-d528-41f9-aa00-52541c4e3123" width="400" /><br>
    <em>Tiempos de propagación de la compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/user-attachments/assets/0b189970-1827-4aa8-b590-457240ed3330" width="400" />
  <img src="https://github.com/user-attachments/assets/79c06728-d344-45be-b8e9-2533aa17d80b" width="400" /><br>
    <em>Tiempos de contaminación de la compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/user-attachments/assets/f6f40392-64dd-4838-853e-42851cbabab8" width="500"  /><br>
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
  <img src="https://github.com/user-attachments/assets/13b9719d-6bc2-4429-91f1-9e7d18d23249" width="400" />
  <img src="https://github.com/user-attachments/assets/3a3aaf33-76b0-4e13-ba32-fe9fecf6d060" width="270" /><br>
</p>

Ahora bien, para la NOR como se sabe que las 3 compuertas van a ser relativamente iguales se determinó la mejor manera, dando como resultado: 
<p align="center">
    <img src="https://github.com/user-attachments/assets/a42c9b1f-84da-4db4-bbee-4a6c0b23e650" width="200"/>
</p>

## Parte 5.
El proceso de diseño del layout de las soluciones comenzó con un análisis del diagrama de palitos y del esquemático a nivel de transistores. Esta etapa inicial fue crucial para obtener una visión clara de cómo podrían ser acomodados en el diseño final.

Como podemos observar en las siguientes figuras, después de la creación de las compuertas, se procedió a realizar tres verificaciones cruciales: DRC (Design Rule Check), LVS (Layout vs. Schematic) y LPE (Layout Parasitic Extraction). 

Una vez que las soluciones pasaron estas verificaciones sin errores, se crearon las compuertas finales, incluyendo las capacitancias parasitarias de cada transistor, entre otras consideraciones importantes. 

Adicionalmente se agregaron las imagenes de las simulaciones de las compuertas, con sus tiempos respectivos.
<p float="center">
  <img src="https://github.com/user-attachments/assets/2416d6ae-f1a7-440d-8684-dcfbc8b86591" width="400" />
  <img src="https://github.com/user-attachments/assets/0d832a62-4d54-43e7-b478-4b07759a8042" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta compuesta</em>
</p>

<p float="center">
  <img src="https://github.com/user-attachments/assets/5a143dc2-0dc2-40fd-8941-3bdafa903bb2" width="400" />
  <img src="https://github.com/user-attachments/assets/f258ab53-f85d-4839-a7fc-711c308a696d" width="250" /><br>
    <em>Esquemático y post-trazado con parásitas del inversor</em>
</p>

<p float="center">
  <img src="https://github.com/user-attachments/assets/579d6959-a615-4b2c-948f-351f07bad9d7" width="400" />
  <img src="https://github.com/user-attachments/assets/25874ded-e092-424c-8659-711f5c1af8ed" width="400" /><br>
    <em>Tiempos de propagación con capacitancias parásitas </em>
</p>

<p float="center">
  <img src="https://github.com/user-attachments/assets/09004777-89ac-4ce9-a2d0-df9b8341c928" width="400" />
  <img src="https://github.com/user-attachments/assets/4b682371-4022-43b5-93fd-47a1cadaa796" width="400" /><br>
    <em>Tiempos de contaminación con capacitancias parásitas</em>
</p>

Ahora bien, editando el deck se realizó una medición del consumo de la compuerta compuesta, dando como resultado:
<p align="center">
    <img src="https://github.com/user-attachments/assets/80b952b1-d3a6-4a4b-9a74-c35c41ddbf5a" width="500"/>
</p>

### Simple

<p float="center">
  <img src="https://github.com/user-attachments/assets/8bf26ab7-bf77-440d-b435-9d225db57e85" width="400" />
  <img src="https://github.com/user-attachments/assets/6ae7633a-ca82-4428-bf8a-3368ac601e8f" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta NOR</em>
</p>   

<p float="center">
  <img src="https://github.com/user-attachments/assets/91a97d59-03ee-4d80-a8c9-239fae83d905" width="400" />
  <img src="https://github.com/user-attachments/assets/d1856f32-b99d-49f3-9645-da969d1d4ece" width="400" /><br>
    <em>Esquemático y post-trazado con parásitas de la compuerta NOR de salida</em>
</p> 


<p float="center">
  <img src="https://github.com/user-attachments/assets/8eca5896-dc74-4e64-bc9e-9c2277c9d9a5" width="450"  /><br>
     <em>Tiempos de propagación y contaminación de la compuerta simple con capacitancias parásitas</em>
</p>

Realiazando nuevamente una modificación en el deck se determinó la potencia consumida por la compuerta simple.
<p align="center">
    <img src="https://github.com/user-attachments/assets/2681e8ca-ddeb-4469-b211-3fbbf2ab5123" width="500"/>
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
