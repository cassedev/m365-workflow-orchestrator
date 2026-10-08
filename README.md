# Gestión Centralizada de Solicitudes: Research, Diseño e Implementaciones (R&D-I)

> **Orquestación ágil de requerimientos con Microsoft 365: Ingesta multicanal (B2B/B2C), validación humana estratégica (Human-in-the-Loop), despliegue operativo en Planner y sincronización recurrente para consumo en Power BI.**

---

## 📌 Contexto y Desafío de Negocio

En entornos operativos con alta demanda técnica y analítica, los requerimientos ingresaban de forma desordenada por múltiples canales (correos sueltos, chats o mensajes directos), lo que provocaba:

* **Falta de visibilidad:** Ausencia de un repositorio centralizado para auditar SLAs y cargas de trabajo.
* **Carga operativa innecesaria:** Reenvío manual de correos y creación manual de tareas en tableros ágiles.
* **Dependencia de IT:** La implementación de una mesa de ayuda tradicional requería largos plazos de desarrollo y costos adicionales.

**Objetivo alcanzado:** Diseñar un circuito autónomo con las herramientas existentes en la organización, reduciendo la intervención manual a un único punto de control y asegurando datos limpios para análisis.

---

## 🔄 Arquitectura del Proceso en 4 Bloques

* **BLOQUE 1: Ingesta & Acuse**  
  MS Forms (B2B / B2C) ➔ Power Automate ➔ Mail Inmediato de Confirmación al Solicitante.

* **BLOQUE 2: Validación Humana (Human-in-the-Loop)**  
  Revisión técnica en Microsoft Lists (Base Maestra) con aprobación y asignación manual única.

* **BLOQUE 3: Despliegue Operativo**  
  Power Automate genera la tarjeta en Microsoft Planner (Bucket inicial: Backlog) y despacha email con ID oficial y link a la App de Consulta.

* **BLOQUE 4: Sincronización Diaria & BI**  
  Flujo programado diario (Daily Sync) que calcula fechas de entrega, transiciona tareas a "En Curso" y mantiene viva la base para el conector de Power BI.

---

## ⚙️ Detalle de las Etapas

### 1. Bloque 1: Ingesta Estandarizada y Acuse Inmediato
* El solicitante carga el requerimiento indicando servicio (Research, Diseño o Implementación), segmento (B2B o B2C) y nivel de prioridad.
* Power Automate procesa los metadatos y envía de forma instantánea un correo de acuse confirmando la recepción y señalando que la solicitud está en evaluación preliminar.

### 2. Bloque 2: Validación Humana (Human-in-the-Loop)
* El requerimiento ingresa en Microsoft Lists en estado Pendiente de Evaluación.
* El equipo técnico valida la viabilidad del pedido directamente en la base maestra. Esta es la única intervención manual del circuito.

### 3. Bloque 3: Despliegue en Planner y Notificación
* Al aprobarse en Lists, el motor de automatización:
  * Crea la tarjeta en el plan de Planner correspondiente en estado inicial de Backlog (sin fecha de vencimiento fijada).
  * Envía un correo electrónico al solicitante con el ID oficial (RDI-2026-XXX) y el acceso directo a la App de Consulta para seguimiento en tiempo real.

### 4. Bloque 4: Sincronización Recurrente y Capa Analítica (BI)
* **Flujo programado diario:** Un proceso desatendido escanea diariamente los tableros de Planner, actualiza los estados de avance (En Curso, Bloqueada, Completada) y estampa las fechas de vencimiento en Lists.
* **Fuente Única de Verdad (SSOT):** La base de Lists permanece depurada y actualizada para conectarse de forma nativa a Power BI, permitiendo la construcción de tableros de SLA, volumen por segmento y tiempos de ciclo sin reprocesamiento manual.

---

## 📈 Impacto Operativo

| Métrica / Dimensión | Proceso Manual Previo | Circuito Automatizado M365 |
| :--- | :---: | :---: |
| **Tiempo de acuse al usuario** | Varias horas / Manual | **Inmediato (< 30 seg)** |
| **Puntos de contacto manual** | 4 a 5 instancias operativas | **1 única validación en Lists** |
| **Asignación y creación de tareas** | 100% manual | **100% automatizada** |
| **Actualización de base y reportes** | Planillas estáticas dispersas | **Sincronización diaria desatendida** |
| **Dependencia de desarrollo IT** | Alta | **0 horas (Solución No-Code / Low-Code)** |