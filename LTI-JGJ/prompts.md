# Asistente usado: Google Gemini

## Prompts usados:

### Prompt 1: 
Eres un experto en producto, con experiencia en sistemas ATS (Applicant Tracking System) que se explica en la imagen adjunta. Vamos a diseñar el software ATS para la startup LTI. ¿Qué funcionalidades básicas tiene un sistema ATS? Descríbemelas en un listado, ordenado de mayor a menor prioridad.

### Prompt 2: 
¿Qué beneficios obtiene el cliente de un sistema ATS para considerar su uso?

### Prompt 3: 
¿Qué alternativas tiene el cliente a usar un sistema ATS y cuando pueden ser relevantes?

### Prompt 4: 
¿Cómo es el customer journey normal de un cliente que usa un Sistema ATS?

### Prompt 5: 
Por qué un cliente elige actualmente usar un sistema ATS? Que debilidades tienen los sistemas ATS actuales del mercado?

### Prompt 6: 
Considera que el software LTI se basará en hacer una gran experiencia del candidato y en que el software de LTI se integrará con los sistemas más empleados actualmente en las empresas. Considera toda la información de esta conversación y realiza lo siguiente:
1. Descripción breve del software LTI con su valor añadido y ventajas competitivas.
2. Explicación de las funciones principales.
3. Genera un diagrama Lean Canvas para el modelo de negocio con el código mermaid.
Antes de que respondas, dime si tienes alguna duda para completar las 3 tareas

1. El segmento objetivo son startups/scaleups.
2. Usaremos un portal donde el candidato vea su progreso en tiempo real y además, usaremos whatsapp para compartir información resumida

### Prompt 7: 
Eres un analista de software experto. Estoy construyendo el software LTI. Enumera y describe brevemente los 3 casos de uso más importantes a implementar para lograr una funcionalidad básica. Representa estos casos de uso en el tipo de diagrama más adecuado usando el formato plantUML. Acorde a la sintaxis y buenas prácticas UML, define y describe lo que sea necesario.

### Prompt 8: 
Eres un brillante arquitecto de software. Eres capaz de diseñar, explicar y diagramar los diferentes aspectos de un sistema de software.
Estoy construyendo el software LTI. A partir de toda la información de esta conversación, qué entidades del modelo de datos son importantes en un sistema ATS? Dame los campos más importantes de cada una y cómo se relacionan entre entidades. Genera el modelo de datos en código diagrama mermaid.

### Prompt 9: 
Eres un experto arquitecto de software, especialista en sistemas ATS. Considera toda la información de esta conversación y dime 3 opciones de arquitectura de software para desarrollar el software LTI. Para cada opción enumera sus ventajas y desventajas y dime cuál de las 3 opciones consideras que es la mejor para el software LTI. antes de responder dime si tienes alguna duda para determinar las opciones de arquitectura de software?

1. delegar el procesamiento pesado a APIs externas.
2. es aceptable una actualización mediante refresco/polling cada vez que el usuario entra
3. una arquitectura que sea extremadamente eficiente recibiendo miles de eventos
4. invertir un poco más de tiempo ahora en desacoplar piezas para no tener "deuda técnica" en 6 meses

### Prompt 10: 
La arquitectura EDA propuesta en qué arquitectura de las más conocidas encaja? Arquitecturas más conocidas:
Arquitectura por capas
Arquitectura de microkernel
Arquitectura orientada a eventos
Arquitectura de microservicios
Arquitectura hexagonal

### Prompt 11: 
Considera que vamos a usar la arquitectura EDA, genera el diagrama en código mermaid

### Prompt 12: 
Considera toda la información de esta conversación. Eres un experto arquitecto de software. Genera un diagrama C4. Antes de responder dime cuales son los componentes del sistema que consideras

### Prompt 13: 
Genera el diagrama c4 que llegue a profundidad con el componente de Sistemas externos