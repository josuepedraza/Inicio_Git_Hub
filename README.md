# 🐳 Introducción a Docker -- Conceptos y Ejercicio Práctico

Este repositorio fue creado con fines educativos para explicar Docker
desde cero, entendiendo sus conceptos fundamentales y aplicándolos en un
ejercicio práctico con Python y Jupyter Notebook.

------------------------------------------------------------------------

# 🚀 1. ¿Qué problema resuelve Docker?

En desarrollo de software es común escuchar:

> "En mi computador funciona, pero en el tuyo no."

Esto sucede por:

-   Diferencias de versiones (Python, librerías, bases de datos)
-   Configuraciones distintas
-   Dependencias faltantes
-   Conflictos entre proyectos

Docker permite crear entornos aislados y reproducibles, asegurando que
una aplicación funcione igual en cualquier máquina.

------------------------------------------------------------------------

# 🧱 2. Conceptos Fundamentales

## 📦 Imagen

Una imagen es una plantilla que contiene:

-   Sistema base (Linux)
-   Lenguaje de programación
-   Librerías
-   Configuración necesaria

No se ejecuta sola.

Es como una receta de cocina.

------------------------------------------------------------------------

## 🐳 Contenedor

Un contenedor es una imagen en ejecución.

Es un entorno aislado que:

-   Puede iniciarse
-   Puede detenerse
-   Puede eliminarse
-   No afecta el sistema principal

Imagen = receta\
Contenedor = comida preparada

------------------------------------------------------------------------

## 🧩 Docker Compose

Docker Compose permite definir y ejecutar uno o varios contenedores
usando un archivo:

docker-compose.yml

Con un solo comando puedes levantar todo el entorno.

------------------------------------------------------------------------

## 🛟 Volúmenes

Los contenedores son temporales.\
Si se eliminan, los datos pueden perderse.

Un volumen permite guardar datos de forma permanente.

### Bind Mount

Comparte una carpeta local con el contenedor.

Ejemplo: .:/home/jovyan/work

Carpeta local\
↔\
Carpeta dentro del contenedor

------------------------------------------------------------------------

### Named Volume

Docker administra el almacenamiento internamente.

Ejemplo: postgres_data:/var/lib/postgresql/data

------------------------------------------------------------------------

## 🔌 Puertos

Permiten acceder al contenedor desde el navegador.

Ejemplo: "8888:8888"

Puerto 8888 de tu computadora\
↓\
Se conecta al puerto 8888 del contenedor

------------------------------------------------------------------------

# 🛠 3. Ejercicio Desarrollado

Se creó un entorno con:

-   Python
-   Jupyter Notebook
-   Docker Compose
-   Volumen compartido

------------------------------------------------------------------------

## 📄 Archivo docker-compose.yml

``` yaml
services:
  jupyter:
    image: jupyter/base-notebook:latest
    container_name: mi_jupyter
    ports:
      - "8888:8888"
    volumes:
      - .:/home/jovyan/work
    environment:
      - JUPYTER_TOKEN=1234
```

------------------------------------------------------------------------

# 🔍 Explicación del Ejercicio

## services

Define los contenedores que se crearán.

En este caso, se define un servicio llamado `jupyter`.

------------------------------------------------------------------------

## image

Se utiliza una imagen oficial que ya incluye:

-   Linux
-   Python
-   Jupyter Notebook

Si no está descargada, Docker la obtiene automáticamente.

------------------------------------------------------------------------

## container_name

Asigna un nombre personalizado al contenedor para facilitar su
administración.

------------------------------------------------------------------------

## ports

Permite acceder desde el navegador a:

http://localhost:8888

------------------------------------------------------------------------

## volumes

Comparte la carpeta local del proyecto con la carpeta interna del
contenedor:

/home/jovyan/work

Los archivos creados en Jupyter se guardan directamente en la carpeta
del proyecto.

------------------------------------------------------------------------

## environment

Define el token de acceso para ingresar a Jupyter:

1234

------------------------------------------------------------------------

# ▶ 4. Cómo Ejecutar el Proyecto

1.  Tener Docker Desktop instalado.
2.  Clonar el repositorio.
3.  Ubicarse en la carpeta del proyecto.
4.  Ejecutar:

docker compose up -d

5.  Abrir en el navegador:

http://localhost:8888

Token:

1234

------------------------------------------------------------------------

# 🛑 Cómo Detener el Entorno

docker compose down

Este comando:

-   Detiene el contenedor
-   Lo elimina
-   Mantiene los archivos locales gracias al volumen

------------------------------------------------------------------------

# 🧠 5. Flujo Completo de Funcionamiento

1.  Docker lee el archivo docker-compose.yml\
2.  Descarga la imagen si no existe\
3.  Crea el contenedor\
4.  Expone el puerto 8888\
5.  Monta el volumen\
6.  Ejecuta Jupyter

------------------------------------------------------------------------

# 🎯 6. Qué Aprendimos

-   Qué es una imagen
-   Qué es un contenedor
-   Qué es Docker Compose
-   Qué son los servicios
-   Qué son los volúmenes
-   Cómo exponer puertos
-   Cómo crear un entorno reproducible

------------------------------------------------------------------------

# 📚 Conclusión

Docker permite crear entornos aislados, reproducibles y portables.\
Evita conflictos de versiones y facilita el desarrollo profesional de
software.

Este ejercicio demuestra cómo levantar un entorno completo de Python y
Jupyter sin instalar nada directamente en el sistema operativo.
