# Solución tecnológica de seguridad y control de acceso de trabajadores de una empresa

# Sistema de Control de Acceso y Seguridad para Trabajadores

## Fase 0: Contextualización del Proyecto

### 1. ¿Qué debemos hacer?
Desarrollar un sistema tecnológico que permita gestionar y controlar el acceso de los trabajadores a las instalaciones de una empresa, garantizando la seguridad y registrando los movimientos.

### 2. ¿Qué se necesita?
- Sistema de autenticación de empleados
- Base de datos de trabajadores
- Registro de entradas y salidas
- Mecanismo de verificación de identidad
- Interfaz de administración

### 3. Elementos (objetos) que se identifican
- Trabajadores
- Credenciales de acceso
- Registros de acceso
- Horarios laborales
- Puntos de acceso

### 4. ¿Qué objetos se incluye?
- Sistema de autenticación
- Base de datos
- Módulo de reportes
- Interfaz de usuario
- Módulo de administración

### 5. ¿Cómo lo genera y que objetos se requiere?
Se genera mediante un desarrollo software que integra: base de datos, algoritmos de verificación, interfaz web/móvil, y hardware de lectura (opcional).

## Fase I: Requerimientos del Sistema

### Requerimiento 1: Autenticación de Trabajadores

| Nombre       | Autenticación de Trabajadores |
|--------------|--------------------------------|
| Descripción  | Sistema para verificar la identidad de los trabajadores al ingresar/salir |
| Entradas     | Credenciales (ID, huella, tarjeta, etc.) |
| Salidas      | Resultado de autenticación, registro de acceso |

### Requerimiento 2: Gestión de Base de Datos

| Nombre       | Gestión de Base de Datos |
|--------------|--------------------------|
| Descripción  | Almacenamiento y gestión de información de trabajadores y accesos |
| Entradas     | Datos de empleados, registros de acceso |
| Salidas      | Base de datos actualizada, consultas de información |

### Requerimiento 3: Registro de Accesos

| Nombre       | Registro de Accesos |
|--------------|---------------------|
| Descripción  | Registrar todas las entradas y salidas de los trabajadores |
| Entradas     | Datos de acceso (hora, fecha, empleado) |
| Salidas      | Historial de accesos, reportes |

### Requerimiento 4: Generación de Reportes

| Nombre       | Generación de Reportes |
|--------------|------------------------|
| Descripción  | Crear reportes de asistencia y movimientos |
| Entradas     | Datos de registros, filtros de búsqueda |
| Salidas      | Reportes en diversos formatos |

### Requerimiento 5: Interfaz de Administración

| Nombre       | Interfaz de Administración |
|--------------|----------------------------|
| Descripción  | Panel para gestionar el sistema y usuarios |
| Entradas     | Comandos de administración, configuraciones |
| Salidas      | Sistema configurado, operaciones ejecutadas |

---

---
### Pseudocódigo - Proceso de Autenticación

```pseudocodigo
INICIO ProcesoAutenticacion
    LEER credencial_ingresada
    BUSCAR trabajador_en_bd CON credencial_ingresada
    
    SI trabajador_en_bd ENCONTRADO ENTONCES
        SI trabajador_activo ENTONCES
            REGISTRAR acceso_exitoso
            PERMITIR acceso
            GUARDAR registro(hora_entrada, trabajador_id)
            MOSTRAR "Acceso permitido"
        SINO
            REGISTRAR acceso_denegado
            MOSTRAR "Trabajador inactivo"
        FIN SI
    SINO
        REGISTRAR credencial_invalida
        MOSTRAR "Credencial no válida"
    FIN SI
FIN ProcesoAutenticacion
```



## Pseudocódigo - Proceso de Autenticación

![Pseudocódigo del Sistema de Autenticación](./images/pseudocodigo-autenticacion.png)

Diagrama del proceso de autenticación de trabajadores
