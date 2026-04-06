# LTI - Ecosistema de Reclutamiento Inteligente 🚀

**LTI** es un sistema de seguimiento de candidatos (ATS) de nueva generación diseñado para eliminar el "agujero negro" de las aplicaciones laborales. A diferencia de los sistemas tradicionales, LTI es una plataforma bidireccional que prioriza la experiencia del candidato y la agilidad operativa de las startups.

---

## 🌟 Valor Añadido y Ventajas Competitivas

* **Transparencia Radical:** El candidato tiene el control total de su proceso a través de un portal de autoservicio con actualizaciones en tiempo real.
* **Fricción Cero:** Integración profunda con **WhatsApp** para comunicaciones críticas, eliminando la dependencia de correos electrónicos.
* **Ecosistema Conectado:** Integración nativa en el flujo de trabajo de la startup (**Slack, Teams, Google/Outlook**).

---

## 🛠 Funcionalidades Principales

1.  **Candidate Experience Portal (CEP):** Panel personalizado para aspirantes con visualización de etapas y perfiles de entrevistadores.
2.  **WhatsApp Sync & Automation:** Bot para envío de resúmenes, confirmación de asistencia y reprogramación automática.
3.  **Collaborative Pipeline (Slack/Teams Native):** Notificaciones inteligentes con botones de acción directamente en canales de equipo.
4.  **Smart Sourcing & Parsing:** Motor de IA para extracción de datos de CVs y pre-clasificación inteligente.
5.  **Unified Calendar & Interview Suite:** Sincronización de agendas y generación automática de salas virtuales.

---

## 📈 Modelo de Negocio (Lean Canvas)

```mermaid
block-beta
  columns 5

  block:problem:1
    p1["**1. PROBLEMA**"]
    p2["- Abandono candidatos\n- Procesos lentos\n- Dispersión (Email/Slack)"]
  end

  block:sol_met:1
    block:sol:1
      s1["**4. SOLUCIÓN**"]
      s2["- Portal tiempo real\n- WhatsApp Sync\n- Integración Slack"]
    end
    block:met:1
      m1["**8. MÉTRICAS**"]
      m2["- Candidate NPS\n- Time-to-hire"]
    end
  end

  block:uvp_block:1
    u1["**3. PROPUESTA VALOR**"]
    u2["**'El ATS que aman y usan'**\n\nReclutamiento transparente\ny ágil en un solo lugar."]
  end

  block:adv_cha:1
    block:adv:1
      a1["**9. VENTAJA**"]
      a2["WhatsApp + Portal\n(First-mover)"]
    end
    block:cha:1
      c1["**5. CANALES**"]
      c2["- Slack Directory\n- LinkedIn Ads"]
    end
  end

  block:segments:1
    seg1["**2. SEGMENTOS**"]
    seg2["**Startups/Scaleups**\n(20-500 emp)\n\n*Early Adopters:* Founders\ny HR Leads Tech."]
  end

  block:costs:2
    cost1["**7. ESTRUCTURA DE COSTOS**"]
    cost2["Cloud/Devs | Marketing | APIs WhatsApp"]
  end

  block:revenue:3
    rev1["**6. FLUJOS DE INGRESO**"]
    rev2["Suscripción SaaS (vacante/user) | Add-ons Integraciones"]
  end

  style p1 fill:#f9f,stroke:#333
  style s1 fill:#bbf,stroke:#333
  style m1 fill:#bbf,stroke:#333
  style u1 fill:#dfd,stroke:#333
  style seg1 fill:#fdb,stroke:#333
  style cost1 fill:#eee,stroke:#333
  style rev1 fill:#eee,stroke:#333
```

---

## 📋 Casos de Uso Principales

### Definición de Casos de Uso
* **UC-01: Gestión y Publicación de Vacantes:** El reclutador crea descripciones de puesto, define etapas del pipeline y publica en portales automáticamente.
* **UC-02: Seguimiento Transparente de Candidatura:** El candidato consulta su estado en tiempo real vía Portal y recibe notificaciones automáticas por WhatsApp.
* **UC-03: Evaluación Colaborativa e Integrada:** El equipo evalúa perfiles y deja feedback directamente desde Slack/Teams, sincronizando el estado en el ATS.

### Diagrama de Casos de Uso (Mermaid)

```mermaid
graph LR
    %% Actores
    Recruiter[Reclutador]
    Candidate[Candidato]
    Manager[Hiring Manager]
    
    subgraph "Sistema LTI ATS"
        UC1((UC-01: Gestión Vacantes))
        UC2((UC-02: Seguimiento Transparente))
        UC3((UC-03: Evaluación Colaborativa))
        UC4((Sincronizar Slack/Teams))
        UC5((Enviar Alerta WhatsApp))
    end

    %% Sistemas Externos
    WhatsApp[[WhatsApp API]]
    Slack[[Slack API]]

    Recruiter --- UC1
    Recruiter --- UC3
    Candidate --- UC2
    Manager --- UC3

    UC2 -.->|include| UC5
    UC3 -.->|include| UC4
    
    UC5 --- WhatsApp
    UC4 --- Slack

    style UC1 fill:#fff,stroke:#333,stroke-width:2px
    style UC2 fill:#fff,stroke:#333,stroke-width:2px
    style UC3 fill:#fff,stroke:#333,stroke-width:2px
    style UC4 fill:#fff,stroke:#333,stroke-width:2px
    style UC5 fill:#fff,stroke:#333,stroke-width:2px
```

---

## 💾 Modelo de Datos

### Entidades Principales y Atributos
1.  **Candidato (Candidate):** Perfil del talento. Incluye `id`, `email`, `telefono_whatsapp`, `token_portal` (acceso sin password) y `cv_url`.
2.  **Vacante (Job_Opening):** Requisitos del puesto. Incluye `id`, `titulo`, `estado` (Abierta, Cerrada) e `id_hiring_manager`.
3.  **Etapa_Pipeline (Pipeline_Stage):** Pasos del proceso (ej. "Entrevista Técnica"). Incluye `id`, `nombre_etapa` y `orden`.
4.  **Aplicación (Application):** Relación candidato-vacante. Registra `id_etapa_actual`, `fecha_postulacion` y `estado_proceso`.
5.  **Evaluación (Assessment):** Feedback del equipo. Incluye `calificacion`, `comentarios` y `slack_thread_id`.
6.  **Notificación (Notification):** Log de auditoría. Registra `canal` (WhatsApp/Slack), `contenido` y `estado_envio`.

### Diagrama Entidad-Relación (ERD)

```mermaid
erDiagram
    CANDIDATO ||--o{ APLICACION : "se postula"
    VACANTE ||--o{ APLICACION : "recibe"
    VACANTE ||--o{ ETAPA_PIPELINE : "define flujo"
    APLICACION ||--o{ EVALUACION : "genera"
    APLICACION ||--o{ NOTIFICACION : "registra comunicacion"
    APLICACION }|--|| ETAPA_PIPELINE : "esta en"

    CANDIDATO {
        uuid id
        string nombre
        string telefono_whatsapp
        string token_portal
    }
    VACANTE {
        uuid id
        string titulo
        string estado
    }
    APLICACION {
        uuid id
        string estado_proceso
        datetime fecha_creacion
    }
```

---

## 🏗 Arquitectura del Sistema (EDA)

LTI utiliza una **Arquitectura Orientada a Eventos (EDA)** para garantizar escalabilidad y desacoplamiento entre la IA, las notificaciones y el núcleo del sistema.

### Flujo de Datos (Arquitectura Detallada)

```mermaid
graph TB
    subgraph "External_Actors"
        C[Candidato]
        WA_API[WhatsApp API]
        SL_API[Slack API]
        AI_API[OpenAI API]
    end

    subgraph "LTI_Infrastructure"
        AGW[API Gateway]
        WH_GW[Webhook Ingestor]
        Bus((Event Bus))
        
        subgraph "Services"
            AppSvc[Core ATS Service]
            AISvc[AI Worker]
            NotifSvc[Notification Engine]
        end

        DB[(PostgreSQL)]
    end

    WA_API --> WH_GW
    SL_API --> WH_GW
    WH_GW --> Bus
    Bus --> AppSvc
    AppSvc --> DB
    AppSvc --> Bus
    Bus --> AISvc
    AISvc --> AI_API
    Bus --> NotifSvc
    NotifSvc --> WA_API
    NotifSvc --> SL_API

    style Bus fill:#f96,stroke:#333,stroke-width:4px
```

### Diagrama C4 (Contenedores)

```mermaid
C4Context
    title Diagrama de Contenedores LTI ATS
    
    Person(candidate, "Candidato", "Usa Portal y WhatsApp.")
    Person(recruiter, "Equipo RRHH", "Usa Slack y Dashboard.")

    System_Boundary(lti_system, "Sistema LTI ATS") {
        Container(portal, "Portal Candidato", "React", "Visualización de progreso.")
        Container(webhook_gw, "Webhook Gateway", "Go", "Ingesta de eventos masivos.")
        ContainerQueue(event_bus, "Event Bus", "Redis", "Bus de eventos asíncronos.")
        Container(core_svc, "Core ATS", "Python", "Lógica de negocio.")
        Container(ai_worker, "AI Worker", "Python", "Procesamiento de CVs.")
        ContainerDb(db, "Database", "PostgreSQL", "Persistencia centralizada.")
    }

    System_Ext(whatsapp, "WhatsApp API")
    System_Ext(slack, "Slack API")
    System_Ext(ai_api, "OpenAI API")

    Rel(whatsapp, webhook_gw, "Webhooks")
    Rel(webhook_gw, event_bus, "Publish")
    Rel(event_bus, core_svc, "Consume")
    Rel(core_svc, ai_worker, "Análisis IA")
```

---
*LTI ATS - Documentación de Producto y Arquitectura - 2026.*