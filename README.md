# :chart_with_upwards_trend:  Data Viz Challenge :chart_with_downwards_trend:
## Desafío: 
### Utilizando un conjunto de datos sobre el historial de visualizaciones de clientes en la plataforma Flow: “Armar una visualización efectiva que ayude a entender/describir el data set y obtener insights” 
## Evaluación:
- 50% Entendimiento: ¿Con qué eficacia la visualización comunica los datos? ¿Cómo ayuda a dar sentido al conjunto de datos? ¿La visualización es clara para un no especialista?       
- 25% Diseño y originalidad: ¿La visualización demuestra un enfoque novedoso del problema? ¿Se presenta la solución de una manera elegante y pulida?
- 25% Utilidad: ¿Es interactivo? ¿Sería útil esta visualización?

## Herramientas a utilizar:

Se aceptaran proyectos desarrollados con cualquier tecnología que permita visual la entrega de los mismos a partir de archivos con formatos de tipo abierto o enlaces web de acceso público.
    Algunas de las opciones disponibles son:

### Tecnologías abiertas:
        Python (matplotlib, Seaborn, Bokeh, Dash, Flask, plotly, etc)
        R (Shiny, ggplot2, ggplotly, etc.)
        D3 JS.

### Otras tecnologías:
        Power Bi* 
        Tableau*
        QlickView*
        Flourish*




*Si bien no existen limitaciones en cuanto al software a utilizar, no se aceptaran archivos de extensiones propietarias tales como .pbix, .twb, etc. En caso de realizar el desarrollo en una tecnología con formatos propietarios, este deberá disponibilizarse a través de una URL pública.

## Entrega
   Se aceptarán distintos tipos de formatos abiertos tales como jpg, png, GIF, mp4, HTML o URL públicas donde se pueda consumir el desarrollo.
   
   **Es condición necesaria que la cantidad de visualizaciones presentadas sea menor o igual a 3. En caso de presentar más de 3 visualizaciones, se tendrán únicamente en cuenta las primeras 3.**
 


### Links importantes :grey_exclamation:

* [Campus Party Digital Edition - Argentina](https://digital.campus-party.org/argentina/)
* [Bases y condiciones](https://drive.google.com/file/d/1ND9V-XvLQgkSGZXpgk_hWjvgSDYEM_e4/view)
* [Inscripción](https://docs.google.com/forms/d/e/1FAIpQLSchI6rmCK5D9ZE9R91Jbxzjl3qB8wjH562DgAnFCEqUReV4pQ/viewform)
* [Link de entrega](https://forms.gle/AUANke251L1Ea3S78)

## Datasets :open_file_folder:
Para el desarrollo del recomendador, se proveen los siguientes conjuntos de datos:
* **train.csv**
* **metadata.csv**
* **iso_3166_1.json**

Estos archivos pueden ser descargados desde [aquí](https://drive.google.com/drive/folders/1_CFg8F6kLzDCewceqPEvf66pzG6Y_s7y?usp=sharing).

##### **train.csv**
Este dataset contiene los registros de visualizaciones de contenidos de Flow del formato *video on demand* (VOD), correspondiente a una muestra aleatoria de más de 113 mil perfiles. A continuación, se detalla el diccionario de variables de esta tabla:
- **customer_id**: código de identificación de cada cliente de Flow (puede tener asociados uno o más **account_id**)
- **account_id**: código de identificación de cada perfil de Flow (se corresponde con un único **customer_id**)
- **device_type**: indica el tipo de dispositivo desde el que se efectuó la visualización. Las categorías posibles son:
    - CLOUD: cliente web
    - PHONE: teléfono celular
    - STATIONARY: *smart* TV
    - STB: *set-top box*, el decodificador Flow
    - TABLET
- **asset_id**: código de identificación de cada activo (video) disponible en la plataforma
- **tunein**: fecha y hora de inicio de cada visualización
- **tuneout**: fecha y hora de finalización de cada visualización
- **resume**: variable *dummy* que indica si se reanuda un consumo anterior del mismo **asset_id**

Así se ven algunos registros de esta tabla:

|customer_id|account_id|device_type|asset_id|             tunein|            tuneout|resume|
|-----------|----------|-----------|--------|-------------------|-------------------|------|
|      14758|     37750|      PHONE|   17473|2021-02-14 20:53:00|2021-02-14 21:31:00|     0|
|      14759|     37751|        STB|   12589|2021-03-25 22:05:00|2021-03-25 22:08:00|     0|
|      14760|     37752|        STB|   24534|2021-01-15 15:35:00|2021-01-15 17:06:00|     1|
|      14760|     37752|        STB|   32059|2021-01-30 10:22:00|2021-01-30 10:41:00|     0|
|      14760|     37752|        STB|   29982|2021-01-30 10:41:00|2021-01-30 12:28:00|     0|

##### **metadata.csv**

Contiene la metadata asociada a cada uno de los contenidos. Las variables incluidas son:
- **asset_id**: código de identificación de cada activo (video) disponible en Flow
- **content_id**: código de identificación que agrupa los distintos **asset_id** asociados a un mismo contenido (por ejemplo, cada episodio de una misma serie tiene su propio **asset_id**, mientras que la serie se identifica con un **content_id** único)
- **title**: título
- **reduced_title**: título reducido
- **episode_title**: título del episodio (válido para contenidos episódicos, como las series)
- **show_type**: tipo de show - las categorías son autorreferenciales con excepción de “Rolling”, que indica que se trata de una serie incompleta, y “Web”, la cual remite a  contenidos pensados íntegramente en formato digital (series web) -
- **released_year**: año de lanzamiento
- **country_of_origin**: país de origen – expresado con el código de dos letras propio del estándar internacional de normalización ISO 3166 -
- **category**: categoría o género al que pertenece el contenido - puede haber una o más -
- **keywords**: palabras clave o *tags* asociadas al contenido - puede haber una o más -
- **description**: descripción (sinopsis)
- **reduced_desc**: descripción (sinopsis) reducida
- **cast_first_name**: nombre y apellido de los actores y actrices principales
- **credits_first_name**: nombre y apellido del director o directora
- **run_time_min**: duración total, expresada en minutos
- **audience**: audiencia *target*
- **made_for_tv**: variable *dummy* que indica si el contenido fue hecho para TV
- **close_caption**: variable *dummy* que indica si el contenido posee subtítulos
- **sex_rating**: variable dummy *que* indica si el contenido tiene escenas de sexo explícitas
- **violence_rating**: variable *dummy* que indica si el contenido tiene escenas de violencia explícitas
- **language_rating**: variable *dummy* que indica si el contenido posee lenguaje que puede ser considerado ofensivo o inapropiado
- **dialog_rating**: variable *dummy* que indica si el contenido posee diálogos que pueden ser considerado ofensivos o inapropiados
- **fv_rating**: variable *dummy* que indica si el contenido tiene rating de FV, que corresponde a público infantil con violencia ficticia
- **pay_per_view**: variable *dummy* que indica si se trata de un alquiler
- **pack_premium_1**: variable *dummy* que indica si se trata de un contenido exclusivo del pack premium 1
- **pack_premium_2**: variable *dummy* que indica si se trata de un contenido exclusivo del pack premium 2
- **create_date**: fecha de creación del activo
- **modify_date**: fecha de modificación del activo
- **start_vod_date**: fecha desde la cual el activo se encuentra disponible en la plataforma
- **end_vod_date**: fecha de finalización de la disponibilidad del activo  en la plataforma

##### **iso_3166_1.json**

Este archivo constituye un diccionario de los códigos de nombres de países propios del estándar internacional de normalización ISO 3166. En este json, las claves corresponden a los códigos de dos letras y los valores, a los respectivos nombres de cada país.

Siempre que lo consideren relevante, los participantes podrán incorporar cualquier otra información externa a este conjunto de datos y metadatos.



 
  

