# EC-PowerSystems
EC-PowerSystems Information

<div style="text-align: justify">

# Herramienta de extracción de datos para Sistemas Eléctricos de Potencia - PowerFactory

La extracción de los datos requeridos para el sistema se llevó a cabo mediante el Lenguaje de Programación DIgSILENT (DPL), estructurado en tres procesos de programación que generan una base de datos organizada, como se muestra en el diagrama de flujo de la Figura X. En el primer proceso, se realizó la inicialización de las variables y se verificó la comunicación entre PowerFactory y Excel, seguido de un flujo de carga para el caso de estudio específico, donde se filtraron los elementos activos, considerando únicamente los objetos Terminal para la extracción de datos, mientras se excluían los objetos Internal Node y Junction Node.

![Diagrama de flujo_DPL_page-0001](https://github.com/wilianguamancuenca/EC-PowerSystems/assets/158780955/8f40c5ff-91ed-498b-adee-7aee6d229850)

Por otro lado, el segundo proceso se encarga del almacenamiento de datos en cuatro hojas de cálculo distintas. En la primera hoja, se recopilan todos los elementos terminales activos previamente filtrados, acompañados de parámetros como voltaje, potencia activa y reactiva, junto con el tipo de barra correspondiente. La segunda hoja se destina al cálculo de parámetros adicionales, incluyendo susceptancias y potencias de línea, así como características específicas de la configuración de los transformadores. En tanto, las hojas 3 y 4 se centran en el almacenamiento de datos relacionados con generadores, compensadores de potencia activa y reactiva, y la numeración de los terminales de los distintos objetos. Todos los datos extraídos previamente se organizan en base a la hoja 1, asignándoles una numeración específica a cada barra. Como parte de este proceso final, los terminales i y j, así como los datos correspondientes a generadores y compensadores de potencia, son reubicados y ordenados en las hojas 1 y 2 según lo dictamine su numeración respectiva, además de identificar campos vacíos y asignarles el valor de 0, concluyendo con la generación de la base de datos final en un archivo .xls.

## Inicialización

Comenzamos descargando el archivo .dz, que contiene el script y el archivo de Excel habilitado para macros. Para importar el archivo .dz a PowerFactory, abrimos el Data Manager y hacemos clic derecho en la carpeta donde deseamos almacenar el script, luego importamos nuestro archivo.



https://github.com/wilianguamancuenca/EC-PowerSystems/assets/158780955/a191aafa-8890-431a-8896-39e8b0ebdb26



Si deseamos importar el archivo dentro de un proyecto, es importante asegurarse de que el proyecto esté desactivado. Además, se recomienda ubicar el archivo en la carpeta "Scripts" que se encuentra en la Libreria del proyecto.

## Funcionamiento del programa

Para que el programa funcione correctamente, es necesario tener la ruta del archivo Excel previamente descargado. Localizamos el script en el Data Manager, hacemos clic derecho y seleccionamos "Editar". Dentro de la pestaña "Basic Options", encontramos un parámetro de entrada de tipo String denominado "Path". En el valor de este parámetro, ingresamos la ruta de acceso del archivo Excel. Es importante que la ruta de acceso no se encuentre entre comillas "".

https://github.com/wilianguamancuenca/EC-PowerSystems/assets/158780955/f3a35493-cb38-446e-b1b6-76629988dd66

Finalmente, guardamos los cambios y ejecutamos el programa. El archivo de Excel descargado se abrirá, y comenzará a grabar los datos. Si el archivo de Excel ya ha sido utilizado previamente y contiene datos adicionales o más hojas, es posible que durante la ejecución del programa, Excel pregunte si se desean borrar para continuar con el uso del programa.

## Interpretación de resultados

Al culminar el programa, los datos extraídos se encuentran en el documento Excel, divididos en dos hojas según su función.

### Barras

- **Bus**: Numeración asignada a las barras desde 1 hasta n.
- **Name**: Nombre de la barra.
- **Tb**: Tipo de barra: Slack=3; PV=2; PQ=0.
- **V0**: Voltaje de barra en p.u.
- **th0**: Ángulo de barra en grados.
- **Pd**: Potencia activa de la barra en MW.
- **Qd**: Potencia reactiva de la barra en MVAR.
- **Pgmax**: Potencia activa máxima que puede ser generada en la barra en MW; si la barra no tiene generadores, es igual a 0.
- **Pgmin**: Potencia activa mínima que puede ser generada en la barra en MW; si la barra no tiene generadores, es igual a 0.
- **Qgmax**: Potencia reactiva máxima que puede ser generada en la barra en MVAR; si la barra no tiene generadores, es igual a 0.
- **Qgmin**: Potencia reactiva mínima que puede ser generada en la barra en MVAR; si la barra no tiene generadores, es igual a 0.
- **Qsvcmax**: Límite máximo de potencia reactiva de elementos SVC.
- **Qsvcmin**: Límite mínimo de potencia reactiva de elementos SVC.
- **Pg0**: Potencia activa despachada en MW.
- **Qg0**: Potencia reactiva despachada en MVAR.
- **Vmax**: Límite máximo de voltaje de barra en p.u.
- **Vmin**: Límite mínimo de voltaje de barra en p.u.
- **Vg**: Voltaje de Setpoint en p.u.
- **at**: 
- **bt**: 
- **ct**:
- **Bshnt**: Susceptancia inyectada a la barra por filtros en p.u.

### Líneas y Transformadores

- **k**: Numeración de las líneas y transformadores desde 1 hasta n.
- **BusName**: Nombre del elemento.
- **i & j**: Numeración "i" correspondiente a los terminales (previamente asignada en la hoja Bus) entre los que se encuentra el elemento.
- **Elm**: Identifica si el elemento es una línea=0 o un transformador=1.
- **r**: Resistencia en p.u.
- **x**: Reactancia en p.u.
- **Bshl**: Susceptancia/2 en p.u.
- **Cl**: Costo de la línea o transformador especificado en la descripción de cada elemento en millones de dólares.
- **n0**: Número de elementos en paralelo.
- **nmax**: Número máximo de líneas que se pueden expandir.
- **Plmax**: Potencia consumida por el elemento en MW.
- **a**: Relación de transformación; para líneas a=1.
- **fi**: Ángulo de fase.
- **amax**: Posición máxima del tap.
- **amin**: Posición mínima del tap.
