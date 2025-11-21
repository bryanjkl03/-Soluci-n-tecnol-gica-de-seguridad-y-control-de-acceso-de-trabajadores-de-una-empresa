# Solución tecnológica de seguridad y control de acceso de trabajadores de una empresa

## Autores
- Brayan José Pérez Orozco
- Andres Nicolas Ruiz Salinas
- David Santiago Ruiz Payanene

## Sistema de Control de Acceso y Seguridad para Trabajadores

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

### Clase Usuario

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| Usuario | String id, String nombre, String apellido | Ninguno (constructor) | Crea un usuario con sus datos básicos. | public Usuario(String id, String nombre, String apellido) |
| getId | Ninguna | String | Retorna el ID del usuario. | public String getId() |
| getNombre | Ninguna | String | Retorna el nombre del usuario. | public String getNombre() |
| getApellido | Ninguna | String | Retorna el apellido del usuario. | public String getApellido() |
| getIniciales | Ninguna | String | Devuelve las iniciales del nombre y apellido. | public String getIniciales() |
| toString | Ninguna | String | Representación textual del usuario. | public String toString() |

### Clase RegistroAcceso

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| RegistroAcceso | String idUsuario, String tipoAcceso | Ninguno (constructor) | Crea un registro de acceso con su tipo y fecha. | public RegistroAcceso(String idUsuario, String tipoAcceso) |
| getIdUsuario | Ninguna | String | Retorna el ID del usuario registrado. | public String getIdUsuario() |
| getTipoAcceso | Ninguna | String | Retorna el tipo de acceso (INGRESO o SALIDA). | public String getTipoAcceso() |
| getFechaHora | Ninguna | Date | Retorna la fecha y hora del registro. | public Date getFechaHora() |
| getFechaHoraFormateada | Ninguna | String | Retorna la fecha formateada. | public String getFechaHoraFormateada() |
| toString | Ninguna | String | Representación textual del registro. | public String toString() |


### Clase GestorArchivos

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| guardarUsuarios | List<Usuario> | void | Guarda la lista de usuarios en un archivo. | public void guardarUsuarios(List<Usuario> usuarios) |
| cargarUsuarios | Ninguna | List<Usuario> | Carga usuarios desde archivo. | public List<Usuario> cargarUsuarios() |
| guardarRegistros | List<RegistroAcceso> | void | Guarda registros de acceso en archivo. | public void guardarRegistros(List<RegistroAcceso> registros) |
| cargarRegistros | Ninguna | List<RegistroAcceso> | Carga registros desde archivo. | public List<RegistroAcceso> cargarRegistros() |
| generarIdUnico | List<Usuario> | String | Genera un ID único para nuevos usuarios. | public String generarIdUnico(List<Usuario> usuarios) |
| tieneIngresoPendiente | String idUsuario, List<RegistroAcceso> | boolean | Verifica si el usuario no ha salido aún. | public boolean tieneIngresoPendiente(String idUsuario, List<RegistroAcceso> registros) |
| puedeIngresar | String idUsuario, List<RegistroAcceso> | boolean | Verifica si puede ingresar. | public boolean puedeIngresar(String idUsuario, List<RegistroAcceso> registros) |
| puedeSalir | String idUsuario, List<RegistroAcceso> | boolean | Verifica si puede salir. | public boolean puedeSalir(String idUsuario, List<RegistroAcceso> registros) |


### Clase InterfazPrincipal

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| InterfazPrincipal | Ninguna | Ninguno (constructor) | Inicializa la interfaz principal. | public InterfazPrincipal() |
| inicializarComponentes | Ninguna | void | Configura todos los componentes gráficos. | private void inicializarComponentes() |
| cargarDatos | Ninguna | void | Carga usuarios y registros desde archivos. | private void cargarDatos() |
| actualizarListaUsuarios | Ninguna | void | Actualiza la vista de la lista de usuarios. | private void actualizarListaUsuarios() |
| actionPerformed | ActionEvent e | void | Maneja eventos de los botones. | public void actionPerformed(ActionEvent e) |
| mostrarRegistros | Ninguna | void | Muestra el historial de accesos. | public void mostrarRegistros() |
| agregarUsuario | Usuario u | void | Añade un usuario a la lista. | public void agregarUsuario(Usuario u) |
| eliminarUsuario | String id | boolean | Elimina un usuario según ID. | public boolean eliminarUsuario(String id) |
| buscarUsuario | String id | Usuario | Busca un usuario por ID. | public Usuario buscarUsuario(String id) |
| agregarRegistro | RegistroAcceso r | void | Añade un registro de acceso. | public void agregarRegistro(RegistroAcceso r) |
| getUsuarios | Ninguna | List<Usuario> | Devuelve la lista de usuarios. | public List<Usuario> getUsuarios() |
| getRegistros | Ninguna | List<RegistroAcceso> | Devuelve todos los registros. | public List<RegistroAcceso> getRegistros() |
| puedeIngresar | String id | boolean | Verifica si el usuario puede ingresar. | public boolean puedeIngresar(String id) |
| puedeSalir | String id | boolean | Verifica si el usuario puede salir. | public boolean puedeSalir(String id) |



### Clase RegistroUsuario

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| RegistroUsuario | InterfazPrincipal | Ninguno | Abre ventana para registrar usuarios. | public RegistroUsuario(InterfazPrincipal ip) |
| inicializarComponentes | Ninguna | void | Configura los elementos del formulario. | private void inicializarComponentes() |
| actionPerformed | ActionEvent e | void | Maneja los botones del formulario. | public void actionPerformed(ActionEvent e) |
| registrarUsuario | Ninguna | void | Crea y agrega un nuevo usuario. | private void registrarUsuario() |


### Clase EliminarUsuario

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| EliminarUsuario | InterfazPrincipal | Ninguno | Ventana para eliminar un usuario. | public EliminarUsuario(InterfazPrincipal ip) |
| inicializarComponentes | Ninguna | void | Configura los controles del formulario. | private void inicializarComponentes() |
| actionPerformed | ActionEvent e | void | Maneja la acción del botón eliminar. | public void actionPerformed(ActionEvent e) |
| eliminarUsuario | Ninguna | void | Elimina un usuario según ID ingresado. | private void eliminarUsuario() |


### Clase IngresoUsuario

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| IngresoUsuario | InterfazPrincipal | Ninguno | Ventana para registrar ingresos. | public IngresoUsuario(InterfazPrincipal ip) |
| inicializarComponentes | Ninguna | void | Configura los elementos de ingreso. | private void inicializarComponentes() |
| actionPerformed | ActionEvent e | void | Controla los botones. | public void actionPerformed(ActionEvent e) |
| registrarIngreso | Ninguna | void | Registra un ingreso si es permitido. | private void registrarIngreso() |


### Clase SalidaUsuario

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| SalidaUsuario | InterfazPrincipal | Ninguno | Ventana para registrar salidas. | public SalidaUsuario(InterfazPrincipal ip) |
| inicializarComponentes | Ninguna | void | Configura los elementos de salida. | private void inicializarComponentes() |
| actionPerformed | ActionEvent e | void | Maneja las acciones de botones. | public void actionPerformed(ActionEvent e) |
| registrarSalida | Ninguna | void | Registra una salida si el usuario puede salir. | private void registrarSalida() |


### Clase Licencia

| Nombre del Método | Entrada | Resultado | Solución planteada | Firma del Método |
|-------------------|---------|-----------|---------------------|------------------|
| Licencia | Ninguna | Ninguno | Muestra la licencia en pantalla. | public Licencia() |
| inicializarComponentes | Ninguna | void | Configura el área de texto con la licencia. | private void inicializarComponentes() |


# Prototipo de diseño de la interfaz de usuario

### Ventana Principal
<img width="506" height="425" alt="Image" src="https://github.com/user-attachments/assets/53cd7440-377b-403e-b1fd-99c4a76f0f5b" />

### Registro de usuarios
<img width="531" height="401" alt="Image" src="https://github.com/user-attachments/assets/9d09664f-5741-494c-9435-676b1b5d05f8" />

### Eliminación de los usuarios
<img width="539" height="399" alt="Image" src="https://github.com/user-attachments/assets/fbc5cdd3-7a0f-49bb-b54f-e0868da1a27e" />

### Ingreso de usuarios
<img width="578" height="407" alt="Image" src="https://github.com/user-attachments/assets/7871f085-eb54-4425-8821-aad0224fef30" />

### Salida de usuarios
<img width="575" height="357" alt="Image" src="https://github.com/user-attachments/assets/5c6149d4-0716-4094-8bad-d3b4a538723d" />

### Licencia de uso
<img width="393" height="365" alt="Image" src="https://github.com/user-attachments/assets/67dbff83-327b-4dc6-a1c1-86a94e405e24" />

# Fase IV: 

 ## 1.	Implementación de los métodos ( construcción de la parte lógica )
### Generación de ID Único
-	Proceso: Se crea un ID con formato "11AA11" (2 números + 2 letras + 2 números)
-	Verificación de unicidad: Se comprueba que el ID generado no exista en la lista actual de usuarios
-	Bucle de generación: Se repite el proceso hasta encontrar un ID único
o	Gestión de Archivos

-    Serialización: Los objetos Usuario y RegistroAcceso se convierten a bytes para guardar en archivos .dat
-	Recuperación de datos: Se cargan las listas desde archivos al iniciar la aplicación
-	Manejo de errores: Si no existen archivos, se retornan listas vacías
o	Validación de Accesos
-	Control de estado: Se verifica el último registro del usuario para determinar si puede ingresar o salir
-	Secuencia obligatoria: Ingreso → Salida → Ingreso (no se permiten dos ingresos consecutivos)

## 2.	Codificación de formulas
-	Fórmula de ID Aleatorio
-	ID = (número 0-9) + (número 0-9) + (letra A-Z) + (letra A-Z) + (número 0-9) + (número 0-9)	
-	Fórmula de Iniciales
-	Iniciales = (primeras 3 letras del nombre) + "*****" + espacio + (primeras 3 letras del apellido) + "*****"
-	Fórmula de Fecha/Hora
-	Fecha Formateada = "DD/MM/YYYY   HH: MM: SS"
## 3.	Asignaciones
### Asignación de Referencias
-	Interfaz Principal se asigna como referencia en todas las ventanas secundarias
-	Listas de usuarios y registros se asignan desde Gestor Archivos al iniciar
### Asignación de Eventos
-	Cada botón tiene asignado un ActionListener
-	Las acciones se asignan a métodos específicos (registrar, eliminar, etc.)
### Asignación de Datos
-	Al crear usuario: ID único + nombre + apellido
-	Al crear registro: ID usuario + tipo acceso + fecha/hora actual
## 4.	Condicionales
-	Validación de Campos Vacíos
-	SI (campo vacío) ENTONCES mostrar error Y retornar.
-	Verificación de Existencia
-	SI (usuario no encontrado) ENTONCES mostrar error Y limpiar campo
-	Control de Estado de Acceso
-	SI (puedeIngresar = falso) ENTONCES mostrar "Debe registrar salida primero"
-	SI (puedeSalir = falso) ENTONCES mostrar "Debe registrar ingreso primero"
-	Confirmación de Identidad
-	SI (usuario confirma) ENTONCES registrar acceso
-	SI NO ENTONCES limpiar campo Y solicitar nuevo intento
-	Persistencia de Datos.
-	SI (operación exitosa) ENTONCES guardar en archivo Y actualizar interfaz


# Fase V: 
