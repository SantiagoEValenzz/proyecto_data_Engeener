Primer Proyecto de Ingeniería de Datos: Uber Data Analysis
==========================================================

Como ingeniero de datos profesional, me encanta el desafío de tomar datos sin procesar de diferentes fuentes y trabajar duro para limpiar, transforme y embellezca los datos para que puedan convertirse en un formato utilizable por parte de las empresas o los analistas de datos. Sin embargo, trabajar en una organización como ingeniero de datos puede conducir a ciertas fases magras cuando los proyectos o desafíos no son suficientes para que la adrenalina bombee. Fue entonces cuando tuve la suerte de encontrarme con el canal        
. Su fantástico canal me ayudó a trabajar en un gran proyecto de ingeniería de datos con Uber Data Analysis (https://www.youtube.com/watch?v=WpQECq5Hx9g). Como compañero ingeniero de datos, el canal de Darshililis realmente me ha ayudado a centrarme más en mis proyectos y también a aprender mucho sobre plataformas en la nube como AWS y GCP. Seguí el video más reciente de Darshilil sobre Uber Data Analysis y mi fin de semana pasó de ‘meh’ a ‘oh yeahhhh’. Hablaré sobre el proyecto y los diferentes componentes que utilicé en el proyecto. Antes de comenzar el proyecto, es importante entender que este proyecto no es para un principiante absoluto en ingeniería de datos. La expectativa es que antes de este proyecto, debe tener una comprensión básica de las tecnologías en la nube, SQL, programación Python y alguna idea sobre el modelado de datos y ETL. Si alguno de estos términos parece extraño y aterrador, comuníquese conmigo y estaré encantado de ayudarlo a comenzar con lo básico.


[url=https://postimg.cc/75RjndsG][img]https://i.postimg.cc/75RjndsG/consola-de-jupiter.png[/img][/url]


¡Los datos que utilizaremos para el análisis serían muy similares a los datos de Uber, pero obviamente Uber puede conseguir que sus conductores se comporten bien, definitivamente no nos darían sus datos reales! Entonces, el conjunto de datos es similar a Uber, pero no del todo. El conjunto de datos que utilizamos son datos de viajes en taxi amarillos y verdes del sitio web del gobierno de NYCics — https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page. El proyecto de datos nos ayudaría a usar los datos de este sitio web y almacenarlos en Google Cloud Storage y luego usaremos Mage para nuestro pipeline ETL. A través de Mage weiosll empujar los datos de nuestros proyectos en Google Big Query. Y como paso final, crearemos nuestro panel de control en Looker Studio para visualizar los datos que transformamos y analizamos.


Flujo de Datos de Fin a Fin para el Proyecto
Permítanme comenzar explicando las diferentes tecnologías enumeradas anteriormente. El GCP (Google Cloud Platform) es el conjunto de productos y servicios de computación en la nube de Google que se proporcionan para varios casos de uso. Los servicios de GCP que utilizaremos son :

Google Cloud Storage: Es un almacenamiento de archivos en línea que GCP proporciona como servicio. Nos ayuda a almacenar, recuperar archivos desde cualquier lugar de la nube con una conexión a Internet.
Google Compute Engine: Es la parte de la suite GCP que nos ayuda a ejecutar máquinas virtuales para ejecutar nuestras aplicaciones. Es fácil de crear, ejecutar y mantener aplicaciones en el motor de cómputo GCPcs.
BigQuery: Es un almacén proporcionado por Google que nos ayuda a almacenar, analizar conjuntos de datos a gran escala utilizando una interfaz de tipo SQL y un lenguaje de consulta. Es rentable y altamente escalable en función de nuestro tamaño y requisito de datos.
Looker: Looker Studio es una herramienta basada en la web de BI utilizada para fines de visualización e informes. Puede tomar datos de múltiples fuentes, incluidas hojas de Google, BigQuery, etc., para crear paneles interactivos que pueden convertir nuestros datos en excelentes gráficos y mejorar la legibilidad de conjuntos de datos complejos.
Hay varias otras herramientas y tecnologías que se utilizan para este proyecto, aparte de los servicios de GCP son:

Jupyter Notebooks : Jupyter Notebooks es una plataforma interactiva de bases web en la que podemos ejecutar, ejecutar fragmentos de código. Esta plataforma ayuda a ejecutar documentos de portátiles a través del navegador web. Es una gran plataforma para probar códigos antes de ponerlos en producción.
Puede seguir este enlace para instalar Jupyter notebook en su sistema — https://jupyter.org/install. Si está utilizando Mac para iniciar Jupyter Notebook, estos son los dos comandos que necesita para iniciarlo en su plataforma. (Suponiendo que tenga la última versión de pip instalada en su computadora portátil):

portátil de instalación pip

cuaderno de jupyter


Consola Jupyter Notebok
2. Mage- Mage es la última herramienta de código abierto para configurar su pipeline ETL. Estas herramientas lo ayudan a enfocar solo su lógica comercial utilizando ciertas plantillas existentes que proporciona a — ‘load’,’transform’ y ‘extract’ los datos. Me encanta su etiqueta line- ‘Data plumbing sin la mierda’. https://www.mage.ai/


Mago.ai
3. Lucidchart: Lucidchart es un software de diagramación que le ayuda a crear diagramas de diseño, diagramas de flujo, etc para su proyecto. Esta herramienta visual es útil cuando queremos explicar un flujo de extremo a extremo de cualquier proyecto, módulo a cualquier persona que pueda o no hablar la terminología tecnológica. La versión gratuita puede ayudarlo a crear hasta tres diagramas — https://www.lucidchart.com/.

4. Modelado de datos: El modelado de datos es el proceso de creación de representación visual de los datos en todo el sistema o partes de él para comprender las conexiones entre cada elemento de datos. Al crear modelos de datos, es imperativo comprender las tablas de hechos y dimensiones.

TABLA DE HECHOS: Este tipo de tabla contiene todas las medidas cuantitativas que utilizamos para el análisis. Por ejemplo: Si nos fijamos en los datos de la escuela - número de estudiantes, clases totales, número total de profesores, número total de departamentos, etc se pueden almacenar de hecho tabla. En pocas palabras, es una tabla que tiene números para las métricas.

TABLA DIMENSIÓN: Este tipo de tabla contiene detalles/descripción de los atributos de los datos. Por ejemplo: Para los estudiantes, tendremos columnas como nombre del estudiante, fecha de nacimiento, dirección, etc en este tipo de tablas.


Tabla de hechos vs Dimensiones
5. Diccionario de datos: Contiene una lista completa de todos los elementos de datos y sus descripciones. En cualquier organización grande, cuando las tablas suben más alto en número, el seguimiento de datos puede ser difícil, por lo que un diccionario de datos puede ayudar a consolidar todos los puntos de datos y sus descripciones. Esto es muy útil cuando construimos nuestros modelos de datos. Para este proyecto, el diccionario de datos se puede encontrar aquí — https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf.


Diccionario de Datos
Ahora que se ordenan algunas terminologías básicas, podemos avanzar a la parte de ejecución del proyecto. Idealmente deberíamos comenzar el proyecto con modelado de datos ya que eso es la parte más básica de cualquier proyecto de datos. Podemos descargar los datos del registro de taxis de Nueva York en nuestros cuadernos Jupyter para analizar los datos en un formato tabular. Los datos de todos los años están disponibles en el sitio web en muchos formatos diferentes.

MODELADO DE DATOS::


Podemos ver los datos en forma tabular usando Jupyter Notebooks usando el paquete Pandas en Python.


Podemos usar la herramienta Lucidchart y arrastrar el diagrama de relación de entidad a nuestra hoja y comenzar a construir los modelos de datos basados en los datos que tenemos en los registros de taxis de Nueva York.


En Lucidchart, busque ‘entity relationship’ y arrástrelo a la hoja para comenzar a construir el modelo de datos
A continuación se muestra el modelo de datos final que se utilizará para el proyecto


Una vez que el modelo de datos esté listo, podemos comenzar con algunas transformaciones en Python.

TRANSFORMACIONES DE PYTHON USANDO CUADERNOS JUPYTER:

Aquí comenzamos nuestra transformación de python asignando una clave principal — ‘trip_id’ a todo el conjunto de datos después de soltar todos los duplicados.

#gotar duplicados
df = df.drop_duplicates().reset_index(drop=True)
df[‘trip_id’] = df.index

Una vez que el dataframe está disponible, creamos varios dataframes desde el dataframe principal para crear tablas de dimensiones que creamos en el modelo anterior.

El código mencionado por Darshil está disponible aquí — https://github.com/darshilparmar/uber-etl-pipeline-data-engineering-project/blob/main/Uber%20Data%20Pipeline%20(Fixed%20Version).ipynb

Este código se implementará posteriormente en Mage a través de Google Compute Engine.
``
GCP: CREACIÓN DE SU CUENTA

Si no tiene su propia cuenta de GCP, puede crear una cuenta de nivel gratuita que le brinde algunos servicios básicos que pueden ayudarlo a comenzar con GCP. Si necesita ayuda para crear la cuenta de nivel gratuita, he escrito un blog al respecto. https://medium.com/@nishasreedharan/create-free-tier-gcp-account-1ec66fa2d536. Si aún enfrenta problemas, no dude en comunicarse conmigo y definitivamente lo ayudaré.

CARGANDO DATOS EN GOOGLE CLOUD STORAGE

Si tiene alguna idea básica sobre los servicios en la nube, debe saber que para la mayoría del almacenamiento basado en la nube comenzamos con la creación de cubos. Del mismo modo, tenemos que crear un cubo para comenzar el proyecto.


Escriba ‘Google cloud storage’ y comience a crear cubos
Cuando cree el cubo, asegúrese de que su público pueda acceder a él utilizando una URL. Sin embargo, esa no es la forma más segura de construir eso mientras se trabaja en un proyecto de grado de producción.


Otorgar acceso público al cubo
Una vez que se haya realizado el depósito, cargue los datos del archivo nyc en el depósito y asegúrese de cambiar los permisos para hacerlo público y accesible a través de la URL. Si te quedas atascado con algún error, consulta ‘Google Cloud y Mage Installation’ parte del video.

GCP COMPUTE ENGINE E INSTALE MAGE

Dado que nuestro proyecto requiere que Mage se ejecute, instalaremos eso en nuestra VM que construimos utilizando el motor de cómputo GCPcs.


Al crear la VM, asegúrese de que HTTP tenga la dirección predeterminada completa y elija el tipo de máquina estándar con 4 CPU y 16 GB de memoria. Una vez que se crea la instancia, debemos hacer clic en ‘SSH’ y esto abrirá su instancia donde puede comenzar con sus comandos. https://github.com/darshilparmar/uber-etl-pipeline-data-engineering-project/blob/main/commands.txt ayudará con todas las instalaciones requeridas en la VM. Puede consultar la página de github de Mageages para instalar Mage. También tiene varias opciones para instalar Mage desde Docker.

EJECUTE MAGE EN COMPUTE ENGINE

Una vez que la instalación es exitosa y una vez que ejecute Mage usando el comando ‘ mage start < project_name > ’. Si todo tiene éxito, puede ver a Mage funcionando en el puerto 6789. Para acceder a Mage desde la interfaz de usuario web, necesitaría la IP externa de su VM ( que puede obtener una vez que haga clic en su VM en GCP ). Puede intentar escribir su Ip externo y el puerto para acceder a Mage. Por ejemplo: 35.127.11.11: 6789. Pero por desgracia! No puedes acceder a él. Esto se debe a que no le dijimos explícitamente a la VM que aceptara la solicitud del puerto 6789. Para remediar esto, debe ir a ‘ Firewall ’ en GCP y hacer clic en ‘ crear la regla del firewall ’.


Firewall GCP
En la nueva regla, proporcione detalles y proporcione la IP como 0.0.0.0/0 y mencione el puerto y cree la regla. Esto debería ayudar a abrir la interfaz de usuario de mago.

CREAR ARCHIVOS EN LA MAPA PARA ETL / TRANSFORMACIÓN

Mage se parece mucho a otras herramientas de orquestación como Airflow con una gran diferencia. Mage le proporciona muchas plantillas para cargar, transformar datos .


Mage UI creado por Data Loader con API como entrada
En la sección API puede agregar la URL pública desde la que se pudieron descargar los datos desde Google Cloud Storage. El código se puede ejecutar utilizando el icono de ejecución en la parte superior del archivo del cargador de datos. La salida debe producir el archivo de datos csv NYC .

En la siguiente parte creamos un archivo para la transformación de datos (usando plantilla genérica), en el que necesitamos importar pandas y escribir el código que usamos en los portátiles Jupyter anteriores. Los datos que se emiten desde el archivo del cargador de datos van al archivo de transformación de datos. Los archivos de transformación convierten datos en marcos de datos de diferentes tablas de hechos y dimensiones mencionadas anteriormente. Los fotogramas de datos se convierten en diccionarios que se transmiten en la siguiente función.

La última parte de Mage es escribir los datos de salida en Big Query. Así que creamos un archivo con exportador de datos con exportación a Big Query. En esto hay detalles de tabla para Big Query y un archivo io.yaml que tiene detalles sobre las credenciales de GCP (BigQuery ). Para obtener las credenciales, vaya a la consola GCP y escriba ‘API & Services’ y vaya a ‘create credentials’ y ‘create service account’ en eso.


Al crear acunt de servicio, permitimos que los servicios en VM interactúen con los servicios en GCP. Una vez que cree la cuenta de servicio, vaya a la cuenta de servicio creada y agregue la clave. Cree una clave json y descargue el archivo. En el archivo json encontrará todas las credenciales requeridas . Puede copiar pegar eso en el archivo yaml en Mage. En el último código de transformador, weesll necesita un conjunto de datos en Bigquery para agregar las tablas.

Para eso, vaya a BigQuery y vaya a ‘create dataset’ y cree un conjunto de datos con múltiples regiones habilitadas.


En el código del transformador de Mageages, agregue los detalles de la tabla con el nombre del conjunto de datos y el nombre de la tabla que se requiere, por ejemplo: fact_table. Si obtiene un error en la nube de google cuando ejecuta el código del transformador, podría deberse a la falta de paquetes de nube de google en la VM. Así que volvemos a ir a la VM y abrimos otra instancia haciendo clic en el botón SSH e instalamos los paquetes de nube de Google utilizando los comandos compartidos en el enlace de arriba. Consulte este enlace — https://github.com/darshilparmar/uber-etl-pipeline-data-engineering-project/tree/main/mage-files para obtener el código de todos los archivos Mage individuales. Una vez que se ejecuta el archivo de transformación, cargará todas las tablas en Big Query.

ANÁLISIS DE DATOS DE GRANDES CONSULTAS

En la consola de BigQuery puede ver que se han copiado todas las tablas de dimensiones y hechos. Ahora puede comenzar a consultar desde la consola.


Consola BigQuery para análisis de datos
Para analizar y crear un tablero fuera del conjunto de datos, podemos crear una tabla separada basada en esta consulta — https://github.com/darshilparmar/uber-etl-pipeline-data-engineering-project/blob/main/analytics_query.sql. Esta consulta solo se une a todos los conjuntos de datos requeridos y extrae solo algunas métricas relevantes como parte del conjunto de datos final que sería necesario mostrar en el panel.

TABLERO DE INSTRUMENTOS DE CONSTRUCCIÓN

Ahora que tenemos la tabla específicamente para análisis, podemos comenzar con la construcción de nuestro primer panel de control en Looker Studio. Vaya a Google y escriba ‘Google Looker Studio’ y haga clic en el primer enlace . Una vez que se abra la interfaz, haga clic en ‘create blank document’ y cuando obtenga las opciones para seleccionar la fuente, seleccione ‘Google Big Query’ como se muestra a continuación.


Seleccione BigQuery como fuente en Looker Studio
Una vez que agregue BigQuery como fuente, es posible que deba autorizarlo por primera vez. Publique el conjunto de datos y el nombre de la tabla que necesitamos cargar en el tablero y aparecerá como una tabla en el tablero. Puede quitar o mantener la mesa y diseñar el tablero según su elección. Como era mi primer tablero, utilicé el que Darshil construyó para comenzar. Puedes dejar que tu creatividad fluya con esto.

Esta es la versión final del tablero construido por Darshil:


Uber Dashboard en Looker
Después de completar este proyecto, mi próximo paso sería recrear este mismo proyecto para un caso de uso diferente, ya que realmente me ayudó a aprender mucho sobre varias tecnologías y resolver varios errores durante el viaje.

¡Espero que disfrutes de esta porción del cielo llamada ingeniería de datos ! Muchas gracias a Darshil por ayudarme a comenzar el viaje para construir proyectos por mí mismo.
