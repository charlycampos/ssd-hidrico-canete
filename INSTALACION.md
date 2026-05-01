# Guía de Instalación y Ejecución - SSD Hídrico Cuenca Cañete

Este documento detalla los pasos necesarios para configurar el entorno de desarrollo, instalar las dependencias requeridas y ejecutar la aplicación del Sistema de Soporte a Decisiones en tu máquina local.

---

## 1. Requisitos Previos
Asegúrate de tener instalado **Python** en tu sistema (se recomienda la versión 3.9 o superior). Puedes verificarlo abriendo una terminal (Símbolo del sistema o PowerShell) y ejecutando:
```bash
python --version
```

---

## 2. Creación del Entorno Virtual (venv)
Es una buena práctica aislar las dependencias del proyecto utilizando un entorno virtual.

1. Abre una terminal (Símbolo del sistema o PowerShell en Windows).
2. Navega hasta la carpeta del proyecto (donde se encuentra el archivo `app_pisco_canete.py`):
   ```bash
   cd "D:\Usuarios\ccampos\Downloads\informacion PISCO"
   ```
3. Crea el entorno virtual ejecutando el siguiente comando:
   ```bash
   python -m venv venv
   ```
   *Esto creará una carpeta llamada `venv` que contendrá el entorno aislado.*

---

## 3. Activación del Entorno Virtual
Antes de instalar cualquier paquete o correr la aplicación, **siempre** debes activar el entorno virtual.

**En Windows (PowerShell / CMD):**
```bash
.\venv\Scripts\activate
```
*Sabrás que está activado porque verás `(venv)` al inicio de la línea en tu terminal.*

---

## 4. Instalación de Dependencias
Con el entorno virtual activado, debes instalar todas las librerías científicas y de visualización que utiliza el código fuente.

Ejecuta el siguiente comando para instalar todos los paquetes necesarios de una sola vez:
```bash
pip install streamlit pandas numpy plotly geopandas scikit-learn openpyxl scipy joblib
```

**Explicación de las librerías:**
*   `streamlit`: El framework principal para la interfaz web.
*   `pandas` y `numpy`: Manipulación de datos y cálculos matriciales.
*   `plotly`: Gráficos interactivos, diagramas Sankey y mapas de calor.
*   `geopandas`: Procesamiento de datos espaciales (shapefiles).
*   `scikit-learn`: Modelos de Machine Learning (Random Forest, K-Means, MinMaxScaler).
*   `openpyxl`: Necesario para que pandas pueda leer archivos `.xlsx` (bases de ANA y MINAGRI).
*   `scipy` y `joblib`: Estadísticas avanzadas y persistencia de modelos entrenados.

---

## 5. Ejecutar la Aplicación
Una vez finalizada la instalación, inicia el servidor de Streamlit ejecutando el script principal:

```bash
streamlit run app_pisco_canete.py
```

### ¿Qué sucede al ejecutar este comando?
1. Se abrirá automáticamente una nueva pestaña en tu navegador web predeterminado (usualmente en la dirección `http://localhost:8501`).
2. Si no se abre sola, puedes copiar y pegar la URL local que aparecerá en tu terminal.
3. El modelo de *Random Forest* se entrenará automáticamente la primera vez que inicies la app y luego se guardará en memoria para arranques futuros más rápidos.

---

## 6. Cerrar la Aplicación
Cuando termines de trabajar:
1. Ve a la terminal donde está corriendo el servidor y presiona `Ctrl + C` para detenerlo.
2. Para salir del entorno virtual, simplemente ejecuta:
   ```bash
   deactivate
   ```
