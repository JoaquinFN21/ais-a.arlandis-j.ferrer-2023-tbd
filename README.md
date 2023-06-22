# AIS-Practica-3-2023

Autor(es): Adrian Arlandis Alonso y Joaquin Ferrer Nuñez

[Repositorio](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd)

[Aplicación Okteto](https://books-reviewer-tbd-joaquinfn21.cloud.okteto.net/)

## Desarrollo con TBD

Una vez creados los workflows y funcionando estos, pasamos a crear la nueva funcionalidad utilizando TBD:

1º Clonamos el repositorio con el comando $ git clone git@github.com:JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd.git

2º Utilizamos el comando cd para entrar a la carpeta del repositorio.

3º Creamos una rama llamada feature-reducirDescripcionLibros con el comando $ git checkout -b feature-reducirDescripcionLibros.

4º Abrimos el repositorio en visual studio y realizamos las modificaciones correspondientes para reducir la descripción de los libros a un máximo de 950               caracteres. Esto se hace en la clase bookDetail cambiando el método:
   public void setDescription(String description) {
        if (description.length() > 950) {
            this.description = description.substring(0, 950) + "...";
        } else {
            this.description = description;
        }
    }
    
5º Ejecutamos $ git status para comprobar si se han realizado cambios.

6º Ejecutamos $ git add . para añadir los cambios.

7º Creamos el commit con el comando $ git commit -m "Reducir descripcion de los libros"

8º Volvemos a la rama master con $ git checkout master

9º Subimos la rama feature al repositorio online con $ git push origin feature-reducirDescripcionLibros. Al subir la rama cuenta como un push en una rama feature, 
   por lo que desencadena la ejecucion del [Workflow1](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/actions/runs/5336335801).

10º Una vez subida la rama, hacemos un pull-request entre master y la rama feature en GitHub. Se hace un merge y se actualiza la rama master. Al ser TBD habria que     eliminar la rama feature en este momento, pero se nos especifica en el enunciado no hacerlo. Al hacer un pull-request de la rama feature a la rama master se        ejecuta el [Workflow1](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/actions/runs/5336344126). Ademas, como tambien se trata de una               integracion en la rama master, tambien se ejecuta el [Workflow2](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/actions/runs/5336346659).

11º Actualizamos la rama master en nuestro repositorio clonado con $ git pull origin master

12º Creamos la rama release-1.1 con el comando $ git checkout -b release-1.1

13º Subimos la nueva rama al repositorio online con el comando $ git push origin release-1.1. Al subir la rama, se trata de un push sobre una rama release, por lo que se ejecuta el [Workflow3](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/actions/runs/5336361627) lo cual genera una [Imagen en DockerHub](https://hub.docker.com/layers/repo2001/books-reviewer/b29015ddef9b15b47ce9e270c752b1b168f58d07/images/sha256-2b3c261f24b69d064e7b0bd45ff23aeaf3636de3f5fb36041e6ee36ecd17b1f4?context=explore) y despliega la aplicacion automaticamente en Okteto.
![Okteto](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/assets/120312771/dd330459-c0db-4847-8217-a7c04a787a76)
![AppLibro](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/assets/120312771/4120619c-85a1-4baa-8c3b-a3baf816fec1)

## Workflow de Nightly
Este workflow se ejecuta automaticamente todas las noches ejecutando todos los Test y creando una imagen en DockerHub cuyo tag es la fecha en la que se ejecuta dicho workflow.
[Ejecucion Workflow](https://github.com/JoaquinFN21/ais-a.arlandis-j.ferrer-2023-tbd/actions/runs/5340575016).
[Imagen generada](https://hub.docker.com/layers/repo2001/books-reviewer/dev-20230622.012523/images/sha256-2b3c261f24b69d064e7b0bd45ff23aeaf3636de3f5fb36041e6ee36ecd17b1f4?context=explore).
