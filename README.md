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
## Conexiones con un archivo

### servidores.txt

````
Tauro:192.162.1.1
Tierra:172.26.0.33
Sol:172.26.0.25
````

### Script

````
#!/bin/bash
FECHA=$(date +%d-%m-%Y)
echo "-----------------------"
echo "INFORME DE SERVIDORES"
echo "Fecha: $FECHA"
echo "-----------------------"
while IFS=':' read -r usuario IP; do
if  ping -c 4 "$IP" > /dev/null 2>&1; then
echo "$usuario : Hay conexion"
else 
echo "$usuario : No Hay conexion"
fi
done < servidores.txt

````

**⚠️ Advertencia importante:**

**while** lee linea por linea, con IFS=':' asociamos el campo separador
 y con read -r usuario IP; asociamos **usuario** y **IP** como dos variables
 
 
 ```` 
while IFS=':' read -r usuario IP;
````
**> /dev/null 2>&1**: elimina los errores en pantalla

````
if  ping -c 4 "$IP" > /dev/null 2>&1
````
