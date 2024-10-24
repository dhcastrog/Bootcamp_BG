# ¿Cómo han cambiado las tendencias de producción de energía global a lo largo del tiempo?

```python
import pandas as pd
import numpy as np
```

## Objetivos
Al final de este caso, deberías sentirte muy cómodo escribiendo tus propias funciones usando pandas y aplicándolas a conjuntos de datos completos. Entenderás cómo funcionan las funciones en Python, incluidas las funciones anónimas (usando la palabra clave lambda), y te sentirás cómodo analizando y manipulando grandes conjuntos de datos. También habrás adquirido experiencia explorando un conjunto de datos que está solo vagamente organizado y sobre el cual tienes muy poca información inicial.


## Introducción

**Contexto empresarial.** La producción, consumo, importación y exportación de electricidad a nivel global es un proceso complejo e interesante por varias razones. Cada país tiene que hacer un seguimiento de una gran cantidad de información para asegurarse de producir suficiente electricidad, y a la vez equilibrar estas necesidades con las implicaciones financieras a mediano plazo y las preocupaciones ambientales.

Eres un analista que trabaja en una organización no gubernamental (ONG) que informa sobre las tendencias energéticas globales. Tu departamento ha adquirido un archivo CSV grande, pero tus colegas están teniendo dificultades para extraer conocimientos relevantes de él usando Excel debido a su tamaño y formato. Aún peor, tiene miles de variables y no están seguros de cuáles son las interesantes. Por ello, te han asignado la responsabilidad de apoyar a los periodistas de tu equipo proporcionándoles datos y conocimientos que puedan convertir en informes escritos.

**Problema empresarial.**  Tu tarea es **desglosar los datos disponibles en archivos más pequeños, comprender la información disponible y extraer conocimientos clave para un próximo informe sobre los patrones de energía global.** En concreto, tu equipo quiere que respondas a las siguientes preguntas:

* ¿Cuánta energía se produce?
* ¿Cuánta energía se consume?
* ¿Cuánta energía se importa y se exporta?
* ¿Cuánta de esta energía es renovable?
* ¿Cómo están cambiando estas tendencias de producción, consumo, importación y exportación a lo largo del tiempo?

**Contexto analítico.** Los datos están almacenados en un gran archivo CSV que contiene información sobre la producción y consumo de energía por país y año. Vas a: 1) dividir los datos en archivos CSV resumidos para compartir con tus colegas; 2) manipular los datos para crear más categorías a partir de las columnas existentes; 3) encontrar los principales actores en diferentes categorías, incluyendo la exportación total de energía y la producción total por tipo (por ejemplo, nuclear); y finalmente 4) encontrar tendencias en los datos, como los países con el crecimiento más rápido en la producción de energía.

```python
import requests
import zipfile
import os

local_zip_path = "all_energy_statistics.zip"  # Guardar el ZIP localmente

# Descargar el archivo
response = requests.get("https://github.com/dhcastrog/Bootcamp_BG/raw/refs/heads/main/Reto4/all_energy_statistics.zip")
with open(local_zip_path, 'wb') as file:
    file.write(response.content)

print("ZIP descargado exitosamente.")

unzip_folder = 'unzipped_data'
os.makedirs(unzip_folder, exist_ok=True)

# Step 3: Extraer el archivo ZIP
with zipfile.ZipFile(local_zip_path, 'r') as zip_ref:
    zip_ref.extractall(unzip_folder)

print("Archivos extraídos exitosamente.")
csv_file_path = os.path.join(unzip_folder, 'all_energy_statistics.csv')
```
