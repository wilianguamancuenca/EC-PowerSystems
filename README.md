# EC-PowerSystems
EC-PowerSystems Information

Se ha desarrollado una herramienta para extraer datos de elementos del sistema eléctrico de potencia modelado mediante el Lenguaje de Programación DIgSILENT (DPL) en PowerFactory.

# Herramienta de extracción de datos para Sistemas Eléctricos de Potencia - PowerFactory

El propósito principal fue obtener información integral sobre el sistema eléctrico, incluyendo datos detallados de barras, líneas, transformadores, generadores y potencia reactiva y activa inyectada. Además, se estableció una conexión con Excel para presentar la información de manera organizada y comprensible.

## Inicialización
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

