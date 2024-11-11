# Proyecto de Extracción de Información de Facturas en PDF

Este proyecto tiene como objetivo leer archivos PDF de facturas y extraer información clave como fecha, CIF, número de factura, teléfono, importe total, razón social, el texto completo de cada factura y el archivo en formato Base64. Utiliza **spaCy** para el procesamiento de lenguaje natural (PLN) y la API de **OpenAI** para el procesamiento de textos.

## Características

- **Extracción de Texto**: Se extrae el contenido textual de archivos PDF de facturas utilizando `pdfplumber`.
- **Entrenamiento de Modelo PLN**: Se entrena un modelo de PLN con `spaCy` para identificar entidades como Fecha, CIF, Número de Factura, Teléfono e Importe Total.
- **Integración con OpenAI**: Utiliza la API de OpenAI para extraer la razón social de cada factura de manera precisa.
- **Almacenamiento Estructurado**: Los datos extraídos se guardan en un archivo CSV y en un archivo Excel para facilitar su análisis.

## Estructura del Proyecto

- `main.ipynb`: Notebook principal que contiene el flujo de extracción y entrenamiento del modelo.
- `facturas_procesadas.csv` y `facturas_procesadas.xlsx`: Archivos resultantes con la información de todas las facturas.
- `mejor_modelo_facturas_ner`: Carpeta donde se guarda el modelo entrenado de spaCy.
- `facturas/`: Carpeta que contiene las facturas en formato PDF para procesar.

## Requisitos

Para ejecutar este proyecto, necesitas instalar las siguientes librerías:

```bash
pip install pdfplumber spacy pandas scikit-learn openai

Asegúrate de configurar correctamente tu clave API de OpenAI como variable de entorno o archivo de configuración para evitar exponerla en el código.

Instrucciones de Uso
Preparar el Entorno:

Clona el repositorio e instala las dependencias necesarias.
Configura tu clave API de OpenAI como variable de entorno para protegerla (por ejemplo, en Linux/MacOS: export OPENAI_API_KEY='tu_clave_api').
Organizar las Facturas:

Coloca los archivos PDF de las facturas en una carpeta (por ejemplo, facturas/).
Ejecutar el Notebook:

Abre el archivo main.ipynb en Jupyter Notebook o en Google Colab.
Ejecuta cada celda en el orden indicado.
El notebook extraerá el texto de cada factura, entrenará el modelo PLN, extraerá los campos de interés y los guardará en archivos .csv y .xlsx.
Guardar y Verificar Resultados:

Los resultados se guardarán en facturas_procesadas.csv y facturas_procesadas.xlsx en el directorio del proyecto.
Configuración del Notebook
Extracción de Texto:

El código recorre los archivos en el directorio de facturas, extrae el texto usando pdfplumber y guarda el texto en archivos .txt.
Entrenamiento de Modelo PLN:

Se cargan datos etiquetados para la división en conjuntos de entrenamiento y prueba.
El modelo spaCy se entrena para reconocer las entidades de interés en el texto de las facturas.
Extracción de Campos Específicos:

Después de entrenar el modelo, se utiliza para extraer Fecha, CIF, Número de Factura, Teléfono e Importe Total de cada factura.
Se llama a la API de OpenAI para extraer la Razón Social mediante un prompt específico.
Exportación de Resultados:

Los datos extraídos se estructuran en un DataFrame de pandas y se guardan en formato .csv y .xlsx para su análisis.
Mejores Prácticas
Protección de la Clave API: Mantén la clave API de OpenAI fuera del código, utilizando variables de entorno.
Manejo de Errores: Implementa manejo de excepciones en funciones críticas para mejorar la robustez del código.
Ajustes del Modelo: Puedes probar diferentes configuraciones de entrenamiento para mejorar el rendimiento del modelo en tus datos.
Contribuciones
Las contribuciones son bienvenidas. Si tienes ideas para mejorar el proyecto, por favor, abre un issue o envía un pull request.
