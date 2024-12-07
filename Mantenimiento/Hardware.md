# Mantenimiento de PC: Hardware y Software

## Mantenimiento de Hardware

1. **Pasta térmica y control de temperaturas:**
   - La pasta térmica ayuda a disipar el calor del procesador y debe cambiarse cada 1-3 años según su calidad.
   - Si el equipo se calienta mucho, verifica que no haya polvo obstruyendo los ventiladores o disipadores.
   - Usa alcohol isopropílico para retirar la pasta antigua y aplica una capa delgada de pasta nueva.

2. **Limpieza de componentes:**
   - **Ventiladores y disipadores:** Usa un pincel antiestático o aire comprimido.
   - **Memoria RAM:** Limpia los contactos con un paño suave y alcohol isopropílico.
   - **Placa base:** Retira el polvo con cuidado usando un pincel pequeño y seco.
   - **Discos duros y SSD:** Aunque no requieren limpieza directa, asegúrate de que estén bien conectados y sujetos para evitar daños.

3. **Herramientas recomendadas:**
   - Destornilladores magnéticos, pinceles antiestáticos, aspiradora de baja potencia y toallitas de alcohol.
   - **Nota:** Evita usar aspiradoras estándar o productos de limpieza que puedan generar electricidad estática.

4. **Verificaciones regulares:**
   - Inspecciona visualmente los conectores y cables. Asegúrate de que no estén desgastados o flojos.
   - Comprueba los filtros de polvo de la carcasa y límpialos cada 3-6 meses para mantener el flujo de aire.

---

## Mantenimiento de Software

1. **Creación de un pendrive booteable:**
   - Descarga *Rufus* y una imagen ISO del sistema operativo que necesites.
   - Configuración estándar: GPT, UEFI, FAT32 (para PCs modernos). Cambia a MBR si el equipo usa BIOS antiguo.
   - Inserta el pendrive, selecciona la ISO en *Rufus*, configura los parámetros y haz clic en "Iniciar".

2. **Optimización del sistema:**
   - Ejecuta `sfc /scannow` para verificar y reparar archivos dañados del sistema operativo.
   - Usa `chkdsk /f /r` para revisar errores en el disco duro y reparar sectores defectuosos.
   - En el Administrador de Tareas, desactiva programas innecesarios en el inicio para mejorar la velocidad del arranque.

3. **Programas útiles:**
   - **Ninite:** Instala aplicaciones esenciales rápidamente.
   - **CrystalDiskInfo:** Diagnostica el estado del disco duro.
   - **Spybot - Search & Destroy:** Protege contra malware.
   - **CCleaner:** Elimina archivos temporales y optimiza el registro (úsalo con precaución).

4. **Actualizaciones y drivers:**
   - Mantén el sistema operativo y los drivers actualizados para evitar problemas de compatibilidad.
   - Descarga drivers directamente desde el sitio oficial del fabricante.

---

## Reflexión Final

Un mantenimiento regular de hardware y software asegura un rendimiento óptimo y prolonga la vida útil del PC. Es importante combinar ambas tareas para evitar problemas futuros y garantizar que el equipo esté siempre en condiciones óptimas.
