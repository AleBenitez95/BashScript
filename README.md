# BashScript
## Informe Disco
````
#!/bin/bash
#Autor: Alejandro Benitez
#Ejercicio
FECHA=$(date +%d-%m-%Y)

################################
echo "Informe de ocupacion del disco" > InformeDisco-$FECHA.inf
################################

echo "Fecha=" $FECHA >> InformeDisco-$FECHA.inf
df -hT >> InformeDisco-$FECHA.inf
echo "Informe generado: InformeDisco-$FECHA.inf"
````
## Tamaño Usuarios Introducido
````
#!/bin/bash
read -p "Cual es tu usuario:" usuario
espacio=$(du -hs)
clear
if grep -q "$usuario" /etc/passwd; then
echo    "$usuario ocupa $espacio" 
else 
echo "El usuario introducido no existe"
fi
````

## Tamaño de Usuarios con cierto rango de UID

````
#!/bin/bash
FECHA=$(date +%d-%m-%Y)
espacio=$(du -hs "/home/$usuario")
echo "Fecha: $FECHA"
echo "Tamaño /home de usuarios:"
awk -F':' '$3 >= 1000 && $3 < 2000 {print $1}' /etc/passwd | while read usuario; do
if [ -d "/home/$usuario" ]; then
espacio=$(du -sh "/home/$usuario" 2>/dev/null | cut -f1)
echo "$usuario : $espacio"
fi
done
````
