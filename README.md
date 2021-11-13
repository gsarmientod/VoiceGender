# Voice Gender 
## Descripción del problema  
El problema abordado tiene como punto de partida el DataSet “voice”, el cual se puede descargar desde el siguiente enlace https://www.kaggle.com/primaryobjects/voicegender. El cual está compuesto por 3.168 muestras de voz de diferentes personas.

El objetivo principal, es desarrollar un modelo de machine learning, que permita identificar si la voz es masculina o femenina.

Las muestras ya han sido pre procesadas mediante la función “specprop” de R,  la cual se puede encontrar documentación en el siguiente enlace https://www.rdocumentation.org/packages/seewave/versions/2.1.8/topics/specprop.

El DataSet cuenta con 21 features, varias de las cuales son creadas por la función “specprop”, entre las que se encuentra datos de frecuencia, entropía espectral, modo de frecuencia, entre otros.

## Procedimientos  
El modelo objetivo, consiste en un modelo de clasificación, para identificar dos clases, masculino y femenino, de acuerdo a las características técnicas de la muestra de voz (frecuencia por ejemplo).  

Dentro de los algoritmos de clasificación utilizados, se encuentran:  
* Regresión logística sin regularización.
* Regresión logística con regularización L1.
* Linear Discriminant Analysis.
* Quadratic Discriminant Analysis.
* KNN.
* Redes neuronales MLP.
* Naive Bayes.
* Random Forest.
* Bagging Classifier.
* Gradient Boosting.
* SVM con kernel lineal.
* SVM con kernel rbf.

Se realizó la reducción de features mediante PCA de 21 a 10 features.

Dentro de la construcción de cada uno de los modelos se usó la función accuracy_score, proporcionada por el módulo sklearn para ir evaluando el accuracy de cada uno de ellos y a su vez se creó una versión de predicción de cada modelo para poder realizar una comparativa al final del ejercicio que permitiera realizar la selección del modelo final.

Con varios de los algoritmos de clasificación utilizados, se realizó una exploración de los mejores hiper parámetros, haciendo uso GridSearchCV  dentro de cada modelo y a partir de dichos resultados, se construyeron versiones de cada uno de ellos.  

## Resultados  
Todos los modelos obtuvieron una precisión por encima del 90%, incluso la regresión logística con regularización.

El modelo que tuvo el menor rmse, fue el SVM con kernel rbf, con una ponderación de 0.14, alcanzando un Accuracy del 98% aproximadamente.  

Se exportó el modelo bajo el nombre “model_GRV.pkl”, el cual quedó en disposición para uso a futuro.  

## Conclusiones  
Para este caso, la mayoría de los modelos arrojaron una precisión alta. No se aprecia una diferencia significativa entre los resultados de cada uno de los modelos.

La variabilidad de hiperparametros en algunos de los modelos, tampoco arrojaron valores diferenciales entre cada una de las ejecuciones, con  lo cual si bien se seleccionó el modelo basado en el algoritmo SVM con kernel rbf como el modelo definitivo para el problema de clasificación, bien se puede usar cualquiera de los otros algoritmos utilizados.

Dadas las diferencias cerradas en cada uno de los modelos, se optaría por usar el más simple, pudiéndose usar como alternativa el modelo basado en regresión logística, dada su sencilla implementación, poco tiempo de ejecución y carencia de variabilidad de hiper parámetros para llegar a tener un buen desempeño.

Por otro lado, una alta precisión en la predicción de todos los modelos, bien nos puede dar a entender que existen características muy marcadas que permiten una fácil separación de las clases o bien estamos frente un problema de overfitting en todos los modelos. Aun así, llama la atención que incluso la regresión logística con regularización arroja unos resultados de alta precisión en sus predicciones con el conjunto de datos de test.


