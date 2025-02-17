# Tutorial de Comandos Básicos de Linux

Este tutorial cubre los **comandos esenciales** para navegar y gestionar archivos en Linux. Cada comando tiene una breve explicación y 5 ejemplos prácticos.

## 1. Comandos de Navegación

### `pwd` - Mostrar el directorio actual
Muestra la ruta completa del directorio en el que te encuentras.

**Ejemplos:**
```sh
pwd
```
_Salida esperada:_ `/home/usuario`

---

### `ls` - Listar archivos y directorios
Muestra el contenido del directorio actual.

**Ejemplos:**
```sh
ls
ls -l  # Lista en formato detallado
ls -a  # Muestra archivos ocultos
ls -lh  # Tamaño de archivos en formato legible
ls -lt  # Ordena por fecha de modificación
```

---

### `cd` - Cambiar de directorio
Permite moverte entre directorios.

**Ejemplos:**
```sh
cd /home/usuario  # Ir a un directorio específico
cd ..  # Subir un nivel
cd /etc  # Ir a /etc directamente
cd -  # Volver al directorio anterior
cd ~  # Ir al directorio personal del usuario
```

---

## 2. Gestión de Archivos y Directorios

### `mkdir` - Crear directorios
Crea un nuevo directorio.

**Ejemplos:**
```sh
mkdir nuevo_directorio
mkdir -p carpeta1/carpeta2  # Crea múltiples carpetas anidadas
mkdir proyectos  # Crea la carpeta 'proyectos'
mkdir ~/Documentos/notas  # Crea una carpeta dentro de Documentos
mkdir backups && cd backups  # Crea la carpeta y entra en ella
```

---

### `rmdir` - Eliminar directorios vacíos
Elimina un directorio solo si está vacío.

**Ejemplos:**
```sh
rmdir carpeta_vacia
rmdir ~/temp  # Borra la carpeta temp si está vacía
rmdir -p a/b/c  # Borra c, luego b si está vacía, luego a si está vacía
mkdir test && rmdir test  # Crea y luego borra test
rmdir old_dir  # Intenta borrar old_dir si no contiene archivos
```

---

### `rm` - Eliminar archivos y directorios
Elimina archivos o directorios (con `-r`).

**Ejemplos:**
```sh
rm archivo.txt  # Borra un archivo
rm -r carpeta  # Borra una carpeta y su contenido
rm -i archivo.txt  # Pregunta antes de borrar
rm -rf /directorio  # Borra forzadamente sin confirmación
rm *.log  # Borra todos los archivos con extensión .log
```

---

### `cp` - Copiar archivos y directorios
Copia archivos de un lugar a otro.

**Ejemplos:**
```sh
cp archivo1.txt copia.txt  # Copia archivo1.txt a copia.txt
cp archivo.txt /home/usuario/  # Copia a otra carpeta
cp -r directorio1 directorio2  # Copia una carpeta y su contenido
cp *.txt backup/  # Copia todos los archivos .txt a backup/
cp -u archivo.txt copia.txt  # Solo copia si es más reciente
```

---

### `mv` - Mover o renombrar archivos y directorios
Mueve archivos o los renombra.

**Ejemplos:**
```sh
mv archivo.txt nuevo_nombre.txt  # Renombra el archivo
mv archivo.txt /otra_carpeta/  # Mueve el archivo a otra carpeta
mv -i archivo.txt /backup/  # Pregunta antes de sobrescribir
mv directorio/ /nueva_ubicacion/  # Mueve una carpeta completa
mv * /home/usuario/todos/  # Mueve todos los archivos a otro directorio
```

---

### `find` - Buscar archivos por nombre
Permite localizar archivos en el sistema.

**Ejemplos:**
```sh
find /home -name "documento.txt"  # Busca en /home
find . -type f -name "*.log"  # Busca archivos .log en el directorio actual
find /var/log -mtime -1  # Archivos modificados en las últimas 24 horas
find / -size +100M  # Archivos mayores de 100MB en todo el sistema
find /home -user usuario  # Archivos pertenecientes a 'usuario'
```

---

### `locate` - Búsqueda rápida de archivos
Busca archivos en la base de datos del sistema.

**Ejemplos:**
```sh
locate archivo.txt  # Busca el archivo.txt en todo el sistema
locate -i documento  # Búsqueda sin distinguir mayúsculas/minúsculas
locate '*.png'  # Busca todos los archivos PNG
locate etc | grep passwd  # Filtra resultados con 'passwd'
sudo updatedb && locate script.sh  # Actualiza la base de datos y busca
```

---