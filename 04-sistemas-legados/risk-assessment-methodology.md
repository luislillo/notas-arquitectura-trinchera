---
title: "Metodología de Evaluación de Riesgos: Cuantificando la Obsolescencia bajo el Estándar IEC 62402"  
date: 2026-06-08  
category: "Sistemas Legados"  
Tags: [legacy, risks, IEC62402, obsolescence, compliance, governance]  
---

# Metodología de Evaluación de Riesgos en Sistemas Legados (IEC 62402)  

En la gobernanza de infraestructuras complejas, proponer la intervención o el reemplazo de un sistema heredado basándose únicamente en argumentos estéticos es inviable. Para que la alta gerencia y los comités de control de cambios validen una estrategia de contención, el equipo de ingeniería debe traducir el desgaste técnico a métricas cuantitativas de riesgo institucional.  

Este documento detalla la metodología estándar de trinchera basada en la norma internacional **IEC 62402 (Gestión de la Obsolescencia)**, para evaluar el riesgo técnico real en motores financieros, pasarelas de mensajería y componentes fiscales de caja negra.  

---

## 🗺️ Índice de Navegación Rápida  

- [1. El Concepto de Obsolescencia según IEC 62402](#1-el-concepto-de-obsolescencia-según-iec-62402)  
- [2. Matriz Cuantitativa de Riesgo (Probabilidad vs. Criticidad)](#2-matriz-cuantitativa-de-riesgo-probabilidad-vs-criticidad)  
- [3. Factores de Evaluación Técnica de Trinchera](#3-factores-de-evaluación-técnica-de-trinchera)  
- [4. Estructura del Reporte para el Comité de Cambios](#4-estructura-del-reporte-para-el-comité-de-cambios)  
- [5. 💡 Nota de Trinchera](#-nota-de-trinchera)  

---

## 1. El Concepto de Obsolescencia según IEC 62402  

La norma dictamina que un software se vuelve obsoleto no por su estética, sino cuando deja de ser mantenible debido a tres vectores de desgaste institucional:  
*   **Obsolescencia Tecnológica:** El software depende de sistemas operativos descontinuados, librerías sin soporte o referencias físicas rígidas que impiden su portabilidad.  
*   **Obsolescencia de Habilidades (Factor Humano):** La pérdida de conocimiento técnico en el mercado para mantener la lógica interna (el riesgo del "Héroe Único").  
*   **Obsolescencia Regulatoria / Compliance:** La incapacidad del componente para cumplir con nuevas normativas de ciberseguridad, encriptación o leyes fiscales (como DORA o NIS 2).  

---

## 2. Matriz Cuantitativa de Riesgo (Probabilidad vs. Criticidad)  

El cálculo del puntaje de riesgo score se rige por el cruce directo de dos variables en una matriz de $5 \times 5$, alineada con el apetito de riesgo de la organización:  

$$\text{Puntaje de Riesgo} = \text{Probabilidad de Inoperabilidad} \times \text{Criticidad para el Negocio}$$  

### A. Escala de Probabilidad de Inoperabilidad (1 a 5)  
1. **Muy Baja:** Sistema inerte pero documentado; el soporte sigue vigente.  
2. **Baja:** Existen dependencias tecnológicas antiguas pero estables bajo control periférico.  
3. **Moderada:** Frecuencia de incidentes (bugs) mensual al alza; no existen suites de prueba automatizadas.  
4. **Alta:** Tecnología descatalogada por el proveedor; el conocimiento técnico interno es crítico y no documentado.  
5. **Inminente:** El componente presenta fallas en caliente ante variaciones mínimas de carga o requerimientos fiscales.  

### B. Escala de Criticidad para el Negocio (1 a 5)  
1. **Insignificante:** El fallo afecta únicamente a flujos cosméticos internos sin impacto financiero.  
2. **Menor:** Degradación temporal del servicio de baja envergadura con recuperación manual inmediata.  
3. **Moderada:** Afecta a un canal operativo secundario; incrementa temporalmente el tiempo de soporte invertido.  
4. **Mayor:** Detención del flujo de caja parcial, pérdida de transacciones por segundo o retraso de hitos institucionales de la PMO.  
5. **Catastrófica:** Sumarios estatales, sanciones fiscales directas o colapso absoluto de la continuidad operativa de la empresa.  

---

## 3. Factores de Evaluación Técnica de Trinchera  

Para que el dato ingresado en la matriz sea fidedigno ante una auditoría (ISO 9001), se analizan tres factores operacionales medibles en los repositorios institucionales:  

*   **Tasa de Incidentes Activos:** Cantidad de tickets de errores registrados en producción imputados directamente al comportamiento opaco de la caja negra legada.  
*   **Métrica de Velocidad y Despliegue:** El tiempo promedio de horas de ingeniería invertidas para empaquetar, validar y desplegar un cambio menor debido a la fragilidad del entorno heredado.  
*   **Nivel de Aislamiento por Contratos:** Si el sistema viejo exige conectarse directamente a la base de datos central sin una interfaz o frontera de red serializada, el nivel de criticidad aumenta automáticamente por riesgo de regresiones en cadena.  

---

## 4. Estructura del Reporte para el Comité de Cambios  

Al presentar la necesidad de mitigar un sistema super-ultra-crítico, el informe técnico oficial que acompaña al ticket de control de cambios institucional debe estructurarse en una sola página:  

1.  **Código del Ticket Asociado:** [ID formal de la PMO o del sistema de control institucional].  
2.  **Identificación del Activo Invisible:** [Ej: Motor Transaccional de Conciliación de Saldos Pasivos].  
3.  **Evaluación bajo IEC 62402:** Puntaje de Riesgo Calculado (Probabilidad $\times$ Criticidad).  
4.  **Justificación de Mitigación Operativa:** [Ej: El software utiliza firmas criptográficas obsoletas. Mantener el componente sin aislamiento técnico mediante un Envoltorio Greenfield expone a la institución a un rechazo del validador fiscal estatal, deteniendo la facturación automática].  

---

## 💡 Nota de Trinchera  

Esa maldita norma IEC 62402 asusta a primera vista por su lenguaje técnico formal, pero en la realidad es tu mejor aliada política. A los directores y comités de control de cambios no les importan tus preferencias por tecnologías modernas; les importan las contingencias operativas y la continuidad del negocio. Cuando cruzas la probabilidad de inoperabilidad con la criticidad real en una matriz estandarizada, dejas de hablar de "código feo" y empiezas a hablar de mitigación de pérdidas financieras y de resguardo legal. Entrega el reporte formal amarrado a su código de documento y al número del ticket institucional. Al demostrar que el equipo técnico utiliza la disciplina y los estándares internacionales para diagnosticar el software heredado, el negocio te entregará la viabilidad y el presupuesto para encapsular la caja negra y programar la nueva estructura limpia con el rigor que corresponde.  
