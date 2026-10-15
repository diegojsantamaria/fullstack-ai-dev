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

## Asincronico vs Sincronico

* Segun la IA
 * Lo sincronico responde inmediatamente, lo asincronico hay que esperar
 * Una llamada sincronica devuelve el control al programa para ejecutar la proxima instruccion enseguida, una llaada asincronica puede bloquear el programa hasta que termine
 * Llamadas Sincronicas
  * print / console.log
 * Llamadas Asincronicas
   * Llamada a una API
   * Consultar una base de datos
   * Lleer un archivo
   * Hacer un input

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

> [!NOTE]
> Aca no hay forma de distinguir si es una llamada sincronica o asincronica

* Esta linea respuesta = requests.get(url) se tiene que ejecutar antez de devolverle el control al programa
* Puede tardar varios MS dependiendo la velocidad de conexion

## Desde javascript

* Requisitos "NodeJS" instalado

### Hola Mundo desde el Server 

```
node --version
```

* Sino lo instalan de : https://nodejs.org/es

* Hola Mundo en javascript

```javascript
console.log("Hola, mundo!");
```

* Para ejecutarlo
```
>node hola-mundo.js
Hola, mundo!
```

### Hola Mundo desde el cliente

* Si lo quiero del lado del cliente

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        console.log("Hola, mundo!");
    </script>
</body>
</html>
```

### Llamada a la api desde el server

* Version 1 : Con await modo bloquante

```
let url = "https://rickandmortyapi.com/api/character"

let respuesta = await fetch(url)

let personajes = await respuesta.json()

console.log(JSON.stringify(personajes, null, 4))
```

> [!NOTE]
> Aca se ve claro con el await que  await fetch(url) es una llamada asincronica


* Version 2 : Con llamadas asincronicas

```
let url = "https://rickandmortyapi.com/api/character"

//La llamada a la API se hace de manera asíncrona, pero el bucle for se ejecuta inmediatamente
fetch(url)
    .then(respuesta => respuesta.json())
    .then(personajes => {
        console.log(JSON.stringify(personajes, null, 4))
    })


for (let i = 0; i < 500; i++) {
    console.log("Esto funciona mientras se hace la llamda a la api")
}
```

### Llamada a API desde el Browser

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script type="module">
        let url = "https://rickandmortyapi.com/api/character"

        let respuesta = await fetch(url)

        let personajes = await respuesta.json()

        alert(JSON.stringify(personajes, null, 4))
    </script>
</body>
</html>
```


---
BREAKE
HAsta y 30
---

# JSon-Server

* Es un paquete de nodejs que permite emular una api rest con un json
* Sirve para emular un backend con todas las operaciones get, post, put, delete hasta tener la version final productiva
* Permite programar la parte de la api rest del cliente

* Instalarla

```
npm install -g json-server
```

> [!NOTE]
> Esto se puede ejecutar en cualquier directorio. El -g instala el paquete localmente

```
json-server --version
```

* Vamos a crear este documento db.json

```json
{
    "personas": [
        {
            "id": 1,
            "nombre": "Juan"
        },
        {
            "id": 2,
            "nombre": "Maria"
        },
        {
            "id": 3,
            "nombre": "Pedro"
        }
    ]
}
```

* Lo ejecutamos con:

```
>json-server --watch db.json
```

* Accedemos en el navegador

```
http://localhost:3000/personas
```

```
http://localhost:3000/personas/1
```

* Lo probamos con Thunder Client desde vscode
  * Probemos los get

* Pruebo el POST
  * POST http://localhost:3000/personas
  * Completar el body con un nombre

<img width="542" height="226" alt="image" src="https://github.com/user-attachments/assets/305a5570-f27d-4bb7-8d7d-5c8f4ee29251" />
