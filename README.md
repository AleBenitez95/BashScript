# BashScript

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
