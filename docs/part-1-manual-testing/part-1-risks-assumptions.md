# ⚠️ Riesgos y Supuestos  
**Parte 1 – Pruebas Manuales (Gherkin)**

Este documento corresponde a la **Parte 1 del ejercicio**, donde se solicita **identificar al menos 3 posibles bugs o riesgos** asociados al formulario de registro de usuarios.

Los riesgos y supuestos descritos a continuación fueron identificados durante el análisis funcional del formulario y están basados en criterios de pruebas manuales.

---

## ⚠️ Riesgos Identificados

1. **Validación insuficiente de los campos**
   - El sistema podría permitir formatos de email inválidos, contraseñas débiles o números de identificación con caracteres no numéricos.
   - Impacto: creación de cuentas inválidas e inconsistencia en los datos.

2. **Registro de usuarios duplicados**
   - Puede no existir una validación que evite el registro de múltiples usuarios con el mismo email o número de identificación.
   - Impacto: duplicación de información y conflictos en procesos de autenticación.

3. **Múltiples envíos del formulario**
   - El botón "Registrarse" podría permitir múltiples envíos por doble clic o por tiempos de respuesta lentos.
   - Impacto: creación de cuentas duplicadas.

4. **Manejo incorrecto de espacios en blanco**
   - Los campos como "Nombre completo" o "Email" podrían no eliminar espacios al inicio o al final antes de guardarse.
   - Impacto: problemas al iniciar sesión o errores inesperados de validación.

5. **Mensajes de error poco claros**
   - Los mensajes de error podrían no indicar claramente qué campo es incorrecto o la razón del error.
   - Impacto: mala experiencia de usuario y aumento de solicitudes de soporte.

---

## 📌 Supuestos

1. Todos los campos del formulario de registro son obligatorios, salvo que se indique lo contrario.
2. El campo email debe ser único y cumplir con un formato válido.
3. El número de identificación debe ser numérico y único.
4. La contraseña debe cumplir con una política mínima de complejidad.
5. Las validaciones se aplican tanto en el lado del cliente como en el servidor.
