# Luismi Bot

## Descripción

Este proyecto consiste en un modelo de una **RNN** para la generación de texto, entrenado con las canciones del más grande artista de todos los tiempos: **Luis Miguel**.

![El Sol de México](https://www.telemadrid.es/2020/06/23/programas/huellas/Luis-Miguel-promesa-convertida-estrella_2243485657_7781616_1300x731.jpg)

## Dataset

El dataset consiste en un archivo **CSV**, producto de un web scraping a la página de [Letras.com](https://www.letras.com/luis-miguel/), con las todas las canciones del **Sol de México**.

## Modelo

El modelo consiste en una **RNN** con dos capas de **GRU** y una capa de **tiempo distribuido**, con una capa **densa** de salida con una neurona.

## Entrenamiento

El modelo se entrena con un optimizador **Adam** y una función de pérdida de **entropía cruzada categórica**.

## Resultados

El modelo alcanzó a tener un loss de tan solo **1.7558** durante el último epoch de entrenamiento, el cual no es muy bueno, mas sin embargo, el modelo es capaz de generar texto con una coherencia aceptable si ajustamos la temperatura de la predicción.

Por ejemplo si le damos una temperatura de **0.1** al modelo con la palabra **amor**, este es capaz de generar texto como el siguiente que incluye **cuando calienta el sol** (lo cual es parte de una canción real de Luis Miguel):

```python
print(complete_text("amor", n_chars=500, temperature=0.1))
```

```
amor de tu piel
se que se si te siento y el sol amor
el sol como el sol a de tu pelo y yo se tu pero y yo se tu pelo yo se tu pero yo se tu pensar
en la vida se a tu piel
se como el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol corazon"
"si te siento y el sol al corazon"
"si te siento y el sol como el sol
cuando calienta el sol
cuando calienta el sol
cuando calienta el sol
cuando ca
```

Inclusive se hicieron algunas otras pruebas con distintas palabras, y el modelo es capaz de generar texto con una coherencia aceptable. Estas se pueden ver dentro del **notebook** de entrenamiento.

## Conclusiones

El modelo no es muy bueno, pero es capaz de generar texto con una coherencia aceptable si ajustamos la temperatura de la predicción. En este caso, se estima que el valor del loss es tan alto debido a que el dataset es muy pequeño, y no se le puede pedir mucho a un modelo con tan pocos datos, que en este caso es toda la discografía de **Luis Miguel** de aproximaadamente **278** canciones.

Fuera del contexto, tambien se habia entrenado el mismo modelo con las canciones de **Bad Bunny**, donde el modelo obtuvo un loss similar, pero con una coherencia mucho peor, principalmente porque las canciones de **Bad Bunny** son muy cortas y no tienen mucho sentido, por lo que el modelo no es capaz de generar texto coherente.