# PANDAS

## Introducción
Este proyecto se centra en el análisis de datos utilizando Pandas, cubriendo varios aspectos desde la importación de datos hasta la limpieza y la ingeniería de características.

## Importación de Datos
Pandas ofrece varias funciones para importar datos:

*   `read_csv()`: Para archivos CSV (valores separados por comas).
*   `read_excel()`: Para archivos de Excel (`.xls`, `.xlsx`).
*   `read_json()`: Para archivos JSON.
*   `read_html()`: Para tablas HTML.
*   `read_sql()`: Para bases de datos relacionales.

### Ejemplo: Importación de Datos
```python
import pandas as pd
url = 'https://gist.githubusercontent.com/ahcamachod/a572cfcc2527046db93101f88011b26e/raw/ffb13f45a79d31223e645611a119397dd127ee3c/alquiler.csv'
datos = pd.read_csv(url, sep=';')
print(datos.head())
```

## Exploración Inicial de Datos

*   **Dimensiones de los Datos**: Verifica el número de filas y columnas utilizando `.shape`.
*   **Información de Columnas**: Visualiza los nombres de las columnas utilizando `.columns`.
*   **Tipos de Datos y Valores Ausentes**: Obtén un resumen con `.info()`.

### Ejemplo: Resumen de Datos
```python
print(datos.shape)
print(datos.columns)
print(datos.info())
```

## Limpieza de Datos

### Manejo de Valores Ausentes
Los valores ausentes se identificaron utilizando `.isnull().sum()` y se rellenaron con ceros utilizando `.fillna(0)`.

### Eliminación de Registros Inconsistentes
Se eliminaron los registros con `Valor == 0` o `Condominio == 0` para asegurar la calidad de los datos.

## Ingeniería de Características

### Nuevas Características Numéricas
*   **`Valor_mensual`**: `Valor` + `Condominio`
*   **`Valor_anual`**: `Valor_mensual` * 12 + `Impuesto`

### Nuevas Características Categóricas
*   **`Descripcion`**: Combinación de `Tipo`, `Colonia`, `Habitaciones` y `Garages`.
*   **`Tiene_suite`**: Indica si una propiedad tiene suites (`'Si'` o `'No'`).

## Conclusión
Este README proporciona una descripción general de los pasos de procesamiento de datos, desde la importación y exploración de los datos brutos hasta la limpieza y la ingeniería de nuevas características. Estos pasos son cruciales para preparar el conjunto de datos para los modelos de aprendizaje automático.
