# 📋 Historial de Cambios & Registro de Proyecto (Changelog)
**Proyecto:** RetailCAD Pro Studio - Diseñador & Optimizador de Tiendas Retail  
**Ubicación:** `C:\Users\pc\.gemini\antigravity\scratch\plano_tienda\`  
**Última Actualización:** 2026-08-26 (Versión 4.0 Super Suite)

---

## 📌 Índice de Módulos & Estado Actual
- [x] **Lienzo 2D CAD Interactivo** (Escala arquitectónica `1:50`, $1\text{m} = 100\text{px}$).
- [x] **🚦 Auditor de Pasillos & Semáforo de Accesibilidad** (🔴 $<0.90\text{m}$, 🟡 $0.90-1.20\text{m}$, 🟢 $>1.20\text{m}$).
- [x] **🚶‍♂️ Simulador de Recorrido de Clientes (Customer Journey)** (Agentes animados, HUD de tiempos y compras completadas).
- [x] **🧩 Multiselección, Agrupación & Portapapeles** (Recuadro Marquee, <kbd>Shift+Clic</kbd>, <kbd>Ctrl+C</kbd>, <kbd>Ctrl+V</kbd>).
- [x] **↶ Historial Deshacer / Rehacer** (<kbd>Ctrl+Z</kbd>, <kbd>Ctrl+Y</kbd> / <kbd>Ctrl+Shift+Z</kbd> con pila de 40 estados).
- [x] **🎨 Visor 3D Realista con Planogramas** (Baldas multinivel, productos simulados, iluminación fría LED y carteles colgantes por departamento).
- [x] **Tiradores de Precisión & Separación de Giro** (Hitboxes ampliados a $20\text{px}$, vástago de rotación a $-34\text{px}$).
- [x] **Proyección Matemática Local para Redimensionar Objetos Girados** (Mantiene la física exacta al estirar muebles con rotación de $0^\circ$ a $360^\circ$).
- [x] **Trazador Manual del Perímetro / Cajón del Local** (Click & Drag + redimensionamiento libre).
- [x] **Cotas Dinámicas en Tiempo Real** (Cálculo automático de separación de pasillos en 4 direcciones).
- [x] **Guías Inteligentes de Simetría & Snap Magnético** (Alineación con ejes, bordes y coincidencia de tamaño).
- [x] **Mapa de Calor & Líneas de Tráfico** (Puntos radiales y rutas continuas de compra).
- [x] **Estandarización de Nomenclatura & Inventario** (`CAM`, `CONG`, `M`, `CAB`, `POS`, `GRAN`, `FRUV`, `HUEV`, `ACCESO`, `SERV`).
- [x] **Diseño & Accesibilidad Impeccable** (Tipografía Inter + JetBrains Mono, temas Claro/Oscuro, WCAG 2.1).
- [x] **Exportadores de Producción** (AutoCAD `.dxf`, Vectorial `.svg`, Imagen HD `.png`, Proyecto `.json`).

---

## 🚀 Registro Cronológico de Versiones & Mejoras

### 🌟 Versión 4.8 (Actual) — Simulación Inteligente con A* Pathfinding & Customer Journey Lógico
* **🧭 Navegación A\* sobre Malla de Obstáculos Dinámica (NavGrid):**
  * **Cero Atravesamiento de Muebles:** Matriz de navegación espacial de alta resolución ($12\text{px}$) que rasteriza automáticamente góndolas, murales, cámaras, islas, cajas y muros con un margen de seguridad perimetral ($11\text{px}$).
  * **Suavizado de Trayectorias (String-Pulling & Raycasting):** Convierte escalones de cuadrícula en líneas de marcha directas y fluidas a través de los pasillos abiertos.
  * **Adaptación en Tiempo Real:** Al mover, rotar o redimensionar cualquier mueble en el plano 2D, la malla de navegación se actualiza instantáneamente.
* **🚫 Cero Rebotes & Cinemática Natural:**
  * **Interpolación Angular Continua:** Giro progresivo del avatar y del carrito según el vector de avance hacia los waypoints.
  * **Fuerza Social de Separación (Soft Flocking):** Los clientes reducen el solapamiento con un suave desvío lateral sin rebotar ni reflejar velocidades.
* **🛒 Ciclo de Vida Lógico del Cliente (Customer Journey):**
  1. **Ingreso:** Entrada por puertas designadas (`ACCESO 01 / 02`).
  2. **Equipamiento:** Recogida de carrito 🛒 en `EST-01` o canasta 🧺 en `CAN-01`.
  3. **Compras:** Recorrido por 2 a 5 estantes/categorías diferentes, con detención de compra ($1.6 - 3.4\text{s}$), giro hacia el mueble y micro-burbuja de producto (🍎, 🥦, 🥛, 🍞, 🧀, 🥩, 🥚, 🌾) que llena visualmente el carrito.
  4. **Cobro:** Selección y cola en cajas (`POS-01 / 02 / 03`), pausa de cobro con halo verde (`💳 Pago POS`).
  5. **Salida:** Egreso por puertas de salida (`ACCESO 03 / 04`) y conteo de estadísticas.

---

### 🌟 Versión 4.7 — Planograma 2D de Canastas & Orientación 3D Corregida
* **📦 Cuadritos y Divisiones de Canastas en 2D:**
  * Dibujo paramétrico de la retícula de canastas individuales en el plano 2D:
    * **Mural Frío (`CAM-01`):** 21 canastas verdes individuales a lo largo de los $7.37\text{m}$.
    * **Mural Seco (`M-09 a 14`):** Doble hilera de canastas negras con borde amarillo a lo largo de los $7.70\text{m}$.
    * **Mueble Central Fruver (`M-03 a 08`):** Retícula modular de 2 hileras de canastas con código de colores.
    * **Islas & Huevos:** Retícula 2x2 de cajas plásticas azules, rojas y maples de huevo.
* **🔄 Corrección de Orientación de Mobiliario 3D:**
  * **Góndolas de Granos (`GRAN-01 & GRAN-02`):** Invertidas para que las baldas, sacos de arroz, frijoles y tiras de precios miren al frente hacia el pasillo (en lugar de hacia la pared trasera).
  * **Cámaras de Frío de 2 Puertas (`CAM-04 & CAM-05`):** Puertas de vidrio orientadas directamente hacia los pasillos de circulación de clientes.
  * **Carteles Colgantes de Precios:** Corregida la rotación normal de los carteles del mural seco para que sean 100% legibles de frente.
  * **Cabeceras Norte / Sur (`CAB-01 & CAB-02`):** Inclinación calibrada hacia los extremos de aproximación.

---

### 🌟 Versión 4.6 — Simulación Multi-Puertas & Vistas Rápidas 3D
* **📸 Distribución Alineada con Foto Aérea General:**
  * **Pared Izquierda:** `CAM-01` Mural Frío Fruver ($7.37\text{m}$) con 21 canastas, dosel LED y faldón comercial + Vitrina de bebidas con puertas de vidrio.
  * **Pasillo Central (3 Islas en Línea):** 
    1. `ISLA-03`: Repollos verdes 🥬 y zapotes en cajas rojas/negras.
    2. `HUEV-01`: Estación de Huevos en maples de 30 unidades.
    3. `ISLA-01`: Cajas plásticas azules apiladas con naranjas y mandarinas 🍊.
  * **Mueble Central Fruver ($4.69\text{m}$):** Mesa longitudinal con aguacates 🥑, tomates 🍅, repollos 🥬, chiles 🫑, limones 🍋, carteles amarillos de precios en mástiles y **Cabecera Bananera con Sombrilla / Parasol Verde ⛱️**.
  * **Pared Derecha:** `M-09 a 14` Mural Seco de Tubérculos & Hortalizas ($7.70\text{m}$) con **tejitas de barro rústicas** en la pared y carteles amarillos.
  * **Góndolas de Granos:** `GRAN-01 & GRAN-02` con estantería metálica blanca, bolsas de frijoles 🫘, sacos de arroz 🌾 y jarabes 🍾.
* **🎯 Desduplicación Inteligente de Cotas y Pasillos:**
  * Eliminado el solapamiento de cajas de cota sobre las píldoras de semáforo de accesibilidad.

---

### 🌟 Versión 4.2 — Modelado Fotorrealista de Mobiliario Central & Mural Seco
* **Mural Abierto de Frutas & Verduras ($7.37\text{m}$ / 21 Cajas):**
  * Basado directamente en las imágenes y plano de ubicación del local.
  * **Estructura Retail:** Carcasa blanca con faldón frontal y moldura verde anti-golpe.
  * **Dosel Superior:** Iluminación LED cálida continua proyectada sobre el producto.
  * **3 Niveles Escalonados:**
    * *Nivel 1 (Superior):* Bandejas y empaques de uvas, fresas y hojas verdes.
    * *Nivel 2 (Medio):* Hortalizas, zanahorias, remolachas y cítricos.
    * *Nivel 3 (Inferior):* 21 canastas plásticas verdes inclinadas $15^\circ$ hacia el cliente con manzanas rojas 🍎, verdes 🍏, peras 🍐, naranjas 🍊 y hortalizas.

---

### 🌟 Versión 4.0 (Super Suite Retail) — Las 4 Grandes Mejoras
1. **🚦 Auditor de Pasillos & Ergonomía de Tráfico:**
   * Motor geométrico de detección de pasillos entre muebles paralelos y muros.
   * Semáforo de accesibilidad en vivo con badges en 2D:
     * 🔴 **Crítico (< 0.90m):** No cabe un carrito o incumple normativa de accesibilidad.
     * 🟡 **Ajustado (0.90m - 1.20m):** Paso de 1 solo carrito.
     * 🟢 **Óptimo (> 1.20m):** Cruce cómodo de 2 carritos.
   * Tarjeta de estado en tiempo real en la barra lateral con contadores de pasillos.
2. **🚶‍♂️ Simulador de Recorrido de Clientes (Customer Journey):**
   * Motor de animación de compradores con carritos 🛒 que ingresan por las puertas (`ACCESO-01/02`), recorren los pasillos calientes y cabeceras de oferta, hacen fila y pagan en cajas (`POS`), y salen por `ACCESO-03/04`.
   * Barra de control HUD flotante: Iniciar/Pausar, Reiniciar, Velocidad ($1\times, 2\times, 4\times$), conteo de clientes activos, compras completadas y tiempo promedio.
3. **🧩 Multiselección, Agrupación & Deshacer/Rehacer:**
   * **Multiselección:** Selección múltiple mediante <kbd>Shift + Clic</kbd> o recuadro de arrastre (Marquee Box Selection) en áreas vacías.
   * **Arrastre en Bloque:** Mover un mueble seleccionado arrastra automáticamente a todo el grupo seleccionado manteniendo distancias relativas.
   * **Agrupación de Muebles (`📦 Agrupar` / `🔓 Desagrupar`):** Permite vincular góndolas y cabeceras como una sola unidad indivisible.
   * **Historial Completo:** Pila de 40 estados con <kbd>Ctrl+Z</kbd> (Deshacer) y <kbd>Ctrl+Y</kbd> (Rehacer).
   * **Portapapeles:** <kbd>Ctrl+C</kbd> y <kbd>Ctrl+V</kbd> para clonar muebles o bloques completos.
4. **🎨 3D Realista & Planogramas Comerciales:**
   * **Estanterías Detalladas:** Góndolas y murales secos con baldas/estantes multinivel y micro-cajas de productos coloridos simulando un planograma real.
   * **Cámaras Frías Avanzadas:** Puertas de cristal tintado cyan translúcido con marco metálico y reflejos.
   * **Cajas Registradoras 3D:** Mueble con cinta transportadora de goma negra y pantalla de terminal POS.
   * **Estación de Carritos 3D:** Filas de carritos metálicos detallados en `EST-01`.
   * **Carteles Colgantes de Departamentos:** Banners aéreos 3D suspendidos del techo (*❄️ LÁCTEOS & FRÍO*, *🛒 ABARROTES Y SECOS*, *💳 ZONA DE COBRO & SALIDA*, *🍊 FRUTERÍA & GRANOS*).

---

### 🌟 Versión 3.7 — Corrección de Tiradores de Bordes & Giro de Precisión
* **Separación de Zonas de Clic (Anti-Conflicto):** 
  * Se distanció el tirador de rotación superior a **$-34\text{px}$** con un vástago visible.
  * Se añadieron **zonas de contacto invisibles aumentadas a $20\text{px} \times 20\text{px}$** en cada tirador de esquina y borde.
* **Proyección Matemática Local en Redimensionamiento:**
  * Al redimensionar muebles rotados, el arrastre se proyecta en los ejes locales mediante $(\cos(-\theta), \sin(-\theta))$, impidiendo que el mueble se deforme o invierta erráticamente.
* **Botones de Giro Rápido:** `↺ -90°`, `↻ +90°`, `↔ Invertir Ancho/Fondo` y atajo <kbd>R</kbd>.

---

### 🌟 Versión 3.6 — Restauración & Potenciación de Mapa de Calor
* **Pestaña Dedicada `🔥 Calor`:** Acceso rápido en el menú superior.
* **Puntos Térmicos Radiales:** 🔴 Muy Caliente, 🟠 Templado, 🔵 Frío.
* **Líneas de Flujo de Tráfico Caliente:** Rutas continuas de compra arrastrables.

---

### 🌟 Versión 3.5 — Cotas Dinámicas & Simetría Inteligente
* **Cotas Dinámicas en Tiempo Real:** Raycasting en 4 direcciones midiendo pasillos exactos.
* **Guías de Simetría (Líneas Fucsias `#ec4899`):** Detección automática al alinear bordes o centros.
* **Snap Magnético ($8\text{ cm}$):** Imantación para alineaciones perfectas.

---

### 🌟 Versión 3.4 — Trazado Manual del Perímetro / Cajón de la Tienda
* **Herramienta `🏗️ Trazar Perímetro`:** Clic y arrastre para definir el cajón exterior con indicador de $m^2$ en vivo.

---

### 🌟 Versión 3.0 — Estandarización de Nomenclatura & Limpieza de Proyecto
* **Estandarización de Códigos Retail:** `CAM-01..05`, `M-01..14`, `CAB-01..06`, `POS-01..03`, `GRAN-01..02`, `FRUV-01..03`, `HUEV-01..02`, `ACCESO-01..04`, `SERV-01..03`.
* **Modal de Limpieza en 3 Opciones:** Lienzo en blanco, solo mobiliario o restablecer valores de fábrica.

---

## 🛠️ Próximas Mejoras & Registro Futuro
1. `[ ]` ...
2. `[ ]` ...
