---
title: "Estrategia de Desacoplamiento: Cómo Desarmar un Monolito en Producción sin Detener el Negocio"  
date: 2026-06-08  
category: "Arquitectura y Diseño"  
tags: [monolith, refactoring, decoupling, patterns, adr]  
---

# Estrategia de Desacoplamiento de Monolitos (Refactorización Segura)

El error más común en la arquitectura de software corporativa es intentar migrar un monolito crítico a microservicios mediante un "Big Bang" (reescribir todo desde cero). Esto destruye presupuestos, paraliza las entregas de valor al negocio y genera un riesgo operacional inaceptable para los auditores de la ISO 9001.  

Esta nota documenta la estrategia de trinchera para aislar y extraer componentes acoplados utilizando patrones de diseño seguros, protegiendo la continuidad operativa del sistema.  

---

## 🗺️ Índice de Navegación Rápida  

- [1. El Problema: El Monolito Frankenstein](#1-el-problema-el-monolito-frankenstein)  
- [2. Patrón de Selección: La Higuera Estranguladora (Strangler Fig Pattern)](#2-patrón-de-selección-la-higuera-estranguladora-strangler-fig-pattern)  
- [3. Refactorización a Nivel de Código (Paso a Paso)](#3-refactorización-a-nivel-de-código-paso-a-paso)  
- [4. El Escudo de Gobernanza: Registro Express de la Decisión (ADR)](#4-el-escudo-de-gobernanza-registro-express-de-la-decisión-adr)  
- [5. 💡 Nota de Trinchera](#-nota-de-trinchera)  

---

## 1. El Problema: El Monolito Frankenstein  

Cuando un sistema heredado crece sin control, los límites del dominio desaparecen. El módulo de facturación termina llamando directamente a las tablas de autenticación o inyectando dependencias cruzadas en la capa de persistencia. Intentar separar esto a la fuerza rompe el flujo de despliegue continuo (CI/CD) y detiene las entregas de la PMO (ISO 21502).  

---

## 2. Patrón de Selección: La Higuera Estranguladora (Strangler Fig Pattern)  

Para cumplir con la resiliencia operativa, la extracción debe ser progresiva e invisible para el usuario final:  

1. **Intercepción:** Se coloca una capa de enrutamiento (API Gateway o un proxy inverso simple) delante del monolito.  
2. **Coexistencia:** Se despliega el nuevo servicio optimizado de forma independiente en una infraestructura inerte.  
3. **Sustitución:** El proxy desvía el tráfico del endpoint antiguo hacia el nuevo servicio de manera gradual (ej. 10% del tráfico primero). El monolito se va "estrangulando" hasta que esa ruta queda obsoleta.  

---

## 3. Refactorización a Nivel de Código (Paso a Paso)

Antes de mover el código a otro servicio físico, debes desacoplarlo lógicamente dentro de la misma solución mediante interfaces inalterables (Principio de Inversión de Dependencias):  

```csharp
// PASO 1: Declarar el contrato duro para aislar el dominio conflictivo
public interface IFacturacionLegacyGateway {
    Task<bool> ProcesarPagoPasivo(Guid clienteId, decimal monto);
}

// PASO 2: Implementar el adaptador que encapsula la cochambre del monolito
public class FacturacionAdapter : IFacturacionLegacyGateway {
    private readonly DbContextLegacy _context;

    public FacturacionAdapter(DbContextLegacy context) {
        _context = context;
    }

    public async Task<bool> ProcesarPagoPasivo(Guid clienteId, decimal monto) {
        // Aquí vive el acoplamiento temporal mientras se extrae el servicio
        var cliente = await _context.Clientes.FindAsync(clienteId);
        return cliente != null;
    }
}
```

Al programar apuntando a `IFacturacionLegacyGateway`, el resto del sistema ya no sabe (ni le importa) si la facturación ocurre en la base de datos vieja o en un microservicio externo en la nube. El desacoplamiento está blindado.  

---

## 4. El Escudo de Gobernanza: Registro Express de la Decisión (ADR)  

Para que el auditor de procesos o la gerencia apruebe esta refactorización sin ponernos trabas burocráticas, registramos este cambio técnico bajo un formato ADR simplificado (Michael Nygard) en menos de 100 líneas:  

* **Título:** ADR-004: Extracción del Módulo de Facturación mediante Patrón Estrangulador.  
* **Estado:** Aceptado.  
* **Contexto:** El tiempo de respuesta del monolito aumentó un 40% debido al acoplamiento de facturación en la base de datos relacional principal.  
* **Decisión:** Implementaremos el patrón Strangler Fig para desviar de forma controlada el tráfico de pagos a una API independiente en .NET 8.  
* **Consecuencias:** Se asume una deuda técnica temporal en la capa de enrutamiento, pero se elimina el riesgo de caída global del monolito y se reduce el tiempo de compilación local en un 15%.  

---

## 💡 Nota de Trinchera  

No intentes venderle una refactorización a la alta gerencia usando jerga de código limpia o quejándote de que el software da asco. A ellos no les importa SOLID ni los patrones de diseño. Véndelo como gestión de riesgos y continuidad de negocio (ISO 9001). Diles: "Si no aislamos este módulo mediante una interfaz, un error en facturación botará el login de los clientes y perderemos un 20% de transacciones diarias". Muéstrales el ADR de una página en el repositorio Git, demuestra que el cambio pasará por un pipeline seguro de pruebas y tendrás la autonomía política necesaria para limpiar el Frankenstein técnico sin que nadie te moleste.  
