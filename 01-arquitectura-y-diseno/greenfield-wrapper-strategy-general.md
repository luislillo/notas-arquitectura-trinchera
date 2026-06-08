---
title: "Estrategia de Envoltorio Moderno: Contención de Legados mediante Ingesta Progresiva"  
date: 2026-06-08  
category: "Arquitectura y Diseño"  
tags: [clean-architecture, building-blocks, legacy, containment, integration]  
---

# Estrategia de Envoltorio Moderno (Ingesta Progresiva sin Tocar el Legado)  

Modificar directamente el código fuente de un sistema crítico heredado es una de las mayores fuentes de estrés técnico y riesgo operacional. Cuando el software carece de pruebas unitarias y el equipo original ya no está en la empresa, cualquier cambio en el "núcleo viejo" puede gatillar fallas en cascada imposibles de predecir.  

Esta nota documenta la estrategia alternativa de **Envoltorio Greenfield**: la creación de una superestructura moderna externa que encapsula el sistema antiguo, permitiendo migrar la lógica de negocio paso a paso de forma controlada y segura.  

---

## 🗺️ Índice de Navegación Rápida  
- [1. La Filosofía del Envoltorio: Dejar el Legado en Paz](#1-la-filosofía-del-envoltorio-dejar-el-legado-en-paz)  
- [2. Paso 1: Montar los Bloques de Construcción (Building Blocks) Libres](#2-paso-1-montar-los-bloques-de-construcción-building-blocks-libres)  
- [3. Paso 2: Diseñar la Nueva Estructura (Clean / Onion Architecture)](#3-paso-2-diseñar-la-nueva-estructura-clean--onion-architecture)  
- [4. Paso 3: Ingesta y Acoplamiento Progresivo de Fuentes](#4-paso-3-ingesta-y-acoplamiento-progresivo-de-fuentes)  
- [5. 💡 Nota de Trinchera](#-nota-de-trinchera)  

---

## 1. La Filosofía del Envoltorio: Dejar el Legado en Paz  

En lugar de abrir el proyecto antiguo y empezar a refactorizar sus clases internas, el sistema viejo se trata estrictamente como una caja negra inerte o una base de datos externa. No se toca su código. Se construye un sistema completamente nuevo (*Greenfield*) al lado, cuyo único objetivo inicial es conectarse a las salidas de datos del legado y exponerlas bajo estándares modernos.  

---

## 2. Paso 1: Montar los Bloques de Construcción (Building Blocks) Libres  

No reinventes la rueda en la nueva estructura. Para acelerar el cumplimiento normativo y la estabilidad del nuevo entorno, utiliza componentes de código abierto consolidados para la infraestructura base:  

* **Autenticación y Seguridad:** Levanta un contenedor con un proveedor de identidad libre (como *Keycloak*) o usa los middlewares nativos de la plataforma para validar tokens JWT.  
* **Persistencia y Migraciones:** Implementa herramientas de migración de esquemas como *FluentMigrator* o *Flyway* para controlar los cambios de la nueva base de datos desde el día uno.  
* **Telemetría:** Inyecta *Serilog* o *OpenTelemetry* para asegurar la trazabilidad que exigen las auditorías de calidad (ISO 9001), algo de lo que los sistemas viejos carecen o se crearon a la marcha.  

---

## 3. Paso 2: Diseñar la Nueva Estructura (Clean / Onion Architecture)  

El nuevo proyecto se inicializa bajo los principios de Clean Architecture. Esto asegura que las reglas del negocio queden totalmente aisladas de la infraestructura técnica y del propio sistema viejo:  

* **Core / Domain:** Capa inerte que contiene las entidades puras y las interfaces (contratos) del negocio.
* **Use Cases / Application:** Orquesta los flujos de datos.  
* **Infrastructure / Adapters:** Aquí ocurre la magia. Se crea un adaptador específico cuya única tarea es consumir la API vieja, leer sus archivos de salida o conectarse a una réplica de su base de datos.  

```text
 ┌─────────────────────────────────────────────────────────────┐  
 │ NUEVA CLEAN ARCHITECTURE (Greenfield)                       │  
 │  ┌───────────────────────────────────────────────────────┐  │  
 │  │ Core / Reglas de Negocio Limpias                      │  │  
 │  └──────────────────────────▲────────────────────────────┘  │  
 │                             │ (Inversión de Dependencia)    │  
 │  ┌──────────────────────────┴────────────────────────────┐  │  
 │  │ Adaptador de Infraestructura: HttpClient / SQL Legacy │  │  
 │  └──────────────────────────┬────────────────────────────┘  │  
 └─────────────────────────────┼───────────────────────────────┘  
                               │ (Llamada de solo lectura)  
                               ▼  
 ┌─────────────────────────────────────────────────────────────┐  
 │ SISTEMA LEGADO EN PRODUCCIÓN (No se toca su código)         │  
 └─────────────────────────────────────────────────────────────┘  
```

---

## 4. Paso 3: Ingesta y Acoplamiento Progresivo de Fuentes

Con la estructura armada, el proceso de migración deja de ser estresante y se convierte en una tarea de inyección paso a paso:  

1. **El Legado como Proveedor:** El nuevo sistema expone un endpoint moderno (ej: `/api/v1/clientes`). Por debajo, el adaptador de infraestructura le pide los datos al sistema viejo de la forma en que este pueda entregarlos (un query SQL directo o un parseo de archivo plano).  
2. **Personalización y Enriquecimiento:** Las nuevas reglas de negocio solicitadas por la gerencia se programan exclusivamente en la capa de *Use Cases* del nuevo sistema. El software viejo ni se entera del cambio.  
3. **Ingesta de Lógica:** Cuando un proceso del monolito viejo deba ser reemplazado por completo, simplemente se programa la nueva lógica dentro del core limpio y se corta la llamada del adaptador hacia el sistema heredado. La migración ocurre en caliente, a nivel de contratos, de forma invisible y segura.  

---

## 💡 Nota de Trinchera  

Ir a modificar el código fuente de un monolito legado sin tests es jugar a la ruleta rusa con tu puesto de trabajo. La estrategia del envoltorio es tu mejor línea de defensa política y técnica: mantienes el sistema viejo corriendo intacto en producción (lo que hace feliz al gerente de operaciones porque el riesgo es cero) mientras tú y tu equipo desarrollan software feliz en un entorno moderno con Clean Architecture, contenedores y tecnologías vigentes. No pelees contra el desorden del código heredado; enciérralo en una fachada técnica, consume sus datos de forma pasiva y ve absorbiendo el negocio a tu propio ritmo y bajo tus propias reglas de ingeniería.  
