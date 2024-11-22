# AWS-Serverless-Application-Model

Crear una aplicación web sin servidor utilizando **AWS Lambda**, **API Gateway**, **AWS Amplify**, **DynamoDB** y **Cognito**.
Como se ve acontinuación

![image](https://github.com/user-attachments/assets/8491c1da-0b18-47ec-9604-c4367264f14f)


## Requisitos previos

Antes de comenzar, asegúrate de tener lo siguiente:
- Una cuenta de AWS activa en este caso se usa acceso de vocarona como proovedor para acceder a AWS.
- Una cuenta de repositorio en este caso se usa github
- Conocimientos básicos sobre AWS y servicios como Lambda, API Gateway, DynamoDB y AWS Amplify.
- Acceso a AWS Management Console.

## Paso 1: Crear un bucket de AWS Amplify para alojar la aplicación web

1. **Accede a la consola de AWS** y ve al servicio **S3** con el siguiente comando 'aws s3 cp s3://ttt-wildrydes/wildrydes-site ./ --recursive'.
2. **Crea un nuevo repositorio** con un nombre único. Este repositorio será donde se almacenarán los archivos estáticos de tu aplicación web (HTML, CSS, JS).
3. Asegúrate de habilitar el acceso público para que los archivos puedan ser accesibles a través de la web.
4. **Sube los archivos estáticos** de tu aplicación (HTML, CSS, JS) al repositorio en este caso github.
5. Configura el repositorio para que sirva como sitio web estático, habilitando la opción correspondiente en las propiedades.

## Paso 2: Configurar Amazon Cognito para la autenticación

1. **Accede a la consola de Cognito** y selecciona el servicio **Cognito**.
2. **Crea un nuevo grupo de usuarios** (User Pool) para gestionar la autenticación de usuarios en este caso especifico se usa un usuario previamente asignado desde el proveedor vocarona que es 'LabRole'.

## Paso 3: Crear una API con API Gateway

1. **Accede a API Gateway** desde la consola de AWS y selecciona la opción **Crear API**.
2. Elige **API REST** y selecciona la opción para crear una nueva API.
3. Crea un **nuevo recurso** que manejará las solicitudes de tu aplicación web (por ejemplo, `/todos`).
4. **Crea un nuevo método** bajo el recurso que acabas de crear, eligiendo el tipo de método (GET, POST, etc.) y configurando la integración con Lambda.

## Paso 4: Crear la función Lambda

1. **Accede al servicio Lambda** y selecciona **Crear función**.
2. Elige la opción **Autor desde cero** y proporciona un nombre para tu función.
3. Configura los permisos y asegúrate de que Lambda pueda acceder a DynamoDB para almacenar y recuperar datos.
4. **Desarrolla el código de la función Lambda** que gestionará la lógica de tu aplicación. Por ejemplo, podrías escribir una función que reciba solicitudes desde API Gateway y consulte una base de datos DynamoDB para recuperar o almacenar información.
5. **Sube y despliega** el código en Lambda.

## Paso 5: Configurar la integración de API Gateway con Lambda

1. En la consola de API Gateway, selecciona el recurso y método que creaste previamente.
2. En la configuración del método, selecciona **Lambda Function** como el tipo de integración y proporciona el nombre de la función Lambda que creaste.
3. **Configura las respuestas** que la API debe devolver (por ejemplo, 200 OK para una solicitud exitosa).
4. **Despliega la API** a un nuevo entorno de despliegue.

## Paso 6: Conectar la aplicación web a API Gateway

1. En los archivos de tu aplicación web (HTML, JS), utiliza JavaScript para hacer solicitudes HTTP a la API Gateway que configuraste.
2. **Añade el código de autenticación** usando el **ID de usuario** y el **ID de cliente** de Cognito para autenticar a los usuarios antes de que puedan acceder a la funcionalidad de la API.
3. Usa las respuestas de la API para actualizar la interfaz de usuario de la aplicación.

## Paso 7: Configurar DynamoDB

1. **Accede al servicio DynamoDB** en la consola de AWS y crea una nueva tabla.
2. Proporciona un nombre para la tabla y configura la clave primaria en este caso es "Rydes" y "RideId" respectivamente.
3. Configura las reglas de lectura y escritura para que Lambda pueda acceder a los datos de DynamoDB.
4. En la función Lambda, implementa la lógica para interactuar con DynamoDB, como insertar, actualizar o leer datos de la tabla.

## Paso 8: Prueba y despliegue

1. **Realiza pruebas locales** en tu aplicación web para asegurarte de que todo funciona correctamente.
2. **Despliega la aplicación** en producción, asegurándote de que la API Gateway esté correctamente conectada con Lambda y DynamoDB, y que la autenticación de Cognito esté funcionando correctamente deberia verse como acontinuación.
![image](https://github.com/user-attachments/assets/4f6bf057-c073-474a-b791-bb7f0d0d0c79)

3. **Test de autenticación** si le das clic en lest ryde deberia poderse registrar como una aplicación web

![image](https://github.com/user-attachments/assets/9319e984-c7b1-4345-9b20-55814ba8c764)

4. Si se realizo bien el registro deberia verse así en DynamoDB

![image](https://github.com/user-attachments/assets/d73fb61c-1425-4f51-bc95-d8a9ae8b314a)

5. Finalmente el registro debería funcionar como autenticador por parte de aws


