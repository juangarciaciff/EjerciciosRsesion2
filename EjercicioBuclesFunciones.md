# Prácticas de R y RStudio
- Ejercicio: **Bucles y funciones**
- Autor: **Juan Antonio García Cuevas**
- Fecha: 07/06/2016

#### Cargar el ﬁchero test en R.
```
    datos <- read.table("C:\\MASTER BIG DATA - CIFF\\HERRAMIENTAS\\R\\test.data", header = F)
    head(datos)
```
```
                V1
    1  0.110891375
    2 -0.301249877
    3 -0.433629030
    4 -0.141848265
    5  0.429285398
    6 -0.003484776
```

#### Escribir una función myMean que calcule la media de un vector x que se le pasa como argumento utilizando un bucle for. La función tiene que devolver el valor de la media. 
```
    myMean <- function(vector) {
      if(!is.numeric(vector)) {
        cat("Error (no es un vector)", "\n")
        return (NA)
      }
  
      suma <- 0;
      for(i in vector) {
        suma <- suma + i
      }
      suma / length(vector)
    }

    myMean(c(1:100000))

```
```
    [1] 50000.5

```

#### Aplicar la función a los datos del ﬁchero test y comprobar que la función es correcta comparando el resultado con la función mean(). 
```
    mean(datos[,1])
```
```
    [1] -0.006254914
```

```
    myMean(datos[,1])
```
```
    [1] -0.006254914
```

#### Escribir una función difTiempos que tenga como argumento un entero n, genere el vector 1, ..., n y devuelta la diferencia del tiempo de ejecución entre myMean y mean. La función también tiene que comprobar que n es positivo, en caso contrario devolverá el valor 0. 
```
    difTiempos <- function(n) {
      if (n < 1) {
        0
      } else {
        v = c(1:n)
        t1 <- system.time(mean(v))[3]
        t2 <- system.time(myMean(v))[3]
        t2 - t1
      }
    }

    difTiempos(5000000)
```
```
    elapsed 
       0.34 
       3.83 
```

#### Llamar a difTiempos para distintos valores de n (105, 106, 107, ...) y ver como evoluciona la diferencia de tiempos.
```
    vector <- seq(length=5, from=1000000, by=1000000)
    vector
    for(item in vector) {
      print(difTiempos(item))
    }
```
```
    elapsed 
       0.81 
    elapsed 
       1.66 
    elapsed 
       2.12 
    elapsed 
       3.04 
    elapsed 
       3.88 
```

