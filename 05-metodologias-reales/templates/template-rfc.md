---
id: RFC-000
title: "Título de la Propuesta Técnica de Cambio Estructural"
date: YYYY-MM-DD
author: "Nombre del Proponente y Rol"
status: [Borrador | En Revisión | Aprobado | Rechazado]
ticket_origen_id: "ID-TICKET-O-SOLICITUD-INSTITUCIONAL"
---

# 📋 Solicitud de Comentarios (RFC): [Título de la Propuesta]  

## 1. Resumen Ejecutivo (Para Roles No Técnicos)  

* **Objetivo de la Propuesta:** [Explica en un párrafo simple qué cambio se propone y qué beneficio directo trae a la operación o al cumplimiento normativo].  
* **Impacto Organizacional:** [Indica brevemente si este cambio altera la forma en que interactúan otros departamentos, proveedores o usuarios institucionales].  

---

## 2. Motivación y Justificación de Riesgos  

Detalla la urgencia técnica u operativa que gatilla esta propuesta. Si esta RFC nace de una solicitud formal de la institución o de un cambio de ley del estado, vincula aquí el **Ticket de Origen ID** indicado en los metadatos.  

* **El Problema Actual:** [Describe la ineficiencia o el riesgo de falla del sistema super-ultra-crítico si se mantiene el estado actual].  
* **Riesgo de Inacción:** [Qué pasa a nivel presupuestario, legal o de continuidad de servicio si la gerencia decide rechazar esta propuesta y no hacer nada].  

---

## 3. Propuesta Técnica Detallada (Estructura Lógica)  

Describe la solución de ingeniería propuesta. Recuerda mantener el nivel de abstracción global necesario para que sea entendible por los comités de revisión técnica.  

### A. Cambios en la Frontera del Sistema  
* [Explica si se alteran las APIs, si se modifican los contratos de datos o si cambia el flujo de red hacia el exterior].  

### B. Módulos y Componentes Afectados  
* [Lista qué subsistemas internos o componentes de la Clean Architecture / Onion serán intervenidos de forma directa].  

### C. Estrategia de Mitigación durante la Implementación  
* [Cómo se planea desarrollar e inyectar este cambio paso a paso para asegurar que el sistema actual no sufra caídas en producción].  

---

## 4. Matriz de Impacto y Restricciones Corporativas  

| Dimensión de Control | Impacto Estimado | Evidencia / Mecanismo de Control |  
| :--- | :--- | :--- |  
| **Continuidad del Servicio** | [Ej: Cero corte / Despliegue en caliente] | Monitoreo de réplicas pasivas de base de datos. |  
| **Esfuerzo Estimado** | [Ej: 80 horas de ingeniería totales] | Planificación de tareas en el tablero corporativo. |  
| **Seguridad y Confidencialidad**| [Ej: Cumple estándar de cifrado X] | Validación con el módulo seguro del Kernel compartido. |  
| **Gobernanza Financiera** | [Ej: Requiere aprobación del Comité] | Justificación adjunta en el ticket de control de cambios. |  

---

## 5. Tabla de Revisiones y Firmas de Aceptación Técnica  
*Este es el registro formal de que el equipo revisó la propuesta en frío antes de elevarla a la gerencia.*  

| Fecha | Nombre del Revisor | Rol / Departamento | Estado de Opinión [Aprobado / Observado] |  
| :--- | :--- | :--- | :--- |  
| | | | |  
| | | | |  

---

## 💡 Nota de Trinchera  

Una RFC es tu herramienta de presión política preferida. Cuando sabes que un módulo va a reventar por obsolescencia o falta de memoria, no te quedes quejándote en las reuniones. Redacta este documento. Detalla con rigor técnico el "Riesgo de Inacción", calcula el impacto y haz que tus pares firmen la tabla de la sección 5. Cuando le entregues este archivo de tres páginas al PM o al gerente con copia al ticket institucional, la pelota queda en su cancha. Si ellos deciden rechazar el cambio o cajonear el documento para ahorrarse el presupuesto, tú ya tienes tu blindaje firmado: si el sistema falla en el futuro por esa misma razón, tu RFC demostrará ante cualquier auditoría que el equipo técnico alertó del riesgo con el método ingenieril correcto y en el formato oficial correspondiente.  
