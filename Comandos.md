# Quick reference
### Notas iniciales
> La correspondecia del codigo es:
```
comando
```
- Descripcion de que podemos hacer con el comando.
> NOTAS:<br> 
Aquello que está entre comillas puedes considerarlo una variable. “ejemplo”, aquello que tiene comillas y asterisco lleva forzosamente las comillas. **”ejemplo”* Aquí sí tenemos que poner las comillas en el comando. <br> 
Debido a el movimiento #BlackLifeMater el estándar de la industria ha tratado de cambiar palabras referentes a este tema. Por ejemplo. <br>
Se reemplaza la palabra "master" con "main" o "primary".Con lo que, la rama principal de un repositorio de Git se llama ahora "main" en lugar de "master".
Se reemplaza la palabra "slave" con "réplica" o "secondary". Por ejemplo, un servidor esclavo en un clúster de servidores se llama ahora "réplica" o "secondary" en lugar de "slave".

### Comandos
```
git config –global user.mail "email@example.some"
```
- Crea tu email para saber quien esta mandado el cambio (esto se hace siempre al instalar git).
```
git config –global user.name "yourNAME|nickName"
```
- Crea el nombre de quien esta haciendo estos cambios (esto se hace siempre al instalar git).
```
git init 
```
- Inicia una carpeta como master o main para git (esto se hace siempre al iniciar una carpeta).
```
git add .
```
- Tiene varias variantes, pero la mas usada es con un punto donde agrega todos los archivos al trackeo de git.
```
git commit
```
- Crea un snapshoot de lo que se esta realizando en ese momento, esto versiona el código debes mandar una descripción de lo que estas mandando siempre.
```
git commit -m *“mensaje”
```
- Manda el mensaje de lo que hiciste sin necesidad de entrar al editor vim o cualquier editor de codigo.
```
git branch
```
- Muestra las ramas existentes en la carpeta.
```
git branch “nombre de la rama”
```
- Crea una rama con el nombre “nombre de la rama”.
```
git checkout “nueva rama”
```
- Nos mueve a la rama “nueva rama”.
```
git checkout –“archivo.txt”
```
- Es un control z para el archivo mientras no usemos git add.
```
git diff
```
- Muestra aquello que se modificó al hacer el git add.
```
git status
```
- Muestra el estado de aquello que estamos trackeando.
```
git log
```
- Nos muestra la historia de los commitis que hemos hecho.
```
git  remote add origin “URL”
```
- Toma el url que le indicas para poder hacer el push origin master O main. 
```
git push origin main
```
- Toma el url que le indicas para poder hacer el push origin master O main. 
```
git pull origin main
```
- Lleva lo que tiene en tu repositorio local al repositorio en github.
```
git clone “URL”
```
- Clona el código desde esa url a tu repositorio local.
```
git rm --cached “node_modules” -r
```
- Nos ayuda a remover lo trackeado anteriormente, básicamente deshace un git add  debemos especificar que archivo o carpeta vamos a untrackear
```
rm -rf .git
```
- Comando para eliminar complemante el trackeo de un archivo iniciado en git.
```
git remote set-url origin git@github.com:EdgarPsrk/jsPractico.git
```
- Donde origin es el standar de la industria y es el alias que recibe esa url, ademas la url que tenemos tiene que ser la del repositorio al que queremos apuntar con este alias.
Este comando sirve para cambiar el set que se agrego en ***git remote add origin "url"*** con lo cual podemos cambiar la direccion a donde estamos apuntando el repositorio para hacer el pull y el push de este.
```
git pull origin main --allow-unrelated-histories
```
- Resulve el problema de conflicto con historias de commit
```
git pull --rebase origin main
```
- Muy mala practica, pero puede ayudar a trackearte en el repositorio.
```
git rebase "branch"
```
- Nos permite hacer cambios silenciosos, funciona como un merge pero pega las ramas de un punto a otro por decir si hacemos cambios en branch2, hacemos commits, despues queremos que esos cambios y commits se pasen a main, debemos hacer un *git rebase main*, esto trae toda la historia de main a branch1, despues pasamos a main y desde ese punto hacemos un *git rebase branch1* elimina branch1, lo cual genera una sola historia de commits y es como si no hubieramos echo esos cambios en otra rama, si no que siempre se trabajo en main.
```
git config --list
```
- Muestra la configuracion global de tu git
### Proceso de un push add origin "branch"
```
git add . 
git commit -m "(agregando tu comentario)"
git pull origin "branch"
git push origin “branch”
```
- Asi agregamos a la rama que indiquemos lo que estamos cambiando. Origin master manda el commit a la rama master del proyecto.
### Creacion de una llave ssh para GitHub
```
ssh-keygen -t rsa -b 4096 -C *"yourEmail@some.com"
```
- Esto nos ayuda a crear una llave ssh para conectar con Git Hub, hay mas algoritmos aparte de rsa, pero este es sufcientemente bueno.
> Pudes obtener mas informacion en la documentacion de git.

[![Documentacion](https://img.utdstc.com/icon/4ae/f58/4aef58c6b9e0de9aa521e06df2d6ecf60f4feeed02f501b0cae42e04ba6f56c7:200)](https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

> Tenemos que revisar que el "agente evaluador de SSH" este activo,despues agregar la llave que creamos, revisar el contenido de la llave publica, que es la que se debe enviar a git hub, mientras que la llave privavda debe de quedarse en tu computadora siempre. despues de esto podemos hacer pull and push desde el protocolo SSH.
```
eval "$(ssh-agent -s)"
```
- Nos ayuda a revisar que el agente de SSH este activo.
```
cd ~/.ssh
```
- Nos lleva a la carpeta donde estan las llaves, ambas tienen el mismo nombre id_rsa pero la llave publica es la que tiene la terminacion .pub mientras que la privada no tiene extencion.
```
ssh-add ~/.ssh/id_rsa
```
- Agrega la llave privada que creamos a el repositorio local.
```
 cat id_rsa.pub
```
- Nos muestra el contenido de la llave publica, este se debe copiar para despues pasarlo a git hub 
> para agregar la llave publica a el apartado de configuraciones/llaves ssh.
Basicamente se crea las llaves, una publica ***(id_rsa.pub)***, una privada ***(id_rsa)***, la priva es de tu entorno local, la publica va a git hub, debemos verificar que el agente de SSH este activo, agregar la llave privada al entorno local y copiar el contenido de la llave publica a git hub.
