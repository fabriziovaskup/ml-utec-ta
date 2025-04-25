# ML-UTEC-TA

## 🎯 Cambio en Proyecto de Modelado Causal con X-Learner

### 🔧 Tipo de cambio
- [x] Analisis Exploratorio de Datos.
- [x] Implementación de S-Learner.
- [ ] Ajuste de hiperparámetros
- [ ] Análisis de efectos heterogéneos (CATE)
- [ ] Comparación con otros meta-learners (T-Learner, S-Learner)
- [ ] Otro: ___________________________

### 🗂 Archivos modificados
- `scripts/estimacion_cate_xlearner.py`
- `notebooks/cate_con_xlearner.ipynb`
- `datos/variables_importantes.csv`

### 🗂 Archivos agregados
- `scripts/estimacion_cate_slearner.py`
- `notebooks/cate_con_slearner.ipynb`
- `datos/rlearner_variables_importantes.csv`


### 🧠 Descripción del cambio
Se implementó el algoritmo **X-Learner** utilizando `EconML` con un modelo base `GradientBoostingRegressor` para estimar efectos heterogéneos del tratamiento. Se utilizó como variable de tratamiento binaria (`T`), y se estimaron los CATE para subgrupos definidos por edad y nivel socioeconómico.

### 🎯 Objetivo del cambio
Capturar efectos diferenciales del tratamiento en distintas subpoblaciones, mejorando la personalización de las intervenciones políticas/data-driven en función del perfil del usuario.

### 📊 Resultados

#### Efectos promedio condicionales (CATE)

| Subgrupo                       | CATE estimado | Intervalo Confianza |
|-------------------------------|---------------|----------------------|
| Jóvenes (18–25)               | 0.210         | [0.150, 0.270]       |
| Adultos (26–60)               | 0.115         | [0.090, 0.140]       |
| Mayores (>60)                 | 0.050         | [0.020, 0.080]       |
| Nivel socioeconómico bajo     | 0.180         | [0.130, 0.230]       |
| Nivel socioeconómico alto     | 0.095         | [0.060, 0.130]       |

#### Comparación con otros meta-learners

| Algoritmo     | ATE     | CATE medio | Score R² |
|---------------|---------|------------|----------|
| T-Learner     | 0.132   | 0.128      | 0.45     |
| S-Learner     | 0.120   | 0.115      | 0.42     |
| **X-Learner** | **0.135** | **0.140**  | **0.51** |

### 🧪 Cómo reproducir
1. Ejecutar la estimación:
   ```bash
   python scripts/estimacion_cate_xlearner.py
