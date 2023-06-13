# Framework-Testing-NiFi

Framework de Testing automatizado utilizando la ApiRest de Apache NiFi, Elasticsearch, Oracle DB, entre otros.

## FAQ

#### ¿En qué lenguaje está desarrollado?

Está desarrollado en Python 3.10 utilizando la plataforma Jupyter Lab.

#### ¿Con qué ApiRest trabaja?

Trabaja con las API de Apache NiFi, Oracle DB y Elasticsearch.

#### ¿Qué bibliotecas utiliza de Python?
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

#### ¿Cuáles son los accesos?
Para poder utilizar el Framework, debes usar los siguientes accesos según la plataforma:
- Apache NiFi: usuario y contraseña de Claro.
- Oracle: usuario, contraseña, puerto y DNS.
- Elasticsearch: URL y api_key.

#### ¿Cuáles son los status de los Processors?
Los status de los processors que utilizamos son:
- RUNNING (en ejecución).
- STOPPED (detenido).

#### ¿Cómo se lee la estructura de los archivos de texto?

- FEATURE
- SCENARIO "Nombre del escenario"
- DATAFLOW "UUID del process group o DATAFLOW"
- ACCION  "Nombre del componente"

#### ¿Cuáles son las ACCIONES?
- PLAY: Inicia el processor.
- STOP: Detiene el processor.
- CHECK: Verifica el contenido de la conexión.
- CLEAR: Limpia el estado del processor.
- PROCESSGROUP: Lee otro process group dentro del actual.
- IMPRIMIR: Muestra la tabla con los resultados.
- CONSULT: Inserta una sentencia SQL.

## Ejecutar localmente

Clonar el proyecto

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

