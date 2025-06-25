# Documentación del proceso de recuperación de archivos ante un borrado accidental.

## Fecha de realización: 25 de junio de 2025

### Error simulado
Para realizar esta actividad se simuló una situación común en la que se borra 
un archivo importante de forma accidental y se confima con un commit.

Para ello se creó el archivo errores.sh y se subió correctamente al repositorio.

Después de eliminó dicho archivo y se confirmó con un commit.

### Recuperación del archivo
En una situación en que nos damos cuenta del error lo primero es hacer un "git reflog" 

Esto nos dice todos los commits que hemos realizado. 

Este punto debemos buscar un commit donde el archivo no estaba borrado y quedarnos con su hash

A partir de este punto se debe elegir que método usar:

Por un lado tenemos el "git reset" es cual es una acción muy agrasiva ya que vuelve el repositorio
a un estado anterior, lo que implica que todo lo que se haya hecho despues de ese commit se perdería.
Es una herramienta que hay que usar con cuidado.

Por otro lado tenemos "git checkout" que permite restaurar un commit específico.
Esta tecnica es más suave y será la que se utilizará para restaurar nuestro archivo errores.sh

Una vez realizado la orden "git checkout 6758fc5" (6758fc5 es el hash de commit que nos interesa)
El archivo errores.sh volverá aparecer en el directorio.
Una vez restaurado Git lo interpreta como un arhcivo modificado por lo que se debe hacer de nuevo 
"git add ." y " git commit -m "" " para guardar los cambios.

#### Lecciones aprendidas
Esta actividad ha sido muy útil para aprender a solucionar un problema tan común como es el borrado accidental.

"git reflog" se puede considerar un salvavidas al poder acceder a todos los commit realizados.

"git checkout es la forma más segura y amable de restaurar archivos específicos.

"git reset" es una herramienta muy potente pero muy destrucctiva, hay que tener mucho cuidado con su uso, y solo
utilizarla cuando se está muy seguro ya que se perderá todo lo posterior al commit restaurado.

Cuando se comete un error no hay que perder la calma ya que Git cuenta con múltiples herramientas para resolver la situación.
