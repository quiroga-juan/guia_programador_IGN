#Configurando Git y GitHub en OSX y Linux
##GIT
[GIT](https://git-scm.com/) en un software de control de versiones que fue diseñado por [Linus Torvalds](https://es.wikipedia.org/wiki/Linus_Torvalds), desde sus inicios fue pensado para que operara cono un software de bajo nivel y que otros se encargaran de crear la interfaz grafica o front-end. pero hoy en día GIT es un software de control de versiones con funcionalidad plena, 100% en la terminal. Si bien es cierto que hoy en día existen varios software con interfaz gráfica, que nos permiten operar con GIT, [aquí lista de Guis para Git](https://git-scm.com/downloads/guis), en este post nos concentraremos en la instalación y configuración de GIT desde la terminal tanto en Linux como en OSX.
###Instalando GIT en Linux
La instalación de GIT en Linux es extremadamente fácil, dependiendo de la versión de Linux que estés usando va a cambiar el gestor de paquetes que necesitemos usar, pero antes de instalar primero verifiquemos si es que ya esta instalado, para la cual abrimos nuestra terminal y ejecutamos el siguiente comando:
>`~ git --version`

Si obtenemos como respuesta: `git version X.X.X` significa que ya lo tenemos instalado, pero si obtenemos algo como `git command not found` procedemos con la instalación.

Debian/Ubuntu
>`~ apt-get install git`

Fedora
>
```BASH
~ yum install git (up to Fedora 21)
~ dnf install git (Fedora 22 and later)
```

Gentoo
>`~ emerge --ask --verbose dev-vcs/git`

Arch Linux
>`~ pacman -S git`

openSUSE
>`~ zypper install git`

FreeBSD
>
```BASH
~ cd /usr/ports/devel/git`
~ make install`
```

Solaris 11 Express
>`~ pkg install developer/versioning/git`

OpenBSD
>`~ pkg_add git`

###Instalando GIT en OSX
Para instalar GIT en OSX lo mejor es dirigirnos al siguiente enlace [https://git-scm.com/download/mac](https://git-scm.com/download/mac), se descargará un paquete el cual instalamos como cualquier aplicación en Mac, Para comprobar que la instalación quedo correcta, abrimos nuestra terminal y ejecutamos el comando que se muestra a continuación y debemos tener como respuesta la versión de GIT que instalamos.
>
```BASH
~ git --version
git version 2.8.1 (Apple Git-66)
```

###Configurando GIT
Las instrucciones para configurar GIT son las mismas para Linux y para OSX, lo que debemos configurar en GIT en nuestro nombre y nuestro email, pero el email es importante que sea uno valido pues será el mismo que usaremos para registrarnos en GitHub mas adelante en este post, para configurar nuestro nombre ejecutamos el siguiente comando en la terminal.
>`~ git config --global user.name "Tu Nombre"`

Para configurar nuestro email
>`~ git config --global user.email "correo@dominio.com"`

Ahora estamos listos para usar GIT de forma local, pero la verdadera potencia de GIT es que permite el trabajo colaborativo en forma distribuida y el complemento perfecto para poder llevar a cabo estas tareas es [GitHub](https://github.com/).

##GitHub
[GitHub](https://github.com/) es una plataforma web que permite administrar proyectos usando el control de versiones GIT, facilitando el desarrollo colaborativo de software.

###Creando nuestra cuenta en GitHub
Para crear nuestra cuenta ingresamos a la siguiente url: [https://github.com/](https://github.com/) y completamos los datos del registro recuerda que debes usar el mismo correo que usaste para configurar GIT en tu equipo.
![SignUp GitHub](https://www.evernote.com/l/ACtS6Qs31OxMrKdk3kwhuru4MYWDtsAC1-UB/image.png)

###Conectando nuestro equipo con GitHub por medio de SSH
Una vez completado nuestro registro en GitHub, debemos indicarle a GitHub de que equipo o equipos nos comunicaremos con el, esta comunicación la haremos por medio de [SSH](https://es.wikipedia.org/wiki/Secure_Shell) (Secure Shell), para esto debemos crear un par de llaves SSH una publica y otra privada. Esto es algo que asusta a algunos desarrolladores que recién comienzan en esto de GIT y GitHub.
Comencemos con la creación de las llaves, para esto vamos a nuestra terminal y revisamos que exista la carpeta `.ssh`dentro del `$HOME`
>
```BASH
~ ls -a | grep .ssh
```

Si obtuvimos como respuesta `.ssh` significa que ya tenemos la carpeta, si no tenemos ningún resultado, debemos crear la carpeta con el siguiente comando:
>
```BASH
~mkdir .ssh
# si consulatamos ahora por la carpeta
~ ls -a | grep .ssh
.ssh # <-- ahora obtenemos la respuesta correcta
```

Con nuestra carpeta `.ssh` lista, crearemos nuestras llave publica y privada, en nuestra terminal ejecutamos el siguiente comando:
>
```BASH
~ ssh-keygen -t rsa -b 4096 -C "correo@domino.com"
# Creates a new ssh key, using the provided email as a label
Generating public/private rsa key pair.
```

Cuando aparezca en el Prompt "Enter a file in which to save the key," presiona Enter. Así aceptaras la ubicación por defecto.
>
```BASH
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```

Luego el Prompt te pedirá ingresar una password, las dejaremos en blanco, así que solo presiona Enter y terminaremos.
>
```BASH
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

Con estos pasos ya hemos creado nuestro par de llaves, lo podemos verificar, revisando el contenido de la carpeta `.ssh`, debemos encontrar ahí dos archivos uno llamado `id_rsa` y otro llamado `id_rsa.pub`, este último archivo es la llave pública y es la que compartiremos. El archivo sin el `.pub` es la llave privada y no se debe compartir con nadie.
Ahora agregaremos nuestra llave ssh al ssh-agent.
Nos aseguramos que el agente esta habilitado:
>
```BASH
# start the ssh-agent in the background
~ eval "$(ssh-agent -s)"
Agent pid 59566
```

Con el agente habilitado, agregamos nuestra llave privada al ssh-agent:
>
```BASH
~ ssh-add ~/.ssh/id_rsa
```

Ahora estamos listos para nuestro último paso, agregar nuestra llave publica n nuestro perfil de GitHub. Antes de ir a nuestro perfil copiaremos la llave publica de la siguiente forma:
>
```BASH
~ cat ~/.ssh/id_rsa.pub
```

Obtendremos el siguiente resultado, el cual copiaremos, teniendo cuidado de no incluir ningún espacio en blanco al principio o al final.
>
```BASH
ssh-rsa AAAAB3NzaC1yc2EAAAADAQ7flDNJhkz98tF/djabnPKkCtjMyBu/Q/WDnkgI1Qs1piLakU26/AlfRk+BkSuSeRtQ2Yl9Jyb5jPrTU2S8bobI3x02qhfcXEBJVCluBuiHWNB5ZihXf3COEnRIHyNR7axWqbByyuPIK5mQI5JhHYZZLVe/YSr1sGcwtNW7nXnAxuz/IOujMuEG82kmDqANIptUNs7q7vYTo+9KTaGBMLFG3YtozlQrUdpzSYMxgGjdH5AlJR+FHpEyBvW9RlQPMSnfFDd202M4pxJ66zGwN1qmbtK0ALXX5rOfd6uyh05qXxhQI1ZNj606UwhFF+h06pNpPYFKtzvBHp2HdDHVr1gCu6BjPWVy7Pl6Xo5hYiVJJsWNOXvXMk5Wavl5VIhKEjrUbdft9PHBU31qeKxbf8Q== correo@dominio.com
~
# PD: está no es una llave real, es solo para ejemplificar.
```

![cat ~/.ssh/id_ras.pub](https://www.evernote.com/l/ACuDf5GEMx1HCpcl3cCNh16_V1T9tH7-78oB/image.png)

Con nuestra llave pública en el porta papeles no dirigimos a: [https://github.com/settings/profile](https://github.com/settings/profile) o podemos hacer click en nuestra foto de perfil ubicada en el extremo superior derecho y seleccionar la opción `settings`
![tu perfil](https://www.evernote.com/l/ACtcEO6yfTlPS5QbLKoBQDQX_GRdl3PGuhcB/image.png)

Ahora seleccionamos la opción `SSH and GPG keys`
>![SSH and GPG keys](https://www.evernote.com/l/ACvARHoUq_tO5a58JyZKE9CSlGUgiffYU50B/image.png)

Hacemos click en `New SHH key`
>![New SHH key](https://www.evernote.com/l/ACvXK9r6PaFAXZWG66V_8diwzz_4L40RLmkB/image.png)

Llego el momento de pegar nuestra llave publica, lo hacemos según la imagen de abajo, en el campo `Title` usar un nombre descriptivo del equipo en el que generaron la llave. damos click en `Add SSH key`.
>![add SSH key](https://www.evernote.com/l/ACuGN3LsMdNLgb3I3c_8OUY-Xa5u4ChVx3EB/image.png)

Si el resultado fue exitoso obtendrán un resultado parecido al siguiente
>![SHH key](https://www.evernote.com/l/ACtLqEl1m1pO6JOO5Zw4WvZsegin-pAFxgoB/image.png)

### Creando nuestro primer proyecto con GIT y GitHub
Ya tenemos todo preparado para crear nuestro primer proyecto con GIT y conectado con GitHub, hay formas de hacerlo podemos iniciar primero en GitHub o podemos hacerlo primero en nuestro equipo con GIT. En este post comenzaremos en nuestro equipo, para lo cual abriremos nuestra terminal y crearemos una carpeta donde guardaremos nuestro proyecto.
>
```BASH
~ mkdir primer-proyecto-git
~ cd primer-proyecto-git
~/primer-proyecto-git 
```
Ya estamos ubicados en nuestra carpeta lo primero que hacemos es inicializar GIT para que comience a traquear los cambios.
>
```BASH
~/primer-proyecto-git git init
Initialized empty Git repository in /Users/almapase/primer-proyecto-git/.git/
~/primer-proyecto-git
```

Inicializado nuestro repositorio, creamos un archivo con algo de texto y hacemos el commit correspondiente para que el repositorio quede actualizado.
>
```BASH
~/primer-proyecto-git echo "<h1>Hola Mundo desde GIT hacia GitHub" >> index.html
~/primer-proyecto-git git add index.html
~/primer-proyecto-git git commit -m "Se creo archivo index.html"
[master (root-commit) 0f678d1] Se creo archivo index.html
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
~/primer-proyecto-git
```

Ahora no dirigimos a [https://github.com/](https://github.com/) y damos click en `New Repository`.
![New Reposiroty](https://www.evernote.com/l/ACs4IOz1axRHqqCeKIRaxm_Jr9LbAmi3G7QB/image.png)

Le damos un nombre a nuestro proyecto, no es obligación que sea el mismo de nuestro repositorio local, con el nombre ingresado damos click en `Create Repository`.
![Create Repository](https://www.evernote.com/l/ACs83Sx7QzxCBYvJrOVjYXWBX5G67gjukVkB/image.png)

Estamos a un paso de completar nuestro objetivo, nos resta seguir las instrucciones que GitHub nos ofrece en pantalla, en nuestro caso usaremos la opción que dice: `…or push an existing repository from the command line`
![push](https://www.evernote.com/l/ACvID3WHwMpLL5KZoCbha0J8ZIpPEc5DuVUB/image.png)
>
```BASH
~/primer-proyecto-git git remote add origin git@github.com:almapase/mi-primer-proyecto.git
~/primer-proyecto-git git push -u origin master
Counting objects: 3, done.
Writing objects: 100% (3/3), 267 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:almapase/mi-primer-proyecto.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
~/primer-proyecto-git
```
Con esto hemos completado nuestro objetivo de configurar git con GitHub.
![Listo](https://www.evernote.com/l/ACvbg2I8dyhOz7s3YzQWoauPw2dCcKqMYfoB/image.png)