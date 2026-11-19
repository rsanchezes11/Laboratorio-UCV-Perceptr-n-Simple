#  Laboratorio UCV: Perceptrón Simple — Aprobación de Créditos

Implementación desde cero de una neurona artificial (**Perceptrón Simple**) en **Python 3.12**, aplicada a un caso de negocio financiero para automatizar la evaluación preliminar de solicitudes de crédito bancario[cite: 1].

---

##  Caso de Negocio

Una entidad bancaria requiere automatizar el filtrado inicial de solicitudes de crédito evaluando dos variables clave de cada cliente[cite: 1]:
1. **Ingreso mensual** ($x_1$, escala normalizada)[cite: 1].
2. **Historial crediticio** ($x_2$, `1` = favorable / `0` = desfavorable)[cite: 1].

El modelo clasifica cada solicitud de forma binaria[cite: 1]:
- **`1`**: Crédito **Aprobado**[cite: 1].
- **`0`**: Crédito **Rechazado**[cite: 1].

---

##  Arquitectura del Proyecto

```text
perceptron-credito-ucv/
├── .github/
│   └── workflows/
│       └── ci.yml              # Pipeline de Integración Continua (GitHub Actions)
├── src/
│   ├── __init__.py
│   ├── dataset.py              # Conjunto de datos etiquetados para entrenamiento
│   └── perceptron.py           # Clase Perceptron (activación, predicción y entrenamiento)
├── tests/
│   ├── __init__.py
│   └── test_perceptron.py      # Pruebas unitarias automatizadas con pytest
├── main.py                     # Script principal de ejecución e inferencia
└── README.md                   # Documentación técnica del proyecto
```[cite: 1, 2]

---

##  Modelo Matemático Implementado

La neurona calcula la suma ponderada de las entradas más un sesgo (*bias*)[cite: 1]:

$$z = \sum_{i=1}^{n} (x_i \cdot w_i) + b$$[cite: 1]

Aplica una **función de activación escalón** (*Step Function*)[cite: 1]:

$$\hat{y} = \begin{cases} 1 & \text{si } z \ge 0 \\ 0 & \text{si } z < 0 \end{cases}$$[cite: 1]

Durante el entrenamiento supervisado, ajusta sus parámetros mediante la **Regla de Aprendizaje del Perceptrón**[cite: 1]:

$$w_i \leftarrow w_i + \eta \cdot (y - \hat{y}) \cdot x_i$$[cite: 1]
$$b \leftarrow b + \eta \cdot (y - \hat{y})$$[cite: 1]

---

##  Instalación y Ejecución Local

### 1. Clonar el repositorio
```bash
git clone [https://github.com/TU_USUARIO/perceptron-credito-ucv.git](https://github.com/TU_USUARIO/perceptron-credito-ucv.git)
cd perceptron-credito-ucv
```[cite: 2]

### 2. Instalar dependencias de pruebas
```bash
pip install pytest
```[cite: 1]

### 3. Ejecutar el modelo predictivo
```bash
python main.py
```[cite: 1]
*Salida esperada para el perfil `[9, 1]`: `1` (Aprobado)[cite: 1].*

### 4. Ejecutar suite de pruebas unitarias
```bash
pytest -v
```[cite: 1]

---

##  CI/CD y Calidad de Código

- **GitHub Actions:** Cada `push` o `pull_request` dispara automáticamente el flujo `CI` en Ubuntu con Python 3.12 para validar las pruebas unitarias mediante `pytest`[cite: 1].
- **SonarCloud:** Análisis estático continuo para garantizar código limpio, libre de *bugs*, vulnerabilidades y *code smells*[cite: 1].

---
