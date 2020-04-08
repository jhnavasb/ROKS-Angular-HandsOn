# ROKS-Angular-HandsOn

# GUIA DE INSTALACIÓN Y DESPLIEGUE DE APP ANGULAR EN OPENSHIFT

_Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en el lenguaje de programación angular y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**._

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

### Haga 'login' a IBM Cloud desde la línea de comando

_Inicialmente debe acceder al shell de IBM Cloud desde el siguiente link:_
```
https://cloud.ibm.com/shell
```
_1.	Inicie sesión desde la consola de IBM Cloud Shell, para hacerlo utilizamos el siguiente comando:_

```
ibmcloud login --sso
```
_Al digitar el comando anterior nos aparece una pregunta la cual debemos responder con una **Y**_

_En este momneto nos pide un codigo de seguridad, el cual debemos obtener en el siguiente link y pegarlo en la consola de IBM Cloud Shell._
```
https://identity-2.us-south.iam.cloud.ibm.com/identity/passcode
```
_Al digitar el comando anterior nos aparecera una pregunta en la cual debemos indicar el numero perteneciente a la cuenta en la que se va a trabajar._

_2.	Configure el entorno de trabajo. Es necesario asignar (target) la region y el grupo de recursos, en donde esta desplegado el cluster de Open Shift, que vamos a utilizar en el ejercicio._

_Para esto debe colocar el siguiente comando en la terminal._
```
ibmcloud target -r us-east -g openshift-workshop
```
_De este modo tenemos el 'login' en IBM Cloud y el ingreso por linea de comando al cluster de Open Shift, para iniciar para el despliegue de la aplicación._


### Acceda el cluster de Open Shift (ROKS) desplegado en IBM Cloud 📦


_3.	Inicie sesión e ingrese desde la CLI de OpenShift al clúster en el que se va a trabajar._

_Para ingresar al clúster que tengamos aprovisionado en nuestra cuenta de IBM Cloud se deben realizar los siguientes pasos:_

_•	Ingresar a la plataforma de IBM cloud con sus credenciales de inicio de sesión, lo puede hacer desde el siguiente link:_

```
https://cloud.ibm.com/
```

_•	Diríjase al resource list._
_Primero debe dar clic en el navigation menu y luego donde dice Resource list, como se puede ver en la siguiente imagen:_

<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">


_•	Diríjase a la sección de clústers y dar clic en el que se desea acceder._

_•	Se da clic en el botón OpenShift web console._

### Haga 'login' en el cluster de Open Shift (ROKS) desde la linea de comando 📦

_•	Ahora en la parte superior derecha se da clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command._

<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">

_•	Y por último volvemos a la terminal que se estaba utilizando pegamos y damos enter._

### Cree un nuevo proyecto en Open Shift para desplegar las aplicaciones 📦

_4.	Cree un nuevo proyecto en el cluster de la siguiente manera:_
```
oc new-project <projectname>
```
_**Nota:** Para el **projectname** coloque **openshift + las iniciales de su nombre y apellido.**_

_5.	Acceda al proyecto que acabo de crear de la siguiente manera:_

```
oc project <projectname>
```

## Despliegue Aplicación Hello World en Angular 📦

_6.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de hello Word en angular:** https://github.com/emeloibmco/AngularHelloWorld_


_7.	Desde el Shell de IBM cloud digite el comando:_

```
git clone <url_repositorio>
```
_8.	Dirigirse desde a esta carpeta con el comando:_

_•	Para la carpeta del proyecto Hello word:_
```
cd AngularHelloWorld
```
_9.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:_
```
npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```
_El resultado de este comando va a ser una respuesta de este tipo, que nos indica que 
la aplicación se desplego correctamente._

<img width="865" alt="2" src="https://user-images.githubusercontent.com/60987042/76918560-9441a500-6894-11ea-954f-62c8076b8903.PNG">

_10.	Para poder acceder al la URL de la aplicación y realizar la verificación de la misma debemos:_

_•Acceder a IBM cloud._

_•Dirigirse al resource list._

_•Dirigirse a la sección de clusters._

_•Ingresar al cluster que lleva por nombre openshift.311._

_•Ingrese a la sección de openshift web console._

_•Buscar el proyecto que creo con sus iniciales y buscar la aplicación que se desplego._

![11](https://user-images.githubusercontent.com/60987042/77017977-f9a39d80-6949-11ea-8b26-4b301e9490f2.png)

_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._


![12](https://user-images.githubusercontent.com/60987042/77018166-89494c00-694a-11ea-9f7e-f05d109631d0.png)


_De esta forma se daría por terminado el despliegue de la aplicación angular en openshift._

## Despliegue Aplicación Lista en Angular 📦

_11.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de listas en angular:** https://github.com/emeloibmco/AngularWebList_

_12.	Desde el Shell de IBM cloud digitar el comando:_

```
Git clone <url_repositorio>
```
_13.	Dirigirse desde a esta carpeta con el comando:_

•	Para la carpeta del proyecto listas.
```
cd AngularWebList
```
_14.	Para desplegar la aplicación en OpenShift es necesario escribir el siguiente comando:_
```
npx nodeshift --strictSSL=false --dockerImage=nodeshift/ubi8-s2i-web-app --imageTag=10.x --build.env OUTPUT_DIR=dist/angular-web-app --expose
```
_15. Para confirmar que la aplicación ha sido desplegada busque la aplicación en el proyecto creado en la consola Web d Open Shift, y seleccione el link con el enlace a la aplicación.

<img width="789" alt="3" src="https://user-images.githubusercontent.com/60987042/76919117-f222bc80-6895-11ea-835e-cb689f2b61bb.PNG">


_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._

<img width="688" alt="4" src="https://user-images.githubusercontent.com/60987042/76919471-074c1b00-6897-11ea-95c7-e8675b91ec80.PNG">


## Despliegue Aplicación Hello World en Nodejs Desde la consola wed de OpenShif 📦

_Para realizar el despliegue desde la consola web de OpenShif de una  manera mas intuitiva se deben seguir los siguientes pasos:_

_1. Ingrese a IBM cloud desde el siguiente link:_
```
https://cloud.ibm.com/login
```
_2. Realice el login con sus credenciales de ingreso._

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
---

_3. Dirijase al resource list._

---
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
---

_**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257_......**_

_4. Dirigirse a la sección de clusters._

---
![111111111111](https://user-images.githubusercontent.com/60987042/77703986-1ebb9000-6f8a-11ea-8593-79b70b9e85b7.png)
---

_5. Ingresar al cluster que lleva por nombre openshift.311._

_6. Ingrese a la sección de openshift web console._

![22222](https://user-images.githubusercontent.com/60987042/77704788-e0bf6b80-6f8b-11ea-95d4-0cd24368b721.png)

_7. En este momento estamos en el catalogo de OpenShift, ahora se debe seleccionar la opcion Node.js_
---

![333](https://user-images.githubusercontent.com/60987042/77705089-c33ed180-6f8c-11ea-987b-c2758d96dec9.png)

---
_8. Una vez seleccionada, presione "Next" y proporcione el nombre de la aplicación, la URL del git donde se encuentra el proyecto a desplegar y presione "Create"._

<p align="center">
<img width="668" alt="img7" src="https://user-images.githubusercontent.com/40369712/77024355-527c3180-695c-11ea-8f74-d58c9d5c8999.png">
</p>

_si desea desplegar desplegar un HelloWord de nodejs puede utilizar el siguiente repositorio de github:_
```
https://github.com/openshift/nodejs-ex.git
```

_9. Para ver el link de despliegue se debe dar clic en "Continue to the project overview"._

![555](https://user-images.githubusercontent.com/60987042/77705724-680dde80-6f8e-11ea-8736-2f7ba04e45c2.png)

---

**Nota:** Espere unos mintos mientras el proceso de construcción y despliegue de la aplicación se termina.

---

_10. Una vez terminado el proceso de despliegue puede dirigirse a Overview, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada._


![66666](https://user-images.githubusercontent.com/60987042/77705939-0437e580-6f8f-11ea-80f7-f8945d7cce92.png)


## Despliegue de una imagen Docker en un contenedor de Opeshift 📦

_Para realizar el despliegue de una aplicación que se encuentra alojada en un una imagen de DockerHub se deben realizar los siguintes pasos:_


_1. Ingrese a IBM cloud desde el siguiente link:_
```
https://cloud.ibm.com/login
```
_2. Realice el login con sus credenciales de ingreso._

---
![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)
---

_3. Dirijase al resource list._
---
<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
---

_**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257**._

_4. Dirigirse a la sección de clusters._

---
![111111111111](https://user-images.githubusercontent.com/60987042/77703986-1ebb9000-6f8a-11ea-8593-79b70b9e85b7.png)
---

_5. Ingresar al cluster que lleva por nombre openshift.311._

_6. Ingrese a la sección de openshift web console._

![22222](https://user-images.githubusercontent.com/60987042/77704788-e0bf6b80-6f8b-11ea-95d4-0cd24368b721.png)

_7. Ahora debemos seleccionar el proyecto en el que queremos trabajar o creamos uno._

![7777](https://user-images.githubusercontent.com/60987042/77706550-b3c18780-6f90-11ea-803e-4e74478cee69.png)

_8. Dar clic en la sección **Add do Project** y luego en la sección ***Deploy Image*._

![888](https://user-images.githubusercontent.com/60987042/77706608-e1a6cc00-6f90-11ea-97fe-bc39d4f4f87c.png)

_9. Al dar clic en Deploy Image se abre una ventana en la cual debemos seleccionar el campo **Image Name** y llenar el campo con la ruta fuente de la imagen docker, y dar enter._

![101010](https://user-images.githubusercontent.com/60987042/77706930-bbcdf700-6f91-11ea-8442-26569c617234.png)


_10. Si reconoce la imagen docker, se debe habilitar la opción para dar clic en **Deploy**_, y al dar clic acá se inicia a desplegar la aplicación por lo que se debe esperar un momento minetras se realiza el despliegue.

_11. Una vez terminado el proceso de despliegue puede dirigirse a Overview, donde podra ver la URL mediante la cual podra acceder a la aplicacion ya desplegada._


![66666](https://user-images.githubusercontent.com/60987042/77705939-0437e580-6f8f-11ea-80f7-f8945d7cce92.png)


## Configurar el Auto escalamiento de Pods en un despliegue de Opeshift 🛠️

Para poder configurar el auto escalamiento de pods de una aplicación de OpenShift debemos seguir los siguinetes pasos:

_1. Ya estando en la pagina principal de OpenShift en IBM cloud, primero debemos ingresar al proyecto que se quiere configurar._

_2. Damos clic en la sección **Applications** y despues donde dice **Deployments**, y ahi buscamos nuestro proyecto y le damos clic._

![1111121212](https://user-images.githubusercontent.com/60987042/77762008-e312db80-7006-11ea-83e0-1cfaf2381db8.png)

_3. Al entrar en nuestro proyecto debemos dar clic en la parte superior derecha, en la sección que dice **Actions*._

![2222121](https://user-images.githubusercontent.com/60987042/77762404-79470180-7007-11ea-987d-d255a7051a09.png)

_4. Dar clic en la sección **Add Autoscaler**._

![autoS](https://user-images.githubusercontent.com/60987042/77762560-b8755280-7007-11ea-92c1-eee23914c7b0.png)

_5. llenamos cada uno de los campos según los requeriminetos que tengamos del numero de pods y del % de CPU, y finalizamos dando clic en **save**._


![ConfAuto](https://user-images.githubusercontent.com/60987042/77762729-f8d4d080-7007-11ea-89e3-ec427faa67af.png)

_6. Verificar si la aplicación quedo aprobiconada con el autoescalamineto._

_Para verificar este paso, damos clic en **Overwiew** y miramos si efectivamente se configuro con Autoscaler._

![wiew](https://user-images.githubusercontent.com/60987042/77763353-edce7000-7008-11ea-92a3-6b05b1afcae7.png)

__


## Despliegue Aplicación CRUD en Angular 📦

Como ejercicio OPCIONAL se puede realizar el despligue de una aplicación en una arquitectura multi-capa.  Esta aplicación de ejemplo es una aplicación que permite crear transacciones (giros), que son almacenados en una base de datos.   

La aplicación esta compuesta por 3 contenedores: 

- Front, front desarrollado en Angular, para la interfaz de usuario Web
- CRUD,  backend desarrollado en express, que expone API's para la operaciones hacia la base de datos
- MongoDB, un contenedor con el motor de la base de datos MongoDB

Para realizar este ejercicio, se pueden seguir las siguientes guias, en donde se encuentra el código de la aplicación de ejemplo: 

Despliegue de base de datos y back-end de la aplicación:
https://github.com/emeloibmco/AngularWebCRUDMongo

Despliegue de front de aplicación:
https://github.com/emeloibmco/AngularWebFrontCRUD

Es recomendable realizar el despliegue del back-end, y luego el despliegue del front.  Se requiere modificar las credenciales y las URL's especificas cuando para completar el ejercicio. 

Como ejercicio adicional, se recomienda configurar ConfigMap para utlizar parametros en variables de ambiente  para las URL's, y Secrets para almacenar credenciales y contraseñas en Open Shift.

La siguiente es la URL de el despliegue de esta aplicación demo:
http://efecty-app-default.openshift311-ea9753cca330b7f05a99ad5b2c8b5da1-0001.us-east.containers.appdomain.cloud/inicio


# _ANEXOS._

_Si se desea realizar el mismo despliegue desde la cli, pero desde la maquina local se deberían seguir los siguientes pasos:_

## Pre-requisitos 📋

_Paso 1: Instale IBM Cloud CLI._

_Instale la interfaz de la línea de comandos de IBM Cloud así:_

_**Para Mac y Linux ™**_
_Ejecute el siguiente comando en la terminal:_
```
curl -sL https://ibm.biz/idt-installer | bash
```
_**Para Windows™ 10 Pro**_
_Pulse con el botón derecho del ratón el icono de Windows™ PowerShell y seleccione **Ejecutar como administrador**, efectué el siguiente comando:_

```
[Net.ServicePointManager]::SecurityProtocol="Tls12";iex(New-Object Net.WebClient).DownloadString('https://ibm.biz/idt-win-installer')
```

_Paso 2: Verificar la instalación._
_Para verificar que las herramientas de desarrollador y la CLI se han instalado correctamente, ejecute el comando **help**:_

```
ibmcloud dev help
```
_Paso 3:	Instalar CLI de OpenShift._

_Desde el siguiente link podremos descargar el respectivo instalador._

```
https://www.okd.io/download.html
```

_Para instalarlo debemos descomprimir la carpeta, encontraremos los siguientes archivos:_

<img width="513" alt="5" src="https://user-images.githubusercontent.com/60987042/76979004-60529800-6905-11ea-9830-5d28e2d5c4af.PNG">

_De estos archivos debemos copiar el que tiene por nombre oc y pegarlo en la carpeta bin que encontramos en la siguiente dirección:_

```
C:\Program Files\IBM\Cloud\bin
```
## Referencias

La documentación en linea de IBM Cloud Red Hat OpenShift Managed, se encuentra en el siguiente enlace:

https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started

En la siguiente página se encuentra la información de administración y configuración de Open Shift 3.11.

https://access.redhat.com/documentation/en-us/openshift_container_platform/3.11/

## Autores ✒️

_Equipo IBM Cloud Tech sales Colombia._

