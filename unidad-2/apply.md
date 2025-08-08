# Unidad 2


## 🛠 Fase: Apply

# Actividad 4

**Estados**
- Modo de configuración (`CONFIG_STATE`)
- Modo de contador (`CONTADOR_STATE`)
- Explocion (`EXPLODE_STATE`)
- Regresar a modo de configuración(`RESET_STATE`)

**Eventos**
- Presionar el boton A (`button_a.was_pressed()`)
- Presionar el boton B (`button_b.was_pressed()`)
- Iniciar contador (`accelerometer.was_gesture('shake')`)
- Fin contador (``)
- Volver modo configuración **touch**

**Acciones**
- `mostrar_Tiempo()` | Mostrar tiempo en pantalla
- `aumentar_Tiempo()` | Aumenta 1 segundo si < 60
- `disminuir_Tiempo()` | Disminuye 1 segundo si > 60
- `iniciar_Cr()` | Inicia la cuenta regresiva
- `detonar_Bomba()` | Sonar speaker
- `resetear_Bomba()` | Volver a modo de configuración
