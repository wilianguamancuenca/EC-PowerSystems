# EC-PowerSystems
EC-PowerSystems Information

# Herramienta de extracción de datos para Sistemas Eléctricos de Potencia - PowerFactory

Se desarrolló una herramienta para la extracción de datos de elementos del sistema eléctrico de potencia mediante el Lenguaje de Programación DIgSILENT (DPL) en PowerFactory y creacioó de una base de datos en Excel. El propósito principal fue obtener información integral sobre el sistema, incluyendo datos detallados de barras, líneas, transformadores, generadores, potencia reactiva y activa inyectada.

Para la inicialización del programa se verificó la comunicación con Excel y se integro a cada *set* unicamente los elementos activos correspondientes. Además, en el *set*  de elementos tipo *.ElmTerm* e consideraron únicamente los objetos *Terminal* para la extracción de datos, excluyendo los objetos *Internal Node* y *Junction Node*.

```c++
verif = xlStart();
if (verif) {
    printf('Error al vincular Excel');
}
sBarras = AllRelevant('*.ElmTerm', 0);
sLineas = AllRelevant('*.ElmLne', 0);
sTrafo = AllRelevant('*.ElmTr2', 0);
sTrafo3 = AllRelevant('*.ElmTr3', 0);
sGen = AllRelevant('*.ElmSym', 0);
sXGrid = AllRelevant('*.ElmXnet', 0);
sGenstat = AllRelevant('*.ElmGenstat', 0);
sPV = AllRelevant('*.ElmPvsys', 0);
sShunt = AllRelevant('*.ElmShnt', 0);
sSvc = AllRelevant('*.ElmSvs', 0);
```
## Extraccion de datos
El almacenamiento de datos se divide en cuatro hojas de cálculo distintas. En la primera hoja, se encuentra los parámetros asociados a los elementos terminales previamente filtrados, como voltaje, potencia activa y reactiva, así como el tipo de barra correspondiente.  En consecuencia...

```

```
La segunda hoja está destinada al cálculo de parámetros, incluyendo susceptancias y potencias de línea, así como características específicas de la configuración de los transformadores. Las hojas 3 y 4 se centran en el almacenamiento de datos relacionados con generadores, compensadores de potencia activa y reactiva y numeración de los terminales de los distintos objetos. 



### bus




Se define los objetos que se desea calcular y se excluyen los elementos inactivos.

  **Número de Elementos Activos**
  - **Barras Activas** 
  - **Líneas Activas**
  - **Transformadores 2 Bobinados Activos**
  - **Transformadores 3 Bobinados Activos**
  - **Generadores Activos**
  - **External Grid Activos**
  - **Generadores Estáticos Activos**
  - **Plantas Solares Activas**
  - **Filtros Activos**
  - **SVCs Activos**

## Parámetros de Barras (Hoja 1 - BUS)
  Se presenta algunos de los parámetros clave de las barras en el sistema:

1. **Número total de barras de tipo terminal:** (Número Total de Barras Tipo Terminal)
2. **Detalles de las barras, incluyendo:**
    -	Nombre
    -	Tensión Inicial (V0)
    -	Ángulo Inicial (Th0)
    -	Carga Activa (Pd)
    -	Carga Reactiva (Qd)
    -	Tensión Máxima (Vmax)
    -	Tensión Mínima (Vmin)

## Análisis Detallado
  ## Parámetros de Líneas y Transformadores (Hoja 2 - LINEAS Y TRAFOS)
   Esta sección presenta un resumen detallado de las líneas y transformadores en el sistema, incluyendo:
  
  - Parámetros eléctricos de líneas: Resistencia (r), Reactancia (x) y Susceptancia (b).
  - Información sobre los transformadores: 2 y 3 bobinados, incluyendo relaciones de transformación, ángulos y limitaciones de potencia.

## Parámetros de Generadores (Hoja 3 - GENERACION)
  Se proporciona un resumen detallado de los generadores en el sistema, incluyendo:
  - **Tipo de generador**: Síncrono, Solar, Estático, etc.
  - Potencia máxima y mínima generada.
  - Limitaciones de potencia reactiva.
  - **Configuraciones de punto de operación inicial:** Pg0, Qg0, Vg.
  - **Parámetros de regulación AVR:** at, bt, ct.

## Análisis de potencia inyectada (Hoja 4 - ESTABILIDAD TRANSITORIA)
  Un análisis para la potencia reactiva y activa que es suministrada al sistema por cada Bus. La capacitancia y reactancia es calculada en términos de la susceptancia para obtener un valor de “Bshunt” por cada barra. 

## Conclusión
Este informe proporciona una visión general detallada de la configuración del sistema eléctrico, destacando información crítica de las barras, líneas, transformadores y generadores. La presentación en hojas de cálculo facilita la interpretación de los datos. Este análisis puede ser utilizado como base para futuras optimizaciones y mejoras en el sistema eléctrico, garantizando la estabilidad y eficiencia operativa.



## Descripción


## Funcionalidades
- Extracción de datos relevantes de modelos de sistemas eléctricos.
- Interfaz de usuario intuitiva para configurar y ejecutar la extracción.
- Compatibilidad con PowerFactory.

## Instalación

