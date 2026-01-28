# Análisis de Evasión de Clientes (Churn) - Telecom X

##  Diccionario de Datos
Para facilitar la interpretación del análisis, se realizó un proceso de renombrado de variables, traduciendo los términos técnicos originales a un lenguaje de negocio claro en español.

| Nombre Original (JSON/Raw) | Nombre Procesado | Descripción de la Variable |
| :--- | :--- | :--- |
| **customerID** | *Eliminada* | Identificador único (no aporta valor predictivo). |
| **gender** | `Genero` | Género del cliente (Masculino/Femenino). |
| **SeniorCitizen** | `Es_Adulto_Mayor` | Indica si el cliente es jubilado (0: No, 1: Sí). |
| **Partner** | `Tiene_Pareja` | Indica si el cliente tiene pareja (Sí/No). |
| **Dependents** | `Tiene_Dependientes` | Indica si el cliente vive con dependientes económicos. |
| **tenure** | `Meses_Permanencia` | Número de meses que el cliente ha permanecido en la empresa. |
| **PhoneService** | `Servicio_Telefonico` | Indica si tiene servicio de teléfono fijo. |
| **MultipleLines** | `Lineas_Multiples` | Indica si tiene múltiples líneas telefónicas. |
| **InternetService** | `Tipo_Internet` | Tipo de proveedor de internet (DSL, Fibra Óptica, No). |
| **OnlineSecurity** | `Seguridad_Online` | Indica si tiene contratado el servicio de seguridad adicional. |
| **OnlineBackup** | `Copia_Seguridad` | Servicio de respaldo en la nube. |
| **DeviceProtection** | `Proteccion_Dispositivo` | Seguro de protección de equipos. |
| **TechSupport** | `Soporte_Tecnico` | Servicio de soporte técnico dedicado. |
| **StreamingTV** | `TV_Streaming` | Indica si usa el servicio de TV por internet. |
| **StreamingMovies** | `Peliculas_Streaming` | Indica si usa el servicio de películas por streaming. |
| **Contract** | `Tipo_Contrato` | Modalidad de contrato (Mes a mes, 1 año, 2 años). |
| **PaperlessBilling** | `Facturacion_Digital` | Indica si recibe la factura de forma digital (sin papel). |
| **PaymentMethod** | `Metodo_Pago` | Medio de pago (Cheque electrónico, tarjeta, transferencia, etc.). |
| **MonthlyCharges** | `Cargos_Mensuales` | Monto cobrado al cliente mensualmente. |
| **TotalCharges** | `Cargos_Totales` | Monto total cobrado al cliente durante toda su relación comercial. |
| **Churn** | `Abandono` | **Variable Objetivo.** Indica si el cliente canceló el servicio (Sí/No). |


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
