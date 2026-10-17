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
anchoColumna: tamaño ancho página - márgenes - medianil / n° columnas

y las columnas se repiten la cantidad de columnas escogidas dentro del área total, incluyendo el valor de los
medianiles, el valor del cálculo de su ancho

### con medianiles
los medianiles son el espacio que hay entre cada columa dentro del área total
los medianiles son 1 menos que el total de columnas

por lo tanto, ante el cálculo del ancoColumna, el área que ocupan es su valor dinámico alterado por el 
total de columnas - 1
o sea:
```
(x * totalColumnas - 1)
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

## links de referencia hasta el momento 
[tipografía y código](https://thecodingtrain.com/tracks/p5js-2.0/p5js-2.0/typography?utm_source=chatgpt.com)

[workshop abierto de tipografía generativa multinivel](https://github.com/spacetypeco/generative-typography-SP22/tree/main)
