# Catálogo de Películas - Prueba Técnica Full Stack

Este repositorio contiene la solución completa a la prueba técnica para la vacante de **Junior Full Stack Developer** en Well Fair.

El proyecto es una aplicación web responsiva para explorar películas utilizando la API de TMDB. Se ha estructurado en un entorno de dos capas (Frontend SPA + Backend BFF) demostrando buenas prácticas de arquitectura, seguridad y manejo de estados.

## Arquitectura de la Solución (Patrón BFF)

En lugar de consumir la API de TMDB directamente desde Angular (lo cual expondría la API Key en el navegador del cliente), se implementó un **Backend-For-Frontend (BFF)** en Spring Boot.

1. **Angular** solicita los datos al BFF.
2. **Spring Boot** inyecta la credencial segura (variable de entorno), consulta a TMDB, procesa el JSON crudo y devuelve un Data Transfer Object (DTO) limpio.

## Estructura del Repositorio

El código está dividido en dos directorios principales. Cada uno contiene su propia documentación detallada y sus instrucciones de ejecución:

- [`/backend`](https://github.com/JOjeda210/Movie-Service) - API REST en **Java 21 + Spring Boot 3.x**.
- [`/frontend`](https://github.com/JOjeda210/Movie-App) - Cliente web en **Angular 22** (Signals, Standalone Components).

## Guía de Inicio Rápido

Para evaluar el proyecto, es necesario levantar ambos servicios localmente. Es **indispensable** contar con una API Key de TMDB para que el backend funcione.

### 1. Levantar el Backend (Spring Boot)

El backend requiere que inyectes tu API Key como variable de entorno (`TMDB_API_KEY`) para mantener la seguridad. Puedes hacerlo desde las configuraciones de ejecución de tu IDE (como IntelliJ IDEA) o por terminal.

**Ejecución por terminal (CLI):** navega a la carpeta `/backend` y ejecuta:

```bash
# Windows (PowerShell)
$env:TMDB_API_KEY="tu_clave_real_aqui"
mvn spring-boot:run

# Linux / macOS
export TMDB_API_KEY="tu_clave_real_aqui"
mvn spring-boot:run
```

El servidor estará disponible en `http://localhost:8080`.

### 2. Levantar el Frontend (Angular)

Abre una nueva terminal, navega a la carpeta `/frontend` y ejecuta:

```bash
npm install
ng serve
```

La aplicación web estará disponible en `http://localhost:4200`.

## Cumplimiento de la Prueba Técnica

| Requisito | Estado | Detalles de Implementación |
|-----------|:------:|----------------------------|
| P1. Configuración y Seguridad | 🟢 | Patrón BFF. API Key protegida por variables de entorno. |
| P2. Listado Populares | 🟢 | Vista principal consumiendo endpoint `/popular`. |
| P3. Buscador | 🟢 | Búsqueda integrada en Navbar, manejando casos vacíos. |
| P4. Detalles | 🟢 | Implementado mediante `MatDialog` de Angular Material. |
| P5. Diseño Responsive | 🟢 | Aplicación fluida adaptada a Móvil, Tablet y Desktop. |
| P6. Manejo de Errores y UI | 🟢 | Componentes aislados: `SkeletonCard` (carga), `EmptyState` (sin datos) y fallback automático para imágenes rotas. |
| Bonus: Favoritos | ⭐ | Gestión mediante `localStorage` + Angular Signals. |
