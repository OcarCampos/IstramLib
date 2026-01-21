# Librería complementaria ISTRAM Chile

## Índice

1. [Introducción](#introducción)
2. [Librerías](#librerías)
3. [Uso](#uso)
    1. [Configuración Global](#configuración-global)
    2. [Configuración por Proyecto](#configuración-por-proyecto)
    3. [Recarga de librerías](#recarga-de-librerías)
4. [Contenido](#contenido)
    1. [Demarcaciones lineales](#demarcaciones-lineales)
    2. [Barreras](#barreras)
    3. [Demarcaciones de piso](#demarcaciones-de-piso)
    4. [Señales verticales](#señales-verticales)
    5. [Símbolos, Etiquetas y Textos 2D](#símbolos-etiquetas-y-textos-2d)
    6. [Obras de Arte](#obras-de-arte)
    7. [Cunetas](#cunetas)
    8. [Soleras](#soleras)
    9. [Talud y Terraplen vectorial](#talud-y-terraplen-vectorial)
    10. [Planimetría](#planimetría)
    11. [Otros Archivos](#otros-archivos)

## Introducción

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

    .\lib\ 
    C:\Ispol\lib_ext\
    C:\Ispol\lib\

La primera es la librería primaria, local o de proyecto, y existe una para cada carpeta de proyecto.

La segunda es la librería secundaria, global o general del usuario. Generalmente en esta se configura la librería
específica por país para ajustarse a la normativa local.

La última es la librería base. Acompaña a cada nueva revisión de ISTRAM y satisface todas las demandas 
de simbología que el programa maneja automáticamente.

ISTRAM buscará los objetos de librería que precise en la librería primaria *.\lib*, lo que no encuentre ahí 
lo irá a buscar a la secundaria o general de usuario *\ISPOL\libuser\*, y por último busca en *\ISPOL\lib* 
(librería terciaria o de base).

La librería local y la de usuario pueden ser carpetas vacías o incluso no existir. No obstante no es 
aconsejable usar ISTRAM sin tener al menos una librería secundaria o de usuario, para que recoja las 
modificaciones propias sin afectar a la de base, y mejor aún, una librería local del proyecto que permita 
modificar localmente los objetos de librería que se deseen sin afectar a los otros proyectos.

### Librería Oficial Chile

La librería oficial de ISTRAM para Chile (lib_cl) se encuentra en la carpeta 

    C:\Ispol\lib_ext 

comprimida en un archivo .zip. Este archivo zip debe descomprimirse a la carpeta 

    C:\Ispol\lib_ext\lib_cl 
    
y luego se debe configurar en el programa la librería segunda de ISTRAM para acceder a esta carpeta.

![Configuración librería segunda](/assets/lib_config.png)

### Librería complementaria Chile

Sin embargo, la librería oficial de ISTRAM para Chile (lib_cl) no contiene todas las señales (verticales y de piso),
ni las configuraciones para obras de arte, o las demarcaciones de piso, tachas, y otras configuraciones propias
de los diseños viales en Chile. Dado lo anterior, se genera este repositorio con las finalidad de complementar la
librería oficial de ISTRAM para Chile (lib_cl) y así contar con una librería completa para el diseño de obras
lineales chilenas.

## Uso

### Configuración Global

La configuración global complementa y sobre escribe elementos presentes en la librería oficial de ISTRAM para Chile (lib_cl).
Para configurar globalmente se debe:

1. Configurar la librería oficial de chile en la carpeta *C:\Ispol\lib_ext\lib_cl*
2. Descargar los archivos de este repositorio.
3. Copiar todos los archivos desde la carpeta *lib_cl_comp* a la carpeta *C:\Ispol\lib_ext\lib_cl*. 
4. Reemplazar los archivos que ya existen en la librería oficial.
5. Recargar las librerías desde ISTRAM para reflejar los cambios realizados.

### Configuración por Proyecto

La configuración por proyecto complementa la librería oficial de ISTRAM para Chile no alterando su contenido, sino que, encapsulando el contenido en la carpeta *.\lib* del proyecto. Se debe considerar que esto se debe realizar para cada proyecto
que se genere dado que es una configuración local y proyecto específica.

1. Configurar la librería oficial de chile en la carpeta *C:\Ispol\lib_ext\lib_cl*
2. Descargar los archivos de este repositorio.
3. Copiar todos los archivos desde la carpeta *lib_cl_comp* a la carpeta *.\lib* del proyecto. 
4. Reemplazar los archivos que ya existen en la carpeta *.\lib* si se requiriera.
5. Recargar las librerías desde ISTRAM para reflejar los cambios realizados.

### Recarga de librerías

![Recarga de librerías](/assets/reload_libraries.png)

## Contenido

Se detallan a continuación los elementos de la librería complementaria:

### Demarcaciones lineales

- L3157: Línea doble continua, LCD/10/12 para TR600.
- L3173: Línea segmentada de separación, LSS/15/300/500 para TB800.
- L3174: Línea continua LC/15. 
- L3175: Línea segmentada de separación, LSS/15/300/500 con TB800.
- L3177: Cerco línea expropiación
- S3172: Símbolo para línea continua LC/15
- S3173: Símbolo para línea continua LC/10
- S3176: Símbolo para línea segmentada, LSS/15/300/500
- S3177: Símbolo para Cerco línea expropiación

- 21/01/2026: Se modifican líneas para que geometría se adapte a peralte.

![LineasTachas](/assets/LineasTachas.png)

### Barreras:

Las barreras H1 por defecto del software son L3250, L3251, L3252 y L3253. Las agregadas
a esta librería complementaria son:

- L3254: Barrera H3 Izquierda (símbolo plano s265)
- L3255: Barrera H3 Derecha  (símbolo plano s265)

- 21/01/2026: Se agregan terminaciones según normativa chilena (12 metros) para las barreras:
    - C3035: Terminación inicio barrera derecha.
    - C3036: Terminación fin barrera derecha.
    - C3037: Terminación inicio barrera izquierda.
    - C3038: Terminación fin barrera izquierda.

Las terminaciones de barrera deben configurarse según requerimiento.


![BarreraH3](/assets/BarreraH3.png)

### Demarcaciones de piso

- S3184: símbolo RR-1 máxima velocidad 40 kms\h para pista vel < 60 kms\h
- S3185: símbolo RR-1 máxima velocidad 50 kms\h para pista vel < 60 kms\h
- S3186: símbolo RR-1 máxima velocidad 60 kms\h para pista vel < 60 kms\h
- S3187: símbolo RR-1 máxima velocidad 70 kms\h para pista vel > 60 kms\h
- S3188: símbolo cruce peatonal de piso. Forma Diamante. Persona cruzando. Agregado 21/01/2026.
- S3150: flecha recta > 60kms\h
- S3151: flecha recta < 60kms\h
- S3170: flecha cambio pista hacia Derecha
- S3171: flecha cambio pista hacia Izquierda
- C3576: Tacha Blanca (debe acompañarse con archivo ifc). 
- C3577: Tacha Roja (debe acompañarse con archivo ifc).
- C3578: Tacha Amarilla (debe acompañarse con archivo ifc).
- C3579: Tachon Amarillo reflector rojo. Agregado 21/01/2026.

![SenalPiso](/assets/SenalPiso.png)

![SenalesPiso](/assets/SenalesPiso.png)

### Señales verticales

- C971: DC-5a (usa S3695 como poste de 1.3m de lib principal). Corregida 21/01/2026
- C972: DDD-1b Agregada 21/01/2026
- C981: DC-5b (usa S3695 como poste de 1.3m de lib principal). Corregida 21/01/2026
- C982: DDD-1a Agregada 21/01/2026
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
- C3336: RPO-3 Símbolo corregido 21/01/2026
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
- C3701: Perfil doble para señalética vertical doble perfil
- C9000: Señal inicio pista lenta con doble perfil.

![senalesverticales](/assets/senalesverticales.png)

![Hectometro](/assets/Hectometro.png)

![Kilometro](/assets/Kilometro.png)

### Símbolos, Etiquetas y Textos 2D

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

### Obras de Arte

ISTRAM incluye la configuración para el dibujo de obras de arte y algunas obras de arte que cumplen con la normativa
española, sin embargo, no incluye ejemplos de obras de arte para Chile. Por ello, se generaron archivos para las obras de
arte utilizadas en el proyecto Embalse Las Palmas y según lo especificado por manual de carreteras. 

Cabe señalar que las Obras de Arte que es posible generar a partir del software ISTRAM **NO CUMPLEN** a cabalidad con lo 
expuesto en manual de carreteras, quedando al debe en detalles estructurales que, dependiendo del NDI o LOD BIM que se deba 
trabajar según el proyecto, deberán desarrollarse con otro software de modelación para cumplir con el NDI o LOD BIM estipulado.

Entre los aspectos estructurales que ISTRAM **no contempla** para las obras de arte se encuentran:

- Pendientes en mampostería: ISTRAM no considera pendientes a 3 aguas para mamposterías de salida o de entrada. Esta viene definido
en Manual de Carreteras Chile.

![PendientesMamposteria](/assets/PendientesMamposteria.png)

- Quiebres en mampostería: ISTRAM no contempla la generación de quiebres en mampostería. Si bien esto no está contemplado
en Manual de Carreteras Chile, en el proyecto para el cual se generó este repositorio, existen obras de arte con esta configuración,
lo cual no fue posible replicar con ISTRAM.

![QuiebreMamposteria](/assets/QuiebreMamposteria.png)

- Imposta Inferior: ISTRAM no conntempla la generación del elemento estructural "imposta" inferior según detallan las imagenes. Al
igual que el caso anterior, esto viene definido en Manual de Carreteras Chile. ISTRAM si contempla la imposta superior.

![ImpostaInferior](/assets/ImpostaInferior.png)

- Emplantillado: ISTRAM no contempla la generación de emplantillados para la estructura completa de las obras de arte. 
Esto viene definido en Manual de Carreteras Chile.

![Emplantillado](/assets/Emplantillado.png)

- Zapatas Muros Ala: el manual de carreteras Chile contempla la generación de medias zapatas como fundación para los muros alas. Sin
embargo, ISTRAM no contempla la generación de zapatas específicas como se muestra en la imagen de la izquierda, sino que sólo es posible
lograr una configuración como muestra la imagen de la derecha.

![zapatas](/assets/zapatas.png)


Dejando claro lo anterior, se detalla el listado de obras de arte que incluye este repositorio:

- OA Cajón Simple HA 100x100
- OA Cajón Simple HA 120x120
- OA Cajón Simple HA 150x150
- OA Cajón Simple HA 165x145
- OA Cajón Simple HA 200x150

![OACajonSimple](/assets/OACajonSimple.png)

- OA Cajón Doble HA 120x120
- OA Cajón Doble HA 200x150

![OACajonDoble](/assets/OACajonDoble.png)

- OA Tubo de Hormigón Base Plana Diametro 1,2 metros.
- OA Tubo de Hormigón Base Plana Diametro 1 metros.

![OATuboHormigon](/assets/OATHBP.png)

### Cunetas

Al igual que el caso de las obras de arte, ISTRAM incluye la configuración para el dibujo de cunetas que cumplen con la normativa española. Sin embargo, no incluye ejemplos de cunetas para Chile. Por ello, se generaron archivos para las cunetas utilizadas en el proyecto Embalse Las Palmas. Se detalla el listado de cunetas que incluye este repositorio y una imágen de ejemplo.

- Cuneta Rectangular Hormigón.
![CunetaRectangularHormigon](/assets/CunetaRectangular.png)

- Cuneta Triangular Hormigón.
![CunetaTriangularHormigon](/assets/CunetaTriangular.png)


### Soleras

Al igual que el caso de las obras de arte, ISTRAM incluye la configuración para el dibujo de soleras disponibles en el mercado español. Sin embargo, no incluye cuentas disponibles en el mercado Chileno. Por ello, se incluyen en este repositorio la solera tipo A.

- Solera Tipo A.
![SoleraTipoA](/assets/SoleraTipoA.png)

### Talud y Terraplen vectorial

Dada la particularidad del proyecto Embalse Las Palmas, los taludes debieron ser generados de forma vectorial para contener en sus banquetas, la pendiente y el contrafoso correspondiente en cada banqueta. Por ello, se incluyen en este repositorio los archivos de vector para taludes y terraplen con imagenes que describen el vector generado.

- Talud-Vectorial-b2.5m-z1.5-h1-10m:    Banqueta 2.5m, pendiente 1.5%, altura 10m.
- Talud-Vectorial-b3m-z1,5-h1-7m:       Banqueta 3m, pendiente 1.5%, altura 7m.
- Talud-Vectorial-b3m-z3-h1-8m:         Banqueta 3m, pendiente 3%, altura 8m.
- Terraplen-Vectorial-b3-z1,5-h1-7m:    Banqueta 3m, pendiente 1.5%, altura 7m.

![TaludContrafoso](/assets/TaludContrafosoBanqueta.png)

![TaludaVariable](/assets/TaludVariable.png)

![Taludes](/assets/Taludes.png)

![Terraplen](/assets/Terraplen.png)

![TaludTerraplen](/assets/TaludTerraplen.png)

### Planimetría

Los símbolos y etiquetas presentados en la sección [Símbolos\Etiquetas\Textos 2D](#símbolos-etiquetas-y-textos-2d) son utilizados para la generación de vistas para planimetría del proyecto generado (Perfiles transversales, símbolos vertices y otras etiquetas). Además, estos se complementan con el archivo de guitarra, el cual se configuró con los colores adecuados según lo presentado en Manual de Carreteras.

- chile_mop_ColoresCL.gui

![Guitarra](/assets/guitarra.png)

Para el caso de los perfiles transversales, basta con utilizar los textos y símbolos presentados en la sección [Símbolos\Etiquetas\Textos 2D](#símbolos-etiquetas-y-textos-2d) y el archivo de guitarra para generar perfiles transversales como se presentan en la imagen a continuación.

![transversales](/assets/transversales.png)

### Otros Archivos

Se incluyen otro tipo de archivos que es posible utilizar con el software ISTRAM:

- InsertSignsTemplate.csv : plantilla para la importación desde CSV de señales verticales u objetos puntuales a modelar en la ruta (tachas y demarcadores de piso). Una vez generada la plantilla esta se carga en la ventana de objetos puntuales.

![ObjetosPuntuales](/assets/InsertPunctualObjects.png)



