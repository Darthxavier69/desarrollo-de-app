# Proyecto: Cappucare - Control de Existencias de Insumos Médicos

## Integrantes del Grupo
* Josué Delgado
* Zachary Bazile
* Breidy Pimienta
* Javier Yañez
* Enlace al repositorio: https://github.com/josue-delgado/EV2_001_RF3

---

## Instrucciones de Ejecución y Credenciales de Prueba
1. Clonar el repositorio o descargar el proyecto empaquetado en formato ZIP.
2. Abrir el proyecto en Android Studio.
3. Sincronizar el proyecto con Gradle y ejecutar la aplicación en un emulador Android (API 33 o superior recomendada).
4. Acceso al sistema: En la pantalla de inicio de sesión, utilizar los botones de "Modo desarrollo" (Entrar como Personal encargado o Entrar como Usuario autorizado) para acceder y recorrer las vistas del sistema sin restricciones de autenticación manual en esta fase.

---

## Requerimientos Implementados

### RF-03: Actualizar el estado de un producto
* Descripción: Permite modificar el estado operativo de cualquier insumo médico del catálogo.
* Estados contemplados: `DISPONIBLE`, `AGOTADO`, `VENCIDO`, `DADO_DE_BAJA`.
* Regla de negocio: Se valida que el sistema impida seleccionar y guardar el mismo estado que el producto ya posee actualmente.

### RT-01: Persistencia local con Room
* Descripción: Estructuración e integración de una base de datos local basada en SQLite utilizando la librería Room de Android Jetpack.
* Componentes técnicos desarrollados:
    * `ProductoEntity`: Mapeo de la entidad de productos para la persistencia estructurada en tablas locales.
    * `CappucareDao`: Interfaz de acceso a datos que gestiona las consultas asíncronas de la aplicación.
    * `AppDatabase`: Clase abstracta de conexión con patrón Singleton encargada de instanciar la base de datos local.
    * Integración en ViewModel: Conexión de la lógica de actualización de estados (`cambiarEstado`) mediante corrutinas de Kotlin (`viewModelScope.launch`), garantizando persistencia directa en el almacenamiento del dispositivo.