# Parte 3 – Base de Datos

  
Se cuenta con una tabla llamada users con la siguiente estructura:

id | name | email | document | created_at

---

Consulta SQL para buscar un usuario por email

Esta consulta permite obtener la información de un usuario específico a partir de su correo electrónico, lo cual es útil para validaciones de registro, login o verificación de duplicados.

    SELECT id, name, email, document, created_at
    FROM users
    WHERE email = 'usuario@test.com';

---

Consulta SQL para contar cuántos usuarios se registraron hoy

Esta consulta permite validar cuántos registros fueron creados en la fecha actual, lo cual es útil para métricas, reportes diarios y validaciones de procesos automáticos.

    SELECT COUNT(*) AS total_users_today
    FROM users
    WHERE DATE(created_at) = CURRENT_DATE;

---

Explicación de por qué es importante que QA conozca bases de datos

Es importante que un QA tenga conocimientos básicos de bases de datos porque le permite validar directamente la información almacenada por la aplicación, asegurando que los datos enviados desde el frontend o la API se persistan correctamente en el sistema.

El conocimiento en SQL ayuda a detectar inconsistencias entre lo que se muestra al usuario y lo que realmente se guarda en la base de datos, identificar registros duplicados, validar reglas de negocio y confirmar que las operaciones CRUD se ejecutan correctamente.

Además, permite al QA investigar defectos de forma más eficiente, apoyar la reproducción de errores, validar procesos backend y colaborar de manera más efectiva con desarrolladores y equipos técnicos, reduciendo el tiempo de diagnóstico y mejorando la calidad del producto final.
