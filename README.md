
# Uber Data Engineer Project


Me apasiona trabajar con datos y convertirlos en información útil para las empresas y los analistas. En mi proyecto, tuve el desafío de tomar datos de diferentes fuentes y prepararlos para su análisis. Antes de comenzar, es importante señalar que este proyecto no es para principiantes en el campo de la ciencia de datos. Se requiere un conocimiento básico de tecnologías en la nube, SQL, Python y conceptos como modelado de datos y ETL.

Si alguno de estos términos suena desconocido o intimidante, no dudes en contactarme y estaré encantado de ayudarte a comprender los conceptos básicos.

Vamos a trabajar con datos similares a los de Uber, pero no exactamente iguales. Utilizaremos información sobre viajes en taxis amarillos y verdes de la ciudad de Nueva York, disponible en el sitio web del gobierno. (https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).
 
Nuestro objetivo es almacenar estos datos en Google Cloud Storage y luego usar Mage para organizarlos. Después, los moveremos a Google Big Query y finalmente crearemos un panel de control en Looker Studio para ver y analizar los datos transformados.

[![flujo-de-datos.png](https://i.postimg.cc/1zWSzYHZ/flujo-de-datos.png)](https://postimg.cc/PL893y96)
*Flujo de Datos de Fin a Fin para el Proyecto.*


Permítanme comenzar explicando las diferentes tecnologías enumeradas anteriormente. 
El **GCP (Google Cloud Platform)** es el conjunto de productos y servicios de computación en la nube de Google que se proporcionan para varios casos de uso. Los servicios de GCP que utilizaremos son:
1.	**Google Cloud Storage**: Es un almacenamiento de archivos en línea que GCP proporciona como servicio. Nos ayuda a almacenar, recuperar archivos desde cualquier lugar de la nube con una conexión a Internet.
2.	**Google Compute Engine**: Es la parte de la suite GCP que nos ayuda a ejecutar máquinas virtuales para ejecutar nuestras aplicaciones. Es fácil de crear, ejecutar y mantener aplicaciones en el motor de cómputo GCPcs.
3.	**BigQuery**: Es un almacén proporcionado por Google que nos ayuda a almacenar, analizar conjuntos de datos a gran escala utilizando una interfaz de tipo SQL y un lenguaje de consulta. Es rentable y altamente escalable en función de nuestro tamaño y requisito de datos.

4.	**Looker**: Looker Studio es una herramienta basada en la web de BI utilizada para fines de visualización e informes. Puede tomar datos de múltiples fuentes, incluidas hojas de Google, BigQuery, etc., para crear paneles interactivos que pueden convertir nuestros datos en excelentes gráficos y mejorar la legibilidad de conjuntos de datos complejos. 
                                                            
Hay varias otras herramientas y tecnologías que se utilizan para este proyecto, aparte de los servicios de GCP son:


1.	**Jupyter Notebooks**: Jupyter Notebooks es una plataforma interactiva de bases web en la que podemos ejecutar, ejecutar fragmentos de código. Esta plataforma ayuda a ejecutar documentos de portátiles a través del navegador web. Es una gran plataforma para probar códigos antes de ponerlos en producción.
Puede seguir este enlace para instalar Jupyter notebook en su sistema — [Instalación de Jupyter Notebook](https://jupyter.org/install). Si está utilizando Mac para iniciar Jupyter Notebook, estos son los dos comandos que necesita para iniciarlo en su plataforma. (Suponiendo que tenga la última versión de pip instalada en su computadora portátil):



[![consola-de-jupiter.png](https://i.postimg.cc/zfD581Tj/consola-de-jupiter.png)](https://postimg.cc/75RjndsG) *Consola Jupyter Notebok*







2. **Mage** - Mage es la última herramienta de código abierto para configurar su pipeline ETL. Estas herramientas lo ayudan a enfocar solo su lógica comercial utilizando ciertas plantillas existentes que proporciona a — ‘load’,’transform’ y ‘extract’ los datos. 
[Sitio web de Mage](https://www.mage.ai/).

[![mago-ia.png](https://i.postimg.cc/fLphctp2/mago-ia.png)](https://postimg.cc/34X67RKm) 
*Mago.ai*
 
3. **Lucidchart**: Lucidchart es un software de diagramación que le ayuda a crear diagramas de diseño, diagramas de flujo, etc para su proyecto. Esta herramienta visual es útil cuando queremos explicar un flujo de extremo a extremo de cualquier proyecto, módulo a cualquier persona que pueda o no hablar la terminología tecnológica. La versión gratuita puede ayudarlo a crear hasta tres diagramas — [Sitio web de Lucidchart](https://www.lucidchart.com/).

4. **Modelado de datos**: El modelado de datos es el proceso de creación de representación visual de los datos en todo el sistema o partes de él para comprender las conexiones entre cada elemento de datos. Al crear modelos de datos, es imperativo comprender las tablas de hechos y dimensiones.
**TABLA DE HECHOS**: Este tipo de tabla contiene todas las medidas cuantitativas que utilizamos para el análisis. Por ejemplo: Si nos fijamos en los datos de la escuela - número de estudiantes, clases totales, número total de profesores, número total de departamentos, etc se pueden almacenar de hecho tabla. En pocas palabras, es una tabla que tiene números para las métricas.


**TABLA DIMENSIÓN:** Este tipo de tabla contiene detalles/descripción de los atributos de los datos. Por ejemplo: Para los estudiantes, tendremos columnas como nombre del estudiante, fecha de nacimiento, dirección, etc en este tipo de tablas.

5. **Diccionario de datos:** Contiene una lista completa de todos los elementos de datos y sus descripciones. En cualquier organización grande, cuando las tablas suben más alto en número, el seguimiento de datos puede ser difícil, por lo que un diccionario de datos puede ayudar a consolidar todos los puntos de datos y sus descripciones. Esto es muy útil cuando construimos nuestros modelos de datos. Para este proyecto, el diccionario de datos se puede encontrar aquí: 
[Diccionario de Datos NYC](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf).


[![diccionario-de-datos.png](https://i.postimg.cc/qMfTgK8g/diccionario-de-datos.png)](https://postimg.cc/MXY4Fv38) *Diccionario de Datos*

Ahora que se ordenan algunas terminologías básicas, podemos avanzar a la parte de ejecución del proyecto. Idealmente deberíamos comenzar el proyecto con modelado de datos ya que eso es la parte más básica de cualquier proyecto de datos. Podemos descargar los datos del registro de taxis de Nueva York en nuestros cuadernos Jupyter para analizar los datos en un formato tabular. Los datos de todos los años están disponibles en el sitio web en muchos formatos diferentes.

**MODELADO DE DATOS**:
[![modelado-de-datos.png](https://i.postimg.cc/v8xyQhxp/modelado-de-datos.png)](https://postimg.cc/ThxF0r99)

Podemos ver los datos en forma tabular usando Jupyter Notebooks usando el paquete Pandas en Python.

[![cosas-de-panda.png](https://i.postimg.cc/63yX4Lj4/cosas-de-panda.png)](https://postimg.cc/YGKVJgwt)

Podemos usar la herramienta Lucidchart y arrastrar el diagrama de relación de entidad a nuestra hoja y comenzar a construir los modelos de datos basados en los datos que tenemos en los registros de taxis de Nueva York.

[![modelodedato2.png](https://i.postimg.cc/bNQjnvTg/modelodedato2.png)](https://postimg.cc/2V8JRrgL)

En Lucidchart, busque ‘entity relationship’ y arrástrelo a la hoja para comenzar a construir el modelo de datos.

A continuación se muestra el modelo de datos final que se utilizará para el proyecto.

[![modelodedatos3.png](https://i.postimg.cc/PJDn2fkt/modelodedatos3.png)](https://postimg.cc/MfzLGST4)

Una vez que el modelo de datos esté listo, podemos comenzar con algunas transformaciones en Python.

**TRANSFORMACIONES DE PYTHON USANDO CUADERNOS JUPYTER:**
Aquí comenzamos nuestra transformación de python asignando una clave principal — ‘trip_id’ a todo el conjunto de datos después de soltar todos los duplicados.
```python
#gotar duplicados
df = df.drop_duplicates().reset_index(drop=True)
df[‘trip_id’] = df.index
```

Una vez que el dataframe está disponible, creamos varios dataframes desde el dataframe principal para crear tablas de dimensiones que creamos en el modelo anterior. Este código se implementará posteriormente en Mage a través de Google Compute Engine.

**GCP: CREACIÓN DE SU CUENTA**

Si no tiene su propia cuenta de GCP, puede crear una cuenta de nivel gratuita que le brinde algunos servicios básicos que pueden ayudarlo a comenzar con GCP.

**CARGANDO DATOS EN GOOGLE CLOUD STORAGE**

Si tiene alguna idea básica sobre los servicios en la nube, debe saber que para la mayoría del almacenamiento basado en la nube comenzamos con la creación de cubos. Del mismo modo, tenemos que crear un cubo para comenzar el proyecto.

[![googlecloudstorage.png](https://i.postimg.cc/Y2fqY88T/googlecloudstorage.png)](https://postimg.cc/pyrHtfwB) *Escriba ‘Google cloud storage’ y comience a crear cubos*


Cuando cree el cubo, asegúrese de que su público pueda acceder a él utilizando una URL. Sin embargo, esa no es la forma más segura de construir eso mientras se trabaja en un proyecto de grado de producción.
 
[![accesopublico.png](https://i.postimg.cc/761D1Y1S/accesopublico.png)](https://postimg.cc/62QDtKmQ)
*Otorgar acceso público al cubo*

Una vez que se haya realizado el depósito, cargue los datos del archivo nyc en el depósito y asegúrese de cambiar los permisos para hacerlo público y accesible a través de la URL. Si te quedas atascado con algún error, consulta ‘Google Cloud y Mage Installation’.

**GCP COMPUTE ENGINE E INSTALE MAGE**

Dado que nuestro proyecto requiere que Mage se ejecute, instalaremos eso en nuestra VM que construimos utilizando el motor de cómputo GCPcs.

[![isstalargcpemage.png](https://i.postimg.cc/X7PMCCMT/isstalargcpemage.png)](https://postimg.cc/F70nt1HZ)


**EJECUTE MAGE EN COMPUTE ENGINE**

Una vez que la instalación es exitosa y una vez que ejecute Mage usando el comando ‘ mage start < project_name > ’. Si todo tiene éxito, puede ver a Mage funcionando en el puerto 6789. Para acceder a Mage desde la interfaz de usuario web, necesitaría la IP externa de su VM ( que puede obtener una vez que haga clic en su VM en GCP ). Puede intentar escribir su Ip externo y el puerto para acceder a Mage. Por ejemplo: 35.127.11.11: 6789. Pero por desgracia! No puedes acceder a él. Esto se debe a que no le dijimos explícitamente a la VM que aceptara la solicitud del puerto 6789. Para remediar esto, debe ir a ‘ Firewall ’ en GCP y hacer clic en ‘ crear la regla del firewall ’.
[![Firewallgcp.png](https://i.postimg.cc/W38CbD6Y/Firewallgcp.png)](https://postimg.cc/BL8Mmnz2)
*Firewall GCP*

En la nueva regla, proporcione detalles y proporcione la IP como 0.0.0.0/0 y mencione el puerto y cree la regla. Esto debería ayudar a abrir la interfaz de usuario de mago.

**CREAR ARCHIVOS EN LA MAPA PARA ETL / TRANSFORMACIÓN**

Mage se parece mucho a otras herramientas de orquestación como Airflow con una gran diferencia. Mage le proporciona muchas plantillas para cargar, transformar datos.

[![Mage-UI-creado-por-Data-Loader-con-API-como-entrada.png](https://i.postimg.cc/fTJpDR35/Mage-UI-creado-por-Data-Loader-con-API-como-entrada.png)](https://postimg.cc/hfRp0g17) *Mage UI creado por Data Loader con API como entrada*

En la sección API puede agregar la URL pública desde la que se pudieron descargar los datos desde Google Cloud Storage. El código se puede ejecutar utilizando el icono de ejecución en la parte superior del archivo del cargador de datos. La salida debe producir el archivo de datos csv NYC .

En la siguiente parte creamos un archivo para la transformación de datos (usando plantilla genérica), en el que necesitamos importar pandas y escribir el código que usamos en los portátiles Jupyter anteriores. Los datos que se emiten desde el archivo del cargador de datos van al archivo de transformación de datos. Los archivos de transformación convierten datos en marcos de datos de diferentes tablas de hechos y dimensiones mencionadas anteriormente. Los fotogramas de datos se convierten en diccionarios que se transmiten en la siguiente función.

La última parte de Mage es escribir los datos de salida en Big Query. Así que creamos un archivo con exportador de datos con exportación a Big Query. En esto hay detalles de tabla para Big Query y un archivo io.yaml que tiene detalles sobre las credenciales de GCP (BigQuery ). Para obtener las credenciales, vaya a la consola GCP y escriba ‘API & Services’ y vaya a ‘create credentials’ y ‘create service account’ en eso.

[![create-services-acount.png](https://i.postimg.cc/kGVs3Djb/create-services-acount.png)](https://postimg.cc/gLW83cbz)


Al crear acunt de servicio, permitimos que los servicios en VM interactúen con los servicios en GCP. Una vez que cree la cuenta de servicio, vaya a la cuenta de servicio creada y agregue la clave. Cree una clave json y descargue el archivo. En el archivo json encontrará todas las credenciales requeridas . Puede copiar pegar eso en el archivo yaml en Mage.

En el último código de transformador, weesll necesita un conjunto de datos en Bigquery para agregar las tablas.
Para eso, vaya a BigQuery y vaya a ‘create dataset’ y cree un conjunto de datos con múltiples regiones habilitadas.

[![ssqlworkspace.png](https://i.postimg.cc/jjdk3qrz/ssqlworkspace.png)](https://postimg.cc/BjkgX0b6)

En el código del transformador de Mageages, agregue los detalles de la tabla con el nombre del conjunto de datos y el nombre de la tabla que se requiere, por ejemplo: fact_table. Si obtiene un error en la nube de google cuando ejecuta el código del transformador, podría deberse a la falta de paquetes de nube de google en la VM. Así que volvemos a ir a la VM y abrimos otra instancia haciendo clic en el botón SSH e instalamos los paquetes de nube de Google.Una vez que se ejecuta el archivo de transformación, cargará todas las tablas en Big Query.

**ANÁLISIS DE DATOS DE GRANDES CONSULTAS**

En la consola de BigQuery puede ver que se han copiado todas las tablas de dimensiones y hechos. Ahora puede comenzar a consultar desde la consola.

[![consolabigquerry.png](https://i.postimg.cc/RF2s0cJR/consolabigquerry.png)](https://postimg.cc/2bFFcLwb)
*Consola BigQuery para análisis de datos*

Para realizar un análisis detallado y construir un panel de control a partir de nuestros datos, podemos generar una tabla separada utilizando una consulta específica. Esta consulta combina todos los conjuntos de datos necesarios y extrae métricas relevantes para construir el conjunto final de datos que será visualizado en el panel.

**CONSTRUCCION DEL DASHBOARD**

Ahora que tenemos la tabla específicamente para análisis, podemos comenzar con la construcción de nuestro primer dashboard de control en Looker Studio. Vaya a Google y escriba ‘Google Looker Studio’ y haga clic en el primer enlace . Una vez que se abra la interfaz, haga clic en ‘create blank document’ y cuando obtenga las opciones para seleccionar la fuente, seleccione ‘Google Big Query’ como se muestra a continuación.

[![Bgi-Queryfuente-Lokker.png](https://i.postimg.cc/jqNvXnJp/Bgi-Queryfuente-Lokker.png)](https://postimg.cc/yW1F6djj) * Seleccione BigQuery como fuente en Looker Studio*

Después de agregar BigQuery como fuente, es posible que necesites autorizarlo por primera vez. Publica el conjunto de datos y el nombre de la tabla que deseas cargar en el panel, y aparecerá como una tabla en el mismo. Tienes la opción de mantener o eliminar la tabla y diseñar el panel según tu preferencia. ¡Deja que tu creatividad fluya y personaliza tu tablero como desees!

**ESTA ES LA VERSION FINAL DEL DASHBOARD CONSTRUIDO** 

[![dashboard.png](https://i.postimg.cc/7Y93s3PW/dashboard.png)](https://postimg.cc/crKt68nR)
*Uber Dashboard en Looker*

Una vez finalizado este proyecto, mi siguiente paso sería replicarlo para otro caso de uso, ya que me ha brindado una valiosa experiencia en diversas tecnologías y me ha permitido superar varios desafíos en el camino. Espero que disfrutes explorando este fascinante mundo de la ingeniería de datos tanto como yo. También quiero expresar mi gratitud a Codigofacilito por ofrecer un excelente bootcamp de ingeniería de datos.
