# 🎓 Predicción de Deserción Estudiantil en Plataformas E-Learning

Este proyecto desarrolla un modelo de aprendizaje supervisado destinado a la identificación temprana de estudiantes en riesgo de abandono escolar dentro de entornos virtuales de aprendizaje. A través del análisis del comportamiento y las interacciones en la plataforma e-learning, el modelo permite a las instituciones académicas intervenir proactivamente para mejorar la retención de los alumnos.

---

## 🎯 Objetivo del Proyecto
Construir y evaluar un modelo predictivo supervisado (como un Árbol de Decisión) que identifique patrones de comportamiento asociados con la deserción estudiantil a partir de los datos históricos de navegación e interactividad.

---

## 📊 Datos Fuente
Los datos provienen de una extracción de la base de datos de **Moodle** alojada en **MariaDB 11.4.10** (exportada el 02-05-2026). 

El análisis se centra específicamente en el curso:
* **Curso:** *Masculinidades Positivas para la Prevención de la Violencia* (ID: 20).
* **Fecha de Inicio del Curso:** 18/08/2024.

### Volumetría de Datos Analizada:
* **Estudiantes matriculados:** 119 alumnos.
* **Eventos en los logs totales:** 132,668 registros.
* **Eventos específicos del curso bajo estudio:** 5,156 interacciones.
* **Registros de completitud evaluados:** 136.

---

## 🛠️ Estructura del Notebook y Ponderación
El desarrollo del proyecto está estructurado de acuerdo a las siguientes fases y pesos metodológicos:

| Sección | Tema | Ponderación | Descripción |
| :---: | :--- | :---: | :--- |
| **1** | Configuración e Importación de Datos | — | Carga de dependencias y desarrollo de un parser SQL personalizado para transformar el dump de MariaDB a DataFrames de Pandas. |
| **2** | Análisis Exploratorio de Datos (EDA) | 30% | Análisis descriptivo inicial y visualización de la distribución temporal de la actividad de los usuarios. |
| **3** | Limpieza y Preparación de Datos | 40% | Manejo de valores nulos, codificación de variables y normalización. |
| **4** | Feature Engineering | 30% | Creación de nuevas variables predictivas (como participación en foros de discusión y completud de módulos). |

---

## 🧰 Tecnologías y Librerías Utilizadas
El proyecto ha sido implementado utilizando el ecosistema de Data Science de Python:
* **Pandas & NumPy:** Manipulación y análisis de estructuras de datos.
* **Scikit-Learn:** Preprocesamiento de datos (Codificación con `LabelEncoder`/`OneHotEncoder`, escalado con `StandardScaler`/`MinMaxScaler` e imputación con `SimpleImputer`) y modelado predictivo.
* **Matplotlib & Seaborn:** Creación de visualizaciones estadísticas y análisis temporal de actividad.
* **Re (Regular Expressions):** Construcción del parser de cadenas SQL orientado al dump de la base de datos.

---

## ⚙️ Características Clave Implementadas

1. **Parser SQL a Pandas Integrado:** Una función optimizada (`load_table`) para extraer registros específicos de tablas de Moodle de un archivo `.sql` de manera directa sin requerir un servidor de base de datos activo en memoria.
2. **Ingeniería de Características (Feature Engineering):** Agregación inteligente de eventos que capturan la participación cualitativa en el entorno virtual, tales como:
   * Publicaciones en foros (`mdl_forum_posts`).
   * Hilos de discusión creados (`mdl_forum_discussions`).
   * Progreso en la finalización de módulos del curso (`mdl_course_modules_completion`).
3. **Análisis del Árbol de Decisión:** Determinación y graficado de las variables más importantes que influyen en el modelo para facilitar la interpretabilidad del negocio o tutoría académica.

---
