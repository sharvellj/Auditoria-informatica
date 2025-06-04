Manejador de Tareas con PyQt6 y Excel

Este proyecto es una aplicación de escritorio desarrollada en Python con PyQt6, diseñada para gestionar tareas de forma eficiente. 
Permite a los usuarios realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre las tareas, y lo más importante, 
persiste todos los datos en un archivo de Excel (.xlsx), asegurando que tu información no se pierda entre sesiones.

Información del Proyecto
Institución: UPTNT "Manuela Sáenz"
Asignatura: Auditoría Informática T4-M3
Desarrollado por: Sharvell Gonzalez

Funcionalidades del Programa
El Manejador de Tareas ofrece las siguientes capacidades clave:

Creación de Tareas: Añade nuevas tareas con una descripción, una fecha de vencimiento y un nivel de prioridad (Baja, Media, Alta).
Visualización de Tareas: Muestra todas las tareas existentes en una tabla clara e interactiva dentro de la interfaz.
Actualización de Tareas: Modifica cualquier detalle de una tarea ya existente, incluyendo su descripción, fecha de vencimiento, prioridad, y especialmente su estado (Pendiente, En Desarrollo, Completada).
Eliminación de Tareas: Permite borrar tareas que ya no son necesarias.
Persistencia de Datos: Todas las tareas son automáticamente guardadas en un archivo de Excel (tasks.xlsx) y cargadas cada vez que se inicia la aplicación, garantizando que tu progreso siempre esté disponible.
Estructura del Proyecto
El proyecto está organizado en una estructura modular para facilitar su mantenimiento y escalabilidad:

mi_manejador_tareas/
├── src/
│   ├── __init__.py         # Indica que 'src' es un paquete Python
│   ├── task.py             # Clase para representar una Tarea (modelo de datos)
│   └── task_manager.py     # Lógica central para interactuar con el archivo Excel (CRUD)
├── tests/
│   ├── __init__.py         # Indica que 'tests' es un paquete Python
│   └── test_task_manager.py # Pruebas unitarias y de integración para la lógica de TaskManager
├── main.py                 # Punto de entrada principal de la aplicación GUI (PyQt6)
└── README.md               # Este archivo de documentación
Requisitos e Instalación
Para ejecutar este programa, necesitarás Python 3.x y las siguientes librerías:

Bash

pip install PyQt6 openpyxl pytest
Cómo Ejecutar la Aplicación
Asegúrate de tener todas las dependencias instaladas (ver sección anterior).
Navega a la carpeta raíz del proyecto (mi_manejador_tareas/) en tu terminal o línea de comandos.
Ejecuta el archivo principal:
Bash

python main.py
La aplicación se iniciará y cargará automáticamente las tareas guardadas en tasks.xlsx (o creará uno nuevo si no existe).
Planificación y Ejecución de Pruebas
Se han implementado 10 pruebas robustas utilizando el framework pytest para auditar y verificar el correcto funcionamiento de la lógica de negocio, especialmente la interacción con el archivo de Excel. Estas pruebas se encuentran en el archivo tests/test_task_manager.py.

Cómo Ejecutar las Pruebas
Asegúrate de haber instalado las dependencias, incluyendo pytest.
Navega a la carpeta raíz del proyecto (mi_manejador_tareas/) en tu terminal.
Ejecuta pytest de la siguiente manera para que reconozca los módulos y ejecute todas las pruebas:
Bash

python -m pytest tests/
Deberías ver un resultado que indique que todas las pruebas pasaron exitosamente.
Detalles de las 10 Pruebas Realizadas
#	Nombre de la Prueba	Parte Crítica que Audita	Escenario de Prueba	Resultados Esperados	Tipo de Prueba
1	test_manager_initialization	Inicialización y Manejo de Archivo Excel	Inicializa TaskManager en un entorno limpio.	El archivo Excel se crea si no existe, con encabezados correctos y sin tareas.	Unitaria / Integración
2	test_add_single_task	Funcionalidad de Creación (CRUD - Create)	Agrega una sola tarea con datos válidos.	La tarea se añade al manager, se le asigna un ID (1), y se persiste en Excel.	Unitaria
3	test_add_multiple_tasks	Generación de ID y Adición Masiva	Agrega varias tareas consecutivamente.	Los IDs se autoincrementan correctamente (1, 2, 3...) y todas las tareas se guardan.	Unitaria
4	test_get_all_tasks	Funcionalidad de Lectura (CRUD - Read)	Carga todas las tareas desde un Excel con datos.	Retorna una lista completa y correcta de todos los objetos Task guardados.	Unitaria
5	test_update_existing_task	Funcionalidad de Actualización (CRUD - Update)	Actualiza la descripción, fecha, prioridad y estado de una tarea existente por su ID.	La tarea se actualiza correctamente en Excel y se verifica su estado al recargar.	Unitaria / Integración
6	test_update_non_existent_task	Robustez de Actualización (Casos Borde)	Intenta actualizar una tarea con un ID que no existe.	La función update_task retorna False y no altera ninguna tarea existente.	Unitaria (Borde)
7	test_delete_existing_task	Funcionalidad de Eliminación (CRUD - Delete)	Elimina una tarea existente por su ID.	La tarea es eliminada de Excel y el recuento de tareas disminuye.	Unitaria / Integración
8	test_delete_non_existent_task	Robustez de Eliminación (Casos Borde)	Intenta eliminar una tarea con un ID que no existe.	La función delete_task retorna False y no altera ninguna tarea existente.	Unitaria (Borde)
9	test_handle_empty_excel_file	Manejo de Archivos Corruptos/Vacíos	Inicializa TaskManager con un archivo Excel vacío o con encabezados incorrectos.	El manager reinicializa la hoja de Excel con los encabezados correctos y sin datos inválidos.	Integración (Robustez)
10	test_data_persistence_on_close_reopen	Persistencia de Datos y Ciclo de Vida del Manager	Agrega tareas, cierra el TaskManager, y luego lo reabre.	Las tareas agregadas previamente se cargan correctamente al reabrir el manager.	Integración (Sistema)

Exportar a Hojas de cálculo
Video Demostrativo
ENLACE A TU VIDEO AQUÍ

El video mostrará:

Una breve introducción al proyecto y sus funcionalidades clave.
Un recorrido por la estructura de archivos y los módulos principales.
La ejecución de las pruebas (python -m pytest tests/) demostrando que todas pasan.
Una demostración en vivo de la interfaz gráfica (GUI), incluyendo:
Agregar nuevas tareas.
Actualizar tareas, prestando especial atención al cambio de estado (Pendiente, En Desarrollo, Completada).
Eliminar tareas.
Verificar la persistencia de datos al cerrar y reabrir la aplicación, mostrando que las tareas y sus estados se cargan correctamente.
