## INTRODUCCION ##


En en este taller vamos a realizar un ejercicio completo con Qgis en el que se va a realizar operaciones a tablas, asignación de datos mediante la unión de tablas y capas, simbolización de nuestras capas y por último la publicación de nuestros resultados vía web.

El objetivo es la representación de resultados electorales en cataluña.

Algunos ejemplos similares son: 

 [Election 2015 results MAPPED: 2015 full list](http://www.telegraph.co.uk/news/general-election-2015/11584325/full-results-map-uk-2015.html)




#1. Cargar capas shape y tablas

•	Para la realización de los ejercicios hay que descargarse y descomprimir los siguientes archivos:

[Comarcas2014](/datos/comarcas_14.rar): Comarcas de Cataluña

[Comarcas2014grid](/datos/capa_grid_base.rar): Comarcas2014grid: comarcas de Cataluña en formato grid (hexágonos)

[Tablas](/datos/tablas.rar): Tablas de resultados electorales periodo 2003-2012 en formato .dbf


 Cargamos las capas y tablas a Qgis : ![gitHub fork](/img/btn_add_capas.png)


![gitHub fork](/img/capas.png)


![gitHub fork](/img/menu_add.png)

Una vez finalizado el proceso anterior, el proyecto tendrá este aspecto.


![gitHub fork](/img/qgis_capas_cargadas.png)


#2. Operaciones entre columnas de una tabla.

Añadir campo nuevo a la tabla 12.dbg llamado “*porc_votos*” de tipo numérico con la calculadora de campos de Qgis ![gitHub fork](/img/calculadora_campos.JPG)
	
Calculamos el nuevo campo sumando los campos de CIU+ERC+CUP.

El menú que realiza las operaciones anteriores tiene que quedar así.
![gitHub fork](/img/add_campos.png)

Comprobar como al final de la tabla 12.dbg nos ha añadido el nuevo campo y lo ha rellenado con la operación de sumar los campos "CIU" + "ERC" + "CUP"

![gitHub fork](/img/campo_relleno.png)


#3. Creación de grid-malla (cartograma)

Este paso consiste en la creación de una malla similar la del objetivo con el fin de 

Para pode generar la malla, es necesario instalar el complemento [mmqgis](http://michaelminn.com/linux/mmqgis/). Desde el menú "complementos/Administrar y gestionar complementos" buscamos el nombre complemento a instalar y presionamos sobre la botón "INSTALAR COMPLEMENTO"

![gitHub fork](/img/mmqgis.png)

Una vez instalado aparecerá un nuevo menú MMQGIS : 

![gitHub fork](/img/menu_mmqgis.png)


Para generar el Grid, activamos la opción "Create Grid Lines Layer"

![gitHub fork](/img/menu_mmqgis_3.png)

En el siguiente menú, aplicamos las opciones de la siguiente imagen: 

![gitHub fork](/img/menu_mmqgis_4.png)

![gitHub fork](/img/menu_mmqgis_5.png)

El resultado será una malla hexagonal y una vez añadida a nuestra vista tendrá el siguiente aspecto:

#4. Añadir información de una tabla al grid

Para la realización de este paso, vamos a utilizar la capa que está en el fichero comarcas2014grid.zip ya que contiene los campos necesarios para poder transferirle información.

![gitHub fork](/img/malla_inicial.png)

La tabla origen es la **12.dbg** y la capa destino es la capa **capa_ grid_base**

Para realizar esta tarea, utilizamos  el menú Union.
 1.- Abrimos las propiedades de la capa: (Botón derecho presionando sobre la capa)

![gitHub fork](/img/menu_union.png)

 2.- Propiedades/Uniones: En el menú *Añadir unión vectorial* asignamos las opciones según la siguiente imagen:

![gitHub fork](/img/union.png)

![gitHub fork](/img/union_campos.png)

Aplicamos la unión y el resultado será la unión entre la tabla **12.dbg** y la capa **capa_ grid_base** tal y como se muestra en la siguiente imagen:

![gitHub fork](/img/union_resultado.png)

Los campos nuevos se añaden al final de la tabla (color amarillo)

#5. Crear simbología

Para simbolizar nuestros resultados, accedemos a las propiedades de la capa y en la opción Estilo asignamos la simbología.

Vamos a crear una simbología por un solo campo. Para ello, seleccionamos las opciones resaltadas en amarillo de la siguiente imagen: 

![gitHub fork](/img/simbolizar_graduado.png)

Si queremos simbolizar por dos campos, tenemos que asignar reglas de estilo. En las siguientes imágenes se muestra un ejemplo.


![gitHub fork](/img/simbolizar_reglas.png)

Seleccionamos "PROVINCIAL" = '08' y volvemos a refinar una regla a intervalos

![gitHub fork](/img/simbolizar_reglas_2.png)

El resultado será similar a la siguiente imagen:

![gitHub fork](/img/simbolizar_reglas_3.png)

#6. Crear webmapping

A continuación vamos a generar una aplicación web con nuestra capa que nos permita visualizar los resultados de nuestro trabajo. Para ello, vamos a utilizar el complemento "qgis2web".

![gitHub fork](/img/complemento_qgis2web.png)

Una vez instalado, abrimos el menú "Export to web map" y generamos la aplicación.

Para el ejemplo, seleccionar los parámetros utilizados en la siguiente imagen:

![gitHub fork](/img/webmap.png)

Una vez finalizado la exportación, la aplicación nos genera un directorio con esta estructura interna

![gitHub fork](/img/qgis2web_estructura_ficheros.png)
 

###pero.. ¿como visualizo mis datos en la web?###

Tan sólo nos queda subir nuestros ficheros a algún repositorio web y llamar a nuestro fichero index.html. Para nuestro ejemplo hemos utilizado  [neocities](https://neocities.org/) que nos permite subir nuestros ficheros hasta un límite de 100 MB de forma gratuita.

Para subir nuestros ficheros, basta con crearse una cuenta almacenar los ficheros generados por la aplicación qgis2web.

![gitHub fork](/img/neocities.png)


[aquí](http://servigis.neocities.org/qgis2web_2015_10_08-14_11_27/index.html) podemos ver el resultado de nuestro ejercicio. 




