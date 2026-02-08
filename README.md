# ⚽ Inazuma Eleven Victory Road: Clustering Analysis

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-orange?logo=scikit-learn)
![API](https://img.shields.io/badge/Data-JSON%20API-lightgrey)
![Status](https://img.shields.io/badge/ARI%20Score-1.0-brightgreen)

> **Deconstruyendo el "Meta" de Inazuma Eleven: Consumo de API, ingeniería de datos y descubrimiento de los 30 arquetipos de jugadores mediante Clustering.**

---

## 🎮 Descripción del Proyecto

Con el lanzamiento de *Inazuma Eleven: Victory Road*, la cantidad de personajes jugables es inmensa (+4500).
Este proyecto nace de la curiosidad por entender cómo los desarrolladores equilibran matemáticamente el juego.

**El objetivo:** Aplicar algoritmos de **Aprendizaje No Supervisado** para agrupar a los jugadores basándonos exclusivamente en sus estadísticas (Tiro, Defensa, Control, etc.) y verificar si existen patrones ocultos más allá de las posiciones clásicas.

---

## 🛠️ Tecnologías y Pipeline

### 1. Obtención de Datos (API Reverse Engineering)
En lugar de realizar scraping lento, identifiqué y consumí directamente la **API JSON** del juego (`comparador_api.php`) utilizando la librería `requests`.
* **Ventaja:** Obtención limpia de datos estructurados de más de 4,500 personajes en segundos.
* **Limpieza:** Tratamiento de nulos y conversión de atributos categóricos.

### 2. Preprocesamiento
* **Escalado:** Uso de `RobustScaler` para manejar outliers en las estadísticas de los jugadores, asegurando que personajes "rotos" (muy fuertes) no distorsionen los grupos.

### 3. Modelado (Clustering)
Se implementaron y compararon tres familias de algoritmos para encontrar la estructura óptima:
* **K-Means** (Particional)
* **Agglomerative Clustering** (Jerárquico)
* **DBSCAN** (Densidad)

---

## 📊 Resultados Clave: Las 30 Plantillas

El hallazgo más importante fue demostrar matemáticamente que el juego no es aleatorio. Los algoritmos convergieron en una estructura perfecta.

| Métrica | Resultado | Interpretación |
| :--- | :--- | :--- |
| **ARI Score** | **1.0 (Perfecto)** | El algoritmo replicó exactamente la estructura interna de balanceo. |
| **Hallazgo** | **30 Arquetipos** | Existen 30 "plantillas" de estadísticas exactas que se repiten entre los 4,500 personajes. |

> **Insight:** Esto permite identificar jugadores desconocidos que pertenecen matemáticamente al mismo "molde" que los mejores jugadores del meta, descubriendo así **joyas ocultas** (mismas stats, diferente nombre).

---

## 📂 Estructura del Repositorio

```bash
├── data/
│   └── datos_personajes_inazuma.csv  # Dataset generado desde la API
├── notebooks/
│   └── Clustering.ipynb              # Script de extracción y modelos
├── requirements.txt                  # Dependencias
└── README.md
