# 🎓 Proyecto Gestor Académico
Autores:  
- Calero Villarreal Jonathan Christian  
- Doicela Pingos Bryan Stalin  
- Méndez Clavijo Carlos Manuel  
- Peña Bastidas Natasha Naomi  

Universidad Técnica de Ambato  
Av. Los Chasquis y Río Payamino  
📧 decanato.fcial@uta.edu.ec

## 📄 Resumen

Este documento presenta la implementación de una API para la conexión a una página web en C# (Visual Studio 2022 y Visual Studio Code), como parte del desarrollo de un proyecto de Programación Avanzada. Se aplican conceptos clave como la conexión a una base de datos, diseño de páginas web con HTML, scripts y CSS, optimizando el uso y desempeño de una aplicación web para la gestión académica.

## 🧾 Abstract

This document presents the implementation of an API for connecting to a webpage in C# (Visual Studio 2022 and Visual Studio Code) as part of an advanced programming implementation topic. Key concepts such as database connection, creating and designing a webpage with Visual Studio Code using HTML, scripts, and CSS are covered to optimize the use and performance of the web application.

---
## 📌 Introducción

El manejo de una API en programación avanzada permite la conexión de datos a una base de datos, facilitando la gestión de información en aplicaciones como páginas web. En este informe se describen funcionalidades como operaciones CRUD, consultas SQL y diseño web con HTML y CSS.

---

## 🎯 Objetivo General

Crear una aplicación web con métodos de consulta SQL y conectarla mediante una API a una página web.

### ✅ Objetivos Específicos

- Aplicar los conocimientos obtenidos en clases para el desarrollo.
- Implementar estructuras de búsqueda SQL.
- Manejar validaciones y excepciones para evitar errores en las conexiones y consultas.
- Diseñar la página web utilizando Visual Studio Code.

---

## 🛠️ Metodología

### 1. Desarrollo

#### 📌 Base de datos en SQL Server  

Para crear la base de datos en SQL Server:


1. Abrir SQL Server Management Studio y debemos conectar a la base de datos
2. En el panel izquierdo, hacer clic derecho en **Databases** > **New Database**.  
3. Asignar un nombre a la base de datos y presionar **Add**.
 

#### 🔑 Comandos clave en SQL

📌Nota: En esta parte vamos a ver los principales comandos en base a sql y su estructuración ya que tomamos en base a esto todas las demás tablas y consultas que se podrán dar.

```sql
-- Crear tabla
CREATE TABLE Estudiantes (
    Id INT PRIMARY KEY,
    Nombre NVARCHAR(50),
    Apellido NVARCHAR(50)
);

-- Insertar registros
INSERT INTO Estudiantes (Id, Nombre, Apellido)
VALUES (1, 'Juan', 'Pérez');

-- Consulta general
SELECT * FROM Estudiantes;

-- Actualizar datos
UPDATE Estudiantes
SET Nombre = 'Carlos'
WHERE Id = 1;

-- Eliminar datos
DELETE FROM Estudiantes
WHERE Id = 1;

-- Eliminar tabla
DROP TABLE Estudiantes;

-- Eliminar base de datos
DROP DATABASE SistemaGestionEstudiantes;

```
- Estas consultas o comando son en general lo más comunes en consultas o manejo en sql server (SSMS).

## 🧩 API y conexión a la base de datos

### Conexión:
Para realizar la conexión de la base de datos correspondientes debemos tener en cuenta el nombre del sql server, que fue asignada al proceso de la instalación. Lo definimos y agregamos el acceso al archivo .json.
### Plantilla:
```sql
{
    "Logging": {
        "LogLevel": {
            "Default": "Information",
            "Microsoft.AspNetCore": "Warning"
        }
    },
    "AllowedHosts": "*",
    "ConnectionStrings": {
        "Connection": "Data Source=”Nombre del usuario en sql server”;Initial Catalog=SistemaGestionEstudiantes;Integrated Security=True;TrustServerCertificate=True"
    }
}

```
## 🕹️ Controladores para el sql

Para el proyecto usamos un controlador mvc en blanco, es un componente dentro del patrón de arquitectura Modelo-Vista-Controlador, que, al crearse, no tiene ninguna lógica o funcionalidad definida.
Para el manejo correcto de los datos en sql en la inserción de un nuevo dato, usamos validaciones y excepciones.

### Plantilla:

```sql
namespace GestionCursosAPI.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class EstudiantesController : ControllerBase {
        private readonly IConfiguration _configuration;

        public EstudiantesController(IConfiguration configuration) {
            _configuration = configuration;
        }
}
```
- IConfiguration: se usa para la cadena de conexión en el json.

## 🌐 Métodos HTTP que maneja un controlador:
### GET :
Sirve para consultar o recuperar información.
### POST:
Se usa para crear nuevos recursos.
### PUT:
Sirve para actualizar completamente un recurso existente.
### DELETE: 
Se utiliza para eliminar un recurso existente.

## 📝	Models API
En la carpeta se define las propiedades de cada sección de nuestro gestor académico.

### Plantilla:
```sql
public class NombreDeLaClase {
    public int Id { get; set; }
    public string Nombre { get; set; } 
    public string Apellido { get; set; }  ….
}
```














