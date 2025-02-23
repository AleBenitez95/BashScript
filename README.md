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
## Tamaño Usuarios
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
