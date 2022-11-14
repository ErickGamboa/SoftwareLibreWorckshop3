# Erick Josué Gamboa Rodríguez
# Configurando e implementando scripts de automatización

- Primeramente se debe de levantar la máquina previamente instalada de vagrant con el comando `vagrant up`

- Se debe de tomar en cuenta que las configuraciones que se van a implementar se realizan en la máquina anfitriona y se ejecutan en la máquina virtual 

- Teniendo esto claro se va a comenzar creando un archivo con el nombre que se desee y con el formato `.sh` (Shell Scripting)

- Se debe proceder a abrir el archivo creado en el auto editor de Visual Studio con el comando `.code`

- Para poder implemenatr un script de automatización en bash se debe de ingresar lo siguiente al inicio del archivo creado `#!/bin/bash`

- Como prueba vamos a ingresar el siguiente script:
```bash
clear

echo "Hello World!"
```

- Para poder probar este script se debe de brindar los permisos al archivo con el siguiente comando `chmod 744`

- Posteriormente se ejecuta el archivo que contiene el script con el siguiente comando `./<nombre del archivo>.sh`

- Después de probar su funcionamiento insertamos un script que posee la implementación de condicionales:
```bash
#!/bin/bash

clear

echo "Ingrese su nombre: "

read name

echo

if [ ${#name} -eq 0 ]; then

echo "Me hubiera gustado conocerte..."

else

echo "Hola $name"

fi
```
- Después se procede a implementar un script que posee la implementación de ciclos:
```bash
while [ true ]; do

printf "Ingrese su año de nacimiento (yyyy): "

read birthyear

if [ -z echo $birthyear | grep -E ^-\?[0-9]*$ ]; then

echo "Debe ingresar un número entero de 4 digitos."

else

break

fi

done
```
- Después se procede a modificar el script para poder identificar la generación del usuario de acuerdo a su edad:
```bash
if [ $birthyear -ge 1995 ]; then

echo "Veo que eres un nativo digital."

elif [ $birthyear -ge 1982 ] && [ $birthyear -lt 1995 ]; then

echo "Veo que eres un millennial."

elif [ $birthyear -ge 1965 ] && [ $birthyear -lt 1982 ]; then

echo "Veo que eres de la maravillosa generación X, apuesto a
que ya tienes hijos."

elif [ $birthyear -ge 1945 ] && [ $birthyear -lt 1965 ]; then

echo "Veo que eres un Baby Boomer, probablemente ya eres abuelo."

fi
```
- Con la intención de crear un script de automatización para generar un backup de la base de datos vamos a seguir los iguientes pasos: 

- Creamos un nuevo archivo de formato `.sh` llamado `backup`

- Se inserta el siguiente script:
```bash
#!/bin/bash

echo "Iniciando respaldo..."


site="northwind.isw811.xyz"

directory="/home/vagrant/backups/"$site"/"

datetime=$(date + "%Y%m%d_%H%M%S")

datebase="northwind"

username="user_laravel"

password="ISW811"


if [ ! -z "$1" ]; then

    filename="$site"_"$1.sql"

else 

    filename="$site"_"$datetime.sql"

fi

mkdir -p $directory

    mysqldump $datebase > "$directory""$filename" -u $username 

    --password=$password


echo "Comprimiendo respaldo..."

cd $directory

tar cvfz "$filename".tar.gz "$filename"

echo "Eliminando el archivo temporal..."

rm $filename
```

- Se brindan los permisos al archivo como se realizó anteriormente `700`

- Se ejecuta el archivo para probar su funcionalidad 

- Finalmente en el `crontap -e` que es un archivo de configuración se configura para que el cronjob se ejecute en las horas y mometos deseados


