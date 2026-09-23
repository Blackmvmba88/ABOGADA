# ABOGADA — BlackMamba LEX

**Legal Intelligence OS para abogados, abogadas y despachos.**

ABOGADA no nace como un chatbot jurídico. Nace como un sistema operativo legal que conecta **clientes, expedientes, documentos, hechos, evidencia, plazos, comunicaciones, dinero y conocimiento jurídico** mediante inteligencia artificial verificable.

> Objetivo: reducir trabajo mecánico, aumentar trazabilidad y convertir cada asunto jurídico en un objeto computable sin sustituir el criterio profesional.

## Principios

1. **Human-in-the-loop:** la IA puede leer, sugerir, preparar y automatizar tareas autorizadas; no toma decisiones jurídicas finales por sí sola.
2. **Evidence first:** toda afirmación relevante debe poder remontarse a una fuente, documento, página, fecha o dato estructurado.
3. **No hallucination by design:** si una fuente no existe o no fue encontrada, el sistema lo declara.
4. **Case-centric:** el expediente es el centro; todo lo demás se relaciona con él.
5. **Legal Knowledge Graph:** además de archivos, el sistema modela relaciones entre personas, hechos, documentos, obligaciones, fechas, evidencia y argumentos.
6. **Privacy and auditability:** permisos, cifrado, bitácora, versionado y trazabilidad desde el primer día.

## Índice funcional

### 1. Expediente inteligente
- ficha única del asunto
- estado actual
- cronología automática
- próximos pasos
- riesgos y bloqueos
- documentos, personas, evidencia y comunicaciones relacionadas

### 2. Intake y clientes
- entrevista inicial asistida
- extracción de hechos y fechas
- detección de información faltante
- revisión preliminar de conflictos
- portal del cliente
- CRM legal

### 3. Document Intelligence
- PDF, Word, imágenes, escaneos, correos y chats exportados
- OCR cuando sea necesario
- clasificación automática
- resumen
- extracción de entidades, cantidades, fechas, cláusulas y obligaciones
- detección de anexos faltantes
- comparación entre versiones

### 4. Contratos
- plantillas
- biblioteca de cláusulas
- generación por variables
- comparación de versiones
- detección de riesgos e inconsistencias
- obligaciones, vencimientos y renovaciones
- flujo de revisión y aprobación

### 5. Investigación jurídica
- legislación
- reglamentos
- jurisprudencia
- criterios
- doctrina y fuentes permitidas
- respuesta con citas verificables
- radar de reformas y cambios normativos

### 6. Timeline & Facts
- extracción de eventos
- fecha del documento vs. fecha del hecho
- hechos conocidos, disputados y pendientes de probar
- contradicciones
- huecos temporales
- navegación cronológica

### 7. Evidencia
- catálogo de pruebas
- procedencia
- hash
- cadena de custodia
- relación con hechos
- duplicados
- contradicciones
- metadatos
- audio, video, fotografías y transcripciones

### 8. Legal Knowledge Graph
Relaciones computables:

```text
PERSONA
  -> firmó -> CONTRATO
  -> contiene -> OBLIGACIÓN
  -> vence -> FECHA
  -> respaldada por -> EVIDENCIA
  -> relacionada con -> HECHO
  -> afecta -> ARGUMENTO
  -> pertenece a -> EXPEDIENTE
```

### 9. Redacción jurídica
- demandas
- contestaciones
- promociones
- recursos
- contratos
- convenios
- dictámenes
- cartas
- informes
- minutas
- respuestas a clientes

### 10. Validador de escritos
Antes de presentar:
- nombres
- expediente
- juzgado
- fechas
- cantidades
- referencias
- anexos
- numeración
- firmas
- campos pendientes
- consistencia interna

### 11. Teoría del caso
- hechos conocidos
- hechos controvertidos
- hechos por demostrar
- evidencia favorable y adversa
- argumentos
- posibles contraargumentos
- preguntas abiertas
- debilidades

### 12. Simulación adversarial
- IA defensora
- IA contraparte
- verificador de evidencia
- verificador de citas
- crítico lógico
- juicio/moot court de práctica

La simulación sirve para preparación; no pretende predecir la conducta real de jueces, autoridades o contrapartes.

### 13. Interrogatorios y declaraciones
- preguntas por objetivo
- evidencia vinculada
- respuestas previas
- contradicciones
- seguimiento sugerido
- preparación oral

### 14. Calendario procesal
- extracción de plazos
- audiencias
- vencimientos
- renovaciones
- comparecencias
- tareas previas
- recordatorios

### 15. Motor de pendientes
Cada asunto mantiene:
- siguiente acción
- responsable
- fecha
- dependencia
- prioridad
- bloqueo

### 16. Comunicaciones
- clasificación de correo
- vinculación al expediente
- extracción de compromisos
- borradores de respuesta
- mensajes pendientes
- archivos adjuntos

### 17. Audio jurídico
Con autorización y dentro del marco legal aplicable:
- transcripción
- identificación de hablantes
- resumen
- fechas
- compromisos
- notas vinculadas al expediente

### 18. Administración del despacho
- carga de trabajo
- horas
- gastos
- honorarios
- anticipos
- cuentas por cobrar
- facturación
- rentabilidad por asunto

### 19. Búsqueda universal
Ejemplo:

> “Encuentra el contrato donde Carlos prometió entregar la maquinaria antes de junio y dime si después cambió esa fecha.”

La búsqueda puede atravesar documentos, notas, correos, expedientes y evidencia autorizada.

### 20. Memoria institucional
- estrategias históricas
- plantillas
- cláusulas
- investigaciones
- procedimientos internos
- lecciones aprendidas

### 21. Automatización por eventos
Ejemplo:

```text
ENTRA NOTIFICACIÓN
      ↓
IDENTIFICA EXPEDIENTE
      ↓
EXTRAE FECHA / EVENTO
      ↓
ACTUALIZA TIMELINE
      ↓
GENERA TAREA
      ↓
AVISA RESPONSABLE
      ↓
PREPARA MATERIAL
      ↓
PROPONE SIGUIENTE ACCIÓN
      ↓
REVISIÓN HUMANA
```

### 22. Niveles de autoridad de IA

| Nivel | Capacidad |
|---|---|
| 0 | Leer |
| 1 | Sugerir |
| 2 | Preparar |
| 3 | Ejecutar con autorización |
| 4 | Automatizar únicamente tareas expresamente permitidas |

### 23. Agentes especializados
- Document Agent
- Research Agent
- Citation Verifier
- Contract Agent
- Timeline Agent
- Evidence Agent
- Calendar Agent
- Communication Agent
- Billing Agent
- Privacy/Audit Agent

Todos coordinados por un **Legal Orchestrator**.

## Arquitectura conceptual

```text
                         ABOGADA
                    BLACKMAMBA LEX
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
     CLIENTES         EXPEDIENTES        DESPACHO
        │                 │                 │
      Intake          Legal Graph        Finanzas
     Conflictos        Timeline          Equipo
      Portal           Evidencia         Agenda
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
   DOCUMENTOS        INVESTIGACIÓN     COMUNICACIÓN
        │                 │                 │
       OCR           Legislación           Email
   Contratos        Jurisprudencia       Mensajes
    Escritos          Verificación        Cliente
        └─────────────────┼─────────────────┘
                          │
                    AI ORCHESTRATOR
                          │
          ┌───────────────┼───────────────┐
          │               │               │
       Agentes       Policy Engine     Audit Log
          │               │               │
          └───────────────┼───────────────┘
                          │
                    HUMAN APPROVAL
```

## Núcleo de datos

Entidades iniciales:

- `Matter` / Expediente
- `Person`
- `Organization`
- `Document`
- `Fact`
- `Event`
- `Evidence`
- `Obligation`
- `Deadline`
- `Argument`
- `Communication`
- `Task`
- `Invoice`
- `SourceCitation`
- `AuditEvent`

## Primera regla técnica

La respuesta de IA ideal debe poder representarse como:

```text
AFIRMACIÓN
  -> FUENTE
  -> DOCUMENTO
  -> PÁGINA / UBICACIÓN
  -> FECHA
  -> EXTRACTO
  -> NIVEL DE CONFIANZA
```

## Fases

### Fase 0 — Foundation
Modelo de dominio, expediente, documentos, timeline, búsqueda y auditoría.

### Fase 1 — Matter Intelligence
Ingesta, OCR, extracción estructurada, resumen verificable y expediente inteligente.

### Fase 2 — Legal Research
Fuentes jurídicas, RAG, citas verificadas y radar normativo.

### Fase 3 — Draft & Review
Generación documental, comparación, validador y contratos.

### Fase 4 — Evidence & Strategy
Evidencia, knowledge graph, teoría del caso y simulación adversarial.

### Fase 5 — Law Firm OS
Portal, calendario, correo, tareas, billing, CRM y automatización.

## Estado

**Proyecto inicializado.**

La especificación detallada vive en `docs/`.

---

**ABOGADA / BlackMamba LEX**

*Legal work becomes computable. Legal judgment remains human.*
