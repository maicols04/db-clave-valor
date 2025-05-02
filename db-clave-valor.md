Titulo

Definición

Ventajas

Caso de uso

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Redis

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Introducción:

Redis es una base de datos NoSQL, clave-valor, en memoria y de código abierto.
Está diseñada para ser muy rápida, y se usa mucho para cosas como:

Caché (guardar datos temporales),

Contadores rápidos,

Listas o colas de trabajo,

Almacenamiento de sesiones (por ejemplo, en aplicaciones web).

Redis guarda los datos directamente en la RAM, lo que lo hace mucho más rápido que las bases de datos tradicionales (como MySQL o PostgreSQL).

---


Explicación DDL

En Redis, el concepto de DDL se refiere a la creación de estructuras de datos como strings, listas, hashes, sets y sorted sets. A diferencia de una base de datos relacional, en Redis no necesitas declarar una estructura antes de usarla. La estructura se crea automáticamente cuando insertas datos en ella.

SET:
Se usa para crear una clave con un valor simple de tipo string.
Sintaxis:
SET clave valor
Ejemplo:
SET nombre "Carlos"

HSET:
Permite crear una estructura tipo hash, similar a un objeto, donde se almacenan campos con sus respectivos valores.
Sintaxis:
HSET clave campo valor
Ejemplo:
HSET usuario nombre "Laura" edad "22"

LPUSH:
Crea una lista o agrega elementos al principio de una lista existente.
Sintaxis:
LPUSH lista elemento1 [elemento2 ...]
Ejemplo:
LPUSH tareas "estudiar" "comer"

SADD:
Se utiliza para crear un conjunto (set) sin valores duplicados.
Sintaxis:
SADD conjunto elemento1 [elemento2 ...]
Ejemplo:
SADD frutas "manzana" "pera"

---


Explicación DML(Data Manipulation Language):

DML (Data Manipulation Language), o Lenguaje de Manipulación de Datos, se refiere a los comandos que permiten consultar, modificar o eliminar datos almacenados en Redis. A diferencia de los comandos DDL (que definen estructuras), los DML trabajan directamente con los valores ya almacenados: los leen, actualizan o eliminan.

GET:
Se usa para obtener el valor asociado a una clave de tipo string.
Sintaxis:
GET clave
Ejemplo:
GET nombre

HGET:
Obtiene el valor de un campo específico dentro de un hash.
Sintaxis:
HGET clave campo
Ejemplo:
HGET usuario nombre

HGETALL:
Devuelve todos los campos y valores de un hash.
Sintaxis:
HGETALL clave
Ejemplo:
HGETALL usuario

DEL:
Elimina una clave completa del almacenamiento, sin importar su tipo.
Sintaxis:
DEL clave
Ejemplo:
DEL nombre

HDEL:
Elimina uno o más campos específicos de un hash.
Sintaxis:
HDEL clave campo [campo2 ...]
Ejemplo:
HDEL usuario edad

---


Problemas de la instalación:

Algunos errores comunes al instalar Redis:

Puerto ocupado
Redis por defecto usa el puerto 6379, si ya está en uso, dará error.

Permisos
Si no tienes permisos de administrador, puede fallar al instalar como servicio o al iniciar.

No se encuentra el comando redis-server o redis-cli
Esto pasa cuando no se añade correctamente a las variables del sistema.

Error de firewall o red (modo remoto)
Si quieres conectarte desde otra máquina, debes configurar Redis para aceptar conexiones externas (editar redis.conf y permitir tu IP).

---


Demostración práctica:

Supongamos que queremos guardar y consultar el nombre de una persona.

1. Guardar un nombre (usando SET):
Vamos a guardar un valor de tipo string.

Comando:
SET nombre "Carlos"
Esto crea una clave llamada nombre con el valor "Carlos".

2. Consultar el valor guardado (usando GET):
Ahora vamos a leer ese valor.

Comando:
GET nombre
Resultado esperado:
"Carlos"

3. Cambiar el valor (usando SET otra vez):
Podemos actualizar fácilmente la clave.

Comando:
SET nombre "Ana"

4. Eliminar la clave (usando DEL):
Si ya no necesitamos ese dato, lo eliminamos.

Comando:
DEL nombre

5. Comprobar que fue eliminado (usando GET):

Comando:
GET nombre
Resultado esperado:
(nil)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Amazon DynamoDB: Juan José

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Explicación DDL

---


Explicación DML

---


Problemas de la instalación

---


Demostración práctica


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Etcd

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Introducción:

Etcd es una base de datos NoSQL distribuida, de código abierto, basada en el modelo clave-valor. Está diseñada para ser altamente disponible y consistente, lo que la hace ideal para entornos distribuidos. Se utiliza principalmente para:

Almacenamiento de configuración distribuida,

Coordinación de servicios,

Descubrimiento de servicios,

Almacenamiento de estado en sistemas como Kubernetes.


Etcd mantiene todos sus datos en memoria pero los persiste en disco, lo que garantiza durabilidad incluso después de reinicios. A diferencia de Redis, está optimizado para mantener la coherencia entre múltiples nodos usando el algoritmo de consenso Raft.

---


Explicación DDL

En Etcd, no existe una estructura formal como en bases de datos relacionales, pero sí se puede hablar de la creación de claves (y directorios lógicos a través del uso de nombres jerárquicos como rutas). Todo se maneja como pares clave-valor.

PUT: Crea o actualiza una clave con un valor.

Sintaxis: etcdctl put clave valor

Ejemplo: etcdctl put usuario "Laura"


Aunque Etcd no tiene estructuras como listas o hashes, se pueden usar claves con prefijos comunes para agrupar lógicamente datos.

Ejemplo: etcdctl put config/app/puerto "8080"

Esto crea una “clave” que puede ser vista como parte de una estructura jerárquica.

---


Explicación DML (Lenguaje de manipulación de datos):

Los comandos de manipulación en Etcd permiten consultar, actualizar y eliminar los datos almacenados.

GET: Consulta el valor de una clave.

Sintaxis: etcdctl get clave

Ejemplo: etcdctl get usuario


GET con prefijo: Muestra todas las claves que comienzan con un prefijo.

Sintaxis: etcdctl get prefijo --prefix

Ejemplo: etcdctl get config/ --prefix


DEL: Elimina una clave.

Sintaxis: etcdctl del clave

Ejemplo: etcdctl del usuario


DEL con prefijo: Elimina todas las claves bajo un cierto prefijo.

Sintaxis: etcdctl del prefijo --prefix

Ejemplo: etcdctl del config/ --prefix

---


Problemas de la instalación:

Algunos errores comunes al instalar o usar Etcd:

Versión incorrecta de etcdctl: Puede haber incompatibilidad entre la versión del cliente y del servidor.

No está en el PATH: Si etcdctl no está en las variables del sistema, no se podrá ejecutar desde la terminal.

Problemas de permisos: Puede fallar si no tienes permisos para abrir los puertos o escribir en disco.

Conflicto de puertos: Usa los puertos 2379 (cliente) y 2380 (peer). Si ya están en uso, Etcd no podrá iniciar.

Configuración de red: Para usar en modo clúster, requiere configuración adecuada del archivo de inicio con los nombres y direcciones IP de los nodos.

---


Demostración práctica

Supongamos que queremos guardar y consultar el nombre de una persona.

Guardar un nombre (usando PUT):
Comando: etcdctl put nombre "Carlos"
Esto crea una clave llamada nombre con el valor "Carlos".

Consultar el valor guardado (usando GET):
Comando: etcdctl get nombre
Resultado esperado:

nombre  
Carlos

Cambiar el valor (usando PUT otra vez):
Comando: etcdctl put nombre "Ana"

Eliminar la clave (usando DEL):
Comando: etcdctl del nombre

Comprobar que fue eliminado (usando GET):
Comando: etcdctl get nombre
Resultado esperado: (no muestra nada, ya no existe)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Oracle: Juliana

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Explicación DDL

---


Explicación DML

---


Problemas de la instalación

---


Demostración práctica


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Microsoft Azure Cosmos: Jorge

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Explicación DDL

---


Explicación DML

---


Problemas de la instalación

---


Demostración práctica


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Memcached: Santiago

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Explicación DDL

---


Explicación DML

---


Problemas de la instalación

---


Demostración práctica


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Bibliografía:

