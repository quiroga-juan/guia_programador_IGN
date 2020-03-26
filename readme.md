
<img src="images/IGN_Argentina.png" alt="IGN" width="350"/>

# Mini-Guía para programador IGN 

## Objetivos

* La guía tiene como objetivo desarrollar algoritmos, programas/rutinas y clases que son utilizadas a menudo para desarrollar tareas del **IGN (Depto. de Marcos de Referencia)**.

* Se quiere que los programas sean lo más modulares posibles y sin repetición de código.

## Requerimientos de software:

* Python (la versión con la que se esté trabajando en ese momento, por ejemplo: v.2.7). En el caso que se pueda, agregar la ruta del programa al **PATH** del sistema. 
* Un entorno de trabajo para correr los programas. En este caso se puede utilizar: Visual Code Studio, PyCharm, o cualquier entorno de trabajo en el que sea cómodo trabajar.
* Un editor de texto plano, por ejemplo: VIM, NotePad++, Sublime, etc.
* Software de control de versiones de archivos para operar con GIT(https://git-scm.com/), por ejemplo GitHub https://github.com/ de escritorio o consola, (se requiere una cuenta).

## Ejercicios

### Python - Nivel Básico
1. Una vez que se tienen los requerimientos de software, realizar un Fork de este repositorio.


2. Imprimir por consola 
```
Hola mundo!
```

#### Manejo de archivos y directorios

3. Abrir un archivo nuevo, nombrarlo como: 
```
IGN_<fecha_actual>.txt
```
*Nota*: \<fecha_actual> es ddmmyyyy. Ejemplo: IGN_01032020.txt. Utilizar libreria *datetime* para obtener la fecha. 

4. Abrir ese mismo archivo y agregarle el siguiente contenido:

```
	1.<hora><min><seg>
	2.<hora><min><seg>+1
	3.<hora><min><seg>+2
	...
	50.<hora><min><seg>+49
```
*Nota*: \<hora>\<min>\<seg> son fijos. Por ejemplo \<hora>=10; \<min>=30; \<seg>=10. Trabajar *hora*, min, seg y el delta como variables de tipo entero.

5. Abrir el archivo del ejercicio anterior y agregarle el siguiente contenido:

```
	1.<hora><min><seg>
	2.<hora><min><seg>+1
	3.<hora><min><seg>+2
	...
	50.<hora><min><seg>+49
```
*Nota*: \<hora>\<min>\<seg> son fijos. Por ejemplo \<hora>=10; \<min>=30; \<seg>=10. Trabajar *hora*, min, seg y el delta como variables de tipo datetime.

6. Crear directorios en la carpeta de trabajo que tengan como nombre el numero de año: comenzando desde el año 1980 y terminando en el 2020, pasando por todos los años intermedios.

7. Crear directorios en la carpeta de trabajo que tengan como nombre el número de año: comenzando desde el año 1980 y terminando en el 2020, pasando por todos los años intermedios. Luego en cada carpeta, crear 12 subcarpetas que tengan como nombre los meses del año y a su vez en los meses pares agregar un archivo con nombre:
```
IGN_<año><mes><dia><hora><min><seg>.txt
```

### Python - Nivel Intermedio

8. Crear directorios en la carpeta de trabajo que tengan como nombre el número de año: comenzando desde el año 1980 y terminando en el 2020, pasando por todos los años intermedios. Luego en cada carpeta, crear 12 subcarpetas que tengan como nombre los meses del año y a su vez en los meses pares agregar un archivo con nombre:
```
IGN_<año><mes><dia><hora><min><seg>.txt
```


#### Manejo de expresiones regulares
> Requiere las siguientes librerias: re.

- Reconocimiento de hora, minutos y segundos del archivo IGN_\<fecha_actual>.txt. Con expresiones regulares. Parsear cada linea obteniendo \<hora>,\<min> y \<seg> en variables separadas.
