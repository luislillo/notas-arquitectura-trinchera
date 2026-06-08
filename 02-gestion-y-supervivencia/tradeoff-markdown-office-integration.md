---
title: "Justificación de Arquitectura: Integración de Docs-as-Code con Plataformas de Colaboración Corporativa"  
date: 2026-06-07  
category: "Gestión y Supervivencia"  
tags: [architecture, documentation, pmbok7, office, tradeoffs]  
---

# Análisis de Compromisos (Tradeoffs) en la Gestión Documental de Ingeniería  

## Declaración del Contexto  

En proyectos de software de gran escala, coexisten dos necesidades críticas respecto a la documentación:  

1. **La Necesidad Técnica:** Mantener el historial de la arquitectura, especificaciones de APIs y ADRs en formatos de texto plano (Markdown) para permitir el control de versiones ramificado, auditorías automáticas vía Git y revisiones por pares en el flujo de desarrollo.  
2. **La Necesidad Funcional/Organizacional:** Garantizar que los interesados del negocio (PMO, gerencia, auditoría interna) tengan acceso a la documentación en plataformas de colaboración estándar (como el ecosistema de Microsoft Office / SharePoint), las cuales soportan flujos de trabajo organizacionales, retención legal y revisiones multi-departamentales.  

El objetivo de este documento es justificar la convivencia de ambos enfoques para un caso de uso corporativo, analizando sus ventajas y limitaciones.  

---

## Análisis Comparativo (Alternativa A vs. Alternativa B)  

### Alternativa A: Docs-as-Code Exclusivo (Markdown en Git)  

* **Cuándo aplica:** Excelente para documentación viva del código, guías de despliegue, esquemas de bases de datos y decisiones técnicas que evolucionan al mismo ritmo que los repositorios de software.  
* **Ventajas:** Trazabilidad exacta por línea de texto, facilidad de ramificación (*branching*) y bajo nivel de fricción para el equipo de desarrollo.  
* **Desventajas:** Curva de aprendizaje alta para roles no técnicos, limitaciones en el formateo visual avanzado requerido para contratos o políticas oficiales, y falta de integración nativa con flujos de aprobación basados en firmas corporativas.  

### Alternativa B: Plataformas Corporativas (Word / SharePoint)  

* **Cuándo aplica:** Es el estándar mandatorio para actas de constitución de proyectos, contratos de proveedores, políticas de seguridad de la información y entregables de hitos que requieren revisiones de la alta dirección.  
* **Ventajas:** Entorno de colaboración visual en tiempo real para múltiples roles no técnicos, gestión avanzada de permisos de acceso organizacionales y cumplimiento nativo con normativas de auditoría empresarial.  
* **Desventajas:** Los archivos binarios o empaquetados (`.docx`) no permiten comparaciones sencillas línea por línea en sistemas de control de versiones y tienden a generar duplicidad de archivos si no se controlan mediante la plataforma nativa.  

---

## Estrategia de Convivencia e Integración  

Para maximizar el valor de ambas herramientas en el ciclo de vida del proyecto, se establece una estrategia de delimitación de fronteras documentales basada en el tipo de artefacto:  

```text
 ┌────────────────────────────────────────────────────────┐
 │ DOCUMENTACIÓN TÉCNICA (Markdown / Repositorio Git)     │
 │ * ADRs, Guías de Arquitectura, Contratos API, Runbooks  │
 └──────────────────────────┬─────────────────────────────┘
                            │ (Sincronización Automatizada / Pandoc)
                            ▼
 ┌────────────────────────────────────────────────────────┐
 │ PORTAL DE CONTROL DE HITOS (SharePoint / Word / Teams) │
 │ * Project Charters, Políticas, Hitos Oficiales         │
 └────────────────────────────────────────────────────────┘
```

1. **Delimitación de Responsabilidades:** La documentación que vive y cambia con el código se mantiene en archivos `.md`. Los documentos de gobernanza administrativa y contratos se gestionan en las plataformas de la organización.
2. **Automatización de la Traducción:** Para los reportes o arquitecturas técnicas que deban ser validados por comités de procesos, se implementan utilidades de conversión (como *Pandoc*) dentro del pipeline de integración continua. Esto traduce el Markdown a plantillas corporativas formateadas de Word de forma automatizada, eliminando el trabajo doble.  

---

## 💡 Nota de Trinchera  

El rol de un arquitecto no es forzar a toda la organización a usar las herramientas de desarrollo, sino construir los puentes para que la información fluya sin fricciones. Las plataformas operativas de colaboración empresarial existen por razones de peso: cumplimiento legal, auditorías financieras y flujos de trabajo multisectoriales que el texto plano simplemente no puede resolver por sí solo. La madurez técnica radica en entender los tradeoffs: usa Git y Markdown para proteger el ritmo de tus ingenieros y la trazabilidad del código; utiliza las herramientas de la suite corporativa para asegurar la comunicación con el negocio. Cuando logras que ambas capas se integren mediante automatización, cumples con la gobernanza sin restarle velocidad a la ingeniería.  
