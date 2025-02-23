#!/bin/bash
read -p "Cual es tu usuario:" usuario
espacio=$(du -hs)
clear
if grep -q "$usuario" /etc/passwd; then
echo    "$usuario ocupa $espacio" 
else 
echo "El usuario introducido no existe"
fi
