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

Diagrama del proceso de autenticación de trabajadores

![Image](https://github.com/user-attachments/assets/1f5baf25-61dd-4fc2-83db-3c6a745cbfdb)

## Fase II: Diseño del Sistema

# Clases identificadas del código:

-Usuario - Representa a un trabajador de la empresa

-RegistroAcceso - Representa un registro de ingreso/salida

-InterfazPrincipal - Control principal del sistema

-GestorArchivos - Maneja la persistencia de datos

-RegistroUsuario - Interfaz para registrar usuarios

-EliminarUsuario - Interfaz para eliminar usuarios

-IngresoUsuario - Interfaz para registrar ingresos

-SalidaUsuario - Interfaz para registrar salidas

-Licencia - Interfaz de términos y condiciones

-Main - Punto de entrada de la aplicación

# Main
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:300px; text-align:left;">
  <tr>
    <th style="background:#f2f2f2; text-align:center;">Main</th>
  </tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - ninguno
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + main(String[] args): void
    </td>
  </tr>
</table>


# interfaz principal
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:350px;">
  <tr><th style="background:#f2f2f2; text-align:center;">InterfazPrincipal</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - listaUsuarios: JList<br>
      - modeloLista: DefaultListModel<br>
      - btnRegistrar: JButton<br>
      - btnEliminar: JButton<br>
      - btnIngreso: JButton<br>
      - btnSalida: JButton<br>
      - btnRegistro: JButton<br>
      - btnLicencia: JButton<br>
      - usuarios: List&lt;Usuario&gt;<br>
      - registros: List&lt;RegistroAcceso&gt;
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + InterfazPrincipal()<br>
      + inicializarComponentes(): void<br>
      + cargarDatos(): void<br>
      + actualizarListaUsuarios(): void<br>
      + actionPerformed(ActionEvent): void<br>
      + mostrarRegistros(): void<br>
      + agregarUsuario(Usuario): void<br>
      + eliminarUsuario(String): boolean<br>
      + buscarUsuario(String): Usuario<br>
      + agregarRegistro(RegistroAcceso): void<br>
      + getUsuarios(): List&lt;Usuario&gt;<br>
      + getRegistros(): List&lt;RegistroAcceso&gt;<br>
      + puedeIngresar(String): boolean<br>
      + puedeSalir(String): boolean
    </td>
  </tr>
</table>


# Usuario
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:300px;">
  <tr><th style="background:#f2f2f2; text-align:center;">Usuario</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - id: String<br>
      - nombre: String<br>
      - apellido: String
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + Usuario(String, String, String)<br>
      + getId(): String<br>
      + getNombre(): String<br>
      + getApellido(): String<br>
      + getIniciales(): String<br>
      + toString(): String
    </td>
  </tr>
</table>

# RegistroAcceso
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:300px;">
  <tr><th style="background:#f2f2f2; text-align:center;">RegistroAcceso</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - idUsuario: String<br>
      - tipoAcceso: String<br>
      - fechaHora: Date
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + RegistroAcceso(String, String)<br>
      + getIdUsuario(): String<br>
      + getTipoAcceso(): String<br>
      + getFechaHora(): Date<br>
      + getFechaHoraFormateada(): String<br>
      + toString(): String
    </td>
  </tr>
</table>

# GestorArchivos
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:350px;">
  <tr><th style="background:#f2f2f2; text-align:center;">GestorArchivos</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - ARCHIVO_USUARIOS: String<br>
      - ARCHIVO_REGISTROS: String
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + guardarUsuarios(List&lt;Usuario&gt;): void<br>
      + cargarUsuarios(): List&lt;Usuario&gt;<br>
      + guardarRegistros(List&lt;RegistroAcceso&gt;): void<br>
      + cargarRegistros(): List&lt;RegistroAcceso&gt;<br>
      + generarIdUnico(List&lt;Usuario&gt;): String<br>
      + tieneIngresoPendiente(String, List&lt;RegistroAcceso&gt;): boolean<br>
      + puedeIngresar(String, List&lt;RegistroAcceso&gt;): boolean<br>
      + puedeSalir(String, List&lt;RegistroAcceso&gt;): boolean
    </td>
  </tr>
</table>

# RegistroUsuario
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:330px;">
  <tr><th style="background:#f2f2f2; text-align:center;">RegistroUsuario</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - campoNombre: JTextField<br>
      - campoApellido: JTextField<br>
      - btnAceptar: JButton<br>
      - btnCancelar: JButton<br>
      - interfazPrincipal: InterfazPrincipal
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + RegistroUsuario(InterfazPrincipal)<br>
      + inicializarComponentes(): void<br>
      + actionPerformed(ActionEvent): void<br>
      + registrarUsuario(): void
    </td>
  </tr>
</table>

# EliminarUsuario
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:320px;">
  <tr><th style="background:#f2f2f2; text-align:center;">EliminarUsuario</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - campoId: JTextField<br>
      - btnEliminar: JButton<br>
      - btnCancelar: JButton<br>
      - interfazPrincipal: InterfazPrincipal
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + EliminarUsuario(InterfazPrincipal)<br>
      + inicializarComponentes(): void<br>
      + actionPerformed(ActionEvent): void<br>
      + eliminarUsuario(): void
    </td>
  </tr>
</table>

# IngresoUsuario
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:320px;">
  <tr><th style="background:#f2f2f2; text-align:center;">IngresoUsuario</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - campoId: JTextField<br>
      - btnIngresar: JButton<br>
      - btnCancelar: JButton<br>
      - interfazPrincipal: InterfazPrincipal
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + IngresoUsuario(InterfazPrincipal)<br>
      + inicializarComponentes(): void<br>
      + actionPerformed(ActionEvent): void<br>
      + registrarIngreso(): void
    </td>
  </tr>
</table>

# SalidaUsuario
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:320px;">
  <tr><th style="background:#f2f2f2; text-align:center;">SalidaUsuario</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - campoId: JTextField<br>
      - btnSalida: JButton<br>
      - btnCancelar: JButton<br>
      - interfazPrincipal: InterfazPrincipal
    </td>
  </tr>
  <tr>
    <td>
      <strongMétodos</strong><br>
      + SalidaUsuario(InterfazPrincipal)<br>
      + inicializarComponentes(): void<br>
      + actionPerformed(ActionEvent): void<br>
      + registrarSalida(): void
    </td>
  </tr>
</table>

# Licencia
<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width:260px;">
  <tr><th style="background:#f2f2f2; text-align:center;">Licencia</th></tr>
  <tr>
    <td>
      <strong>Atributos</strong><br>
      - areaTexto: JTextArea
    </td>
  </tr>
  <tr>
    <td>
      <strong>Métodos</strong><br>
      + Licencia()<br>
      + inicializarComponentes(): void
    </td>
  </tr>
</table>

## Documentacion atributos de la clase
| Clase             | Atributo         | Codificación       | Objetivo                                                     |
|-------------------|------------------|---------------------|--------------------------------------------------------------|
| Usuario           | id               | string                  | Identificador único del usuario (formato 11AA11)            |
| Usuario           | nombre           | string              | Nombre del trabajador                                        |
| Usuario           | apellido         | string            | Apellido del trabajador                                      |
| RegistroAcceso    | idUsuario        | string           | ID del usuario que realiza el acceso                         |
| RegistroAcceso    | tipoAcceso       | string          | Tipo de acceso ("INGRESO" o "SALIDA")                       |
| RegistroAcceso    | fechaHora        | date           | Fecha y hora del registro automático                         |
| InterfazPrincipal | usuarios         | List<Usuario>            | Lista de usuarios registrados en el sistema                  |
| InterfazPrincipal | registros        | List<RegistroAcceso>          | Lista histórica de registros de acceso                       |
| GestorArchivos    | ARCHIVO_USUARIOS | string    | Nombre del archivo para persistir usuarios                   |
| GestorArchivos    | ARCHIVO_REGISTROS| string   | Nombre del archivo para persistir registros                  |
| RegistroUsuario    | campoNombre| JTextField   | Campo para nombre usuario                  |
| RegistroUsuario    | 	campoApellido| JTextField   | Campo para apellido usuario                  |

# Fase III:
# Documentación Métodos de la clase

# Clase InterfazPrincipal


# InterfazPrincipal()
| Nombre del Método | InterfazPrincipal() |
|-------------------|---------------------|
| Entrada (lista de parámetros) | Ninguna |
| Resultado (tipo de dato de retorno) | Ninguno (constructor) |
| Solución planteada | Inicializa la interfaz principal del sistema y configura los componentes gráficos. |
| Firma del Método | public InterfazPrincipal() |


# inicializarComponentes()
| Nombre del Método | inicializarComponentes |
|-------------------|------------------------|
| Entrada (lista de parámetros) | Ninguna |
| Resultado (tipo de dato de retorno) | void |
| Solución planteada | Crea y configura todos los elementos visuales y botones de la interfaz. |
| Firma del Método | public void inicializarComponentes() |

# cargarDatos()
| Nombre del Método | cargarDatos |
|-------------------|-------------|
| Entrada | Ninguna |
| Resultado | void |
| Solución planteada | Carga desde archivo la lista de usuarios y registros almacenados. |
| Firma del Método | public void cargarDatos() |

# actualizarListaUsuarios()
| Nombre del Método | actualizarListaUsuarios |
|-------------------|-------------------------|
| Entrada | Ninguna |
| Resultado | void |
| Solución planteada | Actualiza visualmente la lista de usuarios en pantalla usando el modelo de lista. |
| Firma del Método | public void actualizarListaUsuarios() |

# actionPerformed(ActionEvent)
| Nombre del Método | actionPerformed |
|-------------------|-----------------|
| Entrada | ActionEvent e |
| Resultado | void |
| Solución planteada | Gestiona todas las acciones de botones y ejecuta la operación correspondiente. |
| Firma del Método | public void actionPerformed(ActionEvent e) |

# mostrarRegistros()
| Nombre del Método | mostrarRegistros |
|-------------------|------------------|
| Entrada | Ninguna |
| Resultado | void |
| Solución planteada | Muestra la ventana con el historial completo de registros de acceso. |
| Firma del Método | public void mostrarRegistros() |

# agregarUsuario(Usuario)
| Nombre del Método | agregarUsuario |
|-------------------|----------------|
| Entrada | Usuario u |
| Resultado | void |
| Solución planteada | Añade un nuevo usuario a la lista y actualiza su visualización. |
| Firma del Método | public void agregarUsuario(Usuario u) |

# eliminarUsuario(String)
| Nombre del Método | eliminarUsuario |
|-------------------|-----------------|
| Entrada | String id |
| Resultado | boolean |
| Solución planteada | Elimina un usuario según su ID y devuelve true si fue eliminado. |
| Firma del Método | public boolean eliminarUsuario(String id) |

# buscarUsuario(String)
| Nombre del Método | buscarUsuario |
|-------------------|---------------|
| Entrada | String id |
| Resultado | Usuario |
| Solución planteada | Busca un usuario en la lista por su ID y lo retorna. |
| Firma del Método | public Usuario buscarUsuario(String id) |

# agregarRegistro(RegistroAcceso)
| Nombre del Método | agregarRegistro |
|-------------------|-----------------|
| Entrada | RegistroAcceso r |
| Resultado | void |
| Solución planteada | Añade un nuevo registro de acceso al historial del sistema. |
| Firma del Método | public void agregarRegistro(RegistroAcceso r) |

# getUsuarios()
| Nombre del Método | getUsuarios |
|-------------------|-------------|
| Entrada | Ninguna |
| Resultado | List<Usuario> |
| Solución planteada | Devuelve la lista completa de usuarios registrados. |
| Firma del Método | public List<Usuario> getUsuarios() |

# getRegistros()
| Nombre del Método | getRegistros |
|-------------------|--------------|
| Entrada | Ninguna |
| Resultado | List<RegistroAcceso> |
| Solución planteada | Devuelve la lista completa de registros almacenados. |
| Firma del Método | public List<RegistroAcceso> getRegistros() |

# puedeIngresar(String)
| Nombre del Método | puedeIngresar |
|-------------------|---------------|
| Entrada | String idUsuario |
| Resultado | boolean |
| Solución planteada | Determina si el usuario puede registrar un ingreso según su último estado. |
| Firma del Método | public boolean puedeIngresar(String idUsuario) |

# puedeSalir(String)
| Nombre del Método | puedeSalir |
|-------------------|------------|
| Entrada | String idUsuario |
| Resultado | boolean |
| Solución planteada | Verifica si el usuario puede registrar una salida según su estado anterior. |
| Firma del Método | public boolean puedeSalir(String idUsuario) |
