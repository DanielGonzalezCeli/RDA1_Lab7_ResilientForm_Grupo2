# RDA1_Lab7_ResilientForm_Grupo2

Laboratorio RDA-2 Lab 2.2: Formulario de Registro Ultra-Resiliente y Navegación Predictiva.
Materia: Programación Móvil, PUCE. Profesor: Ing. Juan Francisco Chafla.

Integrantes: Daniel González, Samantha Nuñez, Juan Hoyos y Dilan Mena.

## Qué hace la app

Un formulario con dos campos (nombre y correo) que no pierde lo escrito ante rotación, destrucción de la actividad o cierre total de la app. Además, intercepta el gesto de retroceso con `BackHandler` cuando el formulario tiene datos y lo registra en Logcat con la etiqueta `NAV`.

## SavedStateHandle frente a DataStore

| | SavedStateHandle | DataStore Preferences |
| --- | --- | --- |
| Dónde guarda | Estado guardado del sistema (Bundle) | Archivo en disco |
| Rotación de pantalla | Sobrevive | Sobrevive |
| Destrucción de la actividad | Sobrevive | Sobrevive |
| Cierre total de la app | Se pierde | Sobrevive |
| Tipo de dato ideal | Borradores pequeños y temporales | Datos que deben perdurar |
| Acceso | Lectura y escritura directa con clave | Asíncrono, con Flow y corrutinas |

En este proyecto el **correo** usa SavedStateHandle y el **nombre** usa DataStore.


## Estructura

- `data/UserPreferences.kt`: acceso a DataStore.
- `ui/FormViewModel.kt`: ViewModel con SavedStateHandle y el flujo del nombre.
- `MainActivity.kt`: pantalla Compose y BackHandler.
