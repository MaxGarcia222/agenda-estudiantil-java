# Agenda Estudiantil (Java)

Aplicación de consola para estudiantes, desarrollada en equipo como trabajo final de la materia Programación II en la UTN Facultad Regional Mar del Plata (2025), junto a [Tiago Fueyo](https://github.com/tiagofueyovuillermoz-beep).

Cada usuario inicia sesión con su rol. Los estudiantes tienen tres herramientas de organización (notas, tareas y calendario) y el administrador gestiona los usuarios.

## Funcionalidades

**Usuarios**

- Registro e inicio de sesión con email y contraseña.
- Dos roles: estudiante y administrador.
- El administrador puede listar usuarios, cambiar su rol y eliminarlos.
- Los usuarios se guardan y se cargan desde un archivo JSON.

**Herramientas del estudiante**

- **Notas:** agregar, editar, continuar, cambiar el título, eliminar, ver y listar.
- **Tareas (ToDo):** agregar, completar, desmarcar, eliminar, buscar por texto y listar todas, las completadas o las pendientes.
- **Calendario:** agregar eventos por fecha y verlos por día, por semana o en una vista mensual.

## Conceptos de Java aplicados

- Herencia y clases abstractas: `Usuario` → `Estudiante` / `Administrador`, y `Herramienta` → `Notas` / `GestorTodo` / `Calendario`.
- Interfaces propias (`ConvertibleaJSON`, `DesdeJSON`) y una clase genérica (`GestorJSON<T>`) para guardar y cargar cualquier entidad en JSON.
- Enums, excepciones personalizadas (6) y colecciones (`HashMap`, `List`).
- Fechas con `java.time` (`LocalDate`).
- `switch` con flechas y *pattern matching* con `instanceof`.

## Trabajo en equipo

Trabajamos con una rama por integrante y una rama `dev`, e integramos los cambios con 15 pull requests, incluida la resolución de conflictos.

## Cómo ejecutarlo

**Requisitos:** JDK 25 (el proyecto usa `IO.println`, disponible desde esa versión).

**Con IntelliJ IDEA:**

1. Clonar el repositorio y abrirlo como proyecto.
2. Agregar `json-20240303.jar` como librería: *File → Project Structure → Libraries → +*.
3. Ejecutar `Main.java`.

**Desde la terminal:**

```bash
javac -cp json-20240303.jar -d out $(find src -name "*.java")
java -cp "out:json-20240303.jar" Main
```

En Windows, reemplazá `:` por `;` en el classpath.

**Usuarios de prueba:**

| Rol | Email | Contraseña |
| --- | --- | --- |
| Estudiante | max@gmail.com | 1234 |
| Administrador | admin@gmail.com | admin |

> Las contraseñas se guardan en texto plano porque es un proyecto académico. En un sistema real se guardarían con un hash (por ejemplo, BCrypt).

## Estructura

```text
src/
├── Enums/         Tipos de usuario
├── Exceptions/    Excepciones personalizadas
├── Gestores/      Gestión de usuarios y persistencia en JSON
├── Herramientas/  Notas, tareas y calendario
├── Interfaz/      Interfaces para convertir a JSON y desde JSON
├── Usuarios/      Usuario, Estudiante y Administrador
└── Main.java      Menús de la aplicación
```

## Mejoras pendientes

- Guardar las contraseñas con hash.
- Persistir también las notas, tareas y eventos de cada estudiante.
- Agregar tests con JUnit y migrar el proyecto a Maven.
