# Parte 4 – IA y Automatización

## 1) ¿Qué entiendo por automatización de pruebas?

La automatización de pruebas es el proceso de diseñar, desarrollar y ejecutar scripts o suites de pruebas utilizando herramientas y frameworks para verificar automáticamente el comportamiento de una aplicación o sistema. Su objetivo principal es reducir el esfuerzo manual repetitivo, aumentar la velocidad de ejecución, mejorar la consistencia de las validaciones y habilitar la ejecución frecuente (por ejemplo, en cada build o despliegue). La automatización es especialmente valiosa para pruebas de regresión, smoke, validaciones de APIs y flujos críticos que se repiten continuamente. Sin embargo, no reemplaza las pruebas manuales: ambas se complementan. Un enfoque correcto es automatizar lo estable y repetitivo (lo que aporta alto retorno) y mantener el testing manual para exploración, UX, casos nuevos o cambios frecuentes donde la automatización aún no es costo-efectiva.

## 2) Prompt para generar un test automatizado del formulario de registro usando Cursor o ChatGPT

Prompt sugerido:

Necesito que generes pruebas automatizadas E2E para un formulario de registro de usuario utilizando Playwright con TypeScript y el patrón Page Object Model.

Contexto del formulario:
- Campo: Nombre completo (input)
- Campo: Email (input)
- Campo: Número de identificación (input)
- Campo: Contraseña (input type password)
- Campo: Confirmación de contraseña (input type password)
- Botón: “Registrarse”

Requisitos del test:
- Incluir un test positivo que registre un usuario con datos válidos.
- Validar un mensaje de éxito o una redirección después del registro exitoso.
- Incluir dos tests negativos:
  - Email con formato inválido.
  - Contraseña y confirmación de contraseña que no coinciden.
- Validar mensajes de error específicos por cada campo.

Requisitos técnicos:
- Utilizar Playwright con TypeScript.
- Aplicar el patrón Page Object Model.
- Usar selectores estables (data-testid); si no existen, proponer alternativas seguras.
- Evitar el uso de waits fijos (sleep) y priorizar esperas basadas en estado.

Buenas prácticas:
- Generar datos de prueba únicos (por ejemplo, emails con timestamp).
- Implementar asserts claros y robustos.
- Capturar evidencias en caso de fallo (screenshots o video).
- Mantener el código limpio, legible y reutilizable.

Entrega esperada:
- Código completo de los tests listo para ejecutar.
- Estructura mínima del proyecto (tests/, pages/, playwright.config).
- Instrucciones claras para ejecutar los tests localmente.

## 3) ¿Cómo validaría que el código generado por IA es correcto?

Para validar que el código generado por IA es correcto, yo persolamente preferiría un enfoque incremental. En lugar de generar directamente una suite de pruebas compleja, comenzaría solicitando a la IA un test muy básico tipo “hola mundo” que valide un flujo simple y controlado.

El objetivo inicial de este test sería confirmar que:
- El framework está correctamente configurado.
- El test se ejecuta sin errores.
- La herramienta puede interactuar con la aplicación bajo prueba.
- Las aserciones básicas funcionan como se espera.

Una vez validado que este primer test sencillo funciona correctamente, iría aumentando gradualmente el nivel de detalle y complejidad del código generado por la IA. En cada iteración agregaría nuevos elementos, como más validaciones, escenarios negativos, manejo de datos dinámicos o separación en Page Objects, verificando siempre que los tests sigan siendo estables y comprensibles.

Este enfoque incremental permite:
- Detectar errores de configuración o de concepto desde etapas tempranas.
- Reducir el riesgo de introducir código complejo que sea difícil de depurar.
- Validar paso a paso que el código generado realmente aporta valor y cubre el comportamiento esperado.
- Mantener control y entendimiento total del código automatizado, evitando depender ciegamente de la IA.

Finalmente, contrastaría los resultados de los tests automatizados con los escenarios manuales definidos previamente. Si el test básico funciona, y los tests más complejos fallan correctamente cuando se introduce un defecto intencional, se puede concluir que el código generado por la IA es confiable y está validando adecuadamente el comportamiento del sistema.
