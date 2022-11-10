# Erick Josué Gamboa Rodríguez
# Configurando e implementando scripts de automatización

- Primeramente se debe de levantar la máquina previamente instalada de vagrant con el comando `vagrant up`

- Se debe de tomar en cuenta que las configuraciones que se van a implementar se realizan en la máquina anfitriona y se ejecutan en la máquina virtual 

- Teniendo esto claro se va a comenzar creando un archivo con el nombre que se desee y con el formato `.sh` (Shell Scripting)

- Se debe proceder a abrir el archivo creado en el auto editor de Visual Studio con el comando `.code`

- Para poder implemenatr un script de automatización en bash se debe de ingresar lo siguiente al inicio del archivo creado `#!/bin/bash`

- Como prueba vamos a ingresar el siguiente script:

`clear`

`echo "Hello World!"`

- Para poder probar este script se debe de brindar los permisos al archivo con el siguiente comando `chmod 744`

- Posteriormente se ejecuta el archivo que contiene el script con el siguiente comando `./<nombre del archivo>.sh`