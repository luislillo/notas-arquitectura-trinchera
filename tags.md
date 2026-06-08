# 🏷️ Guía de Etiquetas (Tags) del Repositorio  

Para garantizar el rigor metodológico y facilitar la navegación o búsquedas globales dentro de este repositorio local, cada nota técnica, manifiesto o guía incluye metadatos específicos en su cabecera YAML. Si estás buscando resolver una exigencia regulatoria o un desafío de ingeniería concreto, puedes utilizar estas palabras clave como índices de filtrado.  

---

## 🗺️ Índice de Navegación Rápida  

- [1. Dimensión Tecnológica y de Entorno (El Stack)](#1-dimensión-tecnológica-y-de-entorno-el-stack)  
- [2. Dimensión de Arquitectura y Estrategia Técnica (El Fondo)](#2-dimensión-de-arquitectura-y-estrategia-técnica-el-fondo)  
- [3. Dimensión de Gobernanza y Gestión del Riesgo Institucional (La Forma)](#3-dimensión-de-gobernanza-y-gestión-del-riesgo-institucional-la-forma)  
- [4. 💡 Nota de Trinchera](#-nota-de-trinchera)  

---

## 1. Dimensión Tecnológica y de Entorno (El Stack)  

Estas etiquetas identifican el ecosistema técnico, los lenguajes de programación o el entorno de ejecución donde se aplica la solución de ingeniería:  

* **`csharp`**: Notas enfocadas en el desarrollo, compilación, refactorización y optimización de código bajo C#.  
* **`cpp`**: Contenido orientado al mantenimiento, análisis e integración de componentes en C++.  
* **`dotnet`**: Notas exclusivas del ecosistema nativo de Microsoft .NET, estructuras de espacio de trabajo y archivos de solución.  
* **`llm` / `prompts`**: Ingeniería de prompts en producción, control probabilístico de tokens, inyecciones de seguridad y esquemas JSON estrictos.  
* **`devops`**: Automatización de la evidencia, configuraciones de infraestructura como código y políticas de integración continua (CI/CD).  

---

## 2. Dimensión de Arquitectura y Estrategia Técnica (El Fondo)  

Etiquetas orientadas a las decisiones de diseño estructural, patrones de software y la resolución de problemas en las capas del sistema:  

* **`architecture`**: Directrices globales de diseño, topologías físicas, fronteras de red y delimitación de contratos de APIs.  
* **`patrones`**: Aplicación de patrones de diseño, inversión de dependencias y refactorización para el aislamiento de componentes.  
* **`monolito`**: Estrategias específicas para mantener, modularizar, empaquetar o desarmar sistemas de gran envergadura.  
* **`clean-architecture`**: Implementación de arquitecturas limpias u Onion para separar las reglas de negocio de la infraestructura técnica.  
* **`legado` / `contencion`**: Mecanismos de contención pasiva por contratos y envoltorios Greenfield para sistemas heredados.  

---

## 3. Dimensión de Gobernanza y Gestión del Riesgo Institucional (La Forma)  

Etiquetas destinadas a la alineación estratégica, el cumplimiento de procesos, la auditoría y la comunicación diplomática ante la alta gerencia:  

* **`pmbok7`**: Notas sobre la transición hacia marcos basados en principios de desempeño, adaptabilidad (Tailoring) y entrega de valor.  
* **`cmmi`**: Gestión, control de la configuración y aseguramiento estructurado mediante modelos de madurez tradicionales.  
* **`iso9001`**: Aplicación del enfoque basado en procesos, matrices de riesgos viva, mejora continua y auditorías de calidad de software.  
* **`compliance`**: Análisis técnico y aterrizaje de normativas internacionales de resiliencia operativa y ciberseguridad (DORA, NIS 2).  
* **`auditoria` / `traceability`**: Herramientas de control diario, matrices de trazabilidad documental cruzada y checklists de verificación.  
* **`gobernanza` / `politica`**: Justificaciones metodológicas, análisis de compromisos (tradeoffs), mapas de roles y estrategias de diplomacia técnica.  
 
---

## 💡 Nota de Trinchera  

El ordenamiento por etiquetas en un repositorio docs-as-code no es un ejercicio cosmético; es la estructura jerárquica que transforma texto plano inerte en una base de conocimiento indexable y auditable. Si descargas este repositorio localmente y utilizas herramientas de indexación en tu editor (como la búsqueda global `Ctrl + Shift + F` en VS Code o las consultas integradas de Obsidian), puedes cruzar etiquetas de forma lógica para resolver problemas complejos en segundos. Buscar la combinación de metadatos `tags: [legado, compliance]` te entregará de inmediato las estrategias operativas para aislar una caja negra financiera bajo la norma de resiliencia DORA; buscar `tags: [cmmi, traceability]` te proveerá el mapa exacto para satisfacer a un auditor de procesos mediante la estructura de tu código. Estructura el dato, mantén la consistencia de las etiquetas en cada nueva nota y haz que la matemática de tu motor de búsqueda trabaje a favor del rigor de tu ingeniería.  
