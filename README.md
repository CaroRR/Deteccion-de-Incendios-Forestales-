# Detección-de-Incendios-Forestales-

En este proyecto se muestra la implementación de tres modelos de visión artificial previamente entrenados.
Estos se sometieron a realizar predicciones a un conjunto de datos externo al que fueron entrenados con la finalidad
de analizar la capacidad de cada uno de estos mediante sus métricas y seleccionar el que presente un mejor desempeño.

Dataset y scripts de soporte.
Descripción del origen del dataset.
Link: https://huggingface.co/datasets/odiug77/wildfire
Nombre del repositorio: odiug77/wildfire
El conjunto de datos Wildfire contiene un total de 1,814 imágenes etiquetadas en formato Yolo, sin embargo, después de realizar una exploración se encontró que 5 imágenes no tenían una etiqueta establecida y 2 se encontraban vacías, por lo que se utilizaron al final 1,807 imágenes, de las cuales 1,961 son ejemplos de imágenes con fuego y 2,235 imágenes con humo.

Entorno de Ejecucion: 
Proyecto creado en Google colab con el uso de GPU:
GPU ASISGNADA POR COLAB
GPU disponible: Tesla T4
Versión CUDA de PyTorch: 13.0
Memoria total de GPU: 14.56 GB

PIPELINE
<img width="996" height="1055" alt="image" src="https://github.com/user-attachments/assets/6cddecdf-2048-4a7c-9ad4-5bd9b44708e3" />

Descripción de los modelos preentrenados utilizados
MODELO 1
Modelo de detección de incendios y humo en tiempo real basado en YOLOv26 (Ultralytics). Alcanza un 94,9 % de mAP@50 en tareas de detección de incendios y humo.
Este modelo detecta fuego, humo e indicadores relacionados con incendios en imágenes y vídeos. Está basado en la arquitectura YOLOv26-S y entrenado con 8939 imágenes anotadas.
Clases: Fuego - llamas activas, humo - columnas de humo, otros - Indicadores de incendio relacionados
Nombre del repositorio: "SalahALHaismawi/yolov26-fire-detection"
Link: https://huggingface.co/SalahALHaismawi/yolov26-fire-detection
MODELO 2
Modelo Detector de incendios y humo (ajuste fino D-Fire)
YOLOv8n se ha optimizado con el conjunto de datos D-Fire para la detección de humo y fuego en imágenes.
Clases:0- Humo,1- fuego
Nombre del repositorio:"rabahdev/fire-smoke-yolov8n"
Link: https://huggingface.co/rabahdev/fire-smoke-yolov8n




MODELO 3
Fuego y humo tempranos (YOLOv8)
Un detector YOLOv8n optimizado para incendios domésticos y humo en sus primeras etapas: escenarios de cocina, electricidad y cigarrillos. Forma parte de la colección Model Garden de modelos de visión artificial optimizados.
Clases: fire, smoke.
Nombre del repositorio: "Farhatullah0066/yolov8n-fire-smoke-detection"
Link: https://huggingface.co/mfranzon/fire-smoke-yolov8



Resultados obtenidos
<img width="972" height="331" alt="image" src="https://github.com/user-attachments/assets/201af261-98b4-4b69-a52e-0573e9b2e795" />





Interpretación de resultados.
Modelo 1: Presenta un rendimiento muy bajo. Su recall de 7.21% indica que recupera solo una pequeña proporción de los objetos anotados

Modelo 2: Obtiene el mejor recall, el mayor mAP@50 y el mayor mAP@50–95. También tiene un tiempo de inferencia bajo. Es el mejor candidato inicial para continuar las pruebas.

Modelo 3: Consigue la mayor precisión global, por un margen pequeño frente al Modelo 2, y una inferencia ligeramente más rápida. Sin embargo, su recall es menor, por lo que deja sin detectar más objetos.

Conclusion:

El Modelo 2 se recomienda como el modelo con mayor potencial para continuar el desarrollo del proyecto, debido a que presenta el mejor equilibrio entre desempeño de detección, eficiencia computacional y velocidad de procesamiento.
En la evaluación realizada sobre 1,807 imágenes y 4,196 objetos anotados, el Modelo 2 obtuvo una precisión de 46.44%, un recall de 40.82%, un mAP@50 de 33.59% y un mAP@50-95 de 15.97%. Estos resultados fueron superiores a los del Modelo 3 en recall y en ambas métricas de mAP, mientras que el Modelo 1 presentó un desempeño considerablemente inferior.
Presentó un tiempo de inferencia de aproximadamente 4.1 ms por imagen, lo que permite considerarlo adecuado para aplicaciones de análisis de video en tiempo cercano al real y facilita el procesamiento de múltiples fuentes de video.




