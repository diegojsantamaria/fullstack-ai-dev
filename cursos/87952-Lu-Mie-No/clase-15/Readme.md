# Clase 15 - 28 de Septiembre del 2026

# Repaso

* Arquitectura de Sistema
  * POO
    * Consistencia de Objetos
      * Constructores
      * Getters / Setters
    * Relaciones entre Objetos
      * Cardinalidad entre las Relaciones
  * Diseño por capas
    * Presentacion
    * Dominio
    * Persistencia
  * UML
    * Diagrama de Clases

---

# Ejemplo Practico de la arquitectura en capas

* Vamos a desarrollar un CRUD con API rest
  * CRUD (CREATE READ UPDATE DELETE) en criollo se le dice ABM (Alta Baja modificacion)
  * Vamos a ser un CRUD
* Arquitectura
  * Presentacion
      * API Rest
      * Hecha en Flask
      * Endpoints
  * Dominio / Modelo
    * Clase Alumno
  * Persistencia
    * Clase RepositorioAlumnos
    * Por ahora guarda mis alumnos en memoria

## Primero arranquemos con Flask

* Hoy trabamos en local
# 
