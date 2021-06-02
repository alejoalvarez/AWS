# Cloud Practitioner

## Modelos de informática en la nube 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524619-dd4c1f00-c39c-11eb-80ee-3fa7e1f3ff69.png">
</p>

**SAAS (Software as a Service)**

El SASS (Software as a Service) o Software Como Servicio es aquel en donde la infraestructura, sistema operativo y software es proporcionado por un tercero. Un ejemplo de esto es el servicio de correo electrónico con servicios como Gmail, Outlook entre otros. Otro ejemplo es Dropbox que provee software como un servicio. Este tipo de modelo de software es muy común hoy en día.

**IASS (Infraestructure as a service)**

El IASS (Infraestructure as a Service) o Infraestructura como servicio esta constituido por el hardware requerido para ejecutar nuestra aplicación, es decir por ejemplo todos los recursos que se requieren para que un servicio como Gmail se ejecute, constituyen los elementos de la nube necesarios para que se pueda utilizar dicha aplicación. Cuando todos estos componentes son provistos por un tercero como computo, redes y almacenamiento, podemos hacer uso de estos para que en conjunto formen la infraestructura requerida para montar soluciones en la nube. Cuando utilizamos infraestructura como servicio básicamente estamos rentando esta infraestructura a un tercero. Para ello por lo general utilizamos un hypervisor que nos permite crear hardware requerido de forma virtual, y esto se hace utilizando a su vez un software. Para poder lograr esto el hypervisor crear maquinas virtuales. Una ventaja de utilizar estas maquinas virtuales es que podemos migrar dichas máquinas de un punto a otro. Al proveer acceso a dichas maquinas virtuales, podemos instalar nuestro propio sistema operativo y aplicaciones, esto es conocido como Plataforma como Servicio, y sobre esta plataforma es donde nuestro Software como Servicio vive.

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524692-f359df80-c39c-11eb-8411-fbcdd40cd37e.png">
</p>

**La nube privada**

Es donde controlas todo, se tiene su propio data center y dentro de este se encuentran sus dispositivos de almacenamiento. Las ventajas es que se puede controlar de forma total los componentes de forma directa. La desventajas son que se requiere una gran inversión en equipo, y la vida útil de este hardware es de un promedio de 3 años ademas del costo de salarios de empleados, electricidad, conectividad a Internet, etc.

**La nube híbrida**

En este modelo se combina una parte de la nube para algunos de los servicios como backup y recuperación de datos. Es decir que si no deseamos comprar discos duros todo el tiempo, podemos hacer uso de la nube para hacer copias de la información en caso de desastres. Para poder implementar este modelo es requerido cierto grado de conectividad entre su datacenter y el de la nube.

**La nube pública**

Brinda mucha flexibilidad, pero se requiere utilizar la infraestructura provista y pagar por lo que se va utilizando. La ventaja es que una ves que se dejan de utilizar estos servicios también se deja de pagar por su costo. Es infinitamente escalable y elástica, es decir que puede creer y reducirse en tamaño, y por lo general se cubren solo los costos de los recursos que se están utilizando. Es importante tomar en cuenta que tipo de proveedor se esta utilizando, ya que se desea que se pueda provisionar una red de forma rápida, que se ajuste al cambio continuo


## Zonas de disponibilidad
	
- AZ (Available Zone) Zona de disponibilidad (es donde esta el centro de datos), puede elegir la AZ pero no la región 
- Región (Conjunto de AZ) (Una region tiene varias zonas de disponibilidad, en promedio son 3 AZ por region)
- Hay 22 regiones (Una región es donde se guardan los datos) 
- También hay egges o bordes que se comunican con las regiones para formar el backbone de AWS 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524768-079ddc80-c39d-11eb-8274-e9f7c165d33d.png">
</p>

Para elegir región se usan 4 criterios: 

- Por leyes para saber si se debe guardar o no en esa región, ya que aplica la ley de donde se ponga la región 
- Por latencia, cuando demoramos en acceder 
- Disponibilidad de los servicios 
- Precio de los servicios 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524815-15536200-c39d-11eb-8af3-525a413946f3.png">
</p>

- mas de 205 edge
- Todos los edge tienen DNS 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524867-24d2ab00-c39d-11eb-8d79-16ea4c2748ce.png">
</p>

Formas de interactuar con AWS (Todo en AWS es una API)

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524929-33b95d80-c39d-11eb-9862-efdfcce8abaf.png">
</p>

## EC2  - Elastic Compute Cloud

- Son maquinas virtuales en línea, mejor llamadas instancias
- El procesamiento se cobra por hora
- Puedo seleccionar el sistema operativo que necesite
- Tienen CPU, RAM, uno o mas discos duros
- Generan llaves únicas para poder conectarte a tu maquina Linux o Windows de forma segura 
- Diversas opciones de espacio en disco duro, virtualmente infinito 
- Esta protegida por el Firewall (security group) luego por la subredes, luego por la VPC (y adicional se pueden poner WAF)
- Puedes tener diversas copias de la misma maquina en diversas regiones geográficas 
- Puedes controlar de manera muy fina desde donde se puede conectar uno a la maquina y por que puertos 
- Puedes optar por comprar una IP publica estática para que siempre puedas poner la ultima versión o la ultima maquina en esa IP 
- Puedes respaldar toda la maquina (Ambientes operativo, todo) cada que quieras 
- En cualquier momento se puede escalar a nivel de recursos (CPU, RAM, etc.) 
- Puedes copiar un snapshot a otras regiones, en caso de que cualquier cosa suceda en la que estas 
- Para las instancias nosotros somos los responsables de actualizar el OS 
- Nuestras instancias no se respaldaran sola, nosotros debemos hacerlo 
- Podemos hacer respaldos antes de hacer grandes cambios, para poder hacer rollback en caso de ser necesario
- Si se apaga el servidor adiós datos
- Cuando se crea una instancia de EC2 se debe seleccionar un SO el cual se encuentra en una AMI

**Ventajas**
- Elasticidad (crecer o decrecer según se requiera)
- Se tiene completo control puedo elegir el sistema operativo, hardware sobre el cual corre (cuando prender y apagar las instancias)
- Flexibilidad (Hay 5 tipos de instancias)
    - Nano
    - Micro
    - Small
    - Large
    - Extra large
- Se integra fácilmente con otros servicios AWS
- Disponibilidad (Ofrecen el 99.99% de disponibilidad)
- Seguridad
- Sencillo (se crean facilmente )

### Clasificación de instancias

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120524993-43d13d00-c39d-11eb-880f-bb60f3c96cdc.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525049-521f5900-c39d-11eb-90b2-4f16d10caa15.png">
</p>

## Almacenamiento de datos

## EBS (Elatic Block Store)

- Almacenan información en su propio disco (disco es llamado EBS, se le llama así por que AWS replica la información dentro de la misma AZ)
- Almacenamiento en bloque persistente para instancias
- Protegida a través de la replicación 
- Diferente tipos de unidades:
    - SSD (Unidades de estado solido)
	    - Volúmenes SSD de IOPS provisionadas (io1) (i01 es el mas rapido, por ende es el mas caro, tiene menor latencia)
		- Volúmenes SSD de uso general (gp2)
    - HDD (Unidades de disco duro)
	    - Volúmenes HDD optimizados para el rendimiento (st1) (st1 es lo mas barato por el ancho de banda)
		- Volúmenes HDD fríos (sc1)
- Aumento o reduzca la escala en minutos (Se pueden agregar 1 o n dispositivos de arranque)
- Pague solo por lo que se aprovisione
- Funcionalidades instantáneas
- Los datos no se pueden compartir dado que están en la misma instancia, si necesitamos compartir datos EBS no sirve
- Es como un disco USB, es decir un almacenamiento remoto de bloques que es persistente, se puede cambiar de maquina 
- Cuando la maquina se apaga no se borra el contenido

Pueden ser: 
- Locales - Almacenamiento de instancias, problema cuando la maquina se apaga y se pierden los datos, la idea es usarlo para datos temporales 
- Remotos 

Condiciones para usar EBS:
- Estar en la misma AZ  
- Solo puede estar en un solo servidor a la vez 

## S3 - Simple Storage Service

- Permite guardar archivos en su plataforma de tal forma tus instancias EC2, Lambda y otras son efímeras y puedes borrarlas sin preocupación alguna 
- S3 es un repositorio de archivos rápidos, perfecto para uso de una aplicación a la hora de crear, manipular y almacenar datos 
- S3 permite hacer respaldos en tiempo prácticamente real en otras regiones de AWS 
- S3 es elastic, se puede tener menos o mas recursos
- El almacenamiento de S3 es infinito
- Para comunicar los S3 desde el front a back debe tener CORS (Autorización de origen cruzado)
- No bloquea, es decir que el ultimo que grabe gana
- Los datos se almacen como objetos dentro de buckets
- 99,999999999 % perdurable (99 11)
- Puedo decidir en que region tenerlo
- Puedo dar acceso al bucket completo o atomicamente a los objetos que este tengo guardados
- S3 proporciona una interfaz de servicios web sencilla que se puede utilizar para almacenar y recuperar cualquier cantidad de datos, en cualquier momento, desde cualquier lugar en la web
- Escriba, lea y elimine objetos que contengan desde 1 byte hasta 5 terabytes de datos cada uno. El número de objetos que puede almacenar es ilimitado.
- Cada objeto se almacena en un bucket (balde) y se recupera mediante una clave única asignada por el desarrollador
- Puede elegir una región para optimizar la latencia, minimizar los costos o abordar los requisitos reglamentarios.
- Los objetos almacenados en una región nunca abandonan la región a menos que los transfieras
- Mecanismos de autenticación: se proporcionan para garantizar que los datos se mantengan seguros frente al acceso no autorizado.
- Los objetos se pueden convertir en privados o públicos, y los derechos de cabina se pueden otorgar a usuarios específicos.

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525156-711deb00-c39d-11eb-8ffe-b8edb19baa8b.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525212-7f6c0700-c39d-11eb-8d96-ad3f9b620cdb.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525268-901c7d00-c39d-11eb-9a24-bfc25dbed7be.png">
</p>

## S3 Glacier

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525311-9ca0d580-c39d-11eb-944f-b4414d3dbc24.png">
</p>

- AWS tiene un tipo de almacenamiento mas económico, pero mas lento llamado Glacier 
- Es una muy buena opción si tu tienes que ir guardando algún tipo de archivo histórico, por ejemplo documento de años pasados de transacciones 
- Glacier podrá entregar tus datos/archivos con tiempos de entre 2-15 minutos por archivo  
- Cuando se restaura se pone en S3, ya sea uno nuevo o una que ya este creado
- En S3 se habla de objetos, en glacier se habla de archivos
- Su tamaño es de 40 Teras

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525364-ad514b80-c39d-11eb-954e-f6e54d01613c.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525407-b93d0d80-c39d-11eb-8665-e7b57328c0c8.png">
</p>

## Proteccón de datos

## VPC

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525468-c659fc80-c39d-11eb-85d5-8d85eb1b73ba.png">
</p>

- El firewall que protege la instancia EC2 es comúnmente llamada Security Group
- Cuando creo la VPC defino la cantidad de direcciones IPC que va a tener, se debe tener mucho cuidado al momento de definir dicho rango 
- Red aislada personal a la cual nadie tiene acceso a no ser de que yo autorice 
- Esta definido sobre una región y sus correspondientes AZ
- Es como si fuera un muro para proteger ,is recursos del mundo exterior 
- Agrupar recursos (back, front, base de datos etc.) 
- Puede usar IPV4 o IPV6, para el curso se usa IPV4 
- Una VPC vive sobre una región 
- Una VPC es igual a una región que incluye varias AZ 
- AWS, se reserva los 4 mas bajos y el ultimo mas alto 
- Importante dividir mi red en subredes para tolerar fallas, es decir tenerlas sobre distintas AZ 
- Una subnet vive sobre una única AZ 
- VPC es región y subnet es igual AZ 
- Subnet - Aislar para tener seguridad, y para decir como alguna maquina puede acceder al mundo de internet 
- Subnet public - para que pueda hablar con el mundo exterior 
- Subent private - solo puede hablar localmente 
- La puerta hacia internet se llama internet gateway, y es la única forma de poder salir al mundo exterior 
- Internte gateway - es una especie de router, es gratis en todas las VPC, altamente portable, permite salir al mundo exterior 
- Elastic IP Adresses - son IP fijas, solo dan 5 por región, se debe usar en los siguientes 60 segundo para poder que no me la cobren 
- NAT gateway - Salida que no tiene entrada, la instancias se comunica con el Gateway para poder salir, que salga una IP privada para poder actualizar parches o algo por el estilo 
- Siempre mínimo 2 AZ 
- IP publica estática para que internet vea la subnet publica

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525543-d540af00-c39d-11eb-85c9-0e1347b32ba8.png">
</p>

- El security group puede ser asociada a una o a muchas instancias
- Solo reglas "permitir", sin reglas de "denegar" (por ejemplo desde que ip, desde que rango de ips)

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525582-e2f63480-c39d-11eb-8029-04db8f93dbde.png">
</p>

## Monitoreo

## CloudWatch

- Que esta sucediendo en la infraestructura o en los servidores  
- Las instancias tienen cloud watch 
- El Elastic Load Balancer (ELB) tiene cloud watch 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525631-f3a6aa80-c39d-11eb-85af-ba2b6fe5d5de.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525678-04efb700-c39e-11eb-987b-bcf99a1cbb83.png">
</p>

Beneficios de cloud watch:
- Acceder a todas las metricas desde una unica plataforma
- Mantener la visibilidad de sus aplicaciones, infraestructura y servicios
- Reducir el mean time to resolution (MTTR, tiempo promedio de resolución) y mejorar el costo of ownership (TCP, costo total de propiedad)
- Impulsar la información para optimizar las aplicaciones y los recursos operativos
- Pagar por uso

## Autoscaling

- Cloudwatch, EC2 autoscaling and ELB son los encargados de proporcionar el autoscaling
- EC2 auto scaling ajusta la capacidad según sea necesario
- Subir instancias cuando haya mayor demanda
- Bajar instancias cuando haya menor demanda
- Reemplazar instancias en mal estado
- Pago solo por lo que se utilice

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525744-15079680-c39e-11eb-8be3-a89140478bf9.png">
</p>

## ELB (elastic Load Balancing)
- Distribuye el tráfico de aplicaciones.
- Recibe en HTTP o HTTPS.
- El cliente se conecta a un endpoint o una ip pública que le pega directamente al Elastic load Balancer.
- Luego este componente enruta a instancias (las instancias pueden ser servidores por ejemplo NodeJS).
- El cloud Watch se pega al Elastic Load Balancer para poder monitorear el tráfico.
- Cuando se crea una nueva instancia se le avisa al balanceador para que este lo incorpore y pueda enrutar peticiones.
- El balanceador constantemente pregunta por el estado de salud de las N instancias que se tengan desplegadas.

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525913-46806200-c39e-11eb-8766-b9fd4a603f1a.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120525976-54ce7e00-c39e-11eb-8715-62255af58737.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530337-040d5400-c3a3-11eb-94a6-bd26acf04247.png">
</p>

## Servicio de base de datos

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530433-21422280-c3a3-11eb-85b2-e892c6439fd1.png">
</p>

## RDS - Amazon Relational Database Service

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530488-30c16b80-c3a3-11eb-9c83-4e653f20d6c9.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530572-4a62b300-c3a3-11eb-8062-5c22a339efc7.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530603-59e1fc00-c3a3-11eb-8076-930cc71d0054.png">
</p>

## DynamoDB

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530907-a0375b00-c3a3-11eb-8e78-8dbdf19889c3.png">
</p>

Las tablas pueden ser a nivel regional o a nivel global

Cuando usar DynamoDB:
- Aplicaciones web sin servidor
- Almacén de datos para microservicios
- Backends para aplicaciones moviles
- Tecnología de anuncios
- Videojuegos
- IoT

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120530995-ba713900-c3a3-11eb-9d52-d1ba37d9f62d.png">
</p>

Redshift permite almacenar millones de gigas es decir petabytes

## AWS Database migration Service

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531047-cd840900-c3a3-11eb-9ad6-47359df0763d.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531079-daa0f800-c3a3-11eb-9c02-e73bb7255c88.png">
</p>

## Automatización en la implementación

## CloudFormation
- Permite modelar y aprovisionar todos los recursos de la infraestructura en la nube
- Infraestructura como código
- Crea un stack con los aprovisionamientos que contenga el cloudFormation

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531131-ea204100-c3a3-11eb-8edc-9f99258bffa5.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531183-f6a49980-c3a3-11eb-94d7-e867f1a08eb9.png">
</p>

## Elastic beanstalk 
- Es una plataforma donde en pocos pasos, obtienes un balanceador de cargas y tantas instancias EC2 como uno indique 
- Posee auto scaling (aumentando dependiendo de los criterios, mas CPU, mas memoria etc.) 
- AWS Elastic Beanstalk provides a solution to quickly deploy and manage applications in the AWS Cloud 
- You simply upload your application and Elastic Beanstalk automatically handles the deployment details of capacity provisioning load balancing auto-scalling and application health monitoring  
- Amplia selección de plataformas para aplicaciones
- Variedad de opciones de implementación de aplicaciones
- Monitoreo
- Estado de la aplicación
- Administración y actualizaciones
- Escalado
- Personalización
- Los ambientes soportados son:
    - Docker image
	- Go
	- Java SE
	- Java con tomcat
	- .Net + windows server + IIS
	- NodeJS
	- PHP
	- Python
    - Ruby 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531235-091ed300-c3a4-11eb-9e4b-706848984bba.png">
</p>

## Conectar y compartir datos

## Direct Connect

Conexión de red dedicada entre sus instalaciones y AWS

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531328-1e93fd00-c3a4-11eb-92b7-9ec974370268.png">
</p>

## Rote 53
- Administrador de DNS (Sistema de nombres de dominio)
- Crea nuevos dominios (pruebas, calidad, producción) 
- Uno de los servicios mas interesantes de AWS 
- Comprueba el estado de los servicios
- AWS permite tener un DNS muy avanzado a tu disposición, con el podrás hacer subdominios asignados a instancias y verlos reflejados en segundos 
- Route53 esta disponible en todas las regiones de AWS, por lo que funcionará excelente aun en caso de que algunas de las regiones se pierda 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531393-32d7fa00-c3a4-11eb-9b69-889707f728fc.png">
</p>

## EFS (Elastic File System)
- Bajo costo
- Elasticidad dinámica
- Se puede modificar el objeto múltiples veces

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531470-497e5100-c3a4-11eb-9ce2-8af32fc660e5.png">
</p>

## Lambda y serverless 
- Es un lugar donde puedes ejecutar funciones de tu código 
- Se parece mucho al tema de microservicios (pequeñas unidades haciendo una tarea en especifico) 
- Serverless - No existe un servidor como vimos en EC2, es decir solo esta el código en lambda y AWS se encarga de ejecutarlo cuando necesites 
- Soporta varios lenguajes 
- Memoria mínima de 128 MB, máxima 3000MB con incrementos de 64 MB 
- Se puede correr tu aplicación hasta 300 segundos y tienes un tmp limitado a 512 
- Esta limitada a 1000 ejecuciones concurrentes ONCURRENTES , no tiene limites de ejecuciones secuencias (una tras otra) 
- Están corriendo varias lambas para los diferentes clientes de AWS, solo que son microambientes para cada uno  
- No debemos preocuparnos por la seguridad en AWS ya que ellos se encargan de esa tara 
- AWS monitorea constantemente la ejecución de tus funciones y se encarga de que siempre se tenga el mejor performance 
- Aunque el código este compartido en la infraestructura, este corre en un ambiente virtual exclusivo, aislado de todas las demás ejecuciones de lambda 
- Lambdas deben ser asíncronos 
- Las instrucciones de lamba se guardan en el CloudWatch  
- Administración totalmente automatizada
- Tolerancia a errores
- Pago solo por uso

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531617-73d00e80-c3a4-11eb-8bd9-d80893e95664.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531686-84808480-c3a4-11eb-9bc3-4eaff6296014.png">
</p>

Lambda necesita permisos, se asignan a través de el rol de ejecución

## SNS (Simple Notification Service)
- Servicio de mensajería de publicación o suscripción completamente administrada para aplicaciones distribuidas o sin servidor
- Entrega mensajes de manera fiable con durabilidad
- Escala automáticamente su carga de trabajo
- Simplifique su arquitectura
- Mantenga la privacidad y seguridad de los mensajes
- Servicio totalmente serverless

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531791-a11cbc80-c3a4-11eb-9e28-12739299e639.png">
</p>

## CloudFront

- Es un servicio web de entrega de contenido. Se integra con otros servicios en la nube de AWS para brindar a los desarrolladores y empresas una manera fácil de distribuir contenido a los usuarios en todo el mundo con baja latencia, altas velocidades de transferencia de datos y sin compromisos mínimos de uso. Amazon CloudFront se puede utilizar para ofrecer todo su sitio web, incluido contenido dinámico, estático, de transmisión e interactivo, mediante una red global de ubicaciones de borde. Las solicitudes de contenido se enrutan automáticamente a la ubicación de borde más cercana, por lo que el contenido se entrega con el mejor rendimiento posible a los usuarios finales de todo el mundo.
- Esta instalado en los edge
- Por ejemplo si un cliente tiene su pagina en virgina, y se va para australia, cuando intente ingresar desde australia, el cloudFront por medio del Edge va hasta virginia por la información, luego la cachea para que al proximo ingreso pueda obtener respuesta desde el edge de virginia

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531857-b1349c00-c3a4-11eb-9feb-69130e11563e.png">
</p>

## ElastiCache
- Almacén de datos en memoria completamente administrado y compatible con Memcached y Redis
- Optimiza consultas hacia base de datos
- Trabaja con la memoria RAM por eso es tan optimo a nivel de performance

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531920-c3aed580-c3a4-11eb-8bb6-0cb5ee08f4df.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120531976-d32e1e80-c3a4-11eb-8082-dfc9fffe3858.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532046-e640ee80-c3a4-11eb-8491-83a0a946ffac.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532113-f658ce00-c3a4-11eb-8bfd-a0cfd4acc5da.png">
</p>

## Responsabilidad compartida

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532176-05d81700-c3a5-11eb-8e8c-219b91847fb9.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532268-22744f00-c3a5-11eb-88e5-f085dfa0922c.png">
</p>

## Autenticación y autorización

## IAM  -  Identify and Access Management 
- Controle de forma segura el acceso a los recursos de AWS
- Manejar cuentas, y permitir acceso a ciertas maquinas o funcionalidades 
- Permite gestionar usuarios y sus niveles de acceso a la consola AWS 
- Permite un control centralizado de tu cuenta AWS 
- Permite crear accesos a otros usuarios con tu propia cuenta de AWS 
- Permite crear permisos específicos a cada usuario o grupo de usuarios 
- Permite autenticarse mediante directorio activo  
- Permite autenticarse con tu cuenta de facebook o linkedin 
- Permite la autenticación multifactor (con clave enviada al móvil) 
- Permite crear tu propia política de cambio de password (tipo y frecuencia) 
- Soporta PCI DSS (estándar de seguridad de datos para pagos con tarjetas) 

**Usuarios** - Son las diferentes personas que van a utilizar la consola de AWS 
**Grupos** - Son una colección de usuarios, cada usuario del grupo hereda los permisos del grupo 
**Políticas** - Las políticas se especifican en documentos, de tipo JSON, donde se otorgan permisos específicos sobre lo que se puede hacer un usuario, un grupo de usuarios o un rol 
**Roles** - Se asigna a recursos AWS para permitir que utilicen otros recursos de AWS, ejemplo en donde se crea un rol para que tu servicio de maquina virtual pueda utilizar tu servicio de S3 de almacenamiento de ficheros 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532321-31f39800-c3a5-11eb-922e-43abcb8cff20.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532389-3fa91d80-c3a5-11eb-8aab-3afd7ae599b8.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532480-53ed1a80-c3a5-11eb-8ef4-0bed10841bcb.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532551-60717300-c3a5-11eb-9bda-b83c5d538a3e.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532589-6cf5cb80-c3a5-11eb-8a9f-adc03fbc2d07.png">
</p>

## Niveles de seguridad y normatividad

## Amazon Inspector

Analiza la seguridad de las aplicaciones

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532634-7d0dab00-c3a5-11eb-9380-e1012fc839a1.png">
</p>

## AWS Shield
- Servicio de protección contra DDoS
- DDoS (Denegación de servicio)
    - El objectivo es tumbar el servicio o dejar por fuera cierta aplicación 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532687-8bf45d80-c3a5-11eb-8a0c-6089cda1c89c.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532726-99a9e300-c3a5-11eb-810a-64f38e90f154.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532829-b9d9a200-c3a5-11eb-917b-141cdd1374df.png">
</p>

## Precios

## EC2

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532891-ca8a1800-c3a5-11eb-95bd-610e8c36c423.png">
</p>

Tipos de instancias
- Ondemand 
    - Se arriendan por hora y son las mas caras, y son las que mas se usan no se sabe si es por desconocimiento 
	    - Deberían ser para periodos cortos o cuando no hayan ofertas 
- Reservadas 
    - Son por años o cierto tiempo son mas baratas que las ondemand 
    - Como mínimo por un año, también pueden ser por 1 año 
- SPOT 
    - Son las que están en oferta 
- Host dedicados
    - Servidor físico exclusivo
    - Aplicaciones con requisitos de normatividad especificos

## S3

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532952-d83f9d80-c3a5-11eb-8ed8-f9011d8908de.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120532998-e4c3f600-c3a5-11eb-824f-cbb83feb6494.png">
</p>

## EBS

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533086-fc9b7a00-c3a5-11eb-8237-5814691d7a81.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533154-0f15b380-c3a6-11eb-9d86-4f5ea135767e.png">
</p>

## AWS Cost Explorer

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533216-1e94fc80-c3a6-11eb-89ec-81f3b4dbcf5d.png">
</p>

## Trusted Advisor

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533279-2eacdc00-c3a6-11eb-995e-43e6394787db.png">
</p>

## Arquitectura

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533325-3d938e80-c3a6-11eb-96b3-b526b1d4e475.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533419-54d27c00-c3a6-11eb-985e-b587107375cb.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533497-63209800-c3a6-11eb-8080-f1ae216c8372.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533555-76336800-c3a6-11eb-964b-326e6e88de92.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533606-85b2b100-c3a6-11eb-9717-991bb48c618b.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533663-982cea80-c3a6-11eb-8f17-91cc7ad8c336.png">
</p>

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533709-a549d980-c3a6-11eb-9564-745e9f306aa7.png">
</p>

## Arquitectura de referencia 

<p align="center">
<img height="450" src="https://user-images.githubusercontent.com/13514156/120533764-b5fa4f80-c3a6-11eb-93a3-fe7bafb6a9e5.png">
</p>

