
# Framework-Testing-NiFi

Framework de Testing automatizado utilizando la ApiRest de Apache NiFi, Elastich Search, Oracle DB, entre otros




## FAQ

#### ¿En que lenguaje esta desarrollado?

Esta desarrollado en python 3.10 utilizando la plataforma Jupyter Lab 

#### ¿Con que ApiRest trabaja?

Trabaja con las Api's de Apache NiFi, Oracle DB, elastich serach.

#### ¿Que librerias utiliza de Python?
- response
- requests
- json
- urllib3
- time
- IPython.display
- cx_Oracle
- prettytable
- elasticsearch
- pysftp

####  ¿Cuales son los accesos?
Para poder utilizar el Framework tenes que usar los accesos segun la plataforma:
- Apache NiFi: usuario y contraseña de Claro
- Oracle: Usuario, contraseña, puerto y dns
- elasticsearch:  url y api_key


#### ¿Cuales son los status de los Processors?
Los status de los processors que usaremos son 2
- RUNNING
- STOPPED

#### ¿Como es la lectura de los archivos de texto?

- FEATURE
- SCENARIO "Nombre del escenario"
- DATAFLOW "UUID del process group o DATAFLOW"
- ACCION  "Nombre del componente"

#### ¿Cuales son las ACCIONES?
- PLAY: Inicia el processor
- STOP: Para el processor
- CHECK: verifica el contenido de la connection
- CLEAR:  limpia el STATE del processor
- PROCESSGROUP: leer otro process group dentro del actual
- IMPRIMIR: mostrar la tabla con los resultado
- CONSULT: Para Insertar un sentencia sql
## Run Locally

Clonamos el projecto

```bash
  git clone http://tapias.claro.amx:7990/scm/dsn/framework-testing-nifi.git
```
Iniciamos el Jupyter Lab

```bash
  jupyter lab
```
dirigete a la carpeta del proyecto

```bash
  cd my-project
```

Instalamos las librerias faltantes

```bash
  pip install libreria 
```


## Freamework Referencia

### Nifi 

#### Access

```http
  POST /access/token
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `username`, `password` | `string` | **Obligatorio**. obtencion del token access |

#### Process Groups

```http
  GET /flow/process-groups/{UUID}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`      | `string` | **Obligatorio**. UUID del process group a buscar |


#### Proccessor

```http
  GET /processors/{UUID}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`      | `string` | **Obligatorio**. UUID del processor a buscar |


```http
  PUT /processors/{UUID}/run-status
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`,`revision, status`    | `string` | **Obligatorio**. UUID del processor a buscar, por body la revision y status |



```http
  POST /processors/{UUID}/state/clear-requests
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`      | `string` | **Obligatorio**. UUID del processor a buscar y limpiar el state |


#### Connections

```http
  GET /connections/{UUID}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`      | `string` | **Obligatorio**. UUID del connection |


#### Input Ports

```http
  GET /input-ports/{UUID}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`      | `string` | **Obligatorio**. UUID del Input Ports |


```http
  PUT /input-ports/{UUID}/run-status
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `UUID`,`revision, status`    | `string` | **Obligatorio**. UUID del Input Port a buscar, por body la revision y status |

