# Tutorial de GNSS Solutions™ para Agrimensores

## Introducción

Existe un vacío de documentación accesible y didáctica para los profesionales de la agrimensura de una franja etaria en el tema del procesamiento de datos con software y sobre algunas cuestiones técnicas y conceptuales, como la georreferenciación, los sistemas y marcos de referencia, la conversión y transformación de coordenadas.
El humildísimo objetivo de este tutorial es dar algunas recomendaciones que pueden ser útiles, basadas en la experiencia del autor, para ordenar los pasos y los datos (archivos) que generalmente son necesarios y suficientes para un trabajo de relevamiento GNSS de mediana complejidad, utilizando el software _GNSS Solutions™_ de la empresa _ashtech™_.

## Recomendaciones

- Tener instalada la versión 3.71.1 (o superior) del software, que se puede descargar de [aquí](ftp://ftp.ashtech.com/Land%20Survey/GNSS%20Solutions/software/GNSS%20Solutions%203.71.1/GNSS%20Solutions%203.71.zip).
- Se recomienda fuertemente ahondar en conceptos y no quedarse simplemente en aprender mecánicamente los pasos que aquí se sugieren. Si bien muchas veces puede que alcancen a cubrir lo necesario, es seguro que muchísimas otras cualquier pequeño cambio de las condiciones aquí planteadas pueden generar una traba insoslayable si no se comprende con alguna profundidad lo que se está haciendo.
- Para cubrir aspectos conceptuales existe abundante bibliografía. Se recomienda aquí el libro [GPS, Posicionamiento satelital](http://www.fceia.unr.edu.ar/gps/ep/libro_gps.pdf) que se puede conseguir en el sitio del [Grupo de Geodesia Satelital Rosario](http://www.fceia.unr.edu.ar/gps/) (GGSR) de la UNR, en la sección Publicaciones.

## Adjuntos con este tutorial

Se provee una plantilla para cada trabajo con la estructura de carpetas donde ordenar los archivos de observaciones, cad, etc. La misma se muestra a continuación. Es una buena costumbre copiarla en la carpeta de proyectos del GNSS Solutions, generalmente es

    C:\Mis Proyectos

El archivo _leer.txt_ tiene una explicación de para qué se destina cada carpeta.

    _plantilla\
      cad\
      coord\
      mdt\
      observ\
        base\
        ep\
        remoto\
        rinex\
      leer.txt

## Relevamiento georreferenciado

### Georreferenciación de la base de un relevamiento GNSS

1. Inicie el programa GNSS Solutions.

2. Cree un proyecto con un nombre conveniente para designar el trabajo.

3. En este ejemplo usaremos el nombre _Trabajo_.

4. Paso siguiente le pedirá los archivos de observaciones. Deje el programa a la espera, antes deberá cumplir otros pasos que se explican a continuación.

5. Copie la estructura de carpetas de la plantilla dentro de la carpeta del nuevo proyecto _Trabajo_. Deberá quedar así:

        C:\Mis Proyectos\Trabajo\
          cad\
          coord\
          mdt\
          observ\
            base\
            ep\
            remoto\
            rinex\
          leer.txt

6. Descargue los archivos del receptor base y guarde una copia de ellos en _Trabajo\observ\base_.

7. Descargue los archivos en formato RINEX de la Estación Permanente más cercana o conveniente, por ejemplo UNRO y/o SBAL y/o IGM1 y guarde una copia de los mismos en _Trabajo\observ\ep_.

8. Vuelva al GNSS Solutions donde le pedía los archivos de observaciones y agregue al proyecto los archivos de observaciones de la base y de la o las EP que ya copió en _Trabajo\observ\base_ y en _Trabajo\observ\ep_.

9. Defina como _Punto de control_ a la o las EP y corrija sus coordenadas geodésicas según el Marco de referencia adecuado para la georreferenciación (que puede ser PosGAr 2007). Tenga la precaución de introducir la altura de la antena correspondiente a la BASE del relevamiento.

    > Sirve tener presente que si la base del relevamiento no será usada nuevamente, es decir, no quedó materializada con mojón o estaca o cualquier marca, entonces no es necesario ingresar una altura distinta de cero, esto sólo se utiliza cuando se quiere indicar que el punto de base debe tomarse desde el suelo (mojón o estaca). Pero si el punto no será utilizado posteriormente, entonces es una buena costumbre dejar la altura de la antena de la base en 0.000. Esto significa que el destino (u origen) de los vectores calculados hasta (o desde) la base, serán hasta (o desde) el centro de fase de la antena y no hasta (o desde) el piso.

10. Presione _Aceptar_ y a continuación:

    a. _Para aplicar y procesar líneas de base_ (si tiene sólo una EP como punto de control)
  
    b. _Para importar, procesar y ajustar_ (si tiene más de una EP como punto de control)
    
    > Puede presionar _Aceptar_ y luego _Para importar_ y luego reemplazar el _ítem a_ por la tecla __F5__ (que procesa las líneas base) y el _ítem b_, por la sucesión de teclas __F5__ primero y __F6__ luego (que ajusta la red).

11. Ya tiene los vectores procesados y, si tiene más de un punto de control, la red ajustada, lo que significa que la BASE del relevamiento quedó georreferenciada en el Marco de Referencia correspondiente a las coordenadas que haya elegido para las EP. __Copie las coordenadas Latitud, Longitud y Altura elipsóidica de la BASE__, las utilizará en el siguiente proceso, el de georreferenciación del relevamiento.

12. Una forma de verificar la calidad del relevamiento es a través de las solapas _Vectores_ y _Puntos_ y por medio de los distintos informes. Por ejemplo, es buena señal obtener soluciones fijas y confianzas horizontales y de altura dentro de las tolerancias (ver solapas _Vectores_ y _Puntos_).

13. Cierre el GNSS Solutions.

### Georreferenciación del relevamiento

1. Inicie el programa GNSS Solutions.

2. Cree un proyecto con un nombre conveniente para designar el trabajo. En este ejemplo usaremos el nombre _Trabajo2_.

3. Paso siguiente le pedirá los archivos de observaciones. Deje el programa a la espera, antes deberá cumplir otros pasos que se explican a continuación.

4. Copie la estructura de carpetas de la plantilla dentro de la carpeta del nuevo proyecto _Trabajo2_. Deberá quedar así:

        C:\Mis Proyectos\Trabajo2\
          cad\
          coord\
          mdt\
          observ\
            base\
            ep\
            remoto\
            rinex\
          leer.txt

5. Descargue los archivos de los receptores base y remoto y guarde una copia de ellos en _Trabajo\observ\base_ y _Trabajo\observ\remoto_.

6. Vuelva al GNSS Solutions donde le pedía los archivos de observaciones y agregue al proyecto los archivos de observaciones de la base y del remoto que ya copió en _Trabajo\observ\base_ y en _Trabajo\observ\remoto_.

7. Defina como _Punto de control_ a la BASE y corrija sus coordenadas geodésicas __según lo obtenido en el proceso de Georreferenciación de la Base__ (recuerde las coordenadas que copió en el proceso de georreferenciación de la BASE).

8. Presione _Aceptar_ y a continuación _Para aplicar y procesar líneas de base_ (dado que tiene un solo punto de control, la BASE).

9. Ya tiene los vectores procesados, lo que significa que el relevamiento quedó georreferenciada en el Marco de Referencia correspondiente a las coordenadas que haya elegido para las EP.

10. Una forma de verificar la calidad del relevamiento es a través de las solapas _Vectores_ y _Puntos_ y por medio de los distintos informes. Por ejemplo, es buena señal obtener soluciones fijas y confianzas horizontales y de altura dentro de las tolerancias (ver solapas _Vectores_ y _Puntos_).

## Relevamiento sin georreferenciación

1. Inicie el programa GNSS Solutions.

2. Cree un proyecto con un nombre conveniente para designar el trabajo. En este ejemplo usaremos el nombre _Trabajo_.

3. Paso siguiente le pedirá los archivos de observaciones. Deje el programa a la espera, antes deberá cumplir otros pasos que se explican a continuación.

4. Copie la estructura de carpetas de la plantilla dentro de la carpeta del nuevo proyecto _Trabajo_. Descargue los archivos de los receptores base y remoto y guarde una copia de ellos en _Trabajo\observ\base_ y _Trabajo\observ\remoto_.

5. Vuelva al GNSS Solutions donde le pedía los archivos de observaciones y agregue al proyecto los archivos de observaciones de la base y del remoto que ya copió en _Trabajo\observ\base_ y en _Trabajo\observ\remoto_.

6. Defina como _Punto de control_ a la BASE (no hace falta corregir sus coordenadas, aunque sí tener en cuenta la altura en el caso de que el punto se quiera volver a usar).

7. Presione _Aceptar_ y a continuación _Para aplicar y procesar líneas de base_ (dado que tiene un solo punto de control, la BASE).

8. Ya tiene los vectores procesados, lo que significa que el relevamiento quedó procesado.

9. Una forma de verificar la calidad del relevamiento es a través de las solapas _Vectores_ y _Puntos_ y por medio de los distintos informes. Por ejemplo, es buena señal obtener soluciones fijas y confianzas horizontales y de altura dentro de las tolerancias (ver solapas _Vectores_ y _Puntos_).

## Conversión de coordenadas de geodésicas a una proyección local

Este paso es necesario para poder _calcular_, por ejemplo, una mensura. Lo que se hace aquí, en definitiva, es llevar la nube de puntos relevados a un sistema XYZ _evitando la deformación_. Luego, si se requiere, se deberá hacer el proceso inverso para obtener las coordenadas geodésicas a partir de las _locales_.

1. Luego de haber procesado los datos del relevamiento, aún con el GNSS Solutions abierto, elija un punto del relevamiento que esté ubicado más o menos en el centro de la nube de puntos (puede ser la BASE del relevamiento o un punto no necesariamente relevado, ubicado aproximadamente en el centro de la nube de puntos).

2. Vaya a __Proyecto__ → __Editar opciones__ → en la solapa __Región__, en __Sistema de referencia espacial__, seleccione __\<Nuevo\>__.

3. Aguarde un instante, se abrirá una nueva ventana donde deberá seleccionar Definir un NUEVO sistema PROYECTADO (ESTE, NORTE, ALTURA).

4. Deje como Datum al elipsoide WGS84. Presione Siguiente.

5. Deje como Clase de proyección a Transverse_Mercator. Pero ponga como latitude_of_origin la latitud (aproximada) del punto que seleccionó en el paso 1, y como central_meridian la longitud (aproximada) del mismo punto. Deje los otros parámetros en 1, 0 y 0 si no comprende a qué se refieren. Presione Siguiente.

6. Ponga un nombre adecuado al Sistema (es importante recordarlo para la futura conversión).

## Exportación de la nube de puntos a un archivo DXF

Para __habilitar la exportación a DXF__ debe habilitar las funciones CAD en el menú __Herramientas → Preferencias__, en la solapa __General__ marcar __Mostrar funciones CAD__.

1. Seleccione los puntos que desea exportar en un DXF de la nube que se muestra en la _Vista de levantamiento_ (puede ir a __Ventana → Vista de levantamiento__).

2. Vaya a __Proyecto → Exportar datos geo. a un archivo__... (o directamente presione F8).

3. En la parte izquierda, en __Exportar__, seleccione __Características__ y en la parte derecha, en __Formato__, seleccione __Autocad DXF__. Presione _Aceptar_.

4. Se abre una venta de _Guardar como_, busque la carpeta _Trabajo\cad_, y tipée un nombre para el DXF. Listo, ya tiene la nube de puntos seleccionada en un DXF lista para abrir desde su programa favorito.

## Conversión de coordenadas de proyección local a geodésicas

Este paso es particularmente útil para luego del cálculo de la mensura, donde se tienen las coordenadas de los vértices del polígono resultante en el sistema de proyección local, pero aún no sus coordenadas geodésicas.

1. Inicie el GNSS Solutions.

2. Vaya a __Herramientas → Prueba conver__...

3. Seleccione de un lado, por ejemplo la izquierda, el sistema de coordenadas geodésicas WGS84, y del otro, el sistema local proyectado que haya guardado en su momento (recuerde paso 6 del proceso de Conversión de coordenadas de geodésicas a una proyección local).

4. Ponga del lado del sistema proyectado una por una las coordenadas Este y Norte calculadas en la mensura y presione el botón con la flecha adecuada, así obtendrá las coordenadas geodésicas correspondiente a cada punto (son las que deberá poner en la planilla de georreferenciación para entregar con el plano y el expediente).

## Pasaje de archivos de cualquier formato de Ashetch a RINEX

Este paso puede ser útil para el caso en que se deban entregar con el expediente cuando se requiere georreferenciación en el SCIT de Santa Fe. O para el caso en que se deba asegurar la posibilidad de procesar las observaciones con otros programas.

1. Iniciar el RINEX Converter. (Debe instalarlo con el mismo instalador del GNSS Solutions)

2. Presionar __Add__. Se abre una ventana para seleccionar los archivos. Elija los archivos de la Base, del Remoto y de la o las Estaciones Permanentes (que en su momento copió en __C:\Mis Proyectos\Trabajo\observ\base__ y en __Trabajo\observ\remoto__ y en __Trabajo\observ\ep__).

3. En dodne dice __Into__, seleccione _RINEX Raw Data Files version 2.11_.

    > A menos que comprenda en profundidad las diferencias entre los distintos formatos, con la versión 2.11 se asegurará el buen funcionamiento con casi cualquier software.

4. En __In folder__, seleccione como destino la carpeta _C:\Mis Proyectos\Trabajo\observ\rinex_.

5. Presione __Convert__. Listo, los archivos obtenidos pueden ser copiados a un CD para ser entregados junto al expediente. (Es recomendable, como verificación, realizar todo el procesamiento de nuevo con los archivos RINEX
obtenidos y ver que los resultados son los mismos o varían en cantidades despreciables.)

# Por hacer

- Plantilla para Memoria de georreferenciación (pedida por SCIT)
- Plantilla para Planilla de coordenadas (pedida por SCIT)
- Software de conversión masiva de coordenadas

# Licencia

Este documento se encuentra bajo una Licencia [Creative Commons](http://creativecommons.org/licenses/by-nc-sa/2.5/ar/). Usted es libre de compartir, copiar, distribuir, ejecutar y comunicar públicamente la obra, hacer obras derivadas.
