# My tutorials

Este es un repositorio con la única finalidad de guardar los pasos que voy siguiendo al aprender algo nuevo o utilizar algo que probablemente me olvide. Espero que si estás acá, alguna vez te sirvan de utilidad. 

## Matlab con docker 

Bueno, si bien no hay un tutorial de docker aún, es porque siento que voy a utilizarlo de forma muy seguida por lo que directamente mostraré como utilizar matlab con docker.

Primero es necesario saber que necesitamos docker instalado, pueden hacerlo en la misma página de docker. Luego, corremos 

``` 
docker run --name matlab_container -it -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro -v ~/Del/docker/Matlab:/home/matlab/Documents/MATLAB/Del --shm-size=512M mathworks/matlab:r2022a
```
 Y acá diré, que rayos es todo esto, así que trataré de explicar masomenos lo que entiendo de todo ello.

 Primero que nada, estamos creando un contenedor con la imagen de matlab 2022a que sea capaz de mostrar la interfaz y todo como si tuviesemos matlab instalado en nuestra computadora. Recuerden que las siguientes caracterísitcas la pueden investigar más a fondo en el sitio oficial de Docker.

`--name matlab_container` es el nombre que le asignamos a nuestro contenedor.

`-it` significa que podremos interacturar mediante una pseudoterminal.

`-it` sirve para setear una variable de entorno

`DISPLAY=$DISPLAY` significa que estamos seteando la variable de entorno que define nuestro display al mismo del docker.

`-v` hace referencia a que vamos a alojar un volumen. El primer volumen que alojamos es para que se alojen los recursos gráficos. Por otro lado, el segundo que estamos creando es importante puesto que hace referencia al volumen que iremos a utilizar para compartir los archivos de nuestra computadora local al contenedor en docker. Esto quiere decir que los archivos que yo tenga en la carpeta local `~/Del/docker/Matlab` se irán a compartir en la carpeta `/home/matlab/Documents/MATLAB/Del` del contenedor y viceversa. Por ello les recomiendo cambiar la carpeta local a una dedicada donde vayan a poner sus archivos de matlab, y obviamente el nombre `Del` en la ruta del contenedor a una que ustedes deseen.

`--shm-size=512M` es la cantidad de memoria compartida que será de 512 MB y de acuerdo a MATLAB es la apropiada para que funcione correctamente.

`mathworks/matlab:r2022a` es la imagen de MATLAB, que si no la tienen no se preocupen pues al correr el comando se descargará del DockerHub siempre que tengan internet claro.

Bueno eso es básicamente todo lo que necesitan para correr MATLAB con docker y que puedan compartir archivos fácilmente con su computadora local, al menos de forma básica. Si le han dado a ejecutar verán que les pide pues sus credenciales y una vez eso saldrá MATLAB como si estuviese corriendo en su computadora.

<img src="figures/matlab1.png" alt="matlab_container" style="width:100%">
