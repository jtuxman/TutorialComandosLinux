# CONOZCAMOS EL SHELL DE LINUX
___
# Temas a revisar
1. El Shell de UNIX.
2. Archivos y directorios.(ls,pwd,mkdir, rmdir, rm cp, alias, cat. more)
3. Permisos de archivos
4. Combinando comandos y redicreccionamiento de salida. 
5. Manipulacion de texto.
6. Acceso remoto y transferencia de archivos
___
# El shell de Linux
Ventajas y desventajas contra un ambiente gráfico.


![GUI-vs-CLI-info.jpg.webp](../_resources/GUI-vs-CLI-info.jpg.webp)


___
# Ejecutando comandos

Cada vez que se arranca una terminal se presenta un prompt en pantalla, es el indicador que el shell esta esperando para recibir comandos a ser ejecutados.
```
jmanuel@conacyt:~$
```
Intentemos ejecutar nuestro primer comando, mostrando el directorio home:
```
jmanuel@conacyt:~$ls
```
Salida:
```
jmanuel@conacyt:~$
```
La salida de este comando es:
![8789bc1cc3c5c3d23d80a4328c04dd5b.png](../_resources/8789bc1cc3c5c3d23d80a4328c04dd5b.png)
___
# Estructura de un comando.

![c1c37ac5412dca3e1eb2e9b53ef56eba.png](../_resources/c1c37ac5412dca3e1eb2e9b53ef56eba.png)


___
# Comandos más utilizados
![BasicCommandsBash.png](../_resources/BasicCommandsBash.png)

---
# Ayuda
1. Podemos pasar el parametro  *--help*
como
```
ls --help
```
2. Leer la ayuda con comando **man**
```
man ls
```

![b153ae5a8d5ed5dd8ca58e9529e6844f.png](../_resources/b153ae5a8d5ed5dd8ca58e9529e6844f.png)

el manual presenta ayuda únicamente de los comandos del sistema, no presenta ayuda de programas instalados fuera del manejador de paquetes.
___
# PRACTICA
ejecute los siguientes comandos y explique el resultado:
```
ls -l
ls -lt
lks -l
ls -ltr
ls -la

```


---
# Trabajando con directorios y archivos.
Primero que nada es necesario conocer el arbol de directorios de los sistemas Linux



![FileSystemHierarchy.png](../_resources/FileSystemHierarchy.png)

## Describiendo el árbol con la diagonal (slash)
![b405c601d5be4bd78a150878cf4923c8.png](../_resources/b405c601d5be4bd78a150878cf4923c8.png)

/ es la raiz del sistema
/Users/larry  es el directorio de inicio del usuario larry
/Users/nele es el directorio del usuario nele

# Movernos en el árbol
El comando para movernos en el arbol de directorios será:

```
cd
```
Para mostrarnos en que directorio nos encontramos:
```
pwd
```
Con sus respectivos modificadores
```
cd nombredir
cd rutaabsoluta
cd rutarelativa
cd ..
```
___
## Paréntensis 
El uso de ciertas combinaciones de teclas ayudan a acerlerar el proceso de escribir los comandos más rápidamente.

![LinuxTerminalShorcuts.png](../_resources/LinuxTerminalShorcuts.png)


___
# PRACTICA
1. Encuentre el directorio ``corrected`` dentro de su home y describa el contenido, cuantos archivos comprimidos tiene, cuantos sin comprimir, cuantos directorios, cuantas veces encontró el directorio ``corrected`` en su arbol de directorios.
2. En cuentre el directorio ``alkanes``


¿Qué otras formas existen para buscar los directorios en cuestión? 
___
## Crear y borrar directorios
El comando mkdir nos permite crear directorios mientras que rmdir nos permite  directorios vacio.
```
mkdir nombredirectorio
rmdir nombredirectorio
```
___
## Trabajando con archivos
### Copiando archivos:
El comando cp nos permite realizar copias de un archivo la sintaxis y ejemplo es el siguiente:
```
cp archivo destino
```
Ejemplo:
```
cp shell-lesson-data.zip resp.zip
```
Es posible utilizar rutas absolutas y relativas, por ejemplo:
```
cp /etc/passwd .
cd cursobash/dircurso/shell-lesson-data
cp Documents.tar ../curso/R/
```
Copiar un directorio completo con el modificador -R (verificar los modificadores posibles del comando cp con man)
```
cp -r shell-lesson-data/ backup-data
```
___
## Eliminando archivos
El comando rm nos permite eliminar archivos como directorios que contienen archivos

```
rm archivo
rm -i archivo
rm -rf directorio
```
Se tiene que ser muy precavido y estar seguro con éste último comando porque es complicado recuperar archivos eliminados, y en un servidor en producción se tiene de detener todos los servicios para poder extraer el disco y recuperar los archivos.

___
## Alias de comandos
En este punto es importante mencionar  que es posible acortar la escritura de instrucciones mediante el comando alias
Para ver que alias tenemos definidos en el sistema ejecutar solo el comando:
```
alias 
```
![52ee9a897b840482c2f60ebec7430adb.png](../_resources/52ee9a897b840482c2f60ebec7430adb.png)
el si
```
alias ls='ls -ltr --color=auto'
```
___
## Donde definir los alias de comandos
Depende del shell utilizado por el sistema se puede definir que al inicio de la sesión, en este caso que nosotros estamos utilizando el shell bash, los comandos de inicio de sesión se ejecutan son los que estan en el archivo .bashrc
```
cat .bashrc
```
![58c578a97e875f5e4308ab34b956433a.png](../_resources/58c578a97e875f5e4308ab34b956433a.png)

___
## Variables de entorno.
Las variables de entorno permiten cambiar el comportamiento de los programas, así como permiten proporcionarle datos al SHELL para la ejecución de programas.
Existen varias formas de conocer el contenido de las variables de entono, si no sabe  cuales variables estan definidas en el SHELL ejecutar el comando
```
env
```
![2ee1d73ed85831686d1cfa8cac598896.png](../_resources/2ee1d73ed85831686d1cfa8cac598896.png)
___
Si conoce cuales variables están definidas ejecutar el comando 
```
echo NombreVariable
echo $PATH
```
![fc41b33481913f71d89e685c7c7b44de.png](../_resources/fc41b33481913f71d89e685c7c7b44de.png)

__
## Definir y modificar variables de entorno
Para definir una variable de entorno solo escribir de la siguiente forma:
```
VAR="contenido variable"
```
Por convención se definen con mayúsculas los nombres de variables.
__
## Conectando comandos y redireccionando las salidas.
### Flujos de datos en unix.
Existen 3 flujos de datos cuando se ejecutan comandos en el SHELL
- STDIN Entrada estandar que suele ser el teclado
- SDTOUT salida estandar.
- STDERR Es el flujo a donde se envían los errores 


---
![0d29c7f034ba072c8a1257e98f01ff37.png](../_resources/0d29c7f034ba072c8a1257e98f01ff37.png)
---
![a4b9898159066a9f1d93def5f19184ff.png](../_resources/a4b9898159066a9f1d93def5f19184ff.png)
---
![d5a18c3859bd982373b8cb5e55681cd2.png](../_resources/d5a18c3859bd982373b8cb5e55681cd2.png)
---
## Redireccionamiento E/S a un archivo
Teclear los siguientes comandos en su terminal y explicar:
(Redireccionamiento <>)
```
ls 
ls 1> test
lsx 
lsx 1> test
lsx 2> test
head /etc/passwd 1> cuentas
```
---
X





X

---
![c6a1c329912b219e4138d05e2cfc45f8.png](../_resources/c6a1c329912b219e4138d05e2cfc45f8.png)
__
## Redireccionamiento a otro comando
Se puede redireccionar la salida de un comando hacia otro comando, para poder procesar la información que nos producen los comandos precedecesores.
```
file * | grep directory | wc -l
```
___
## Mirando el contenido de archivos.
Encuentre el directorio llamado alkanes
![d70bb4f5e3a491bbbca7190b611146c3.png](../_resources/d70bb4f5e3a491bbbca7190b611146c3.png)

### Caracteres comodines
![e1dfd85c93f5dba73f538f4b6b659cef.png](../_resources/e1dfd85c93f5dba73f538f4b6b659cef.png)
Caracter  * Permite buscar coincidencias de palabras completas ó partes de palabras
*.pdb  todos los archivos
p*.pdb  pentane.pdb y propane.pdbCaracter 

?ethane.pdb coincidecon  methane.pdb
???ane.pdb  coincide con cualquier palabra con 3 letras finalizadas por ane.pdb,  por ejemplo cubane.pdb  ethane.pdb  octane.pdb.
___
## Mirando dentro de archivos
Entrar al directorio molecules
```
cd molecules
```
Muestra el contenido del archivo
```
cat cubane.pdb
```

Encabezado de archivo
```
head cubane.pdb
```

Lineas finales del archivo
```
tail -n 2 cubane.pdb
```

Muestra el contenido del archivo
```
less cubane.pdb
```

Cuenta las lineas de todos los archivos extensión pdb
```
wc *.pdb
```

Encontrando patrones:
```
grep "ATOM" cubane.pdb
```

___
 # EJERCICIO
 1.  Del directorio **dircurso/coronavirus/variants** concatenar todos los archivos en uno solo.
 2. Crear un nuevo archivo llamado alpha.csv, que debe contener solo el patron Alpha
 3. Contar cuantas ocurrencias existen de esa variante
 4. Repita el mismo procedimiento para contar la variante Delta del coronavirus en todo esos paises
 5. Ejecute los siguientes comandos y explique el resultado:
 ```
 cat *.csv | cut -d "," -f 2 | sort
 cat *_variants.csv | cut -d "," -f 2 | sort | uniq
 
 ```
 
 ___
 ![bc926d571e9bf03dbaffe4f7c1a342cc.png](../_resources/bc926d571e9bf03dbaffe4f7c1a342cc.png)
 
Parte de la presentación fue tomada de:
https://cambiotraining.github.io/unix-shell

---
Acceso mediante autenticación de llave publica

Conceptos clave
- Creación de llave.
- Copia de llave
-- ssh-copy-id
-- scp (aprender transferencia de archivos)
-- ssh comandos.

----
Ejecutar comandos en segundo plano
nohup
screen

---
Verificar la carga del servidor

Top
htop

---
comando file, gzip, tar

---
comprensión permisos

---
enlaces simbolicos


