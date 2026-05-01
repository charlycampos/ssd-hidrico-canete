# Manual de Usuario - SSD Hídrico Cuenca Cañete

## 1. Información General del Proyecto
**Título:** Sistema de Soporte a Decisiones para la Gestión Inteligente de Micro-Cuencas — Cuenca Cañete, Perú.
**Investigadores:** Mg. Charly H. Campos Guerra y Mg. Eber A. Quispe Paco (UNAC 2026).
**Objetivo Principal:** Implementar un Sistema de Soporte a Decisiones (SSD) basado en Ciencia de Datos para calcular y demostrar la distribución equitativa de agua en zonas rurales de altura, mitigando la exclusión de comunidades no formalizadas.

---

## 2. Fuentes de Datos Integradas
El sistema procesa y fusiona tres fuentes de datos críticas:
1. **SENAMHI (PISCO HyM GR2M v1.1):** 471 meses de datos históricos de caudales (1981-2020) en 39 subcuencas.
2. **ANA (Autoridad Nacional del Agua):** Datos reales observados recientes (2023-2026) en la cuenca Cañete-Fortaleza.
3. **MINAGRI (Catastro AMCRD 2020):** Base de datos de infraestructura agrícola y estatus de formalización de las comisiones de regantes.

---

## 3. Motor de Ciencia de Datos (El Algoritmo SSD)
En lugar de repartir el agua de forma tradicional (proporcional al tamaño del canal), el sistema usa un enfoque avanzado:

*   **Índice de Vulnerabilidad Hídrica (IVH):** Un indicador calculado matemáticamente que castiga (aumenta la vulnerabilidad) a las comunidades que **no tienen derechos de agua formalizados** y a aquellas con **menor presupuesto histórico por kilómetro de canal**.
*   **K-Means Clustering (Machine Learning):** Agrupa automáticamente a todas las comunidades en 3 niveles de prioridad (Alta, Media, Baja vulnerabilidad).
*   **Asignación Híbrida:** Multiplica el tamaño físico de la demanda (km) por el factor de vulnerabilidad. Así, las comunidades en el clúster más vulnerable reciben una inyección proporcional mayor de agua para asegurar su supervivencia agrícola.

---

## 4. Estructura de la Aplicación

### Panel Lateral (Controles del Usuario)
*   **Año Histórico:** Permite explorar el comportamiento del río en el pasado.
*   **Caudal Ecológico (%):** Define cuánta agua del río debe reservarse obligatoriamente para la naturaleza antes de repartir a los agricultores.
*   **Criterio de Distribución:** Te permite alternar entre el algoritmo de Ciencia de Datos (IVH + K-Means) o visiones tradicionales (solo por Km, Igualitaria, etc.).
*   **Escenarios Climáticos:** Permite simular estrés hídrico aplicando factores de reducción (ej. Sequía severa -50%, Cambio Climático RCP 8.5) o aumento (Año húmedo) al caudal actual.

### Pestaña 1: 💧 Distribución por Zona
Muestra el impacto real del SSD en la equidad social.
*   **KPIs:** Muestra el Índice de Gini hídrico. Un Gini menor indica mayor justicia en el reparto.
*   **Diagrama de Sankey (Antes vs Después):** Un mapa de flujos interactivo. En la vista "ANTES", visualiza en rojo/naranja a las comunidades excluidas por falta de papeles. En la vista "DESPUÉS", muestra cómo el SSD les asigna agua, integrándolas al sistema.
*   **Gráfico Comparativo de Barras:** Muestra exactamente la diferencia en metros cúbicos (`m³/s`) que recibe cada comunidad con y sin el sistema.

### Pestaña 2: 🤖 Predicción ML
Proyecta el futuro hídrico para anticiparse a la crisis.
*   **Modelo Random Forest:** Entrenado con 40 años de historia, evalúa variables como la estacionalidad (mes) y la inercia del río (lag) para predecir los próximos 6 meses.
*   **Gráfico de Validación:** Compara lo que el modelo predice frente a las mediciones reales de la ANA.
*   **Mapa de Calor (Heatmap):** Una matriz térmica que advierte qué comunidades sufrirán mayores recortes en los meses futuros más secos.
*   **Simulador de Flujo Futuro:** Un selector que permite elegir un mes del futuro (ej. Octubre 2026). Inmediatamente, genera una red Sankey que muestra cómo el algoritmo K-Means + IVH recomienda repartir esa agua proyectada.

### Pestaña 3: 🎯 El Problema
Contextualiza por qué se construyó la herramienta.
*   Cuantifica el problema institucional mostrando cuántos kilómetros de canales (y comunidades) operan al margen de la ley por la burocracia, demostrando que son el grupo más vulnerable ante una sequía.

### Pestaña 4: 📋 Metodología
Documentación técnica integrada en la app. Resumen de hiperparámetros del modelo (Random Forest, 100 árboles), métricas de error (RMSE, R²), algoritmo matemático de equidad y bases legales (Ley de Recursos Hídricos N° 29338).
