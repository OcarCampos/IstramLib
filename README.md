# Librería complementaria ISTRAM Chile


ISTRAM es una aplicación para el diseño de proyectos de ingeniería civil,
especializado en obras lineales como rutas, calles, carreteras, líneas de tren,
túneles, líneas de tuberías industriales, etc. 

Su potencia de cálculo y la concepción global del proyecto destacan por sobre otros
softwares de diseño de obras lineales.

Este repositorio recopila los archivos de librería que no se encuentran presentes en
la librería oficial de ISTRAM para Chile (lib_cl), pero que son indispensables para 
la correcta generación de proyectos siguiendo las normativas de Chile según el
[Manual de Carreteras](https://mc.mop.gob.cl/)  y según lo expuesto por el 
[Ministerio de Transporte de Chile](https://www.conaset.cl/repositorio-senales-de-transito/). 

## Librerías

Los objetos gráficos de ISTRAM (líneas, símbolos, textos y células) tienen declarado
en los ficheros .edm su tipo asociado, pero no la representación correspondiente. 

Esta representación está recogida en la LIBRERÍA que no es más que una carpeta que 
contiene un conjunto de ficheros, cada uno de los cuales declara un tipo.

Existen así la serie de los L# para representar las líneas, los S# para los puntos, 
los R# para los textos y los C# para las células, donde # es un número de 0 a 9999 
excepto para los rótulos, cuyo número está limitado a 999.

Estos ficheros describen las características y comandos necesarios para ser ejecutados 
ligados a un símbolo, una línea o un texto y contienen toda la representación gráfica 
que se ejecutará cada vez que un objeto de su tipo esté presente en el dibujo.

En la librería existen también ficheros de configuración que afectan al estado o al 
comportamiento de ISTRAM en diversas operaciones, como pueden ser tablas de normativa, 
modos de dibujo de ejes de obra lineal, ficheros de configuración, etc.

ISTRAM contempla el manejo de una librería "distribuida" o, si se prefiere, varias librerías 
según una escala jerárquica de búsqueda. Así, durante el arranque se establecen por defecto 
las siguientes rutas o “paths” para cada librería:

1. ./lib/ 
2. /ISPOL/libuser/
3. /ISPOL/lib/

La primera es la librería primaria, local o de proyecto, y existe una para cada carpeta de proyecto.

La segunda es la librería secundaria, global o general del usuario. Generalmente en esta se configura la librería
específica por país para ajustarse a la normativa local.

La última es la librería base. Acompaña a cada nueva revisión de ISTRAM y satisface todas las demandas 
de simbología que el programa maneja automáticamente.

ISTRAM buscará los objetos de librería que precise en la librería primaria *./lib*, lo que no encuentre ahí 
lo irá a buscar a la secundaria o general de usuario */ISPOL/libuser/*, y por último busca en */ISPOL/lib* 
(librería terciaria o de base).

La librería local y la de usuario pueden ser carpetas vacías o incluso no existir. No obstante no es 
aconsejable usar ISTRAM sin tener al menos una librería secundaria o de usuario, para que recoja las 
modificaciones propias sin afectar a la de base, y mejor aún, una librería local del proyecto que permita 
modificar localmente los objetos de librería que se deseen sin afectar a los otros proyectos.

## Librería Oficial Chile

La librería oficial de ISTRAM para Chile (lib_cl) se encuentra en la carpeta 

    C:\Ispol\lib_ext 

comprimida en un archivo .zip. Este archivo zip debe descomprimirse a la carpeta 

    C:\Ispol\lib_ext\lib_cl 
    
y luego se debe configurar en el programa la librería segunda de ISTRAM para acceder a esta carpeta.

![Configuración librería segunda](/assets/lib_config.png)

## Librería complementaria Chile

Sin embargo, la librería oficial de ISTRAM para Chile (lib_cl) no contiene todas las señales (verticales y de piso),
ni las configuraciones para obras de arte, o las demarcaciones de piso, tachas, y otras configuraciones propias
de los diseños viales en Chile. Dado lo anterior, se genera este repositorio con las finalidad de complementar la
librería oficial de ISTRAM para Chile (lib_cl) y así contar con una librería completa para el diseño de obras
lineales chilenas.

# Uso

## Configuración Global

La configuración global complementa y sobre escribe elementos presentes en la librería oficial de ISTRAM para Chile (lib_cl).
Para configurar globalmente se debe:

1. Configurar la librería oficial de chile en la carpeta *C:\Ispol\lib_ext\lib_cl*
2. Descargar los archivos de este repositorio.
3. Copiar todos los archivos desde la carpeta *lib_cl_comp* a la carpeta *C:\Ispol\lib_ext\lib_cl*. 
4. Reemplazar los archivos que ya existen en la librería oficial.
5. Recargar las librerías desde ISTRAM para reflejar los cambios realizados.

## Configuración por Proyecto

La configuración por proyecto complementa la librería oficial de ISTRAM para Chile no alterando su contenido, sino que, encapsulando el contenido en la carpeta *.\lib* del proyecto. Se debe considerar que esto se debe realizar para cada proyecto
que se genere dado que es una configuración local y proyecto específica.

1. Configurar la librería oficial de chile en la carpeta *C:\Ispol\lib_ext\lib_cl*
2. Descargar los archivos de este repositorio.
3. Copiar todos los archivos desde la carpeta *lib_cl_comp* a la carpeta *.\lib* del proyecto. 
4. Reemplazar los archivos que ya existen en la carpeta *.\lib* si se requiriera.
5. Recargar las librerías desde ISTRAM para reflejar los cambios realizados.

## Recarga de librerías

![Recarga de librerías](/assets/reload_libraries.png)

# Contenido

Se detallana a continuación los elementos de la librería complementaria:

## Demarcaciones lineales

- L3157: Linea doble continua, LCD/10/12 para TR600.
- L3173: Línea segmentada de separación, LSS/15/300/500 para TB800.
- L3174: Línea continua LC/15. 
- S3172: símbolo para línea continua 15 cm ancho
- S3173: símbolo para línea continua 10 cm ancho
- S3176: símbolo para línea segmentada Chile (Línea 15 cm ancho 3 metros largo)

## Barreras:

 Las barreras H1 por defecto del software son L3250, L3251, L3252 y L3253. Las agregadas
 a esta librería complementaria son:

- L3254: Barrera H3 Izquierda (símbolo plano s265)
- L3255: Barrera H3 Derecha  (símbolo plano s265)

## Demarcaciones de piso

- S3184: símbolo RR-1 máxima velocidad 40 kms/h para pista vel < 60 kms/h
- S3185: símbolo RR-1 máxima velocidad 50 kms/h para pista vel < 60 kms/h
- S3186: símbolo RR-1 máxima velocidad 60 kms/h para pista vel < 60 kms/h
- S3187: símbolo RR-1 máxima velocidad 70 kms/h para pista vel > 60 kms/h
- S3150: flecha recta > 60kms/h
- S3151: flecha recta < 60kms/h
- S3170: flecha cambio pista hacia Derecha
- S3171: flecha cambio pista hacia Izquierda
- C3576: Tacha Blanca (debe acompañarse con archivo ifc). 
- C3577: Tacha Roja (debe acompañarse con archivo ifc).
- C3578: Tacha Amarilla (debe acompañarse con archivo ifc).

## Señales verticales

- C971: DC-5a (usa S3695 como poste de 1.3m de lib principal)
- C981: DC-5b (usa S3695 como poste de 1.3m de lib principal)
- C3250: PG-1a
- C3251: PG-1b
- C3252: PG-2a (sin placa inferior)
- C3249: PG-2a (con placa inferior)
- C3253: PG-2b (sin placa inferior)
- C3248: PG-2b (con placa inferior)
- C3254: PG-3a
- C3255: PG-3b
- C3256: PG-4a
- C3257: PG-4b
- C3258: PG-5a
- C3259: PG-5b
- C3260: PG-6a
- C3261: PG-6b
- C3262: PG-7a (sin placa inferior)
- C3263: PG-7b (sin placa inferior)
- C3247: PG-7b (con placa inferior)
- C3264: PG-7c (sin placa inferior)
- C3265: PG-7d (sin placa inferior)
- C3246: PG-7d (con placa inferior)
- C3266: PG-8a
- C3267: PG-8b
- C3271: PF-1b
- C3272: PF-1c
- C3275: PF-3b
- C3276: PF-3c
- C3358: RR-1 VEL. VARIABLE TEXTO
- C3336: RPO-3
- C3367: RR-9
- C3374: RO-2a
- C3375: RO-2b
- C3376: RO-3a
- C3378: RO-3c
- C3379: RO-4
- C3380: RO-5
- C3416: DC-7a
- C3417: DC-7b
- C3418: IE-1
- C3419: IPR 1 - Verde - Grande.
- C3437: ID-2 Señal de posición - km y m. (Hectómetro)
- C3438: ID-2 Señal de posición - Ruta y Km. (Kilómetro)
- C3514: IT-38
- C3701: perfil doble para señalética

## Símbolos/Etiquetas/Textos 2D

Los elementos a continuación son utilizados exclusivamente en la visualización 2D del software,
ya sea para la visualización de los corredores o la generación de planos. Se actualizaron los colores
tanto para visualización PDF como impresión digital para acercarse a lo descrito en manual de carreteras. 
Los nombres son solo descriptivos ya que la mayoría son realmente etiquetas para visualización 2D.

- S6 : Vertice
- S127 : Texto distancia eje y cota
- S128 : Ref.
- S130 : DM
- S131 : Bombeo.
- S132 : Largo
- S133 : Curva convexa.
- S134 : Curva concava.
- S135 : Etiqueta.
- S136 : Etiqueta
- S137 : Vertice
- S138 : DM
- S139 : Cota.
- S141 : Curva.
- S142 : PC
- S143 : FC
- S144 : Peralte.
- S145 : Alineación.
- S146 : Distancia curvatura.
- S186 : Viñeta guitarra.
- S265 : Símbolo para barrera H3 en plano.
- S393 : Data decimal.
- S398 : Data decimal.
- S438 : Símbolo redondo valores geométricos ruta.
- S481 : Etiqueta	
- S482 : Circular.
- S497 : Vertice.
- S498 : vertice
- S536 : Peralte.
- S557 : DM
- S559 : Data decimal.
- S560 : Cota terreno
- S563 : Etiqueta
- S567 : Alineacion circular.
- S572 : Recta.
- S573 : R=1
- S579 : Cota.
- S580 : Etiqueta.
- S594 : Peralte.
- S595 : Peralte.
- S752 : T circular.
- S673 : PC-DM
- S674 : FC-DM
- S900 : Cotas rasantes.
- S901 : Cotas subrasantes.
- S987 : Alfa.
- R0 : Texto.
- R24 : Texto.
- L32 : Líneas guitarra.
- L40 : Líneas guitarra.
- L60 : Líneas guitarra.
- L61 : Líneas guitarra.
- L62 : Líneas guitarra.
- L64 : Líneas guitarra.
- L66 : Líneas guitarra.
- L308 : Líneas guitarra.



