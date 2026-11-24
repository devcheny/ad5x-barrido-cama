# Publicación en Printables

## Ajustes de la publicación

- **Título:** AD5X · Barrido automático de la cama con espátula y soporte abatible (ZMOD + cola de Moonraker)
- **Categoría:** 3D Printers › 3D Printer Accessories
- **Etiquetas:** ad5x, flashforge, zmod, klipper, autoeject, bed clearing, print farm, queue, servo, spatula
- **Licencia:** Open Community License (OCL). Elige la versión que ofrezca Printables al subir.
- **Remix de:** <https://www.printables.com/model/1580430-flashforge-ad5x-cooling-fan-duct-mod>. Márcalo como remix al subir, para que enlace al original.
- **Archivos para subir:**
  - Modelos: `stl/` (tapa_v5, espatula_v5, puerta_soporte, base_servo) y `soporte_fijo/soporte_fijo.stl`.
  - Proyecto de Orca con todas las piezas (5 placas): `3mf/ad5x_barrido_completo.3mf`.
  - CAD: `step/`.
- **Fotos:** `docs/soporte_servo.jpg` y, si puedes, una foto o un vídeo del barrido.

---

## Descripción (pegar en Printables)

**Impresión en serie para la Flashforge AD5X con ZMOD.** Al terminar cada trabajo de la cola de Moonraker, la impresora enfría la cama y saca una espátula de un soporte abatible movido por un servo. La espátula se engancha al cabezal con una cola de milano. La impresora empuja las piezas fuera de la cama, deja la espátula y lanza la siguiente impresión.

### Qué hace
- Barre piezas de hasta 150 mm de alto: las de más de 80 mm las empuja primero más arriba, para que pasen bajo el puente delantero, y luego repasa a ras de cama. Si la pieza es más alta o el material no se puede barrer, **pausa la cola** para que la retires a mano.
- Sabe dónde están las piezas (Excluir objetos) y solo hace las pasadas necesarias.
- **Empuje lento para PETG**, con home de X/Y después de cada pasada para recuperar posibles pasos perdidos.
- **Detecta piezas pegadas con la báscula de la cama.** Reintenta hasta 3 veces, con 5 minutos de espera entre intentos. Si la pieza no se suelta, deja la espátula y pausa la cola.
- El soporte **solo se despliega para coger y dejar la espátula**. El resto del tiempo está plegado fuera de la máquina, así que no se pierde superficie de cama.
- Baja la temperatura de la cama al final de la impresión para que se enfríe antes.

### Piezas (PETG)
- **tapa_v5:** tapa del cabezal con la cola de milano. Es un remix de la *AD5X Cooling Fan Duct Mod* de H.P.: imanes de 6×2, panal cerrado y columnas del ventilador cónicas.
- **espatula_v5:** espátula de 65 mm con embudo de entrada.
- **puerta_soporte + base_servo:** soporte abatible con servo MG90S, atornillado al pilar delantero derecho.
- **soporte_fijo:** alternativa sin servo. En ese caso se pierden los 30 mm de la derecha de la cama.

El proyecto `.3mf` incluye la orientación y los ajustes que he usado: 0,20 mm, PETG, PEI texturizada.

### Material
- 11 imanes de 6×2 mm.
- Servo MG90S.
- Arduino Uno (vale un clon CH340) como segunda placa de Klipper.
- Condensador de 470–1000 µF.
- Tornillo M3×20 para la bisagra.
- 3 tornillos para el pilar.

### Software
Las macros de Klipper, el firmware del Uno, la configuración de Moonraker y Orca, y la guía de montaje y calibración completa están en GitHub:
**➜ [enlace a tu repositorio]**

### Avisos
- Probado en una sola AD5X: **calibra las posiciones en la tuya**.
- El PETG se pega muchísimo a la PEI lisa. Usa PEI texturizada o un antiadherente.
- Vigila las primeras impresiones.

### Créditos y licencia
La tapa es un remix de [Flashforge AD5X Cooling Fan Duct Mod](https://www.printables.com/model/1580430-flashforge-ad5x-cooling-fan-duct-mod) de H.P. Todo se publica bajo la **Open Community License**: puedes modificarlo y compartirlo, pero **no venderlo**.
