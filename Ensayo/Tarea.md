Tarea 1 GTDCA
=============

los nombres de las personas estan delimitadas por doble comilla
en el caso de las Señoras los nombres de pila están entre peréntesis. 
el titulo Mr, Miss, Mrs, Dr etc se encuentra después de la primera coma dentro del nombre.

 contenido de archivos
grep '"'  *csv | cut -d'"' -f2 | cut -d',' -f2 | cut -d'.' -f1 | sort -k 1| uniq -c

 1309 registros en los dos archivos csv
grep '"'  -h *csv | cut -d '"' -f2 > titanic.txt

proceso de 1214 registros distintos de Mrs
grep "Mrs\. " titanic.txt -v | cut -d'"' -f2 | cut -d ',' -f1 > seg2
grep "Mrs\. " titanic.txt -v | cut -d'"' -f2 | cut -d ',' -f2 | cut -d "(" -f1  > seg1
paste -d ' ' seg1 seg2 > seg3

proceso 197 registros correspondientes a Mrs. 
grep "Mrs\. " titanic.txt  | cut -d'"' -f2 | cut -d ',' -f2 | cut -d'.' -f1 > segA
grep "Mrs\. " titanic.txt  | cut -d'"' -f2 | cut -d ',' -f2 | cut -d'.' -f2 | cut -d'(' -f2 | cut -d')' -f1  > segB
paste -d ' ' segA segB > segC

 union de archivos de nombres
cat  seg3 segC >  titanicnames.txt

 Notas:  En algunos registros de nombres que NO pertenecen a Señoras existe informacion entre paréntesis que  no fue recuperada considerada.  En 
        Para algunas Señoras el nombre reportado no muestra apellido porque entre paréntesis unicamente estaba el nombre de pila y no se anexó  el apellido del esposo


La broma... significa "lo que sea"  una expresión regular le puede pasar a otra "cualquier cosa"  :>).

