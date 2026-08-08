# Análisis de Ventas de un Negocio de E-Commerce

## Descripción

Proyecto personal de análisis de datos enfocado en las ventas de un negocio de comercio electrónico.  
El objetivo es comprender el comportamiento temporal de las ventas, identificar patrones de compra de los clientes, construir un dashboard interactivo para la visualización de indicadores clave y proponer posibles acciones que contribuyan a la toma de decisiones comerciales.

El análisis fue realizado utilizando únicamente la información disponible en el dataset. Variables adicionales como categorías de productos, costos, márgenes de ganancia o información demográfica de los clientes permitirían profundizar considerablemente el análisis.

---

## Objetivos

- Limpiar y preparar los datos para su análisis
- Analizar el comportamiento temporal de las ventas (por hora, día y mes)
- Estudiar el comportamiento y la fidelización de los clientes
- Segmentar clientes mediante el modelo RFM (Recency, Frequency, Monetary)
- Construir un dashboard interactivo en Power BI

---

## Procesamiento de datos

- Renombre de columnas al español para mayor claridad
- Tratamiento de valores nulos: clientes sin identificación conservados bajo la etiqueta "Desconocido"; productos sin descripción reemplazados por "No tiene"
- Eliminación de transacciones con cantidades o precios negativos (devoluciones y correcciones)
- Detección y eliminación de filas duplicadas
- Conversión de la columna de fecha al formato datetime con formato explícito
- Extracción de variables temporales: año, mes, día, hora y minuto
- Creación de la variable `ingreso` como producto entre cantidad y precio unitario
- Se eliminó un 3.14% de los registros originales durante la limpieza

---

## Análisis exploratorio

### Análisis de clientes
- Cálculo de la tasa de retención: el 65.59% de los clientes realizó más de una compra
- Concentración de ingresos: el 5% de los clientes con mayor gasto generó el 42.1% de los ingresos; el 10% generó el 52.8% de los ingresos; y el 20% generó el 66.18%
- Distribución de la frecuencia de compra por cliente

### Segmentación RFM
Se construyó un modelo RFM que clasifica a cada cliente en tres dimensiones:
- **Recency**: tiempo transcurrido desde la última compra
- **Frequency**: cantidad de compras realizadas
- **Monetary**: monto total gastado

A partir de quintiles en cada dimensión, se asignó a cada cliente uno de los siguientes segmentos:

| Segmento | Descripción |
|---|---|
| Mejor cliente | Compra reciente, alta frecuencia y alto gasto |
| Buen cliente | Compra reciente, frecuencia y gasto moderados-altos |
| Cliente leal | Alta frecuencia de compra |
| Nuevo | Compra reciente con pocas compras registradas |
| En riesgo | No compra hace tiempo pero tiene historial de compras |
| Perdido | Compra lejana y baja frecuencia |
| Ocasional | No encaja en ningún perfil definido |

---

## Resultados

- El negocio presenta indicadores favorables de fidelización: dos tercios de los clientes realizan compras recurrentes
- Los ingresos están moderadamente concentrados en los clientes de mayor valor, sin depender exclusivamente de un grupo reducido
- El segmento más numeroso es el de clientes ocasionales. Además, se identifica un grupo considerable de clientes en riesgo, lo que señala oportunidades de mejora en convertir compradores esporádicos en clientes recurrentes.
- La mayoría de los clientes que realizaron una única compra terminan formando parte del grupo de clientes inactivos, lo que sugiere que otro desafío importante del negocio es incentivar la segunda compra
- El porcentaje de clientes nuevos es relativamente reducido, lo que indica la importancia de complementar la fidelización y retención con estrategias de captación

---

## Dashboard

Se construyó un dashboard interactivo en Power BI con dos páginas:

- **Métricas temporales**: ventas e ingresos por hora, día de la semana y mes
- **Rankings**: productos y clientes que más ingresos y ventas generaron; países con mayor facturación

El dashboard incluye filtros por país, fecha y tipo de cliente (registrado / desconocido). Tambien incluye tarjetas para visualizar distintos datos como la cantidad de ventas, ingreso, cantidad de facturas e ingreso promedio por factura

---

## Tecnologías utilizadas

- Python (Pandas, NumPy, Seaborn)
- Power BI

---

## Fuente de datos

Dataset obtenido de Kaggle:  
https://www.kaggle.com/datasets/umerkk12/online-retail-business

---

## Archivos

- `analisis_e-commerce.ipynb`: limpieza de datos y análisis completo
- `Dashboard.pbix`: dashboard interactivo en Power BI
- `OnlineRetail.csv`: base de datos original
- `ventas_limpio.csv`: base de datos procesada, utilizada en el dashboard
