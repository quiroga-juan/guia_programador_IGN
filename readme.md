<h1 align="center">
Guía de ejercicio para el programador IGN 
</h1>

<p> 
<img src="images/IGN_Argentina.png" align="right" width="350">
</p>

## Objetivos

* La guía tiene como objetivo desarrollar algoritmos, programas/rutinas y/o clases que son utilizadas a menudo en el **IGN (Depto. de Marcos de Referencia)**.

* Se pide que los programas sean lo más modulares posibles.

## Requerimientos de software:

### Para Nivel Básico e Intermedio
* Python (la versión con la que se esté trabajando en ese momento, por ejemplo: v.2.7). En el caso que se pueda, agregar la ruta del programa al **PATH** del sistema ([Tutorial](https://answers.microsoft.com/es-es/windows/forum/all/windows-10-variables-de-entorno-windows-10-version/703ea5fa-1db4-46da-8ff7-6261140bf58b)). 
* Un entorno de trabajo para correr los programas. En este caso se puede utilizar: Visual Code Studio, PyCharm, o cualquier entorno de trabajo en el que sea cómodo trabajar.
* Un editor de texto plano, por ejemplo: VIM, NotePad++, Sublime, etc.
* Software de control de versiones de archivos para operar con GIT(https://git-scm.com/), por ejemplo GitHub https://github.com/ de escritorio o consola, (se requiere una cuenta).

### Para Nivel Avanzado

* Base de datos PostgreSQL con alguna interfaz gráfica. Por ejemplo [pgAdmin](https://www.pgadmin.org/).

## Ejercicios Python - Nivel Básico

### GitHub

0. Una vez que se tienen los requerimientos de software, realizar un Fork de este repositorio y trabajar en el repositorio propio de GitHub. [Tutorial](https://www.youtube.com/watch?v=9YUaf-uxuRM).

### Manejo de archivos y directorios
Poner cada ejercicio en una carpeta diferente

1. Crear un archivo y nombrarlo como: 
```
IGN_<fecha_actual>.txt
```

*Nota*: \<fecha_actual> tiene el formato ddmmyyyy. Ejemplo: IGN_01032020.txt. Utilizar libreria *datetime* para obtener la fecha. 

2. Crear un archivo, nombrarlo como el ejercicio 1 y agregarle el siguiente contenido:

```
	1.<hora>:<min>:<seg>
	2.<hora>:<min>:<seg>+1
	3.<hora>:<min>:<seg>+2
	...
	50.<hora>:<min>:<seg>+49
```

Se le suma 1 segundo a cada linea anterior. Utilizar el ciclo *for* para imprimir.
El archivo quedaría con un formato:
```
	1.10:23:01
	2.10:23:02
	3.10:23:03
	...
	50.10:23:50
```
*Nota*: \<hora>\<min>\<seg> son fijos. Por ejemplo \<hora>=10; \<min>=23; \<seg>=1, utilizando variables de tipo entero. 

3. Crear un archivo, nombrarlo como el ejercicio 1 y agregarle el siguiente contenido:

```
	1.<hora>:<min>:<seg>
	2.<hora>:<min>:<seg>+1
	3.<hora>:<min>:<seg>+2
	...
	10.<hora>:<min>:<seg>+9
```
*Nota*: En este caso \<hora>\<min>\<seg> son del momento que se ejecuta el programa. Usar la libreria time para utilizar variables de tipo time.

4. Crear directorios en la carpeta de trabajo que tengan como nombre el numero de año: comenzando desde el año 1980 y terminando en el 2020, pasando por todos los años intermedios.

5. Crear directorios en la carpeta de trabajo que tengan como nombre el número de año: comenzando desde el año 1980 y terminando en el 2020, pasando por todos los años intermedios. Luego en cada carpeta, crear 12 subcarpetas que tengan como nombre los meses del año.


## Ejercicios Python - Nivel Intermedio
> Requiere las siguientes librerias: [zip](https://docs.python.org/2.7/library/zipfile.html), [gzip](https://docs.python.org/2/library/gzip.html).
### Manejo de archivos y directorios

6. A partir del ejercicio 5:

En cada carpeta del mes agregar un archivo con nombre:
```
IGN_<año><mes><dia><hora><min><seg>.txt
```
*Nota*: Las variables \<año>\<mes> son las mismas de donde se encuentra ubicado el archivo. Las variables \<hora>\<min>\<seg> son las del día de hoy (conviene trabajar con variables de tipo datetime).


### Manejo de expresiones regulares
> Requiere las siguientes librerias: [re](https://docs.python.org/2/library/re.html).

7. Reconocimiento de hora, minutos y segundos del archivo IGN_\<fecha_actual>.txt del ejercicio 2. Con expresiones regulares parsear cada linea obteniendo \<hora>,\<min> y \<seg> en variables separadas.

8. A partir del ejercicio 7, imprimir el contenido que se obtuvo con las expresiones regulares con el siguiente formato:

```
<hora> <min> <seg>
<hora> <min> <seg>
<hora> <min> <seg>
...
<hora> <min> <seg>
```
