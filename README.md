# Análisis de Evasión de Clientes (Churn) - Telecom X

##  Descripción Ejecutiva
Este proyecto aborda una problemática crítica de negocio para la empresa de telecomunicaciones **Telecom X**: la alta tasa de cancelación de suscriptores (*Churn*). 

Actuando bajo el rol de Analista de Datos, se desarrolló un ciclo completo de inteligencia de negocios (ETL y EDA) para transformar datos crudos en insights estratégicos, identificando los patrones de comportamiento de los clientes que abandonan la compañía y proponiendo acciones de retención basadas en evidencia.

---

##  Stack Tecnológico y Librerías
El proyecto fue desarrollado íntegramente en **Python**, utilizando las siguientes librerías especializadas para cada etapa del proceso:

* **`requests`**: Extracción de datos. Se utilizó para conectar con la API fuente y descargar la información cruda en formato JSON.
* **`pandas`**: Núcleo del análisis. Utilizada para la normalización del JSON (aplanamiento de diccionarios), limpieza de datos nulos, transformación de tipos de variables y manipulación tabular (DataFrames).
* **`numpy`**: Soporte matemático. Implementada para el manejo eficiente de valores numéricos y tratamiento de vectores.
* **`matplotlib.pyplot`**: Visualización base. Utilizada para la configuración de lienzos (`figure`, `subplots`) y personalización fina de los gráficos.
* **`seaborn`**: Visualización estadística. Empleada para generar gráficos avanzados (Countplots, Boxplots) que permitieron identificar patrones complejos y correlaciones visuales de manera estética y clara.

---

##  Metodología del Proyecto

### 1. Extracción y Transformación (ETL)
* **Normalización:** Se procesó un archivo JSON anidado proveniente de una API, reestructurando diccionarios complejos para obtener un dataset tabular limpio de **7,032 registros** y **21 columnas**.
* **Limpieza:** Se identificaron y eliminaron registros con valores vacíos en variables críticas (`Churn`, `TotalCharges`) y se estandarizaron los tipos de datos (conversión de `Object` a `Float` en cargos mensuales).
* **Ingeniería de Características:** Binarización de variables categóricas clave para facilitar el análisis estadístico.

### 2. Análisis Exploratorio de Datos (EDA)
Se realizaron análisis univariados y bivariados para detectar "puntos de dolor" en la experiencia del cliente:
* **Análisis Categórico:** Evaluación de fugas por tipo de contrato, método de pago y servicios contratados.
* **Análisis Numérico:** Estudio de distribuciones de cargos mensuales, totales y antigüedad (*Tenure*) mediante Boxplots.

---

##  Principales Hallazgos (Insights)

El análisis reveló patrones claros que explican la fuga de clientes:

1.  **Vulnerabilidad Contractual:** Los clientes con contratos **"Mes a Mes"** presentan una tasa de abandono drásticamente superior a los de contratos anuales (fidelidad >90%).
2.  **Fricción en Pagos:** El método de pago **"Electronic Check"** es un factor crítico de riesgo; los usuarios que lo utilizan tienen una probabilidad de fuga significativamente mayor que aquellos con pagos automatizados.
3.  **Problema en el Segmento Premium:** Los usuarios de **Fibra Óptica** (servicio de mayor costo) muestran mayores índices de cancelación que los de DSL, sugiriendo una insatisfacción con la relación calidad-precio.
4.  **Curva de Permanencia:** El riesgo de pérdida es crítico durante los primeros **12 meses**. Superado el primer año, la fidelidad del cliente se estabiliza.

---

##  Conclusiones y Recomendaciones
Para mitigar la tasa de Churn, se sugieren las siguientes estrategias basadas en datos:
* Implementar un programa de **Onboarding y Fidelización** agresivo durante el primer año de vida del cliente.
* Incentivar la migración de pagos manuales a **Débito Automático** mediante descuentos porcentuales.
* Revisar la competitividad y calidad técnica del servicio de **Fibra Óptica**.
* Promover contratos de largo plazo (1-2 años) ofreciendo beneficios exclusivos para reducir la volatilidad del segmento "Mes a Mes".

---

##  Autor
**Maria Camila Sierra Ospina** *Junior Software Developer & Data Analyst* ```
