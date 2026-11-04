# Guía de conocimientos para desarrollar software

> Una ruta de referencia para aprender a analizar, diseñar, construir, probar, proteger y mantener software.
>
> **Objetivo:** desarrollar criterio de ingeniería de software, no solamente aprender la sintaxis de un lenguaje.

---

## Cómo utilizar esta guía

- [ ] Marca cada concepto cuando puedas explicarlo con tus propias palabras.
- [ ] Practica cada tema escribiendo código y construyendo proyectos pequeños.
- [ ] No avances únicamente por memorizar definiciones: demuestra lo aprendido.
- [ ] Vuelve a los temas anteriores cuando un proyecto te muestre que necesitas reforzarlos.

**Importante:** no es necesario dominar todos los temas al mismo tiempo. Aprende los fundamentos primero y aumenta gradualmente la complejidad.

---

# 1. Fundamentos de programación

Son la base para aprender cualquier lenguaje de programación.

- [ ] Variables y constantes.
- [ ] Tipos de datos.
- [ ] Operadores aritméticos, lógicos y relacionales.
- [ ] Condicionales.
- [ ] Ciclos e iteraciones.
- [ ] Funciones y procedimientos.
- [ ] Parámetros y argumentos.
- [ ] Alcance de variables (*scope*).
- [ ] Colecciones y estructuras de datos básicas.
- [ ] Manejo de errores y excepciones.
- [ ] Recursividad.
- [ ] Algoritmos.
- [ ] Complejidad computacional: notación Big O.

**Meta práctica:** resolver problemas pequeños sin depender de copiar soluciones.

# 2. Paradigmas de programación

Un paradigma es una forma de organizar y expresar la solución de un problema.

- [ ] Programación imperativa.
- [ ] Programación declarativa.
- [ ] Programación orientada a objetos (POO).
- [ ] Programación funcional.
- [ ] Programación dirigida por eventos.
- [ ] Programación reactiva.
- [ ] Programación asíncrona.

### En qué profundizar

**Programación orientada a objetos**
- [ ] Clases y objetos.
- [ ] Atributos y métodos.
- [ ] Constructores.
- [ ] Encapsulamiento.
- [ ] Abstracción.
- [ ] Herencia.
- [ ] Polimorfismo.
- [ ] Interfaces.
- [ ] Composición.

**Programación funcional**
- [ ] Funciones puras.
- [ ] Inmutabilidad.
- [ ] Funciones de orden superior.
- [ ] Funciones anónimas o *lambda*.
- [ ] Closures.
- [ ] Composición de funciones.
- [ ] `map`, `filter` / `where` y `reduce` / `fold`.
- [ ] Manejo de efectos secundarios.

**Meta práctica:** saber cuándo conviene utilizar objetos, funciones y una combinación de ambos enfoques.

# 3. Principios de diseño y calidad del código

Ayudan a construir código comprensible, mantenible y fácil de probar.

- [ ] **SOLID:** cinco principios para diseñar software orientado a objetos.
  - [ ] SRP — Principio de responsabilidad única.
  - [ ] OCP — Principio abierto/cerrado.
  - [ ] LSP — Principio de sustitución de Liskov.
  - [ ] ISP — Principio de segregación de interfaces.
  - [ ] DIP — Principio de inversión de dependencias.
- [ ] **DRY:** evitar duplicación innecesaria.
- [ ] **KISS:** mantener las soluciones simples.
- [ ] **YAGNI:** no construir funcionalidades antes de necesitarlas.
- [ ] Separación de responsabilidades (*Separation of Concerns*).
- [ ] Alta cohesión (*High Cohesion*).
- [ ] Bajo acoplamiento (*Low Coupling*).
- [ ] Composición sobre herencia (*Composition over Inheritance*).
- [ ] Ley de Demeter.
- [ ] Fail Fast: detectar errores pronto.
- [ ] Código limpio (*Clean Code*).
- [ ] Refactorización (*Refactoring*).
- [ ] Nombres claros y consistentes.
- [ ] Funciones y módulos con responsabilidades claras.

**Nota:** los principios son herramientas de criterio, no reglas que deban aplicarse mecánicamente en todos los casos.

# 4. Arquitectura de software

La arquitectura define cómo se organiza un sistema y cómo se relacionan sus partes.

- [ ] Arquitectura cliente-servidor.
- [ ] Arquitectura monolítica.
- [ ] Arquitectura en capas.
- [ ] MVC (Modelo-Vista-Controlador).
- [ ] Arquitectura limpia (*Clean Architecture*).
- [ ] Arquitectura hexagonal (Ports and Adapters).
- [ ] Arquitectura orientada a servicios.
- [ ] Microservicios y sus costos operativos.
- [ ] Modularidad.
- [ ] Inyección de dependencias (DI).
- [ ] Inversión de control (IoC).
- [ ] Patrones de diseño (*Design Patterns*).
- [ ] Escalabilidad.
- [ ] Mantenibilidad.
- [ ] Disponibilidad y tolerancia a fallos.

**Orden sugerido:** comienza por arquitectura en capas y MVC. Estudia Clean Architecture y arquitectura hexagonal cuando tengas experiencia construyendo aplicaciones completas. No necesitas microservicios para todos los proyectos.

# 5. Estructuras de datos y algoritmos

Permiten organizar información y resolver problemas de manera eficiente.

- [ ] Arreglos (*arrays*) y listas.
- [ ] Listas enlazadas.
- [ ] Pilas (*Stack*).
- [ ] Colas (*Queue*).
- [ ] Conjuntos (*Set*).
- [ ] Tablas hash y mapas (*Hash Map*).
- [ ] Árboles.
- [ ] Grafos.
- [ ] Búsqueda lineal y binaria.
- [ ] Algoritmos de ordenamiento.
- [ ] Recorridos y búsquedas en árboles y grafos.
- [ ] Complejidad temporal y espacial.
- [ ] Notación Big O.

**Meta práctica:** elegir una estructura de datos según las operaciones que el programa necesita realizar.

# 6. Bases de datos

Permiten almacenar, consultar y mantener la información de una aplicación.

### Fundamentos
- [ ] Bases de datos relacionales.
- [ ] Bases de datos NoSQL y sus casos de uso.
- [ ] SQL.
- [ ] Modelado entidad-relación.
- [ ] Tablas, filas y columnas.
- [ ] Claves primarias y foráneas.
- [ ] Relaciones uno a uno, uno a muchos y muchos a muchos.
- [ ] Normalización.
- [ ] Restricciones e integridad referencial.
- [ ] Índices.
- [ ] Consultas, filtros, agrupaciones y uniones (*JOIN*).
- [ ] Transacciones y propiedades ACID.
- [ ] Copias de seguridad y restauración.
- [ ] Funciones definidas por el usuario (UDF).
- [ ] Procedimientos almacenados (Stored Procedures).
- [ ] Triggers (disparadores).
- [ ] Eventos INSERT, UPDATE y DELETE.
- [ ] Triggers BEFORE y AFTER.
- [ ] Auditoría de cambios mediante triggers.
    

### Integración con aplicaciones
- [ ] Migraciones.
- [ ] ORM (Object-Relational Mapping).
- [ ] Pool de conexiones.
- [ ] Consultas parametrizadas.
- [ ] Control de concurrencia.
- [ ] Gestión de errores de persistencia.

# 7. Desarrollo backend y APIs

El backend implementa la lógica del servidor, aplica reglas de negocio y gestiona el acceso a los datos.

- [ ] Modelo cliente-servidor.
- [ ] HTTP y HTTPS.
- [ ] Solicitudes y respuestas.
- [ ] Métodos HTTP: GET, POST, PUT, PATCH y DELETE.
- [ ] Códigos de estado HTTP.
- [ ] Encabezados (*headers*).
- [ ] JSON.
- [ ] API REST y principios REST.
- [ ] CRUD.
- [ ] Rutas y controladores.
- [ ] Servicios y lógica de negocio.
- [ ] Repositorios y acceso a datos.
- [ ] Middleware.
- [ ] Validación de datos.
- [ ] Serialización y deserialización.
- [ ] Manejo centralizado de errores.
- [ ] Autenticación y autorización.
- [ ] Sesiones y tokens.
- [ ] Paginación, ordenamiento y filtrado.
- [ ] Documentación de APIs (por ejemplo, OpenAPI).
- [ ] WebSockets y comunicación en tiempo real.
- [ ] Idempotencia y diseño robusto de endpoints.

# 8. Seguridad aplicada al desarrollo

La seguridad debe considerarse desde el diseño y durante todo el ciclo de vida del software.

### Principios y controles
- [ ] Security by Design.
- [ ] Defensa en profundidad.
- [ ] Principio de mínimo privilegio.
- [ ] Validación de entradas en el servidor.
- [ ] Codificación de salida y sanitización cuando corresponda.
- [ ] Autenticación.
- [ ] Autorización.
- [ ] Control de acceso basado en roles (RBAC) y atributos (ABAC).
- [ ] Hashing seguro de contraseñas (Argon2id o bcrypt).
- [ ] Cifrado simétrico y asimétrico.
- [ ] Gestión segura de sesiones y tokens.
- [ ] Gestión de secretos y variables de entorno.
- [ ] HTTPS/TLS.
- [ ] Rate limiting.
- [ ] CORS configurado según el origen permitido.
- [ ] Protección de endpoints y recursos.
- [ ] Registro de eventos y auditoría.
- [ ] Actualización y revisión de dependencias.
- [ ] Copias de seguridad y recuperación.

### Vulnerabilidades que debes reconocer
- [ ] SQL Injection.
- [ ] Cross-Site Scripting (XSS).
- [ ] Cross-Site Request Forgery (CSRF).
- [ ] Fallos de autenticación.
- [ ] Fallos de autorización y control de acceso.
- [ ] Exposición de información sensible.
- [ ] Configuraciones inseguras.
- [ ] Vulnerabilidades en dependencias.
- [ ] Server-Side Request Forgery (SSRF).

### Referencias
- [ ] OWASP Top 10.
- [ ] OWASP Application Security Verification Standard (ASVS).
- [ ] Principios de desarrollo seguro.
- [ ] Modelado de amenazas (*Threat Modeling*).

**Regla esencial:** nunca confíes en que el frontend protegerá un recurso. El backend debe validar la identidad, los permisos y los datos en cada operación relevante.

# 9. Testing y calidad de software

Las pruebas ayudan a comprobar que el sistema funciona y que los cambios no rompen lo que ya funcionaba.

- [ ] Pruebas unitarias.
- [ ] Pruebas de integración.
- [ ] Pruebas funcionales.
- [ ] Pruebas end-to-end (E2E).
- [ ] Pruebas de regresión.
- [ ] Pruebas de aceptación.
- [ ] TDD (Test-Driven Development).
- [ ] BDD (Behavior-Driven Development).
- [ ] Dobles de prueba: mocks, stubs y fakes.
- [ ] Cobertura de código y sus limitaciones.
- [ ] Debugging.
- [ ] Análisis estático.
- [ ] Análisis dinámico.
- [ ] Pruebas de seguridad.
- [ ] Pruebas de rendimiento básicas.

# 10. Herramientas y prácticas profesionales

- [ ] Git.
- [ ] GitHub o una plataforma equivalente.
- [ ] Ramas y estrategias de trabajo.
- [ ] Commits claros.
- [ ] Resolución de conflictos.
- [ ] Pull requests y revisión de código (*Code Review*).
- [ ] Terminal y línea de comandos.
- [ ] Linux y fundamentos del sistema operativo.
- [ ] Docker y contenedores.
- [ ] Gestión de dependencias.
- [ ] Variables de entorno.
- [ ] CI/CD (integración y entrega/despliegue continuos).
- [ ] Documentación técnica.
- [ ] Gestión de tareas.
- [ ] Metodologías ágiles (Scrum, Kanban).
- [ ] Despliegue (*Deployment*).
- [ ] Monitoreo y observabilidad: logs, métricas y trazas.
- [ ] Gestión de incidentes y mantenimiento.

---

# Ruta de aprendizaje recomendada

Esta secuencia permite avanzar desde los fundamentos hasta la construcción y operación de sistemas reales.

## Nivel 1 — Fundamentos
- [ ] Lógica de programación.
- [ ] Variables, tipos, operadores y control de flujo.
- [ ] Funciones y colecciones.
- [ ] Algoritmos y estructuras de datos básicas.
- [ ] Manejo de errores.

**Resultado esperado:** resolver problemas pequeños y explicar cómo funciona tu solución.

## Nivel 2 — Construcción de programas
- [ ] Programación orientada a objetos.
- [ ] Programación funcional.
- [ ] SOLID.
- [ ] DRY, KISS y YAGNI.
- [ ] Clean Code y refactorización.
- [ ] Patrones de diseño básicos.

**Resultado esperado:** construir programas modulares, legibles y fáciles de modificar.

## Nivel 3 — Aplicaciones y datos
- [ ] SQL y modelado de bases de datos.
- [ ] HTTP y JSON.
- [ ] Backend y APIs REST.
- [ ] Validación de datos.
- [ ] Autenticación y autorización.
- [ ] ORM y migraciones.

**Resultado esperado:** desarrollar una API que persista datos y aplique reglas de negocio.

## Nivel 4 — Ingeniería y calidad
- [ ] Arquitectura en capas y MVC.
- [ ] Testing automatizado.
- [ ] Git y trabajo con ramas.
- [ ] Docker.
- [ ] Documentación.
- [ ] Revisión y refactorización de código.

**Resultado esperado:** mantener una aplicación organizada, probada y reproducible.

## Nivel 5 — Seguridad
- [ ] Principios de desarrollo seguro.
- [ ] OWASP Top 10.
- [ ] Protección de contraseñas y sesiones.
- [ ] Control de acceso.
- [ ] Seguridad de APIs.
- [ ] Gestión de secretos y dependencias.
- [ ] Pruebas de seguridad.

**Resultado esperado:** identificar riesgos comunes y aplicar controles adecuados.

## Nivel 6 — Operación y profesionalización
- [ ] CI/CD.
- [ ] Despliegue.
- [ ] Monitoreo y observabilidad.
- [ ] Copias de seguridad y recuperación.
- [ ] Rendimiento y escalabilidad.
- [ ] Mantenimiento y gestión de incidentes.

**Resultado esperado:** desplegar y mantener una aplicación en un entorno real.

---

# Los 15 conceptos prioritarios

Si necesitas una lista corta para comenzar, utiliza este orden:

1. [ ] Algoritmos y estructuras de datos.
2. [ ] Programación orientada a objetos.
3. [ ] Programación funcional.
4. [ ] SOLID.
5. [ ] DRY, KISS y YAGNI.
6. [ ] Complejidad computacional (Big O).
7. [ ] Clean Code y refactorización.
8. [ ] Patrones de diseño.
9. [ ] Arquitectura en capas.
10. [ ] Bases de datos relacionales y SQL.
11. [ ] HTTP y APIs REST.
12. [ ] Autenticación y autorización.
13. [ ] Testing automatizado.
14. [ ] Git y Docker.
15. [ ] OWASP y Security by Design.

---

# Proyectos para poner en práctica los conceptos

Aprende aplicando los temas en proyectos que aumenten gradualmente de complejidad.

## Proyecto 1 — Gestor de tareas
- [ ] Crear, consultar, actualizar y eliminar tareas.
- [ ] Practicar variables, funciones, colecciones y condicionales.
- [ ] Separar la lógica en funciones y módulos.
- [ ] Añadir validaciones y manejo de errores.

## Proyecto 2 — Gestor de mascotas
- [ ] Crear clases y objetos.
- [ ] Aplicar encapsulamiento y composición.
- [ ] Filtrar y transformar colecciones.
- [ ] Separar responsabilidades.
- [ ] Escribir pruebas unitarias.

## Proyecto 3 — API de gestión veterinaria
- [ ] Crear una API REST.
- [ ] Conectar PostgreSQL.
- [ ] Modelar mascotas, propietarios y citas.
- [ ] Implementar validación en el backend.
- [ ] Añadir autenticación y autorización.
- [ ] Proteger contraseñas y endpoints.
- [ ] Crear pruebas unitarias y de integración.
- [ ] Documentar y contenerizar la aplicación con Docker.

---

# Tecnologías sugeridas para practicar

Una ruta posible, no una obligación:

| Área | Tecnología para practicar |
|---|---|
| Fundamentos y POO | Dart |
| Backend tipado | TypeScript |
| Framework backend | NestJS |
| Base de datos relacional | PostgreSQL |
| Control de versiones | Git y GitHub |
| Contenedores | Docker |
| Pruebas | Jest o Vitest; herramientas de pruebas HTTP |
| Documentación de API | OpenAPI / Swagger |

**Recuerda:** los conceptos son más importantes que las herramientas. Cuando comprendas los fundamentos, podrás trasladarlos a otros lenguajes y frameworks.

---

# Criterio para considerar un tema aprendido

Antes de marcar un concepto como dominado, comprueba que puedes:

- [ ] Explicarlo con tus propias palabras.
- [ ] Reconocer cuándo es útil y cuándo no.
- [ ] Aplicarlo en un ejemplo sin copiar una solución.
- [ ] Identificar errores habituales.
- [ ] Explicar sus ventajas, limitaciones y riesgos.
- [ ] Utilizarlo dentro de un proyecto.
- [ ] Probar que la implementación funciona.

## Idea final

Desarrollar software implica mucho más que escribir código. Un buen desarrollador aprende a **analizar problemas, diseñar soluciones, construir sistemas, verificar su funcionamiento, proteger la información y mantener el software a lo largo del tiempo**.

No intentes aprender toda esta guía de una vez. Avanza por niveles, practica cada concepto y construye proyectos que demuestren lo que sabes.
