# ROKS-Angular-HandsOn

# GUIA DE INSTALACIÓN Y DESPLIEGUE DE APP ANGULAR EN OPENSHIFT

_Para el desarrollo de este proyecto se tiene como base el desarrollo de una aplicación basada en el lenguaje de programación angular y su posterior despliegue en un **Cluster de OpenShift** que se encuentra alojado en **IBM Cloud**._

## Despliegue en OpenShift desde IBM Cloud shell: 🚀

_Iniciualmente debe acceder al shell de IBM Cloud desde el siguinete link:_
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
_Al digitar el comando anterior nos aparecera una pregunta en la cual debemos indicar el numero perteneciente a la cuenta en la que se va a tranajar._

_2.	Configure el entorno de trabajo. Para esto debe colocar el siguiente comando en la terminal._
```
ibmcloud target
```
_Si se ve que faltan faltan algunos campos por configurar,  para hacerlo se debe digitar los siguientes comandos._
```
ibmcloud target -r us-east -g openshift-workshop
```
_y por ultimo digitar el siguiente comando:_
```
ibmcloud target --cf
```
_Al digitar el comando anterior nos aparecera una pregunta en la cual debemos el numero perteneciente a la organizacion en la que se desea trabajar._

_De este modo damos por terminada la configuración inicial para el despliegue de la aplicación._


## Despliegue 📦


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

_•	Ahora en la parte superior derecha se da clic sobre el ID del correo con el que ingresamos y luego en la sección que dice Copy Login Command._


<img width="144" alt="1" src="https://user-images.githubusercontent.com/60987042/76917049-53479180-6890-11ea-91a1-b2c2c9213729.PNG">

_•	Y por último volvemos a la terminal que se estaba utilizando pegamos y damos enter._

_4.	Cree un nuevo proyecto en el cluster de la siguiente manera:_
```
oc new-project <projectname>
```
_**Nota:** Para el **projectname** coloque **openshift + las iniciales de su nombre y apellido.**_

_5.	Acceda al proyecto que acabo de crear de la siguiente manera:_

```
oc project <projectname>
```

_6.	Clone el repositorio de la aplicación que se desea desplegar._

_**App de hello Word en angular:** https://github.com/emeloibmco/AngularHelloWorld_

_**App de listas en angular:** https://github.com/emeloibmco/AngularWebList_

_7.	Desde el Shell de IBM cloud digitar el comando:_

```
Git clone <url_repositorio>
```
_8.	Dirigirse desde a esta carpeta con el comando:_

_•	Para la carpeta del proyecto Hello word:_
```
cd AngularHelloWorld
```
•	Para la carpeta del proyecto listas.
```
cd AngularWebList
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

<img width="789" alt="3" src="https://user-images.githubusercontent.com/60987042/76919117-f222bc80-6895-11ea-835e-cb689f2b61bb.PNG">

_Y por último solo faltaría dar clic en el link que lo llevara a la aplicación desplegada._

<img width="688" alt="4" src="https://user-images.githubusercontent.com/60987042/76919471-074c1b00-6897-11ea-95c7-e8675b91ec80.PNG">

_De esta forma se daría por terminado el despliegue de la aplicación angular en openshift._

# _ANEXOS._

_Si se desea realizar el mismo despliegue, pero desde la maquina local se deberían seguir los siguientes pasos:_

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


## Autores ✒️

_Equipo IBM Cloud Tech sales Colombia._

