# Clase 21 - 21 de Octubre del 2026

# Repaso 

* Bases de Datos
  * Motores de Base de Datos
    * Relacionales
      * SQLite
      * SQLServer
      * Postgres
      * Oracle
      * MySQL
    * No Relacionales
      * MongoDB
    * Vectoriales (Guardar Embeddings)
      * ChromaDB
  * Arquitectura
    * Cliente-Servidor
    * Standalone
  * HostigDB
    * Supabase
  * SQLite
    * Instalacion
    * Standalone
    * Uso
      * DBBrowser
      * CLI / Terminal (Sqlite3)
  * SQL (Structured Query Language)
    * DDL
      * CREATE TABLE
    * DML
      * INSERT
      * UPDATE
      * COMMIT
    * DQL
      * SELECT

# Novedades

* Spotify Borra temas con IA
  * https://www.abc.es/tecnologia/redes/spotify-frena-fraude-inteligencia-artificial-borra-millones-20261021192722-nt.html

# SQLite desde Python

* Creamos el colab de la clase
  * https://colab.research.google.com/drive/1XQh6wQ7Q4IMfLt20grSZp_1XQgHhYHVp?usp=sharing
 
* Libreria SQLITE
  * modulo sqlite3
    * Viene siempre instalado
  * Clase Connection 
    * Representa una conexion con una BD
    * Crea o abre la base de datos
  * Clase Cursor
    * Me permite ejecutar acciones sobre la base de datos mediante el metodo execute
    * Me permite recorrer tambien las tablas

* Estructura basica para interactuar con SQLITE

```python
import sqlite3

#Abrir una bd o crearla si no existe
conn = sqlite3.connect('personas.db')

#Crear un cursor
cursor = conn.cursor()

## Hago lo que tengo que hacer

cursor.execute(...)

conn.commit();
conn.close();
```
 
* Creamos la bd

```python
import sqlite3

#Abrir una bd o crearla si no existe
conn = sqlite3.connect('personas.db')

#Crear un cursor
cursor = conn.cursor()

# Creo una tabla personas con ID, nombre, apellido
ddl_tabla_personas = """
CREATE TABLE personas (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nombre TEXT NOT NULL,
    apellido TEXT NOT NULL
);
"""

cursor.execute(ddl_tabla_personas)

# Confirmar los cambios
conn.commit()

# Cerrar la conexión
conn.close()
```

* Crear agunos registros

```python
import sqlite3

#Abrir una bd o crearla si no existe
conn = sqlite3.connect('personas.db')

#Crear un cursor
cursor = conn.cursor()

# Los ? se llaman parametros que tenemos que definir a lahora de ejecutar la consulta
dml_insertar_persona = """
INSERT INTO personas (nombre, apellido)
VALUES (?, ?);
"""

nombre = input("Ingrese el nombre: ")
apellido = input("Ingrese el apellido: ");

cursor.execute(dml_insertar_persona, (nombre, apellido) )

conn.commit();
conn.close();

print("Persona creada correctamente")
```

> [!NOTE]
> Ejecutar esta celda varias veces

* Listamos la tabla de personas

```python
import sqlite3

#Abrir una bd o crearla si no existe
conn = sqlite3.connect('personas.db')

#Crear un cursor
cursor = conn.cursor()

## Hago lo que tengo que hacer
dql_select_personas = "SELECT * FROM personas;"

cursor.execute(dql_select_personas)

# Devuelve todos los registros de la consulta en una lista de tuplas
personas = cursor.fetchall()

for persona in personas:
    print(persona)


conn.commit();
conn.close();
```

* Este va para ustedes
  * # Quiero preguntarle el id al usuario y que borre el registro con ese id

```python
import sqlite3
#Abrir una base de datos o crearla si no existe
conn = sqlite3.connect('personas.db')
#Crear un cursor
cursor = conn.cursor()

#Los ? son parámetros
dml_borrar_persona = "DELETE FROM personas WHERE id = ?;"
id_persona = input("Ingrese el ID de la persona a borrar: ")
cursor.execute(dml_borrar_persona, (id_persona,) )

# Confirmar los cambios
conn.commit();
# Cerrar la conexión
conn.close();
```

> [!NOTE]
> La coma no pertenece a SQL, sino a la sintaxis de Python para crear una tupla de un solo elemento. esto dice la IA

* Descargr el archivo personas.db y abrirlo localmente con el dbbrowser

---
# BREAK
Hasta y 25?
---
