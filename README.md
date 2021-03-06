<div align="center">
    <img alt="nestjs-starter" width="250" height="auto" src="https://camo.githubusercontent.com/c704e8013883cc3a04c7657e656fe30be5b188145d759a6aaff441658c5ffae0/68747470733a2f2f6e6573746a732e636f6d2f696d672f6c6f676f5f746578742e737667" />
    <h1>NestJS Starter</h1>
</div>

<p align="center">
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=Node&message=v14.15.4&labelColor=339933&color=757575&logoColor=FFFFFF&logo=Node.js" alt="Node.js"/>
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=Npm&message=v6.14.10&labelColor=CB3837&logoColor=FFFFFF&color=757575&logo=npm" alt="Npm"/>
    <img src="https://img.shields.io/static/v1.svg?style=flat&label=NestJs&message=v8.2.6&labelColor=E0234E&logoColor=FFFFFF&color=757575&logo=Nestjs" alt="NestJs"/>
    <a href="https://github.com/rudemex/nestjs-starter/releases/latest">
        <img alt="Last Release" src="https://img.shields.io/github/v/tag/rudemex/nestjs-starter?label=release">
    </a>
    <a href="./license.md">
        <img alt="GitHub license" src="https://img.shields.io/github/license/rudemex/nestjs-starter?style=flat">
    </a>
    <br>
    <a href="https://github.com/rudemex/nestjs-starter/actions/workflows/master.yml" target="_blank">
        <img alt="GitHub Workflow Status" src="https://github.com/rudemex/nestjs-starter/actions/workflows/master.yml/badge.svg?branch=master">
    </a>
    <a href="https://app.codecov.io/gh/rudemex/nestjs-starter/" target="_blank">
        <img alt="Codecov" src="https://img.shields.io/codecov/c/github/rudemex/nestjs-starter?logoColor=FFFFFF&logo=Codecov&labelColor=#F01F7A">
    </a>
    <a href="https://sonarcloud.io/summary/new_code?id=rudemex_nestjs-starter" target="_blank">    
        <img src="https://sonarcloud.io/api/project_badges/measure?project=rudemex_nestjs-starter&metric=alert_status" alt="sonarcloud">
    </a>    
    <a href="https://snyk.io/test/github/rudemex/nestjs-starter" target="_blank">
        <img src="https://snyk.io/test/github/rudemex/nestjs-starter/badge.svg" alt="Snyk">
    </a>
    <br/> 
</p>

## Glosario

- [???? Demo](https://rudemex-nestjs-starter.herokuapp.com/api)
- [???? Requerimientos b??sicos](#basic-requirements)
- [??????? Instalar dependencias](#install-dependencies)
- [?????? Configuraci??n](#configurations)
- [???? Scripts](#scripts)
- [???? Swagger](#swagger-info)
- [???? Toolkit](#toolkit)
- [???? Commits](#commits)
- [???? Changelog](./CHANGELOG.md)
- [???? License MIT](license.md)

---

<a name="basic-requirements"></a>

## ???? Requerimientos b??sicos

- Node.js v14.15.4 or higher ([Download](https://nodejs.org/es/download/))
- NPM v6.14.10 or higher
- NestJS v8.2.0 or higher ([Documentaci??n](https://nestjs.com/))

<a name="install-dependencies"></a>

## ??????? Instalar dependencias

Cuando tenemos los requisitos b??sicos, clonamos el repositorio, vamos a la carpeta del proyecto e instalamos sus
dependencias.

```
 npm install
```

<a name="configurations"></a>

## ?????? Configuraci??n

Este starter viene con el archivo **.env.example** y **.env.test**, el cual contiene las configuraciones b??sicas para
que funcione la aplicaci??n.

Para el entorno de desarrollo local, es necesario contar con un archivo **.env** del cual se puede utilizar el archivo
de ejemplo para generarlo.

```sh
# SERVER
PORT=8080
CONTEXT=api
ORIGINS=http://localhost:3000,http://localhost:8080
ALLOWED_HEADERS=Content-Type,Authorization,Set-Cookie,Access-Control-Allow-Origin,Cache-Control,Pragma
ALLOWED_METHODS=GET,HEAD,PUT,POST,DELETE,PATCH,OPTIONS
CORS_ENABLED=true
CORS_CREDENTIALS=false

# SWAGGER ENVIRONMENTS
SWAGGER_PATH=docs
SWAGGER_ENABLED=true

# PARAMS
TEST_KEY="testKeyEnv-dev"

# SERVICES
RICK_AND_MORTY_API_URL=https://rickandmortyapi.com/api
```

<details>
<summary>???? Para ver en detalle todas las propiedades de la configuraci??n, hace click ac??.</summary>

#### Server

`PORT`: Es el puerto por el cual va a correr el servidor.

- Type: `Number`
- Default: `8080`

`CONTEXT`: Es el contexto el que se puede acceder a la API del servidor, de esta manera no se exponen los endpoints en
la ruta principal de la aplicaci??n. Se escribe sin el `/` (slash).

- Type: `String`
- Default: `api`

`ORIGINS`: Es una whitelist para que la aplicaci??n s??lo pueda ser consumida por urls confiables y evitar cualquier tipo
de solicitudes no deseadas y maliciosas. Debes escribir las urls separadas por una coma.

- Type: `String`
- Default: `http://localhost:3000,http://localhost:8080`

`ALLOWED_HEADERS`: Par??metros que va a recibir por el header en los request.

- Type: `String`
- Default: `Content-Type,Authorization,Set-Cookie,Access-Control-Allow-Origin,Cache-Control,Pragma`

`ALLOWED_METHODS`: M??todos http disponibles para el cors

- Type: `String`
- Default: `GET,HEAD,PUT,POST,DELETE,PATCH,OPTIONS`

`CORS_ENABLED`: Habilita o deshabilita el uso de CORS en el servidor.

- Type: `Boolean`
- Default: `false`

`CORS_CREDENTIALS`: Habilita o deshabilita el uso de las credenciales en las peticiones CORS en el servidor.

- Type: `Boolean`
- Default: `false`

#### Swagger

`SWAGGER_PATH`: Define la ruta de la documentaci??n **Swagger**, se escribe sin el `/` (slash).

- Type: `String`
- Default: `docs`

`SWAGGER_ENABLED`: Habilitar o deshabilitar la documentaci??n **Swagger** de los endpoints del servidor.

- Type: `Boolean`
- Default: `true`

#### Params, Services y Otros environments

A modo de ejemplo, se pueden cargar todas las variables de entorno que requieras, es importante seguir con el esquema
de `key:value` para configurarlas.

```
# PARAMS
TEST_KEY="testKeyEnv-dev"

# SERVICES
RICK_AND_MORTY_API_URL=https://rickandmortyapi.com/api
```

</details>

Este proyecto utiliza el m??dulo `@nestjs/config`, el cual centraliza todas las variables de entorno en un solo lugar y
te permite consumirlas como **typing** para evitar errores de typo, como asi tambi??n evitar usar el **process.env** en
todo el proyecto, lo que te permite darle soporte m??s f??cil si se requiere cambiar el **KEY** de la variable de entorno.

Tambi??n cuenta con un validador de variables de entorno, que nos permite validar el tipo de dato y si es requerido o no
dicha variable.

Todos estos features los podemos encontrar en la carpeta **./src/config**, en dicha carpeta podemos encontrar el archivo
**environments.ts** que es un manejador de env files dependiendo el **NODE_ENV** que tenga nuestra aplicaci??n.

<a name="scripts"></a>

## ???? Scripts

Inicia la aplicaci??n en modo desarrollo

```
npm run start:dev
```

Inicia los test con coverage

```
npm run test
```

Realiza el build de la aplicaci??n

```
npm run build
```

Inicia la aplicaci??n en modo productivo

```
npm run start
```

#### Otros scripts

Formatea el c??digo

```
npm run format
```

Eslintea el c??digo

```
npm run lint
```

<a name="swagger-info"></a>

## ???? Swagger

El proyecto cuenta con un **Swagger** (OpenAPI 3.0.0) que tiene documentado los endpoints con sus
definiciones. [Demo Swagger](https://rudemex-nestjs-starter.herokuapp.com/docs/)

Para expandir la documentaci??n, es importante aplicar los decoradores correspondientes a la
aplicaci??n. [NestJS OpenApi](https://docs.nestjs.com/openapi/introduction)

Esta documentaci??n puede ser activada o desactivada desde la configuraci??n por medio las variables de entorno del
proyecto.

```sh
SWAGGER_PATH=docs
SWAGGER_ENABLED=true
```

#### URL

Acceso a la documentaci??n y testeo de los endpoints: `http://localhost:8080/docs`

#### Scheme

```
<http|https>://<server_url><:port>/<swagger-path>
```

#### Exportar el swagger en JSON

Se puede exportar la documentaci??n a un **JSON** agregando el sufijo **-json** al path
definido. [Demo Swagger JSON](https://rudemex-nestjs-starter.herokuapp.com/docs-json)

- Default: `http://localhost:8080/docs-json`
- Schema: `<http|https>://<server_url><:port>/<swagger-path>-json`

<a name="toolkit"></a>

## ???? Toolkit

Los m??dulos de la siguiente lista, est??n pensados para ser consumidos para la arquitectura de este starter, o
arquitectura similar siguiendo los lineamientos de `schematics`.

| Package                                                                        | Descripci??n                                | Versi??n                                                                                                                               | Changelog                                                                           |
| ------------------------------------------------------------------------------ | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [`@tresdoce/nestjs-archetype`](https://github.com/tresdoce/nestjs-archetype)   | M??dulo de informaci??n del proyecto         | [![version](https://img.shields.io/npm/v/@tresdoce/nestjs-archetype.svg)](https://www.npmjs.com/package/@tresdoce/nestjs-archetype)   | [changelog](https://github.com/tresdoce/nestjs-archetype/blob/master/CHANGELOG.md)  |
| [`@tresdoce/nestjs-commons`](https://github.com/tresdoce/nestjs-commons)       | Configuraci??n centralizada                 | [![version](https://img.shields.io/npm/v/@tresdoce/nestjs-commons.svg)](https://www.npmjs.com/package/@tresdoce/nestjs-commons)       | [changelog](https://github.com/tresdoce/nestjs-commons/blob/master/CHANGELOG.md)    |
| [`@tresdoce/nestjs-health`](https://github.com/tresdoce/nestjs-health)         | M??dulo de health check: liveness/readiness | [![version](https://img.shields.io/npm/v/@tresdoce/nestjs-health.svg)](https://www.npmjs.com/package/@tresdoce/nestjs-health)         | [changelog](https://github.com/tresdoce/nestjs-health/blob/master/CHANGELOG.md)     |
| [`@tresdoce/nestjs-database`](https://github.com/tresdoce/nestjs-database)     | M??dulo conexi??n a base de datos Mongo      | [![version](https://img.shields.io/npm/v/@tresdoce/nestjs-database.svg)](https://www.npmjs.com/package/@tresdoce/nestjs-database)     | [changelog](https://github.com/tresdoce/nestjs-database/blob/master/CHANGELOG.md)   |
| [`@tresdoce/nestjs-httpclient`](https://github.com/tresdoce/nestjs-httpclient) | M??dulo http con axios y axios-retry        | [![version](https://img.shields.io/npm/v/@tresdoce/nestjs-httpclient.svg)](https://www.npmjs.com/package/@tresdoce/nestjs-httpclient) | [changelog](https://github.com/tresdoce/nestjs-httpclient/blob/master/CHANGELOG.md) |

<a name="commits"></a>

## ???? Commits

Para los mensajes de commits se toma como
referencia [`conventional commits`](https://www.conventionalcommits.org/en/v1.0.0-beta.4/#summary).

```
<type>[optional scope]: <description>

[optional body]

[optional footer]
```

- **type:** chore, docs, feat, fix, refactor (m??s comunes)
- **scope:** indica la p??gina, componente, funcionalidad
- **description:** comienza en min??sculas y no debe superar los 72 caracteres.

## ???? Changelog

All notable changes to this project will be documented in [Changelog](./CHANGELOG.md) file.

---

<div align="center">
    <a href="mailto:mdelgado@tresdoce.com.ar" target="_blank" alt="Send an email">
        <img src="./.readme-static/logo-mex-red.svg" width="120" alt="Mex" />
    </a><br/>
    <!--<a href="mailto:mdelgado@tresdoce.com.ar" target="_blank" alt="Send an email">
        <img src="https://img.shields.io/static/v1.svg?style=flat-square&label=&message=Sr.%20Fullstack%20Developer&labelColor=1A1A1A&color=999999&logo=hackaday" alt="Mex Delgado" />
    </a><br/><br/>-->
    <p>Made with ???</p>
</div>
