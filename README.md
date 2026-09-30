# DareNBet 🎲

Aplicación web **tipo red social** con **apuestas entre usuarios**, **foro** y **blog**, desarrollada en **Java EE (Jakarta EE 10)** con **Servlets + JSP** siguiendo el patrón **Modelo-Vista-Controlador (MVC)**.

> Proyecto en grupo de la asignatura *Servicios y Sistemas Web* (3º Grado en Ingeniería Informática, Universidad de Valladolid, curso 2024-25).

## Funcionalidades

- **Registro e inicio de sesión** de usuarios, con validación de formularios.
- **Apuestas**: crear apuestas con varias opciones, apostar créditos, dar *like/dislike* y consultar el historial en *Mis apuestas*.
- **Gamificación**: sistema de créditos, reclamación periódica de créditos y **ranking** de usuarios.
- **Foro**: publicaciones, comentarios y votos.
- **Blog**: creación y eliminación de entradas.
- Configuración de perfil y páginas de error personalizadas (404, 500).

## Tecnologías

| Capa | Tecnología |
|---|---|
| Backend | Java 11, Jakarta Servlets, JSTL |
| Vista | JSP, HTML5, CSS3 |
| Persistencia | MariaDB/MySQL vía JDBC, patrón DAO, *connection pool* JNDI (Tomcat) |
| Build | Maven (empaquetado WAR) |
| Servidor | Apache Tomcat |

## Arquitectura

```
src/main/java/uva/ssw/entrega/
├── modelo/        → Entidades (Usuario, Apuesta, OpcionApuesta, Post, Comentario, Entrada…)
├── bd/            → Acceso a datos: DAOs + ConnectionPool
└── controlador/   → Servlets (login, registro, apuestas, foro, blog, ranking…)
src/main/webapp/
├── *.jsp          → Vistas
├── estilos/       → CSS
└── META-INF/context.xml → Configuración del pool de conexiones
```

## Cómo ejecutarlo

1. Crear una base de datos MariaDB/MySQL llamada `dareNbet` con las tablas `Usuario`, `Apuesta`, `OpcionApuesta`, `UsuarioApuesta`, `Post`, `Comentario`, `VotosPost` y `Entrada`.
2. Poner tus credenciales en `src/main/webapp/META-INF/context.xml` (`TU_USUARIO` / `TU_CONTRASENA`).
3. Compilar y desplegar en Tomcat:
   ```bash
   mvn clean package
   # copiar target/*.war a la carpeta webapps/ de Tomcat
   ```
4. Abrir `http://localhost:8080/DareNBet/`.

## Mi contribución

Desarrollé el **módulo de apuestas**: la página de apuestas y sus estilos, la lógica para apostar (`ServletApostar`), el historial *Mis apuestas* (`ServletMisApuestas`, `UsuarioApuestasDAO`, `UsuarioApuesta`) y el **registro de usuarios** (`ServletRegistro`).

## Posibles mejoras

- Guardar las contraseñas con *hash* (p. ej. BCrypt) en lugar de texto plano.
- Añadir el script SQL de creación de la base de datos y datos de ejemplo.
- Tests automáticos de los DAOs.

## Autores

Proyecto realizado en equipo por **Alfredo del Val** ([@Krazyfred](https://github.com/Krazyfred)) y sus compañeros de grupo.
