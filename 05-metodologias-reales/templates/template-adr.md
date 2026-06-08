---
id: ADR-000
title: "Título de la Decisión Técnica de Arquitectura"
date: YYYY-MM-DD
status: [Propuesto | Aceptado | Rechazado | Supercedido por ADR-XXX]
control_cambios_id: "ID-TICKET-CORPORATIVO-O-ESTATAL"
impacto_presupuestario: [Ninguno | Requiere Horas Extra | Aprobado por Comité]
---

# 📝 Registro de Decisión de Arquitectura: [Título Corto]  

## 1. Identificación y Control Institucional  

* **Código de Control de Cambios Asociado:** [Inserta el ID del ticket formal, acta de la PMO o resolución administrativa que gatilla este cambio].  
* **Autor / Rol Técnico:** [Nombre del Arquitecto o Líder Técnico responsable].  
* **Nivel de Aprobación Requerido:** [Mesa Técnica / Comite de Cambios / Sponsor de Proyecto].  

---

## 2. Contexto Operativo y Necesidad del Negocio  

Describe la situación actual, el dolor técnico o el requerimiento normativo que obliga a tomar una decisión.  
*Ejemplo: El sistema de firma electrónica actual heredado no es compatible con el nuevo estándar de encriptación exigido por el decreto estatal X, lo que bloquea la tramitación de expedientes.*  

---

## 3. Alternativas Evaluadas y Análisis de Compromisos (Tradeoffs)  

### Alternativa A: [Nombre de la Opción A]  
* **Descripción Técnica:** Cómo se implementaría.  
* **Impacto Operacional:** Riesgos para el sistema super-ultra-crítico durante la ventana de mantenimiento.  
* **Costo / Esfuerzo:** Estimación en horas de ingeniería o recursos de infraestructura.  

### Alternativa B: [Nombre de la Opción B]  
* **Descripción Técnica:** Cómo se implementaría.  
* **Impacto Operacional:** Riesgos o limitaciones que introduce.  
* **Costo / Esfuerzo:** Estimación de recursos.  

---

## 4. Decisión Seleccionada y Justificación de Impacto

Detalla cuál alternativa se eligió y por qué. Esta sección es tu defensa ante el auditor; debe justificar cómo la opción elegida minimiza el riesgo presupuestario y resguarda la continuidad del servicio público o corporativo.  

* **Opción Elegida:** Alternativa [A/B].  
* **Argumento Central:** [Ejemplo: Se selecciona la Alternativa B porque, aunque requiere un 10% más de desarrollo inicial, no exige detener la base de datos central, manteniendo la disponibilidad operativa 24/7 exigida por el contrato].  

---

## 5. Consecuencias y Deuda Técnica Asumida

Todo cambio real tiene un costo técnico colateral. Documenta explícitamente qué compromisos se asumen para cumplir con los plazos del negocio:  
* **En el corto plazo:** [Ejemplo: Aumento temporal de la latencia en el endpoint X mientras se completa la ingesta progresiva].  
* **En el largo plazo:** [Ejemplo: Necesidad de depreciar el módulo Y en la próxima ventana de mantenimiento mayor].  

---

## 💡 Nota de Trinchera  

Cuando el comité de control de cambios o un jefe de finanzas revise esta decisión, no va a juzgar si usaste el patrón de diseño más elegante del año. Va a buscar el código del ticket, el impacto en las lucas y la seguridad de que el sistema no se va a caer. Al llenar este ADR, asegúrate de que la sección de consecuencias sea transparente. Si asumes deuda técnica para cumplir con una fecha legal de la institución, déjalo firmado aquí. Este documento es tu bitácora de navegación y tu blindaje administrativo: si el software muestra comportamientos esperados pero degradados debido al cambio, este ADR demuestra que la gerencia aceptó ese riesgo técnico a cambio de cumplir con el objetivo del negocio.  
