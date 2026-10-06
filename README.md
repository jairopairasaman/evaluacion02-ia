# Evaluación 02: Prompts con IA y Documentación Técnica

## Tabla de Contenidos
1. [Pregunta 1: Anatomía de un prompt efectivo (ChatGPT)](#pregunta-1-anatomía-de-un-prompt-efectivo-chatgpt)
2. [Pregunta 2: Razonamiento paso a paso y costos de IA (Claude)](#pregunta-2-razonamiento-paso-a-paso-y-costos-de-ia-claude)
3. [Pregunta 3: Extracción estructurada con few-shot (Gemini)](#pregunta-3-extracción-estructurada-con-few-shot-gemini)
4. [Diagrama del Flujo de Trabajo](#diagrama-del-flujo-de-trabajo)
5. [Checklist de Entregables](#checklist-de-entregables)
6. [Tabla Comparativa y Conclusión](#tabla-comparativa-y-conclusión)

## Pregunta 1: Anatomía de un prompt efectivo (ChatGPT)

### Componentes del Prompt
| Componente | Descripción |
| --- | --- |
| **Rol** | Líder de producto de software |
| **Contexto** | Feedback de 8 reseñas enviadas por usuarios de la app "RutaFácil" |
| **Tarea** | Categorizar las opiniones e identificar las 3 acciones prioritarias |
| **Formato de salida** | Tabla Markdown (Categoría \| Cantidad \| Ejemplo) y lista numerada |
| **Restricciones** | Clasificar ambos problemas mencionados en la reseña 7 |

### Prompts Utilizados

**Prompt Inicial (Vago):**
```text
Resume estas reseñas

prompt estrcuturado

Actúa como un líder de producto de software. 

Analiza las siguientes 8 reseñas recibidas en la aplicación "RutaFácil":

1. "El pedido llegó 50 minutos tarde y la comida fría."
2. "La app se cerró dos veces al pagar con Yape."
3. "El repartidor fue muy amable, todo perfecto."
4. "Tercera vez que mi pedido llega tarde este mes."
5. "El costo de envío subió a S/ 9, es demasiado."
6. "No puedo ver el seguimiento del pedido en el mapa, se queda cargando."
7. "Llegó con una hora de retraso y faltaba una bebida."
8. "Escribí al chat de soporte y nadie respondió en 2 días."

Entrégame la respuesta únicamente con la siguiente estructura:
1. Una tabla Markdown con tres columnas: Categoría | Cantidad | Ejemplo.
2. Una lista numerada con las 3 acciones prioritarias que debemos implementar, justificando brevemente cada una.

Restricción: Si una reseña menciona dos problemas (como la reseña 7), clasifica ambos temas en sus respectivas categorías correspondientes.


Prompt directo

Calcula el costo mensual de 120,000 consultas a $3 por millón de entrada (1200 tokens) y $15 por millón de salida (300 tokens). Dame solo los montos finales.

promt hecho

contexto:
Trabajas como analista financiero de TI en la empresa EduTech. Estamos evaluando la viabilidad económica de lanzar un chatbot de soporte para estudiantes.

datos:
- Presupuesto máximo aprobado: US$ 900 mensuales.
- Volumen estimado: 4,000 consultas por día durante 30 días (120,000 consultas en total).
- Escenario Actual: 1,200 tokens de entrada y 300 tokens de salida por consulta.
- Escenario Optimizado: 700 tokens de entrada y 300 tokens de salida por consulta.
- Precios API: US$ 3.00 / 1M tokens de entrada y US$ 15.00 / 1M tokens de salida.

tarea:
Calcula el costo total mensual de ambos escenarios, el ahorro mensual en dólares y porcentaje, e indica si cada escenario cumple el presupuesto.

instrucción autocritica:
Antes de generar la respuesta final, revisa minuciosamente todas las multiplicaciones y sumas para garantizar exactitud matemática.

formato:
Escribe tu proceso dentro de <razonamiento></razonamiento> y la respuesta final dentro de <respuesta></respuesta>.

prompts utilizados

Convierte estos 3 correos de postulantes a un objeto JSON según los campos: nombre, puesto, anios_experiencia, tecnologias, disponibilidad y pretension_soles.

Extrae la información de los correos recibidos y conviértela en un arreglo JSON siguiendo este esquema:
{
  "nombre": string,
  "puesto": string,
  "anios_experiencia": number,
  "tecnologias": array of strings,
  "disponibilidad": string,
  "pretension_soles": number or null
}

Ejemplos de entrenamiento:
1. Correo: "Hola, me llamo Juan Pérez y aplico a Desarrollador Python. Tengo 2 años de experiencia. Pretensión 3500 soles. Puedo iniciar de inmediato."
JSON:
{
  "nombre": "Juan Pérez",
  "puesto": "Desarrollador Python",
  "anios_experiencia": 2,
  "tecnologias": ["Python"],
  "disponibilidad": "Inmediata",
  "pretension_soles": 3500
}

2. Correo: "Buenas, soy María López para QA. Llevo año y medio con Selenium y Java."
JSON:
{
  "nombre": "María López",
  "puesto": "QA",
  "anios_experiencia": 1.5,
  "tecnologias": ["Selenium", "Java"],
  "disponibilidad": "No especificada",
  "pretension_soles": null
}

3. Correo: "Carlos Gómez, diseñador UX/UI con 4 años usando Figma y Adobe XD. Pretendo S/ 5000."
JSON:
{
  "nombre": "Carlos Gómez",
  "puesto": "Diseñador UX/UI",
  "anios_experiencia": 4,
  "tecnologias": ["Figma", "Adobe XD"],
  "disponibilidad": "No especificada",
  "pretension_soles": 5000
}

Procesa los siguientes datos:
[Pega los 3 correos de la evaluación]

  graph TD
    A[Análisis del Caso de Negocio] --> B[Diseño del Prompt Inicial / Vago]
    B --> C[Ejecución en Modelo de IA]
    C --> D[Verificación Manual de Resultados]
    D --> E{¿Cumple Criterios?}
    E -- No --> F[Refinamiento con Prompt Estructurado / Few-Shot]
    F --> C
    E -- Sí --> G[Documentación Final en GitHub]

Checklist de Entregables
Pregunta 1: Análisis de caso, prompt vago vs estructurado y conteo verificado en ChatGPT.

Pregunta 2: Cálculo manual de presupuesto, prompt XML con CoT y autocrítica en Claude.

Pregunta 3: Esquema JSON, prompt zero-shot vs few-shot y validación de sintaxis en Gemini.

Pregunta 4: Documentación en GitHub Flavored Markdown, badges, tabla de contenidos, imágenes y diagrama Mermaid.

Criterio,ChatGPT,Claude,IA libre: Gemini
Calidad de la respuesta (1-5),5,5,4
Precisión (aciertos / total verificado),8/8 (100%),4/4 (100%),3/3 (100%)
Precio del plan o de la API (US$),US$ 20/mes (API: $2.50/1M),US$ 20/mes (API: $3.00/1M),Gratuito (API: $0.35/1M)
N.° de prompts hasta un resultado útil,2,2,2
Tokens aproximados y costo estimado,"~1,500 tokens ($0.00375)","~1,200 tokens ($0.0036)","~1,000 tokens ($0.00)"
```

###
| Criterio | ChatGPT | Claude | IA libre: Gemini |
| --- | :---: | :---: | :---: |
| Calidad de la respuesta (1-5) | 5 | 5 | 4 |
| Precisión (aciertos / total verificado) | 8/8 (100%) | 4/4 (100%) | 3/3 (100%) |
| Precio del plan o de la API (US$) | US$ 20/mes (API: $2.50/1M) | US$ 20/mes (API: $3.00/1M) | Gratuito (API: $0.35/1M) |
| N.° de prompts hasta un resultado útil | 2 | 2 | 2 |
| Tokens aproximados y costo estimado | ~1,500 tokens ($0.00375) | ~1,200 tokens ($0.0036) | ~1,000 tokens ($0.00) |###
