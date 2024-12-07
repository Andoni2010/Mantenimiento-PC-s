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

## **Reparación de Windows**

Utiliza los siguientes comandos y herramientas para reparar el sistema operativo:

1. **Verificar la salud de los archivos:**
   - Ejecutar: `sfc /scannow`.

2. **Comprobar el estado del sistema:**
   - `DISM /online /cleanup-Image /checkHealth`: Verifica la integridad del sistema.
   - `DISM /online /cleanup-Image /scanHealth`: Realiza una búsqueda más profunda.

3. **Restaurar el sistema operativo:**
   - `DISM /online /cleanup-Image /restoreHealth`: Repara los componentes dañados.

4. **fallo del disco duro:**
   - `chkdsk C: /F /R`: busca errores y los repara.
  
---

## 5. Diagnóstico de Drivers

### **Comprobación de Drivers**  
- Abrir **Administrador de dispositivos** y verificar si algún dispositivo tiene un signo amarillo de advertencia. Esto indica que hay un problema con el driver o que no está instalado correctamente.
- Si no encontramos el error directamente, usamos herramientas como **Verifier** (Herramienta de Verificación de Controladores de Windows) para encontrar drivers defectuosos.
  - **Verifier**: Permite realizar una prueba más exhaustiva de los drivers instalados y encontrar aquellos que no estén funcionando correctamente.

### **Reparación de Drivers**  
1. **Administrador de dispositivos**:
   - Desinstalar el dispositivo con problemas y luego reiniciar el sistema para que Windows intente reinstalar los drivers automáticamente.
2. **Cambio de hardware**:
   - Si el error persiste después de desinstalar e intentar reinstalar los drivers, podría ser necesario verificar el hardware. Esto incluye asegurarse de que el dispositivo esté correctamente conectado o reemplazar el componente defectuoso.
3. **Uso de herramientas adicionales**:
   - **Driver Booster**: Una herramienta útil para escanear y actualizar todos los drivers de manera automática.
   - **Wagnardsoft (Display Driver Uninstaller)**: Utilizado para desinstalar completamente los drivers gráficos para que no haya conflictos.
   - Si el problema persiste tras realizar estas acciones, podríamos necesitar contactar al fabricante del hardware para más asistencia o considerar un cambio de hardware.
  
---

## 6. Reparación de Malware

### **Definición de Malware**  
El malware es un software diseñado para causar daño, obtener acceso no autorizado a sistemas, o robar información. Existen varios tipos:
- **Virus**: Programas que se reproducen y se diseminan a través de sistemas y archivos.
- **Spyware**: Software que recoge información sobre el usuario sin su consentimiento.
- **Adware**: Software que muestra anuncios no deseados.

### **Diagnóstico y Reparación**  
1. **Uso de Ninite**:
   - Utilizar **Ninite** para actualizar y descargar las aplicaciones necesarias como SuperAntiSpyware y Spybot.
   - **SuperAntiSpyware**: Herramienta potente para la eliminación de spyware y adware.
   - **Spybot - Search & Destroy**: Ayuda a detectar y eliminar spyware, malware y otros programas no deseados.
2. **Uso de Medicat**:
   - Arrancar **Medicat** y utilizar las herramientas de antivirus y antimalware incluidas en el paquete.
   - **Malwarebytes**: Realizar un escaneo exhaustivo del sistema para detectar y eliminar posibles amenazas.
3. **Acción final**:  
   - Si el sistema está limpio después de la reparación de malware, asegúrate de que el sistema esté completamente actualizado y que el antivirus esté habilitado para protección continua.

---

## 7. Diagnóstico de Redes

### **Comprobación de Red**  
1. **Ping**:
   - Realiza un `ping` a la dirección IP del router o del servidor para verificar la conectividad básica.
   - Ejemplo de comando: `ping 192.168.1.1`.
   - Si no se recibe respuesta, puede haber un problema de conexión en la red interna.
2. **Traceroute (tracert)**:
   - Usa el comando `tracert` para trazar la ruta de la red entre tu equipo y un destino.
   - Ejemplo de comando: `tracert www.google.com`.
   - Este comando te permite ver en qué punto de la red está ocurriendo un problema (pérdidas de paquetes, latencia, etc.).

### **Reparación de la Red**  
1. **Restablecer la conexión**:
   - Si el ping no tiene éxito, intenta restablecer la conexión de red, deshabilitando y habilitando el adaptador de red desde el Administrador de dispositivos.
   - Si el problema persiste, revisa los cables, reinicia el router o accede a la configuración de red para restablecer la conexión.
2. **Comprobaciones avanzadas**:
   - Si el problema de red sigue sin resolverse, podrías intentar verificar la configuración del firewall, los puertos y la configuración DNS.
   - También es importante revisar los routers y switches de la red para asegurarse de que no haya fallos en la infraestructura.
   - Si el problema es más grave, podrías requerir la asistencia de un profesional de redes para verificar el hardware de la red.



