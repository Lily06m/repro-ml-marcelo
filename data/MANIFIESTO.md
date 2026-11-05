# Manifiesto de datos

| Campo | Valor |
|---|---|
| Nombre del archivo en `data/raw/` | DadosV3.csv |
| Fuente (institución) | Kaggle, dataset publicado por Saurabh Shahane. Los datos provienen de un centro deportivo de Lisboa (Portugal) |
| URL exacta de descarga | https://www.kaggle.com/datasets/saurabhshahane/sport-services-dataset |
| Fecha de descarga | 2026-11-01 |
| Licencia o condiciones de uso | Open Data Commons Database Contents License (DbCL) v1.0, según la ficha del dataset en Kaggle |
| ¿Se permite redistribuir? | Sí. El archivo pesa 4,3 MB, menos del límite de 100 MB de GitHub, por eso se incluye en el repositorio |
| Filas × columnas (raw) | 14 942 × 47 |
| MD5 del archivo raw | 7651033e85d057d52b27b1cfa4a67755 |
| MD5 del archivo processed | beefd1187915dfb085a7fd1d4afc119f |

El archivo usa punto y coma (`;`) como separador, por eso `src/prepare_data.py` lo lee con `sep=";"`.

## Diccionario de las variables usadas

| Variable | Tipo | Descripción | Unidad / categorías |
|---|---|---|---|
| Dropout | Objetivo | Estado final del socio en el servicio | 0 = permanece, 1 = abandona |
| Age | Numérica | Edad del socio | Años |
| EnrollmentDuration | Numérica | Antigüedad del socio en el centro deportivo | Meses |
| LifetimeValue | Numérica | Valor monetario acumulado que generó el socio | Euros |
| AverageFrequency | Numérica | Frecuencia promedio de visitas del socio | Visitas por unidad de tiempo |
| RealNumberOfVisits | Numérica | Número de asistencias registradas en el control de acceso | Visitas |
| NumberOfActivities | Numérica | Cantidad de actividades deportivas que practica o contrató | Actividades |
| NumberOfRenewals | Numérica | Cantidad de renovaciones de la suscripción | Renovaciones |
| Gender | Categórica | Género reportado por el socio | Female, Male |

## Transformaciones de raw a processed
1. Se quitaron espacios en los nombres de columnas.
2. Se eliminaron filas duplicadas (no había ninguna: se mantienen las 14 942 filas).
3. No se definieron códigos de faltantes (`CODIGOS_FALTANTES` está vacío), por lo que este paso no cambia los datos.
4. Se eliminaron las filas sin valor en la variable objetivo (no había ninguna).
5. Sin limpieza propia adicional: el EDA del grupo no encontró valores faltantes y se conservaron los valores atípicos porque corresponden a socios reales.
