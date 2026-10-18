# exploracion-editorial-codigo
comprensión de construcción de retículas, definicón y uso de parámetros para composición editorial a través de código

#### 17 oct

## área total de trabajo
es el espacio dentro de los márgenes de la página
su ancho es el área por donde se *esparcen* las columnas

por lo tanto para el cálculo del ancho de las columnas, primero hay que determinar ese valor
```
// ocupa el ancho del canvas total 
tamañoAnchoPágina: width - márgenes * 2
```
lo mismo sucede para el largo y si queremos hacer una grilla dinámica que se adapte a los
diversos formatos en los que se puede diseñar, entonces trabajar en un rectángulo que parte desde
la coordenada que determine el valor de los márgenes y que tiene un máximo de alto y ancho
que contempla el total del área menos el valor de los márgenes 

```
  rect(
    layout.margin,
    layout.margin,
    width - 2 * layout.margin,
    height - 2 * layout.margin
  );
```

## una grilla
una grilla permite descomponer un espacio en distintas áreas para una composición consistente

se compone de columnas, medianiles y márgenes ubicados en un área tótal.

### y sus columnas
las columnas construyen áreas proporcionales dentro del **ancho** área total
su tamaño depende del
* ancho área total
* márgenes
* medianiles

su ancho puede expresar como:
```
anchoColumna: tamaño ancho página - márgenes - medianil / n° columnas
```

y las columnas se repiten la cantidad de columnas escogidas dentro del área total, incluyendo el valor de los
medianiles, el valor del cálculo de su ancho

### con medianiles
los medianiles son el espacio que hay entre cada columa dentro del área total
los medianiles son 1 menos que el total de columnas

por lo tanto, ante el cálculo del ancoColumna, el área que ocupan es su valor dinámico alterado por el 
total de columnas - 1
o sea:
```
areaTotalMedianil = (medianil * totalColumnas - 1)
```

y entonces:
```
anchoColumna = (tamañoAnchoPágina - márgenes - (totalColumnas - 1) * medianil)
```

### ancho del área total
es el espacio dentro de los márgenes laterales de la página
es el área por donde se *esparcen* las columnas

por lo tanto para el cálculo del ancho de las columnas, primero hay que determinar ese valor
```
// ocupa el ancho del canvas total 
tamañoAnchoPágina: width - márgenes * 2
```
y entonces, com se menciona anteriormente 
```
anchoColumna: tamañoAnchoPágina - márgenes - areaTotalMedianil / n° columnas
```

#### 18 oct

### nuevas preguntas
1. cómo automatizar la ubicación en x según las columnas del archivo?
2. cómo automatizar ubicación y? indicar ubicación del mouse
3. establecer distancias, referencia padding de figma
4. puedo hacer este código una función reutilzable en otros sketch?

### una vez que sabes el ancho de las columnas
cuando el ancho de las columnas es dinámico con los parámetros y formatos de trabajo establecidos
podemos identificar dónde empieza una y termina otra dentro de la ubicaciónX a partir de un array

```
function columnX(index) {
  return layout.margen +
    index * (anchoColumna() + layout.medianil);
}
```
que contempla **márgenes, ancho de la columna y medianil** en su cálculo

con esto podemos comenzar a ocupar las columnas como referencia de ubicación en X

### área total
antes hablamos del [ancho del área total](#ancho-del-área-total) . ahora contemplaremos largo y ancho
esta es el área de trabajo dentro de los márgenes y forma un rectángulo que comienza en el vértice demarcado por los márgenes superiores y lat izq, y termina en el vértice que marca el valor del margen inferior con el lat derecho.

si todos los márgenes son igual, entonces se puede interpretar así:
```
 noFill();
  stroke(230, 75, 90, 160);
  rect(
    layout.margin,
    layout.margin,
    width - 2 * layout.margin,
    height - 2 * layout.margin
  );
```


## links de referencia hasta el momento 
[tipografía y código](https://thecodingtrain.com/tracks/p5js-2.0/p5js-2.0/typography?utm_source=chatgpt.com)

[workshop abierto de tipografía generativa multinivel](https://github.com/spacetypeco/generative-typography-SP22/tree/main)
