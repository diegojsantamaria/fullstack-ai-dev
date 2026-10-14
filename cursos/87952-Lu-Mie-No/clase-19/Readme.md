# Clase 19 - 14 Octubre del 2026

# Repaso

* Dev
  * Port Forwarding
  * Expusimos nuestra API rest al publico
    * Pero no se podia llamar desde otro sitio
    * Tuvimos que habilitarle cors
* AiDev
  * Arquitectura Cliente-Servidor
    * Programamos el cliente con Lovable
      * Utilizar Bun para empaquetar y ejecutar el cliente

---

# Tarea pendiente

* Completar la API rest con el PUT y el DELETE
  * https://forms.cloud.microsoft/Pages/ResponsePage.aspx?id=FPbD6dnIlUCa1IfSyafYxE4uGCthyi9EnQYg85vv3slUMDdKUklRTkg5M0kzWEgzMVRXNThMUDVTNy4u
 
> [!NOTE]
> No se olviden de completar. Tengo solo 7 respuestas

---

# Colab de la clase

> https://colab.research.google.com/drive/1xh0dJAbk5udUapZ5I5zdEK7IW5fBHcRB?usp=sharing

---

# Consumir Api Rest

## Api para consumir

* https://rickandmortyapi.com/api/character
* https://spapi.dev/api/characters

## Desde python

```
import requests
import json

url = "https://rickandmortyapi.com/api/character"

respuesta = requests.get(url)

personajes = respuesta.json()

##print(type(json))
##print(json)
print(json.dumps(personajes, indent=4, ensure_ascii=False))
```

## Desde javascript

# Base de Datos


