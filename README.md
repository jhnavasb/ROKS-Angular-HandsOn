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

_2.	Configure el entorno de trabajo. Es necesario asignar (target) la region y el grupo de recursos, en donde esta desplegado el cluster de Open Shift, que vamos a utilizar en el ejercicio.

Para esto debe colocar el siguiente comando en la terminal._
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
Git clone <url_repositorio>
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

## Despliegue Aplicación Hello World en Nodejs Desde la consola wed de OpenShif 📦

_Para realizar el despliegue desde la consola web de OpenShif de una  manera mas intuitiva se deben seguir los siguientes pasos:_

_1. Ingrese a IBM cloud desde el siguiente link:_
```
https://cloud.ibm.com/login
```
_2. Realice el login con sus credenciales de ingreso._

![Captura de pantalla de 2020-03-26 17-25-55](https://user-images.githubusercontent.com/60987042/77702638-f8482580-6f86-11ea-9a83-9714df69ec38.png)

_3. Dirijase al resource list._

<img width="696" alt="7" src="https://user-images.githubusercontent.com/60987042/76996077-da434b00-691e-11ea-92be-558da48f7d97.PNG">
_**NOTA:** En la parte superior derecha al lado de "Manage", aparece las diferentes cuantas que tiene disponibles para trabajar. Para este caso debe asegurase que se encuentre en la cuenta:**1699257_......**_

_4. Dirigirse a la sección de clusters._

![111111111111](https://user-images.githubusercontent.com/60987042/77703986-1ebb9000-6f8a-11ea-8593-79b70b9e85b7.png)

_5. Ingresar al cluster que lleva por nombre openshift.311._

_6. Ingrese a la sección de openshift web console._

![22222](https://user-images.githubusercontent.com/60987042/77704788-e0bf6b80-6f8b-11ea-95d4-0cd24368b721.png)

**a.** Dirijase al catalogo y seleccione la opcion Node.js

**b.** Una vez seleccionada, presione "Next" y proporciones el nombre de la aplicación, la URL del git donde se encuentra el proyecto a desplegar y presione "Create".

<p align="center">
<img width="668" alt="img7" src="https://user-images.githubusercontent.com/40369712/77024355-527c3180-695c-11ea-8f74-d58c9d5c8999.png">
</p>

---

**Nota:** Espere unos mintos mientras el proceso de construcción y despliegue de la aplicación se termina.

---

**b.** Una vez terminado el proceso de despliegue puede dirigirse a Overview, donde podra ver la URL mediante la cual podra acceder al CRUD de MongoDB

<p align="center">
<img width="783" alt="img9" src="https://user-images.githubusercontent.com/40369712/77024952-d682e900-695d-11ea-8724-ffa8b08c8b58.png">
</p>


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

