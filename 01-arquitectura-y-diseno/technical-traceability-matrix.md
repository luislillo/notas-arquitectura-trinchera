---
title: "Matriz Maestra de Trazabilidad Técnica: Mapeando la Arquitectura con la Gobernanza"  
date: 2026-06-07  
category: "Arquitectura y Diseño"  
tags: [architecture, cmmi, scrum, pmbok, clean-architecture, traceability]  
---

# Matriz Maestra de Trazabilidad Técnica (Gestión vs. Código)  

Este documento es una superestructura de cumplimiento cruzado basada en estándares de la industria (IEEE para documentación, marcos oficiales de CMMI, la Scrum Guide y principios de diseño de Robert C. Martin). Su propósito es servir como inventario de control para mapear de forma exacta dónde vive la evidencia de gestión dentro de una arquitectura de software moderna (Clean Architecture o Monolito Estructurado).  

Usa esta matriz como lista de chequeo para tu proceso de limpieza: lo que no encuentres en tus carpetas técnicas o de documentación es un "hueco" de información y un riesgo de auditoría.  

---

## 📊 Matriz Maestra de Artefactos del SDLC  

*Tipos de Archivo:* **(O)** Obligatorio/Core, **(S)** Soporte/Referencia, **(E)** Evidencia/Auditoría.  

| Dimensión / Etapa | Artefacto Ágil (Scrum/Kanban) | Requerimiento CMMI / Tradicional | Ubicación en el Código (Clean / Mono) | Tipo | Propósito del Enlace (Sincronía) |  
| :--- | :--- | :--- | :--- | :---: | :--- |  
| **1. Identidad** | Vision Box / Goal | Acta de Constitución (PID) | `README.md` / `root/` | **O** | Define por qué existe el proyecto y sus límites macro. |  
| **2. Requisitos** | Product Backlog / User Stories | Matriz de Trazabilidad (RTM) / Especificación (RS) | `domain/entities/` o `models/` | **O** | El "Qué": Reglas de negocio duras que no cambian. |  
| **3. Criterios** | Criterios de Aceptación | Especificación Funcional | `tests/features/` (Gherkin/.feature) | **E** | Reglas de validación automáticas y ejecutables. |  
| **4. Arquitectura** | Story Maps / Wireframes | Diseño de Alto Nivel (HLD) / ADRs | `docs/architecture/` (Markdown) | **S** | El "Cómo": Decisiones estructurales justificadas. |  
| **5. Procesos** | Flujos de Tareas | Diseño Detallado (LLD) / Secuencias | `use_cases/` o `services/` | **O** | Orquestación del flujo del negocio en el código. |  
| **6. Interfaz** | Estándar UI / Prototipos | Especificación de Interfaz | `adapters/ui/` o `views/` | **S** | El "Dónde": Capa de presentación y vistas externas. |  
| **7. Integración** | Contratos de API | Control de Interfaces Externas | `adapters/gateways/` o `api/` (Swagger) | **O** | El "Con quién": Integraciones con servicios de terceros. |  
| **8. Configuración** | DoD (Definición de Done) | Plan de Gestión de Configuración (CMP) | `infra/config/` o `config/` | **O** | Variables de entorno, secretos y políticas de ramas Git. |  
| **9. Persistencia** | Esquema del Almacén | Diccionario de Datos / Modelo ER | `infra/persistence/` o `db/migrations/` | **O** | Estructura, migración y forma de guardar los datos. |  
| **10. Calidad / QA** | Sprint Demo Notes | Plan de Verificación (VER) | `tests/unit/` o `tests/integration/` | **E** | Cobertura de código y evidencia automatizada de QA. |  
| **11. Despliegue** | Incremento de Producto | Plan de Instalación (PI) / Acta | `docker-compose.yml` / `.github/workflows/` | **O** | Infraestructura como código. Cómo llega a producción. |  
| **12. Trazabilidad** | Release Notes | Historial de Cambios | `CHANGELOG.md` | **E** | Registro cronológico inalterable de versiones lanzadas. |  
| **13. Soporte** | Retrospective Actions | Reporte de Incidentes / Deuda Técnica | `monitoring/` o `alerts.config` | **S** | Salud del sistema y alertas operativas en tiempo real. |  
| **14. Seguridad** | Políticas de Acceso | Análisis de Riesgos de Seguridad | `infra/auth/` o `middleware/` | **E** | Protección de datos, cifrado y control de accesos. |  

---

## 🛠️ Cómo usar esta matriz para tu "Limpieza"

1. **Mapeo de Presencia:** Revisa tus carpetas y marca con una "X" los componentes de la matriz que ya tienes nombrados y ubicados de forma estandarizada.  
2. **Identificación de Huérfanos:** Detecta archivos sueltos en las carpetas de gestión administrativa que no tengan un reflejo directo en tu estructura técnica (o viceversa). Si existe un requerimiento pero no hay un caso de uso o una entidad en el código, el requerimiento está huérfano.  
3. **Normalización de Nombres:** Utiliza la matriz para estandarizar nomenclaturas. Por ejemplo, define que todos los contratos y adaptadores de la fila 7 (Integración) deban seguir estrictamente el prefijo de archivo `INT-` o la interfaz `IGateway`.  
4. **Aislamiento de Riesgos:** Si un módulo reutilizable del core del negocio no cuenta con su respectiva fila de "Calidad" (pruebas unitarias) o "Arquitectura" (su archivo de decisión de diseño), márcalo inmediatamente como riesgo técnico crítico.  

---

## 💡 Nota de Trinchera  

Esta tabla es tu santo grial para desarmar auditores tradicionales. Cuando llegue un inspector de la ISO 9001 o un evaluador de CMMI exigiendo ver el "Plan de Gestión de Configuración" o el "Reporte de Diseño Detallado", no les entregues una carpeta llena de archivos Word desactualizados que redactaste corriendo la noche anterior. Muéstrales esta matriz y diles: "¿El Plan de Configuración? Está en la configuración de protección de ramas en Git y en las variables de entorno de la carpeta `/infra/config/`. ¿El Diseño Detallado? Está mapeado de forma auto-documentada en la capa de interfaces de la Clean Architecture. ¿La evidencia de verificación de calidad? Mire el último log de ejecución del pipeline de CI/CD que corre las pruebas en `/tests/`". Eleva el nivel del juego: demuestra que en el desarrollo de software moderno, el código bien estructurado y la infraestructura automatizada son la única documentación real e inalterable.  
