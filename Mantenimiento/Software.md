# Mantenimiento de Software: Herramientas y Metodologías

## Herramientas esenciales
1. **Ordenador:** Equipo funcional para realizar las tareas de diagnóstico y reparación.
2. **Pendrive de 32GB:** Almacenamiento portátil para cargar herramientas y sistemas operativos de emergencia.
3. **Medicat:** Suite de herramientas diagnósticas avanzadas.
   - Requiere procesadores de 64 bits y BIOS UEFI.
   - Es necesario desactivar **Windows Defender** antes de instalarlo, ya que puede interferir en el proceso.
4. **Ventoy:** Herramienta para gestionar sistemas operativos y utilidades desde el pendrive.
   - **Medicat** se carga en **Ventoy** para facilitar su uso.
5. **Red:** Conexión a Internet para descargas, actualizaciones y herramientas de soporte en línea.
6. **Utilidades adicionales:**
   - **Windows Repair Toolbox:** Herramienta para diagnósticos y reparaciones de Windows.
   - **FixWin:** Solución rápida para problemas comunes de Windows.

## Metodología General
1. **Observación y toma de datos:**
   - Hablar con el cliente para identificar qué estaba haciendo cuando ocurrió el problema.
   - Registrar cualquier síntoma o error que haya notado.
2. **Elaboración de diagnóstico inicial:**
   - Identificar la parte del sistema que puede estar fallando:
     - **BOOT:** Problemas en el arranque del sistema operativo.
     - **BIOS:** Configuración o errores en la placa base.
     - **Malware:** Posibles infecciones de software malicioso.
3. **Comprobaciones iniciales:**
   - Evaluar posibles fallos físicos o de configuración en el ordenador.
4. **Diagnóstico de certeza:**
   - Confirmar los problemas observados, como pantallazos azules u otros errores detectados.
5. **Reparación:**
   - Aplicar herramientas y soluciones específicas, como **antivirus**, **FixWin**, entre otros.

---

## 2. Diagnóstico de BIOS/UEFI

### Errores comunes en BIOS/UEFI:
- **Invalid system disk**
- **Boot error**
- **Hard disk error**
- **NTLDR bootloader error**
- **Errores con pitidos:**
   - **1 pitido largo:** Error de memoria RAM.
   - **2 pitidos cortos:** Error en la tarjeta gráfica.
   - **3 pitidos largos:** Error en la tarjeta madre o memoria RAM.
   - **4 pitidos:** Error en la RAM o en el procesador.
   - **5 pitidos largos:** Error de CPU o chip.
   (Cada BIOS puede tener sus propios códigos de pitidos. Estos son solo ejemplos comunes)

### Causas comunes de errores:
- **Conexión de dispositivos periféricos** (ej. Pendrive conectado a los puertos traseros del PC)
- **Overclocking mal realizado**
- **Desgaste de la pila de la placa base**

### Importancia de mantener la BIOS actualizada:
- Es esencial verificar que la BIOS esté actualizada. Esto se puede hacer con herramientas como **CPU-Z**.
  
### Reparación de BIOS:
- **Resetear la pila:** Retirar la pila de la placa base y reiniciar el sistema puede ayudar a restaurar los valores predeterminados.
- **Clear CMOS (CLRMO):** Usar el puente de CLRMO en la placa base para resetear la BIOS.
- **BIOS Flashback:** Si la placa base lo soporta, se puede restaurar la BIOS utilizando el método de BIOS Flashback.

Dentro de la BIOS, también puedes cargar los valores predeterminados de la BIOS con **"Load Optimized Defaults"** y luego guardar los cambios.

---

## 3. Diagnóstico del BOOT

### ¿Qué es el BOOT?
El **BOOT** es el proceso que realiza el sistema para arrancar.
1. La **BIOS/UEFI** lee el disco duro.
2. El disco duro tiene particiones donde reside el **bootloader**, que indica cómo iniciar el sistema operativo.

### Tipos de particiones:
- **MBR (Master Boot Record):**
   - Estructura más antigua.
   - Soporta particiones de hasta 2TB y 4 particiones primarias.
   
- **GPT (GUID Partition Table):**
   - Estructura moderna.
   - Soporta discos de mayor capacidad y particiones ilimitadas.

### Cómo identificar el tipo de partición:
1. Presiona `Win + R` para abrir la ventana de ejecución.
2. Escribe `diskpart` y presiona Enter.
3. En la ventana de CMD, escribe `list disk` para ver los discos disponibles.
4. Luego, selecciona el disco que deseas examinar escribiendo `select disk X` (donde "X" es el número del disco).
5. Para ver las particiones de ese disco, escribe `list partition`.

## **Reparación del BOOT**
- Acceder al **Símbolo del sistema** y utilizar los siguientes comandos:
  - **bootrec /fixmbr:** Corrige el Master Boot Record.
  - **bootrec /rebuildbcd:** Reconstruye el cargador de arranque.
  - **bootrec /scanOS:** Escanea los sistemas operativos instalados.

### **Herramientas útiles:**
- **Medicat Boot Repair Disk**
- **System Tool**
- **Boot Repair**

---

## 4. Diagnóstico de Windows**

El diagnóstico del sistema sigue un orden lógico de fallos:
1. **BIOS/UEFI.**
2. **BOOT.**
3. **Windows.**

Para investigar errores como los pantallazos azules, usa herramientas como **BlueScreenView** (Nirsoft) para analizar las causas.

---

## **Reparación de Windows**

Utiliza los siguientes comandos y herramientas para reparar el sistema operativo:

1. **Verificar la salud de los archivos:**
   - Ejecutar: `sfc /scannow`.

2. **Comprobar el estado del sistema:**
   - `DISM /online /cleanup-Image /checkHealth`: Verifica la integridad del sistema.
   - `DISM /online /cleanup-Image /scanHealth`: Realiza una búsqueda más profunda.

3. **Restaurar el sistema operativo:**
   - `DISM /online /cleanup-Image /restoreHealth`: Repara los componentes dañados.

