#UNIVERSIDAD DE CÓRDOBA
#Departamento de Informática y Análisis Numérico

#Ingeniería del Software, Conocimiento y Bases de Datos

Campus Universitario de Rabanales Edificio Albert Einstein, Planta 3 14071 Córdoba (ESPAÑA)

ALLINONE
1. Introducción Este documento describe las características de un problema simulado del mundo real para que sea resuelto por los alumnos del Grado de Informática en el desarrollo de la asignatura de Ingeniería del Software. El análisis y diseño de una solución software requiere del estudio conjunto de la información que será manejada por el sistema y de la funcionalidad que tendrá asociada el sistema para dar respuesta a los requisitos y objetivos perseguidos por el cliente. 

2. Descripción del problema El sistema software (AllinOne) es una aplicación móvil cuya funcionalidad es la de integrar a diferentes sistemas de mensajería que están (o estarán) disponibles en el mercado y que son utilizados por los usuarios móviles. Su finalidad es que con una única aplicación los usuarios puedan utilizar la mensajería push de sistemas como Whatsapp, Telegram, etc., y mensajería instantánea integradas en redes sociales como Facebook (messenger). 

Las características básicas de la aplicación son las siguientes: 
- Los usuarios deben descargarse la aplicación desde los almacenes disponibles para el sistema operativo de su dispositivo móvil. 
- El registro en el sistema es obligatorio y puede realizarse en el sistema o a través de las cuentas Facebook, Twitter, Gmail o iTunes. 
- El coste de la aplicación es gratuito, aunque la aplicación puede tener recursos o extras que el usuario puede contratar (por ejemplo, emoticonos). 
- El usuario puede personalizar el sistema seleccionando el motor/aplicación de mensajería que utilizará para enviar sus mensajes. 
- En el registro debe indicarse el número de teléfono del dispositivo, datos del usuario y correo electrónico. Un usuario que disponga de más de un dispositivo no requiere de un nuevo registro de usuario por cada dispositivo, pero sí registrar el dispositivo en el sistema. 
- El proceso de registro requiere una confirmación del usuario que realiza en base a un correo electrónico o SMS en el que se le envía un código de seguridad para confirmar el registro.
- El sistema en cada momento tendrá constancia de los usuarios conectados al sistema (aquellos usuarios dados de alta que tengan su terminal móvil encendido) y aquellos usuarios desconectados. 
- Los administradores del sistema en cualquier momento podrán solicitar al sistema información de cualquier usuario y estadísticas del uso del sistema por parte de los usuarios del mismo. 

La funcionalidad principal de este sistema básicamente es la siguiente: 
- El usuario se descarga la aplicación, se registra y configura. 
- La configuración del sistema supone activar el envío de mensajes a través de ninguna (el propio sistema), una o varias de las aplicaciones externas reconocidas por el sistema. Para utilizar estas plataformas externas el usuario debe estar dado de alta en ellas previamente (Whatsapp, Facebook, etc.) 
- La configuración del envío del mensaje puede realizarse: 
	a) Se envía el mensaje al receptor por el sistema únicamente. 
	b) Se envía por el sistema y una o varias de las plataformas externas disponibles para el receptor. Sólo se puede enviar por plataformas externas si estas están habilitadas por el receptor. 
	c) Se envía sólo por el sistema y si no hay confirmación de lectura en un tiempo definido se envía en orden por una lista de las plataformas externas disponibles para el receptor (hasta confirmación de lectura). 
	d) Cuando el sistema envía un mensaje, el receptor recibe una notificación. 
	e) Independientemente de la plataforma utilizada para enviar el mensaje, el receptor accede a los mensajes a través de la aplicación móvil. 

La información que desea mantener referente al problema es la siguiente: 

1. Sobre las personas 
- Los nombres, apellidos, dirección, número de teléfono, etc. 
- El identificador del teléfono móvil asociado al usuario del sistema. 
- Logueo/identificación de acceso a aquellas plataformas externas que desea utilizar para el envío y recepción de mensajes (Facebook, Google, etc.). 
- La aplicación AllinOne dispone de funcionalidad que posibilita a los usuarios crear contactos, examinar contactos y sus datos, así como conocer las plataformas habilitadas por cada contacto. 

- El identificador del teléfono o registro del usuario en el subsistema de notificaciones de la aplicación. 
- Una persona puede tener uno o varios dispositivos móviles y tener instalada la aplicación en uno o varios de los dispositivos. 

3. Sobre los Mensajes 
- Los mensajes son enviados a dispositivos cuando son remitidos únicamente a través del sistema, por lo que en este caso un mensaje solo es recibido en uno de los teléfonos móviles propiedad de un usuario 
- Cuando los mensajes son emitidos a través del sistema y plataformas externas, el mensaje llega a todos los dispositivos del usuario en los que tenga habilitado en su configuración la plataforma externa por la que se envió el mensaje. 
- La recepción de un mensaje supone siempre una notificación por parte del sistema en el/los dispositivos receptores. 
- Las notificaciones informan de: 
	a) emisor, 
	b) plataformas de emisión, 
	c) texto corto del mensaje (si lo hay). 
- El estado de las notificaciones. Las notificaciones enviadas por el sistema pueden ser fallidas o exitosas. Aunque una notificación llegue al receptor, el receptor puede no leerla, borrarla sin leer o leerla. 
- Los emisores de los mensajes sólo conocen el estado de sus mensajes dependiendo de si el receptor da permiso en su configuración. 
- Los mensajes pueden enviarse a: 
	a) Un único dispositivo 
	b) A un conjunto de dispositivos 
	c) A un único receptor (todos sus dispositivos) 
	d) A un conjunto de receptores (todos sus dispositivos). 

4. Sobre la configuración 
- Los usuarios pueden configurar la aplicación de igual o diferente forma en cada uno de sus dispositivos.
- En la configuración, como se ha descrito anteriormente, se establece las plataformas de envío de mensajes y el mecanismo de envío. 
- En la configuración se establece las plataformas de recepción de mensajes permitidas para que otros usuarios las utilicen en el envío de mensajes. 
- En la configuración también se establecen otras opciones de usabilidad, como por ejemplo: sonido, tono, uso de redes, etc. 
- El usuario puede cancelar su suscripción al servicio en cualquier momento, así como cambiar la configuración. 

5. Sobre el Sistema 
- El sistema mantendrá información de los usuarios, sus datos de configuración y preferencias, el uso del sistema y su actividad. 
- El sistema mantendrá información durante 12 meses del contenido y plataformas utilizadas para el envío de mensajes y la actividad realizada. 
- El sistema mantendrá durante 24 meses los datos del usuario aunque se hayan dado de baja. 
- El sistema dispondrá de herramientas para la realización de estadísticas personalizadas, por grupos de usuarios, regiones, plataformas, etc. Considerando esta información se debe diseñar un sistema software mediante el cual pueda llevar a cabo los siguientes procesos: 
	1. La consulta completa por parte de los administradores del sistema de toda la información acerca de los usuarios y uso por parte de estos del mismo. 
	2. El uso del sistema por parte de los usuarios, es decir: los usuarios podrán conectarse, desconectarse, enviar y recibir mensajes. 
	3. El envío de mensajes desde el sistema a los usuarios, los cuales siempre van acompañados de notificaciones previas. 

Estos mensajes consistirán en: 
- Mensajes comunicando nuevos "extras" que pueden ser utilizados o contratados por los usuarios 
- Mensajes de error comunicando cualquier error que se produzca por el mal uso del sistema por parte de los usuarios.

Ingeniería del Software
