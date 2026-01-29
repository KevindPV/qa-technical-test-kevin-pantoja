# Parte 2 – Pruebas de API (Postman)

Este documento contiene la solución correspondiente al **punto 2 del ejercicio**, enfocada en pruebas de API utilizando Postman.



## 📌 Escenario

### API ficticia
**POST** `https://api.bia-energy.test/users`

### Body esperado
```json
{
  "name": "Juan Pérez",
  "email": "juan@test.com",
  "document": "12345678",
  "password": "Password123"
}

```


## Test exitoso

### Descripción  
Validar que la API permita crear un usuario cuando todos los campos requeridos contienen datos válidos.

Request

    {
      "name": "Juan Pérez",
      "email": "juan@test.com",
      "document": "12345678",
      "password": "Password123"
    }

Status code esperado
```json
201 Created
```

Validaciones sobre el response  
- El response debe tener formato JSON.  
- Debe retornar un identificador único del usuario (id o userId).  
- Los campos name, email y document deben coincidir con los valores enviados.  
- El campo password no debe ser retornado en el response.

---

## Test fallido 1 – Email con formato inválido

Descripción  
Validar que la API rechace la creación del usuario cuando el email no cumple con un formato válido.

Request

    {
      "name": "Juan Pérez",
      "email": "juan@test",
      "document": "12345678",
      "password": "Password123"
    }

Status code esperado  
```json
400 Bad Request
```

Validaciones sobre el response  
- El response debe tener formato JSON.  
- Debe incluir un mensaje de error claro y descriptivo.  
- El mensaje debe indicar que el campo email es inválido.

---

## Test fallido 2 – Campo obligatorio faltante

Descripción  
Validar que la API rechace la creación del usuario cuando falta un campo obligatorio.

Request

    {
      "name": "Juan Pérez",
      "email": "juan@test.com",
      "password": "Password123"
    }

Status code esperado
```json
Error 400 – Bad Request: el campo obligatorio `document` está ausente en el request.
```

Validaciones sobre el response  
- El response debe tener formato JSON.  
- Debe indicar claramente que el campo obligatorio document está ausente.  
- El mensaje de error debe ser claro y entendible para el consumidor de la API.

---

## Organización de los tests en Postman (Opcional)

Los tests pueden organizarse en Postman de la siguiente manera:

Colección  
BIA Energy - Users API

Carpeta  
POST /users

Requests incluidos  
1. Create user – success (201)  
2. Create user – invalid email (400)  
3. Create user – missing document (400)

Buenas prácticas  
- Definir la variable de entorno {{baseUrl}} con el valor https://api.bia-energy.test  
- Utilizar emails dinámicos (por ejemplo con timestamp) para evitar registros duplicados.  
- Agregar scripts de test en Postman para validar status codes, estructura del response y que no se exponga información sensible como la contraseña.

---

Conclusión  

Este documento cumple con los requerimientos del ejercicio de API Testing, describiendo un caso exitoso, dos casos fallidos, los códigos de estado esperados, las validaciones sobre el response y una organización clara de los tests en Postman.
