# Documentación del Proceso de Recolección de Datos para el Proyecto de Predicción Anual del Banco Portugues
## 1. Fuentes

**Identificación de las fuentes:**
- Base de datos interna del CRM

**Descripción de las fuentes:**
- La base de datos CRM cuenta con registros de datos de los clientes, datos financieros de los clientes y datos recogidos mediante llamadas en las diferentes campañas realizadas.
  
## 2. Métodos de recolección de datos

**Procedimientos:**
- Exportación programada en formato CSV, subida a un servicio de la nube de AWS diariamente. De esta tarea se encarga el servicio de IT contratado a una consultora.

**Frecuencia de recolección:**
- Diario
  
**Scripts de Descarga:**

```python

import pandas as pd

csv_url = "https://aws.lanube.com/bancoportugues/main/DataCustomers.csv"
df = pd.read_csv(csv_url)
print(df.info())

```

## 3. Formato y estructura de los datos

**Tipos de datos:**
- Numéricos: `age`, `balance`, `duration`, `campaign`, `pdays`, `previous`
- Categóricos: `job`, `marital`, `education`, `contact`, `poutcome`, `month`, `day_of_week`
- Binarios: `default`, `housing`, `loan`, `deposit`

**Formato:**
- Datos tabulares en fichero csv.

## 4. Limitaciones de los datos

- Aunque los datos se actualizan automaticamente, se depende de la consultora para arreglar cualquier problema.

## 5. Consideraciones sobre Datos Sensibles

**Tipos de Datos Sensibles:**
- Información Personal Identificable (PII): `age`, `job`
- Información Financera Sensible: `balance`
- Datos Comportamentales Sensibles:`duration`, `contact`

**Medidas de Protección:**
- **Anonimización:**
  - No se recogerán datos que puedan comprometer la privacidad de los clientes
- **Acceso Restringido:**
  - Solamente tienen acceso a los datos las personas autorizadas para ello.
- **Cumplimiento de la Regulación:**
  - Cumplimiento con la RPGD
