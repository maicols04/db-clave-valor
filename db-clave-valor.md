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

-


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

-


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

-


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

-


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

-


Explicación DML

-


Problemas de la instalación

-


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

-


Explicación DDL

En Etcd, no existe una estructura formal como en bases de datos relacionales, pero sí se puede hablar de la creación de claves (y directorios lógicos a través del uso de nombres jerárquicos como rutas). Todo se maneja como pares clave-valor.

PUT: Crea o actualiza una clave con un valor.

Sintaxis: etcdctl put clave valor

Ejemplo: etcdctl put usuario "Laura"


Aunque Etcd no tiene estructuras como listas o hashes, se pueden usar claves con prefijos comunes para agrupar lógicamente datos.

Ejemplo: etcdctl put config/app/puerto "8080"

Esto crea una “clave” que puede ser vista como parte de una estructura jerárquica.

-


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

-


Problemas de la instalación:

Algunos errores comunes al instalar o usar Etcd:

Versión incorrecta de etcdctl: Puede haber incompatibilidad entre la versión del cliente y del servidor.

No está en el PATH: Si etcdctl no está en las variables del sistema, no se podrá ejecutar desde la terminal.

Problemas de permisos: Puede fallar si no tienes permisos para abrir los puertos o escribir en disco.

Conflicto de puertos: Usa los puertos 2379 (cliente) y 2380 (peer). Si ya están en uso, Etcd no podrá iniciar.

Configuración de red: Para usar en modo clúster, requiere configuración adecuada del archivo de inicio con los nombres y direcciones IP de los nodos.

-


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

Oracle NoSQL

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Introducción

Oracle NoSQL Database es un sistema de gestión de bases de datos NoSQL desarrollado por Oracle Corporation, diseñado para manejar grandes volúmenes de datos no estructurados o semi-estructurados con alta escalabilidad, baja latencia y disponibilidad continua. A diferencia de las bases de datos relacionales tradicionales, Oracle NoSQL permite almacenar datos en un formato flexible como clave-valor, lo cual es ideal para aplicaciones modernas que requieren rendimiento en tiempo real, como IoT, comercio electrónico, análisis en tiempo real y servicios en la nube.

-

Explicación DDL

En Oracle NoSQL, el DDL (Data Definition Language) es fundamental para definir la estructura de la base de datos, incluyendo la creación, modificación y eliminación de objetos como tablas y esquemas. Es una parte esencial del manejo de datos en la plataforma.
Tipos de objetos:
El DDL en Oracle NoSQL trabaja con tablas, esquemas, y otros objetos de la base de datos.
Conceptos clave del DDL en Oracle NoSQL:

Creación:
Se utiliza para crear tablas, esquemas y otros objetos de base de datos.
Ejemplo:
CREATE TABLE usuarios (id INT, nombre VARCHAR(255), email VARCHAR(255));

Modificación:
Permite cambiar la estructura de los objetos, como agregar o eliminar columnas, o cambiar el tipo de datos de una columna.
Ejemplo:
ALTER TABLE usuarios
ADD COLUMN edad INT;

Eliminación:
Se utiliza para borrar objetos de la base de datos, como tablas o esquemas.
Ejemplo:
DROP TABLE usuarios;

Ver todas las tablas:
SHOW TABLES;

Describir una tabla:
DESCRIBE TABLE usuarios;

-

Explicación DML

En Oracle NoSQL, el DML (Data Manipulation Language) no funciona con comandos SQL tradicionales como INSERT, UPDATE, DELETE, SELECT. En su lugar, estas operaciones se realizan mediante llamadas a métodos de su API (en Java, Python, etc.), ya que Oracle NoSQL está diseñado como una base de datos clave-valor distribuida, no relacional.
Sin embargo, las operaciones de DML sí existen, solo que tienen otra forma de ejecutarse.

Insertar: Inserta un nuevo registro
Sintaxis:
PutRequest

Actualizar: Igual que en la inserción; reemplaza el valor existente si la clave coincide
Sintaxis:
PutRequest

Borrar: Elimina un registro por clave primaria.
Sintaxis:
DeleteRequest

Consultar: Recupera registros por clave o mediante consulta
Sintaxis:
GetRequest ó QueryRequest

-

Problemas de la instalación

Compatibilidad del sistema operativo
Oracle NoSQL está diseñado para Linux.
Problema: No existe soporte nativo para Windows.
Solución: Usar WSL (Windows Subsystem for Linux), máquinas virtuales o contenedores Docker.

Dependencia de Java
Oracle NoSQL requiere Java 8 o superior.
Problemas comunes:
Java no instalado o mal configurado (JAVA_HOME)
Versiones incompatibles
Solución: Verificar java -version y definir correctamente las variables de entorno.

Problemas con scripts y permisos
Scripts como startstore.sh o kvlite.sh requieren Bash y permisos de ejecución.
Problema: En sistemas como Windows, estos scripts pueden fallar.
Solución: Usar Bash (Git Bash, WSL) y otorgar permisos (chmod +x script.sh).

Configuración de nodos y topología
En instalaciones de clúster, errores de configuración pueden evitar que los nodos se comuniquen correctamente.
Problemas comunes:
IPs mal definidas
Conflictos de zona
Solución: Revisar cuidadosamente el archivo de configuración de la topología.

Recursos insuficientes
Oracle NoSQL puede requerir varios GB de RAM y espacio en disco, especialmente en clústeres.
Problema: Fallos por falta de memoria o espacio.
Solución: Ejecutarlo en entornos con recursos adecuados.

-

Demostración práctica

// Supongamos que ya tienes configurado el acceso a Oracle NoSQL
NoSQLHandle db = conectarAlServicio();

// Insertar un valor
db.put("usuario:001", "Laura");

// Leer el valor
String nombre = db.get("usuario:001");
System.out.println("Nombre guardado: " + nombre);

// Actualizar el valor
db.put("usuario:001", "Laura Martínez");

// Eliminar el valor
db.delete("usuario:001");

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Hazelcast

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Introcducción:

Hazelcast es un Data Grid en memoria, distribuido y de código abierto, utilizado principalmente para almacenar y gestionar datos en memoria (RAM) a través de múltiples nodos. Es especialmente útil para aplicaciones que necesitan alta disponibilidad y bajo tiempo de respuesta. Aunque Hazelcast se puede utilizar como una base de datos NoSQL, no está diseñado para ser un sistema de almacenamiento persistente como MySQL o MongoDB, sino que trabaja en memoria para operaciones rápidas. 

Algunas de sus aplicaciones comunes son:

Cacheo distribuido (almacenamiento de datos temporales)

Sesiones de usuario en aplicaciones web

Procesamiento de datos en tiempo real

Colas distribuidas para microservicios

-

Explicación DDL

En Hazelcast, no existe un lenguaje específico para definir estructuras de datos como en las bases de datos tradicionales. El concepto de DDL en Hazelcast se refiere más a crear e inicializar las estructuras de datos distribuidas dentro del clúster. Algunas de estas estructuras son:

IMap: Similar a un mapa clave-valor en memoria.

IQueue: Cola distribuida para almacenar elementos en orden.

IList: Lista distribuida similar a un array, pero distribuido entre los nodos.

ISet: Conjunto distribuido que garantiza que no haya valores duplicados.

Ejemplo:

HazelcastInstance hazelcast = Hazelcast.newHazelcastInstance();
IMap<String, String> mapa = hazelcast.getMap("usuarios"); --> Para crear un mapa distribuida
IQueue<String> cola = hazelcast.getQueue("tareas"); --> Para crear una cola distribuida

-

Explicación DML

Hazelcast también tiene comandos DML que te permiten manipular (consultar, modificar o eliminar) los datos que ya están almacenados en sus estructuras distribuidas.

put: Inserta o actualiza una clave en un mapa distribuido.
Ejemplo:
mapa.put("u001", "Juan");
mapa.put("u002", "Ana");

get: Consulta el valor asociado a una clave.
Ejemplo:
String nombre = mapa.get("u001");
Resultado esperado: "Juan"

remove: Elimina una clave de una estructura.
Ejemplo:
mapa.remove("u002");

clear: Limpia todos los elementos de una estructura.
Ejemplo:
mapa.clear();

size: Obtiene el tamaño de una estructura de datos.
Ejemplo:
int tamaño = mapa.size();
Resultado esperado: 1, porque como y se había eliminado "u002", sólo quedaría "u001"

-

Problemas de la instalación

Puerto ocupado:

Hazelcast usa por defecto el puerto 5701. Si está ocupado, puede causar problemas.

Error al iniciar el clúster:

Si los nodos del clúster no pueden comunicarse entre sí, hay que asegurarse de que los puertos necesarios (por defecto el 5701) no estén bloqueados por un firewall.

Falta de permisos:

Asegurarse de tener permisos de administrador si se instala Hazelcast como un servicio o en entornos protegidos.

Configuración incorrecta de red (Modo distribuido):

Si se trabaja con un clúster, verificar la configuración de red, asegurando que los nodos puedan encontrarse a través de la red.

No puede conectarse al clúster:

Asegúrarse de que el archivo de configuración esté correctamente configurado para aceptar nodos nuevos.

-

Demostración práctica

A continuación se muestra una simulación en la que se observa cómo guardar, actualizar, consultar y eliminar productos en un inventario distribuido usando Hazelcast.

import com.hazelcast.core.Hazelcast;
import com.hazelcast.core.HazelcastInstance;
import com.hazelcast.core.IMap;

public class InventarioProductos {
    public static void main(String[] args) {
        // Inicia una instancia de Hazelcast
        HazelcastInstance hazelcast = Hazelcast.newHazelcastInstance();

        // Crear o acceder al mapa distribuido de productos
        IMap<String, Integer> inventario = hazelcast.getMap("inventario");

        // Agregar productos (clave: nombre del producto, valor: cantidad en stock)
        inventario.put("Laptop", 10);
        inventario.put("Mouse", 25);
        inventario.put("Teclado", 15);

        // Consultar stock de un producto
        System.out.println("Stock de Mouse: " + inventario.get("Mouse"));

        // Actualizar stock (por ejemplo, se vendieron 5 Mouses)
        inventario.put("Mouse", inventario.get("Mouse") - 5);
        System.out.println("Stock actualizado de Mouse: " + inventario.get("Mouse"));

        // Eliminar un producto del inventario
        inventario.remove("Teclado");
        System.out.println("¿Teclado sigue en inventario? " + inventario.containsKey("Teclado"));

        // Mostrar el inventario completo
        System.out.println("Inventario actual: " + inventario);
    }
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Memcached: Santiago

---------------------------------------------------------------------------------------------------------------------------------------------------------------------


Explicación DDL

-


Explicación DML

-


Problemas de la instalación

-


Demostración práctica


---------------------------------------------------------------------------------------------------------------------------------------------------------------------

Bibliografía:

https://docs.hazelcast.com/

