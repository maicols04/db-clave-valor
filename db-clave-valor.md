<h1>Índice</h1>
<ul>
   <li>
      <a href="#titulo">CLAVE VALOR</a>
      <ul>
         <li><a href="#definicion">Definición</a></li>
         <li><a href="#ventajas">Ventajas</a></li>
         <li><a href="#desventajas">Desventajas</a></li>
         <li><a href="#caso-de-uso">Caso de uso</a></li>
      </ul>
   </li>
   <li>
      <a href="#redis">Redis</a>
      <ul>
         <li><a href="#redis-intro">Introducción</a></li>
         <li><a href="#redis-ddl">Explicación DDL</a></li>
         <li><a href="#redis-dml">Explicación DML</a></li>
         <li><a href="#redis-problemas">Problemas de la instalación</a></li>
         <li><a href="#redis-demo">Demostración práctica</a></li>
      </ul>
   </li>
   <li>
      <a href="#etcd">Etcd</a>
      <ul>
         <li><a href="#etcd-intro">Introducción</a></li>
         <li><a href="#etcd-ddl">Explicación DDL</a></li>
         <li><a href="#etcd-dml">Explicación DML</a></li>
         <li><a href="#etcd-problemas">Problemas de la instalación</a></li>
         <li><a href="#etcd-demo">Demostración práctica</a></li>
      </ul>
   </li>
   <li>
      <a href="#oracle">Oracle NoSQL</a>
      <ul>
         <li><a href="#oracle-intro">Introducción</a></li>
         <li><a href="#oracle-ddl">Explicación DDL</a></li>
         <li><a href="#oracle-dml">Explicación DML</a></li>
         <li><a href="#oracle-problemas">Problemas de la instalación</a></li>
      </ul>
   </li>
   <li>
      <a href="#dynamodb">Amazon DynamoDB: Juan José</a>
      <ul>
         <li><a href="#dynamodb-ddl">Explicación DDL</a></li>
         <li><a href="#dynamodb-dml">Explicación DML</a></li>
         <li><a href="#dynamodb-problemas">Problemas de la instalación</a></li>
         <li><a href="#dynamodb-demo">Demostración práctica</a></li>
      </ul>
   </li>
   <li>
      <a href="#memcached">Memcached: Santiago</a>
      <ul>
         <li><a href="#memcached-ddl">Explicación DDL</a></li>
         <li><a href="#memcached-dml">Explicación DML</a></li>
         <li><a href="#memcached-problemas">Problemas de la instalación</a></li>
         <li><a href="#memcached-demo">Demostración práctica</a></li>
      </ul>
   </li>
   <li><a href="#bibliografia">Bibliografía</a></li>
</ul>
<hr>
<br>
<article id="clave-valor">
   <h1 id="titulo">CLAVE VALOR</h1>
   <br>
   <hr>
   <h2 id="definicion">Definición</h2>
   <p>Las bases de datos clave-valor (Key-Value) son de tipo no relacionales. Utilizan un modelo simple de almacenamiento de datos. Gracias a sus características de alta eficacia en ejecución de lectura y escritura de datos; los desarrolladores tienen una gran eficacia al usar este tipo de bases de datos. Las bases de datos clave-valor son altamente divisibles; permiten el escalado horizontal a escalas que otros tipos de bases de datos no pueden alcanzar.
   El modelo de bases de datos clave-valor almacena los datos usando pares, donde una clave única se asocia a un valor. Es como un diccionario: buscas una palabra, que sería la clave, y te devuelve su definición, que sería el valor.
   Este modelo no maneja estructuras complejas ni relaciones entre datos. Es directo, rápido y fácil de entender. Solo necesitas conocer la clave para obtener el valor asociado.
   </p>
   <br>
   <hr>
   <h2 id="ventajas">Ventajas</h2>
   <p>
   Primero, tiene un altísimo rendimiento en lecturas y escrituras. Como todo está asociado a una clave única, encontrar o guardar algo es cuestión de milisegundos.

   Segundo, es muy fácil de escalar horizontalmente. Si necesitas manejar más datos o más peticiones, solo agregas más servidores y listo. Esto lo hace ideal para aplicaciones con mucho tráfico.

   Y tercero, es perfecto para almacenar datos simples, como preferencias de usuario, carritos de compra o sesiones de usuario en aplicaciones web.
   </p>
   <br>
   <hr>
   <h2 id="desventajas">Desventajas</h2>
   <p>La primera es que no sirve para consultas complejas. Si necesitas buscar datos que cumplan ciertas condiciones o hacer combinaciones entre distintos datos, este modelo no te lo permite.
   
   La segunda desventaja es que no gestiona relaciones entre datos. No puedes establecer conexiones entre una tabla de clientes y una de pedidos, como se hace en una base relacional.
   
   Y tercero, solo puedes buscar por clave. Si no tienes la clave exacta, no puedes encontrar el dato.
   </p>
   <br>
   <hr>
   <h2 id="caso-de-uso">Casos de uso</h2>
   <p>Se usa mucho en aplicaciones que necesitan guardar y recuperar información de forma rápida. Por ejemplo:
   
   - En un carrito de compras de una tienda virtual, donde cada usuario tiene una clave y su carrito como valor.
   - En el almacenamiento de sesiones de usuario en una aplicación web, para validar rápidamente quién está conectado.
   - En sistemas de caché, donde se guardan resultados de consultas para no tener que generarlos otra vez.
   - Y en configuraciones rápidas de aplicaciones, donde los valores pueden cambiarse en tiempo real.
   </p>
   <br>
</article>
<hr>
<br><br>
<article id="redis">
   <hr>
   <h1>Redis</h1>
   <hr>
   <br>
   <h2 id="redis-intro">Introducción</h2>
   <p>
      Redis es una base de datos NoSQL, clave-valor, en memoria y de código abierto.
      Está diseñada para ser muy rápida, y se usa mucho para cosas como:
   </p>
   <ul>
      <li>Caché (guardar datos temporales)</li>
      <li>Contadores rápidos</li>
      <li>Listas o colas de trabajo</li>
      <li>Almacenamiento de sesiones (por ejemplo, en aplicaciones web)</li>
   </ul>
   <p>
      Redis guarda los datos directamente en la RAM, lo que lo hace mucho más rápido
      que las bases de datos tradicionales (como MySQL o PostgreSQL).
   </p>
   <br>
   <hr>
   <h2 id="redis-ddl">Explicación DDL</h2>
   <p>
      En Redis, el concepto de DDL se refiere a la creación de estructuras de datos como
      strings, listas, hashes, sets y sorted sets. A diferencia de una base de datos
      relacional, en Redis no necesitas declarar una estructura antes de usarla.
      La estructura se crea automáticamente cuando insertas datos en ella.
   </p>
   <ul>
      <li>
         <strong>SET:</strong> Se usa para crear una clave con un valor simple de tipo string.<br>
         <em>Sintaxis:</em> <code>SET clave valor</code><br>
         <em>Ejemplo:</em> <code>SET nombre "Carlos"</code>
      </li>
      <li>
         <strong>HSET:</strong> Permite crear una estructura tipo hash, similar a un objeto, donde se almacenan campos con sus respectivos valores.<br>
         <em>Sintaxis:</em> <code>HSET clave campo valor</code><br>
         <em>Ejemplo:</em> <code>HSET usuario nombre "Laura" edad "22"</code>
      </li>
      <li>
         <strong>LPUSH:</strong> Crea una lista o agrega elementos al principio de una lista existente.<br>
         <em>Sintaxis:</em> <code>LPUSH lista elemento1 [elemento2 ...]</code><br>
         <em>Ejemplo:</em> <code>LPUSH tareas "estudiar" "comer"</code>
      </li>
      <li>
         <strong>SADD:</strong> Se utiliza para crear un conjunto (set) sin valores duplicados.<br>
         <em>Sintaxis:</em> <code>SADD conjunto elemento1 [elemento2 ...]</code><br>
         <em>Ejemplo:</em> <code>SADD frutas "manzana" "pera"</code>
      </li>
   </ul>
</article>
<br>
<hr>
<h2 id="redis-dml">Explicación DML</h2>
<p>
   DML (Data Manipulation Language), o Lenguaje de Manipulación de Datos, se refiere a los comandos que permiten consultar, modificar o eliminar datos almacenados en Redis. A diferencia de los comandos DDL (que definen estructuras), los DML trabajan directamente con los valores ya almacenados: los leen, actualizan o eliminan.
</p>
<ul>
   <h3>GET:</h3>
   Se usa para obtener el valor asociado a una clave de tipo string.<br>
   <em>Sintaxis:</em> <code>GET clave</code><br>
   <em>Ejemplo:</em> <code>GET nombre</code><br><br>
   <h3>HGET:</h3>
   Obtiene el valor de un campo específico dentro de un hash.<br>
   <em>Sintaxis:</em> <code>HGET clave campo</code><br>
   <em>Ejemplo:</em> <code>HGET usuario nombre</code><br><br>
   <h3>HGETALL:</h3>
   Devuelve todos los campos y valores de un hash.<br>
   <em>Sintaxis:</em> <code>HGETALL clave</code><br>
   <em>Ejemplo:</em> <code>HGETALL usuario</code><br><br>
   <h3>DEL:</h3>
   Elimina una clave completa del almacenamiento, sin importar su tipo.<br>
   <em>Sintaxis:</em> <code>DEL clave</code><br>
   <em>Ejemplo:</em> <code>DEL nombre</code><br><br>
   <h3>HDEL:</h3>
   Elimina uno o más campos específicos de un hash.<br>
   <em>Sintaxis:</em> <code>HDEL clave campo</code><br>
   <em>Ejemplo:</em> <code>HDEL usuario edad</code><br><br>
   </li><br>
</ul>
<br>
<hr>
<h2 id="redis-problemas">Problemas de la instalación</h2>
<ul>
   <li><strong>Puerto ocupado:</strong> Redis usa por defecto el puerto 6379</li>
   <li><strong>Permisos:</strong> Se requieren privilegios de administrador</li>
   <li><strong>Comandos no encontrados:</strong> Verifica variables de entorno</li>
   <li><strong>Error de firewall o red (modo remoto):</strong> Si quieres conectarte desde otra máquina, debes configurar Redis para aceptar conexiones externas (editar redis.conf y permitir tu IP).
   </li>
   <li><strong>Conexión remota:</strong> Configura <code>redis.conf</code> para permitir tu IP</li>
</ul>
<br>
<hr>
<h2 id="redis-demo">Demostración práctica</h2>
<p>Supongamos que queremos guardar y consultar el nombre de una persona.</p>
<ol>
   <li><strong>Guardar un nombre (usando SET):</strong> <code>SET nombre "Carlos"</code></li>
   <p>Esto crea una clave llamada nombre con el valor "Carlos".</p>
   <li><strong>Consultar el valor guardado (usando GET):</strong> <code>GET nombre</code> → "Carlos"</li>
   <br>
   <li><strong>Cambiar el valor (usando SET otra vez):</strong> <code>SET nombre "Ana"</code></li>
   <br>
   <li><strong>Eliminar la clave (usando DEL):</strong> <code>DEL nombre</code></li>
   <p>Si ya no necesitamos ese dato, lo eliminamos.</p>
   <li><strong>Comprobar que fue eliminado (usando GET):</strong> <code>GET nombre</code> → (nil)</li>
   <p>Resultado esperado:(nil)</p>
</ol>
</article>
<hr>
<br><br>
<article id="etcd">
<hr>
<h1>Etcd</h1>
<hr>
<br>
<article id="etcd-intro">
   <h2>Introducción:</h2>
   <br>
   Etcd es una base de datos NoSQL distribuida, de código abierto, basada en el modelo clave-valor. Está diseñada para ser altamente disponible y consistente, lo que la hace ideal para entornos distribuidos. Se utiliza principalmente para:
   <ul>
      <li>Almacenamiento de configuración distribuida</li>
      <li>Coordinación de servicios</li>
      <li>Descubrimiento de servicios</li>
      <li>Almacenamiento de estado en sistemas como Kubernetes</li>
   </ul>
   Etcd mantiene todos sus datos en memoria pero los persiste en disco, lo que garantiza durabilidad incluso después de reinicios. A diferencia de Redis, está optimizado para mantener la coherencia entre múltiples nodos usando el algoritmo de consenso Raft.
</article>
<br>
<br>
<hr>
<article>
   <h2 id="etcd-ddl">Explicación DDL:</h2>
   <br><br>
   <p>En Etcd, no existe una estructura formal como en bases de datos relacionales, pero sí se puede hablar de la creación de claves (y directorios lógicos a través del uso de nombres jerárquicos como rutas). Todo se maneja como pares clave-valor.</p>
   <br><br>
   <h3>PUT:</h3>
   Crea o actualiza una clave con un valor.<br>
   <em>Sintaxis:</em> <code>etcdctl put clave valor</code><br>
   <em>Ejemplo:</em> <code>etcdctl put usuario "Laura"</code><br><br>
   Aunque Etcd no tiene estructuras como listas o hashes, se pueden usar claves con prefijos comunes para agrupar lógicamente datos.<br>
   <em>Ejemplo:</em> <code>etcdctl put config/app/puerto "8080"</code><br>
   Esto crea una clave que puede ser vista como parte de una estructura jerárquica.
</article>
<br>
<br>
<hr>
<article id="etcd-dml">
   <h2>Explicación DML (Lenguaje de manipulación de datos):</h2>
   <br><br>
   <p>Los comandos de manipulación en Etcd permiten consultar, actualizar y eliminar los datos almacenados.
   </p>
   <h3>GET:</h3>
   Consulta el valor de una clave.<br>
   <em>Sintaxis:</em> <code>etcdctl get clave</code><br>
   <em>Ejemplo:</em> <code>etcdctl get usuario</code><br><br>
   <h3>GET con prefijo:</h3>
   Muestra todas las claves que comienzan con un prefijo.<br>
   <em>Sintaxis:</em> <code>etcdctl get prefijo --prefix</code><br>
   <em>Ejemplo:</em> <code>etcdctl get config/ --prefix</code><br><br>
   <h3>DEL:</h3>
   Elimina una clave.<br>
   <em>Sintaxis:</em> <code>etcdctl del clave</code><br>
   <em>Ejemplo:</em> <code>etcdctl del usuario</code><br><br>
   <h3>DEL con prefijo:</h3>
   Elimina todas las claves bajo un cierto prefijo.<br>
   <em>Sintaxis:</em> <code>etcdctl del prefijo --prefix</code><br>
   <em>Ejemplo:</em> <code>etcdctl del config/ --prefix</code>
</article>
<br>
<br>
<hr>
<article id="etcd-problemas">
   <h2>Problemas de la instalación:</h2><br><br>
   Algunos errores comunes al instalar o usar Etcd:
   <ul>
      <li><strong>Versión incorrecta de etcdctl:</strong> Puede haber incompatibilidad entre la versión del cliente y del servidor.</li>
      <li><strong>No está en el PATH:</strong> Si etcdctl no está en las variables del sistema, no se podrá ejecutar desde la terminal.</li>
      <li><strong>Problemas de permisos:</strong> Puede fallar si no tienes permisos para abrir los puertos o escribir en disco.</li>
      <li><strong>Conflicto de puertos:</strong> Usa los puertos 2379 (cliente) y 2380 (peer). Si ya están en uso, Etcd no podrá iniciar.</li>
      <li><strong>Configuración de red:</strong> Para usar en modo clúster, requiere configuración adecuada del archivo de inicio con los nombres y direcciones IP de los nodos.</li>
   </ul>
</article>
<br>
<br>
<br>
<hr>
<article id="etcd-demo">
   <h2>Demostración práctica:</h2>
   <br><br>
   Supongamos que queremos guardar y consultar el nombre de una persona.<br><br>
   <h3>Guardar un nombre (usando PUT):</h3>
   <br>
   <code>etcdctl put nombre "Carlos"</code><br>
   Esto crea una clave llamada <code>nombre</code> con el valor "Carlos".<br><br>
   <h3>Consultar el valor guardado (usando GET):</h3>
   <br>
   <code>etcdctl get nombre</code><br>
   Resultado esperado:<br>
   <pre>
nombre
Carlos
  </pre>
   <br>
   <h3>Cambiar el valor (usando PUT otra vez):</h3>
   <br>
   <code>etcdctl put nombre "Ana"</code><br><br>
   <h3>Eliminar la clave (usando DEL):</h3>
   <br>
   <code>etcdctl del nombre</code><br><br>
   <h3>Comprobar que fue eliminado (usando GET):</h3>
   <br>
   <code>etcdctl get nombre</code><br>
   Resultado esperado: (no muestra nada, ya no existe)
</article>
<br>
<hr>
<br>
<article id="oracle">
<hr>
<h1>Oracle NoSQL</h1>
<hr>
<br>
<article id="oracle-intro">
   <h2>Introducción</h2>
   <p>
      Oracle NoSQL Database es un sistema de gestión de bases de datos NoSQL desarrollado por Oracle Corporation, diseñado para manejar grandes volúmenes de datos no estructurados o semi-estructurados con alta escalabilidad, baja latencia y disponibilidad continua.
   </p>
   <p>
      A diferencia de las bases de datos relacionales tradicionales, Oracle NoSQL permite almacenar datos en un formato flexible como clave-valor, ideal para aplicaciones modernas como IoT, comercio electrónico, análisis en tiempo real y servicios en la nube.
   </p>
</article>
<hr>
<article id="oracle-ddl">
   <h2>Explicación DDL</h2>
   <p><strong>El DDL (Data Definition Language)</strong> En Oracle NoSQL, el DDL (Data Definition Language) es fundamental para definir la estructura de la base de datos, incluyendo la creación, modificación y eliminación de objetos como tablas y esquemas. Es una parte esencial del manejo de datos en la plataforma.
      Tipos de objetos:
      El DDL en Oracle NoSQL trabaja con tablas, esquemas, y otros objetos de la base de datos.
      Conceptos clave del DDL en Oracle NoSQL:
   </p>
   <ul>
   <h3>Creación:</h3>
   Se utiliza para crear tablas, esquemas y otros objetos de base de datos.
   <br>
   <em>Sintaxis:</em> <code>CREATE TABLE "nombre" (Columnas)</nombre></code><br>
   <em>Ejemplo:</em> CREATE TABLE usuarios (id INT, nombre VARCHAR(255), email VARCHAR(255));
   <br><br>
   <h3>Modificación:</h3>
   Permite cambiar la estructura de los objetos, como agregar o eliminar columnas, o cambiar el tipo de datos de una columna.
   <br>
   <em>Sintaxis:</em> <code> ALTER TABLE --- ADD COLUMN</nombre></code><br>
   <em>Ejemplo:</em><br> ALTER TABLE usuarios<br>
   ADD COLUMN edad INT;
   <br><br>
   <h3>Eliminación:</h3>
   Se utiliza para borrar objetos de la base de datos, como tablas o esquemas.
   <br>
   <em>Sintaxis:</em> <code>DROP TABLE "nombre_tabla"</nombre></code><br>
   <em>Ejemplo:</em> DROP TABLE usuarios;
   <br><br>
   <h3>Ver todas las tablas:</h3>
   Se utiliza para mostrar todas la tablas
   <br>
   <em>Sintaxis:</em> <code>SHOW TABLES;</nombre></code><br>
   <em>Ejemplo:</em> SHOW TABLES;
   <br><br>
   <h3>Describir una tabla:</h3>
   Describir una tabla:
   <br>
   <em>Sintaxis:</em> <code>DESCRIBE TABLE "nombre_tabla";</nombre></code><br>
   <em>Ejemplo:</em> DESCRIBE TABLE usuarios;
   <br><br>
</article>
<hr>
<article id="oracle-dml">
   <h2>Explicación DML</h2>
   <p>
      En Oracle NoSQL, el DML (Data Manipulation Language) no funciona con comandos SQL tradicionales como INSERT, UPDATE, DELETE, SELECT. En su lugar, estas operaciones se realizan mediante llamadas a métodos de su API (en Java, Python, etc.), ya que Oracle NoSQL está diseñado como una base de datos clave-valor distribuida, no relacional.
      Sin embargo, las operaciones de DML sí existen, solo que tienen otra forma de ejecutarse.
   </p>
   <ul>
   <h3>Insertar / Actualizar:</h3>
   Se utiliza para Insertar o actualizar un registro
   <br>
   <em>Sintaxis:</em> <code>PutRequest</nombre></code><br>
   <br><br>
   <h3>Borrar:</h3>
   Elimina un registro por clave primaria.
   <br>
   <em>Sintaxis:</em> <code>DeleteRequest</nombre></code><br>
   <br><br>
   <h3>Consultar:</h3>
   Elimina un registro por clave primaria.
   <br>
   <em>Sintaxis:</em> <code>GetRequest</code> o <code>QueryRequest</code><br>
   <br><br>
</article>
<hr>
<article id="oracle-problemas">
   <h2>Problemas de la instalación</h2>
   <ul>
      <li><strong>Compatibilidad:</strong> Solo soportado oficialmente en Linux.<br>
         <em>Solución:</em> WSL, máquinas virtuales o Docker.
      </li>
      <li><strong>Dependencias:</strong> Requiere Java 8+.<br>
         <em>Solución:</em> Configurar JAVA_HOME correctamente.
      </li>
      <li><strong>Scripts y permisos:</strong> Requieren Bash y permisos de ejecución.<br>
         <em>Solución:</em> Usar Bash y <code>chmod +x</code>.
      </li>
      <li><strong>Topología:</strong> Problemas al definir nodos e IPs.<br>
         <em>Solución:</em> Revisar el archivo de configuración.
      </li>
      <li><strong>Recursos:</strong> Alta demanda de RAM y disco.<br>
         <em>Solución:</em> Usar entornos con buena capacidad.
      </li>
   </ul>
</article>
<hr>
<article id="oracle-demo">
   <h2>Demostración práctica</h2>
   <p><strong>Supongamos que ya tienes configurado el acceso a Oracle NoSQL</strong></p>
   <pre><code>NoSQLHandle db = conectarAlServicio();</code></pre>
   <p><strong>Insertar un valor</strong></p>
   <pre><code>db.put("usuario:001", "Laura");</code></pre>
   <p><strong>Leer el valor</strong></p>
   <pre><code>String nombre = db.get("usuario:001");
    System.out.println("Nombre guardado: " + nombre);</code></pre>
   <p><strong>Actualizar el valor</strong></p>
   <pre><code>db.put("usuario:001", "Laura Martínez");</code></pre>
   <p><strong>Eliminar el valor</strong></p>
   <pre><code>db.delete("usuario:001");</code></pre>
</article>
<hr>
<br><br>
<article id="hazelcast">
   <hr>
   <h2>Hazelcast</h2>
   <hr>
   <br>
   <section id="hazelcast-intro">
      <h2>Introducción:</h2>
      <br>
      Hazelcast es un Data Grid en memoria, distribuido y de código abierto, utilizado principalmente para almacenar y gestionar datos en memoria (RAM) a través de múltiples nodos. Es especialmente útil para aplicaciones que necesitan alta disponibilidad y bajo tiempo de respuesta. Aunque Hazelcast se puede utilizar como una base de datos NoSQL, no está diseñado para ser un sistema de almacenamiento persistente como MySQL o MongoDB, sino que trabaja en memoria para operaciones rápidas.<br><br>
      <h3>Algunas de sus aplicaciones comunes son:</h3>
      <ul>
         <li>Cacheo distribuido (almacenamiento de datos temporales)</li>
         <li>Sesiones de usuario en aplicaciones web</li>
         <li>Procesamiento de datos en tiempo real</li>
         <li>Colas distribuidas para microservicios</li>
      </ul>
   </section>
   <br>
   <section id="hazelcast-ddl">
      <h2>Explicación DDL:</h2>
      <br>
      En Hazelcast, no existe un lenguaje específico para definir estructuras de datos como en las bases de datos tradicionales. El concepto de DDL en Hazelcast se refiere más a crear e inicializar las estructuras de datos distribuidas dentro del clúster. Algunas de estas estructuras son:
      <ul>
         <li><strong>IMap:</strong> Similar a un mapa clave-valor en memoria.</li>
         <li><strong>IQueue:</strong> Cola distribuida para almacenar elementos en orden.</li>
         <li><strong>IList:</strong> Lista distribuida similar a un array, pero distribuido entre los nodos.</li>
         <li><strong>ISet:</strong> Conjunto distribuido que garantiza que no haya valores duplicados.</li>
      </ul>
      <br>
      <strong>Ejemplo:</strong><br>
      <code>
      HazelcastInstance hazelcast = Hazelcast.newHazelcastInstance();<br>
      IMap&lt;String, String&gt; mapa = hazelcast.getMap("usuarios");<br>
      IQueue&lt;String&gt; cola = hazelcast.getQueue("tareas");
      </code>
   </section>
   <br>
   <section id="hazelcast-dml">
      <h2>Explicación DML:</h2>
      <br>
      Hazelcast también tiene comandos DML que te permiten manipular (consultar, modificar o eliminar) los datos que ya están almacenados en sus estructuras distribuidas. <br><br>
      <ul>
         <li><strong>put:</strong> Inserta o actualiza una clave en un mapa distribuido.<br>
            <code>mapa.put("u001", "Juan");</code>
         </li>
         <li><strong>get:</strong> Consulta el valor asociado a una clave.<br>
            <code>String nombre = mapa.get("u001");</code> → Resultado esperado: "Juan"
         </li>
         <li><strong>remove:</strong> Elimina una clave de una estructura.<br>
            <code>mapa.remove("u002");</code>
         </li>
         <li><strong>clear:</strong> Limpia todos los elementos de una estructura.<br>
            <code>mapa.clear();</code>
         </li>
         <li><strong>size:</strong> Obtiene el tamaño de una estructura de datos.<br>
            <code>int tamaño = mapa.size();</code> → Resultado esperado: 1
         </li>
      </ul>
   </section>
   <br>
   <section id="hazelcast-problemas">
      <h2>Problemas de la instalación:</h2>
      <br>
      <ul>
         <li><strong>Puerto ocupado:</strong> Hazelcast usa por defecto el puerto 5701. Si está ocupado, puede causar problemas.</li>
         <li><strong>Error al iniciar el clúster:</strong> Verifica que los puertos estén abiertos y accesibles.</li>
         <li><strong>Falta de permisos:</strong> Se necesitan permisos de administrador en algunas instalaciones.</li>
         <li><strong>Configuración incorrecta de red:</strong> Asegúrate de que los nodos puedan verse entre sí.</li>
         <li><strong>No puede conectarse al clúster:</strong> Verifica el archivo de configuración para aceptar nodos nuevos.</li>
      </ul>
   </section>
   <br>
   <section id="hazelcast-demo">
      <h2>Demostración práctica:</h2>
      <pre><code>
import com.hazelcast.core.Hazelcast;
import com.hazelcast.core.HazelcastInstance;
import com.hazelcast.core.IMap;

public class InventarioProductos {
public static void main(String[] args) {
HazelcastInstance hazelcast = Hazelcast.newHazelcastInstance();
IMap&lt;String, Integer&gt; inventario = hazelcast.getMap("inventario");

        inventario.put("Laptop", 10);
        inventario.put("Mouse", 25);
        inventario.put("Teclado", 15);

        System.out.println("Stock de Mouse: " + inventario.get("Mouse"));

        inventario.put("Mouse", inventario.get("Mouse") - 5);
        System.out.println("Stock actualizado de Mouse: " + inventario.get("Mouse"));

        inventario.remove("Teclado");
        System.out.println("¿Teclado sigue en inventario? " + inventario.containsKey("Teclado"));

        System.out.println("Inventario actual: " + inventario);
    }

}
</code></pre>
   </section>
</article>
<hr>
<br><br>
<article id="dynamodb">
   <hr>
   <h1>Amazon DynamoDB: Juan José</h1>
   <hr>
   <h2 id="dynamodb-ddl">Explicación DDL</h2>
   <p>-</p>
   <h2 id="dynamodb-dml">Explicación DML</h2>
   <p>-</p>
   <h2 id="dynamodb-problemas">Problemas de la instalación</h2>
   <p>-</p>
   <h2 id="dynamodb-demo">Demostración práctica</h2>
   <p>-</p>
</article>
<hr>
<br><br>
<article id="memcached">
   <hr>
   <h1>Memcached: Santiago</h1>
   <hr>
   <h2 id="memcached-ddl">Explicación DDL</h2>
   <p>-</p>
   <h2 id="memcached-dml">Explicación DML</h2>
   <p>-</p>
   <h2 id="memcached-problemas">Problemas de la instalación</h2>
   <p>-</p>
   <h2 id="memcached-demo">Demostración práctica</h2>
   <p>-</p>
</article>
<hr>
<br><br>
<article id="bibliografia">
   <hr>
   <h1>Bibliografía:</h1>
   <hr>
   <ul>
      <li><a href="https://redis.io/">Redis - Página oficial</a></li>
      <li><a href="https://etcd.io/">Etcd - Página oficial</a></li>
      <li><a href="https://oracle.com/database/technologies/nosql-database.html">Oracle NoSQL - Página oficial</a></li>
      <li><a href="https://aws.amazon.com/dynamodb/">Amazon DynamoDB - Página oficial</a></li>
      <li><a href="https://memcached.org/">Memcached - Página oficial</a></li>
      <li><a href="https://docs.hazelcast.com/">Hazelcast - Página oficial</a></li>
   </ul>
</article>