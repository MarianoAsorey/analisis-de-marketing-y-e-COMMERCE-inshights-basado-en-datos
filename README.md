# Análisis de Marketing & E-Commerce Insights

  Este proyecto consiste en un análisis integral de datos reales de un e-commerce con el objetivo de optimizar la toma de decisiones estratégicas.  Se evaluó la **rentabilidad de las campañas de marketing**, el **comportamiento del catálogo de productos mediante segmentación avanzada** (Clustering) y la **calidad de la base de clientes a nivel global.**

### ▬ Flujo de trabajo

* **Normalización de los datos:** Uso de **clean_names()** para estandarizar encabezados.
* **Parseo Temporal:** Conversión de timestamps y fechas para análisis
* **Tratamiento de Anomalías:** Filtrado de transacciones con ingresos negativos o nulos

### ▬ Objetivos del proyecto

* Analizar la interacción de los usuarios con el sitio a lo largo del funnel de compra.
* Medir y comparar la performance de las campañas de marketing en términos de revenue y eficiencia.
* Identificar qué clientes aportan mayor valor al negocio.
* Evaluar qué productos impulsan los ingresos y la rentabilidad.

### ▬ Datos de entrada

- `campaigns.csv`  
- `customers.csv`  
- `events.csv`  
- `products.csv`  
- `transactions.csv`

> Todos en codificación UTF-8. Para mayor detalle de los datasets utilizados, dirigase a la carpeta Data.

## Dependencias en R

- `tidyverse`  
- `janitor`  
- `lubridate`  
- `scales`
-  `ggrepel`
- `knitr` 
- `kableExtra` 
- `ggcorrplot` 
- `maps` 
- `treemapify` 
- `readr`

### 🔎 Principales resultados

* El canal de Email es el mas eficiente, logrando un ROI del 90%
* Los rubros de Electrónica y Hogar son los pilares comerciales, concentrando mas del 65% de la facturación
* Del total de usuarios con intención de compra, el 60,4% concreta la transacción, identificando un 39,6% de abandono en el carrito
* Se detectaron productos específicos (P882 y P1063) cuyas tasas de devolución del 15% duplican el promedio de su categoría
* La Campaña 14 (Email - Retention) alcanzó un ROI récord de 338%
* EE.UU. e India representan el 55% de la base de clientes.

### 📄Informe completo 
Podras ver el **PDF del informe**, en donde explico con mas detalle estos resultados, como tambien las visualizaciones realizadas en R.

 [Ver informe en PDF](docs/Análisis%20sectorial%20y%20territorial%20del%20empleo%20productivo%20en%20Argentina%20(2021%20-%202022).pdf)

Los gráficos y tablas se encuentran en la carpeta outputs.

### 🔎 Metodologia aplicada

Dado que el dataset no disponia de costos reales de la campaña, utilicé un modelo de asignación de costos por canal
.
* Para cada campaña, el costo total se calcula como:

$$
\text{Costo Campaña}_c = \text{Duración}_c \times \text{Costo Diario}_{canal(c)}
$$

* Donde la duración de la campaña se define como:

$$
\text{Duración}_c = (\text{Fecha Fin}_c - \text{Fecha Inicio}_c) + 1
$$

* Una transacción se atribuye a una campaña si ocurre dentro del siguiente intervalo:

$$
\text{Fecha}_t \in [\text{Fecha Inicio}_c,\; \text{Fecha Fin}_c + 14]
$$

 ##### Asignación de Costos a Nivel Producto

* Para evaluar rentabilidad por producto, el costo total de cada campaña se distribuye proporcionalmente según los ingresos generados por cada producto.

$$
\text{Costo Producto}_{p,c} =
\text{Costo Campaña}_c \times
\frac{\text{Ingresos}_{p,c}}{\sum\limits_{p \in c} \text{Ingresos}_{p,c}}
$$

### 📊 Indicadores clave

ROI – Retorno sobre la Inversión

$$
\text{ROI} = \frac{\text{Ingresos} - \text{Costo}}{\text{Costo}}
$$

CPA – Costo por Adquisición

$$
\text{CPA} = \frac{\text{Costo}}{\text{Cantidad de Compradores}}
$$




