# Análisis de Marketing & E-Commerce

  Este proyecto consiste en un análisis integral de datos reales de un e-commerce con el objetivo de optimizar la toma de decisiones estratégicas.  Se evaluó la **rentabilidad de las campañas de marketing**, el **comportamiento del catálogo de productos mediante segmentación avanzada** (Clustering) y la **calidad de la base de clientes a nivel global.**

## 🔴 Flujo de trabajo

* **Normalización de los datos:** Uso de **clean_names()** para estandarizar encabezados.
* **Parseo Temporal:** Conversión de timestamps y fechas para análisis
* **Tratamiento de Anomalías:** Filtrado de transacciones con ingresos negativos o nulos

## 🟢 Objetivos del proyecto

* Analizar la interacción de los usuarios con el sitio a lo largo del funnel de compra.
* Medir y comparar la performance de las campañas de marketing en términos de revenue y eficiencia.
* Identificar qué clientes aportan mayor valor al negocio.
* Evaluar qué productos impulsan los ingresos y la rentabilidad.

## 🔵 Datos de entrada

- `campaigns.csv`  
- `customers.csv`  
- `events.csv`  
- `products.csv`  
- `transactions.csv`

> Todos en codificación UTF-8. Para mayor detalle de los datasets utilizados, dirigase a la carpeta Data.

### Dependencias en R

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
>La instalacion se encuentra en la carpeta scripts

## 🔎 Principales resultados

* El canal de Email es el mas eficiente, logrando un ROI del 90%
* Los rubros de Electrónica y Hogar son los pilares comerciales, concentrando mas del 65% de la facturación
* Del total de usuarios con intención de compra, el 60,4% concreta la transacción, identificando un 39,6% de abandono en el carrito
* Se detectaron productos específicos (P882 y P1063) cuyas tasas de devolución del 15% duplican el promedio de su categoría
* La Campaña 14 (Email - Retention) alcanzó un ROI récord de 338%
* EE.UU. e India representan el 55% de la base de clientes.
  
### 📄Informe completo 
Podras ver el **PDF del informe**, en donde se explica con mas detalle estos resultados, como tambien las visualizaciones realizadas en R.

 [Ver informe en PDF](docs/Análisis%20sectorial%20y%20territorial%20del%20empleo%20productivo%20en%20Argentina%20(2021%20-%202022).pdf)
 
 > Los gráficos y tablas se encuentran en la carpeta outputs.
----------
## Distribucion del codigo

El codigo esta dividido en tres scripts para facilitar su comprension: 
* `instalacion.py` para la instalación de las librerias requeridas, 
* `limpieza.py` correspondiente al codigo para homogeneizar valores temporales y filtrar ingresos negativos 
* `EDA.py` con el proceso de exploración de las tablas junto a la visualizaciones creadas

> El analisis exploratorio se divide en tres niveles: por campañas, por productos y por clientes. Dichos analisis estan diferenciados en el propio codigo con las letras A, B, C respectivamente para facilitar la lectura de los mismos.

##  Metodologia aplicada

  Ante la ausencia de costos reales en el dataset original, se construyó un **proxy de gasto por campaña** en base a costos diarios por canal:

### 💵 Modelo de costeo

| |  |
| :--- | :--- |
| **Costo por Campaña** | Estimado mediante un costo diario fijo según el canal de marketing |
| **Costos Diarios** | Email ($80), Display ($120), Social ($180), Affiliate ($120), Paid Search ($250). |
| **Ventana de Atribución** | Se capturan transacciones hasta **14 días después** del fin de la campaña. |


### 📋 Calculos

| | |
| :--- | :--- |
| **Duración de Campaña** | $Duración_{c} = (Fecha Fin_{c} - Fecha Inicio_{c}) + 1$ |
| **Costo Total de Campaña** | $Costo Campaña_{c} = Duración_{c} \times Costo Diario_{canal(c)}$ |
| **Atribución por Producto** | $Costo Producto_{p,c} = Costo Campaña_{c} \times \frac{Ingresos_{p,c}}{\sum_{p \in c} Ingresos_{p,c}}$ |

### 📊 Indicadores Clave (KPIs)

  Se definieron los siguientes indicadores para medir el desempeño y la eficiencia financiera del ecosistema:

| |  |  |
| :--- | :--- | :--- |
| **ROI** | **Retorno sobre la Inversión:** Mide la rentabilidad neta por cada dólar invertido. | $$ROI = \frac{Ingresos - Costo}{Costo}$$ |
| **CPA** | **Costo por Adquisición:** Determina el costo promedio para convertir a un nuevo comprador único. | $$CPA = \frac{Costo}{Cant.\ Compradores}$$ |

----------------
Autor: Mariano Asorey



