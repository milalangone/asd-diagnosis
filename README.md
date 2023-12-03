# ASD diagnosis with Machine Learning

Desarrollo de un algoritmo que, a partir de determinadas características extraídas de la señal de un EEG, permite identificar si este corresponde a un paciente con Trastorno del Espectro Autista o no. Se trabaja con la base de datos provista por [(Dickinson, Jeste and Milne, 2022)](https://doi.org/10.1016/j.cortex.2021.09.022). En ella, encontramos 56 [EEGs (link a base de datos)](https://drive.google.com/drive/folders/1B6WPMtwgXMk6FHE6pvimm81ZHwLYCpCQ): 28 de pacientes diagnosticados con el trastorno y 28 sin. Los EEGs fueron medidos con 64 electrodos siguiendo las normativas indicadas por el sistema "BioSemi Active Two System" y el "Standard 1020".

Las características utilizadas fueron:

* Variaciones en el pico de frecuencia alfa (PAF)
* Espectro de frecuencias relativo de cada banda (alpha, beta, gamma, delta, theta).
* Proporción relativa de la banda alpha respecto a las otras (U-shape)
* Proporción absoluta entre las bandas alpha y delta

Las variaciones que se observan de un EEG con ASD con respecto a otro sin ASD, son las que permiten la clasificación de los EEGs a partir del uso de distintas técnicas de *Machine Learning*.

Se utilizaron y compararon *Support Vector Machine*, *K-nearest neighbor* y *Random Forest*. Los resultados obtenidos con cada modelo son:

Modelo|Efectividad [%]
------|--------------
SVM   | 71
K-NN  | 65
RF    | 36
DT    | 41

Cabe destacar que para los resultados se tienen en consideración tanto la precisión como la sensibilidad, buscando que el modelo sea equilibrado. De esta manera, nos aseguramos que los valores reflejen resultados precisos, con la menor cantidad de falsos negativos y positivos.

El trabajo presenta algunas limitaciones que deben ser tenidas en consideración en caso de querer mejorar el algortimo desarrollado. En primer lugar, la cantidad de muestras utilizadas (n = 56) es muy baja. Con un mayor n se pueden tener tres grupos para analizar: uno de entrenamiento, otro de validación y otro de prueba.

Por otro lado, tampoco se realizó una distinción por edad en el momento de analizar los EEGs: si bien la media de edad era de 30 años, el rango de edad de los pacientes es muy amplia (18 - 67). Entonces, algunos cambios vinculados con las variaciones de PSD podrían estar relacionados con la edad del paciente y no con su diagnóstico. Esto podría verse reflejado, por ejemplo, en el hecho de que en SVM tenemos un alto porcentaje de falsos positivos (ver matriz de confusión: 38%).
