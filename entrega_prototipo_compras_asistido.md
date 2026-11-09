# Entrega: Prototipo de sistema de compras asistido para personas con discapacidad visual

Proyecto: sistema global de compras asistido (ceguera total y baja visión), integrado a los terminales POS de los comercios para sincronizar catálogo, precios, lectura de productos y flujo de pago accesible.

---

# Entregable 1: Análisis de prototipos

## 1. Público objetivo

- **Quién usará la aplicación:** personas adultas con ceguera total o baja visión, de origen congénito o asociado a la edad. Compran en comercios con terminal POS y hoy dependen de un acompañante o del personal de tienda para identificar productos y pagar.
- **Contexto de uso:** presencial, de pie y en movimiento, con ruido ambiente. Suelen tener una sola mano libre, porque la otra sostiene el bastón, al perro guía o las bolsas.
- **Necesidades:**
  - Conocer el nombre y el precio de cada producto sin ayuda.
  - Saber el total acumulado.
  - Pagar con certeza del monto cobrado.
  - Recibir un comprobante legible.
- **Conocimientos digitales:** usan smartphone con lector de pantalla (TalkBack en Android, VoiceOver en iOS). El nivel es heterogéneo, de básico a intermedio, y menor en personas mayores.
- **Barreras:**
  - Etiquetas y precios solo visuales.
  - Pantallas táctiles de POS sin retroalimentación táctil ni auditiva.
  - Apps con botones sin etiqueta, bajo contraste y texto pequeño.
  - Gestos complejos y sesiones con límite de tiempo.

## 2. Objetivo central del prototipo

- **Necesidad que resuelve:** la falta de autonomía en la compra. Hoy una persona ciega o con baja visión no puede verificar por sí misma qué producto toma, cuánto cuesta ni cuánto paga.
- **Acción principal:** escanear un producto y recibir por voz y en pantalla su nombre, precio y disponibilidad, consultados en tiempo real al catálogo del POS del comercio. Esa acción alimenta el carrito y desemboca en el pago accesible.

## 3. Flujo del usuario

**Ruta del usuario paso a paso:**

1. Abrir la app. Se detecta el comercio mediante QR de entrada o ubicación, y la app anuncia: "Conectado a [comercio]".
2. Autenticarse con biometría o sesión recordada, sin CAPTCHA ni límite de tiempo.
3. Elegir el modo desde la pantalla de inicio: "Escanear producto" (acción principal) o "Buscar por voz".
4. Escanear el código de barras con la cámara, con guía sonora y háptica para encuadrar.
5. La app consulta el catálogo del POS y lee la ficha: nombre, precio, precio por unidad y stock.
6. Agregar al carrito con un botón grande o un gesto simple. La app confirma por voz y con vibración, y anuncia el total acumulado.
7. Revisar el carrito. Se lee la lista de productos y el total, con opción de eliminar ítems.
8. Pagar: la app lee el monto y pide confirmación explícita. El cobro se ejecuta en el POS, y los datos de tarjeta se procesan únicamente en el terminal, no en la app.
9. Recibir el comprobante: lectura por voz del resumen y envío digital en formato accesible.

## 4. Diseño de interfaz (UI)

| Elemento | ¿Está claro y funcional? | Qué mejorar |
|---|---|---|
| **Tipografía** | Sans-serif sin adornos (Atkinson Hyperlegible, diseñada para baja visión). Texto base mínimo de 20 px, títulos de 28 a 32 px, interlineado 1,5. | Soportar ampliación al 200 % sin pérdida de contenido (WCAG 1.4.4). Evitar mayúsculas continuas y cursivas. |
| **Colores** | Paleta de alto contraste AAA (Entregable 2). La información nunca depende solo del color. | Agregar modo claro y oscuro, seleccionable por el usuario. Verificar todos los pares con un medidor de contraste. |
| **Botones** | Un botón primario por pantalla. Etiqueta con verbo y objeto ("Escanear producto", "Pagar ahora"). Ancho completo. | Área táctil mínima de 44×44 px (WCAG 2.5.5, AAA). Foco visible de 3 px en amarillo. Separación mínima de 8 px entre botones. |
| **Íconos** | Trazo grueso y forma simple. Siempre acompañados de texto. | Etiqueta accesible (`aria-label` o `contentDescription`) en cada ícono funcional. Íconos decorativos ocultos al lector de pantalla. Contraste mínimo de 3:1. |
| **Menús** | Barra inferior de 4 opciones fijas (Escanear, Buscar, Carrito, Cuenta), alcanzable con el pulgar. | Mismo orden en todas las pantallas. Sin menús que dependan de hover o gestos complejos. Orden de foco igual al orden visual. |

## 5. Principios de Experiencia de Usuario (UX) aplicados

- [X] **Consistencia visual y funcional.** Se repiten la misma barra inferior, la misma tipografía, el mismo botón primario amarillo y el mismo patrón de confirmación (voz, vibración y texto) en las nueve etapas del flujo.
- [X] **Accesibilidad (colores, lenguaje, navegación simple).** Contraste AAA, ampliación de texto al 200 %, etiquetas para lector de pantalla, lenguaje simple y área táctil de 44 px. Para ceguera total, la estructura semántica (encabezados, regiones y orden de foco) reemplaza a lo visual.
- [X] **Simplicidad y claridad.** Una acción principal por pantalla y máximo 4 opciones de navegación. No hay formularios largos, porque el catálogo viene sincronizado desde el POS y el usuario no escribe datos del producto.
- [X] **Retroalimentación al usuario.** Cada acción responde con voz, vibración y texto: producto leído, ítem agregado, total actualizado y pago confirmado. El estado de conexión con el POS ("Conectado", "Sincronizando", "Sin conexión") se anuncia en texto y sonido, no solo con color.
- [X] **Jerarquía visual clara.** El título y la acción principal ocupan el mayor tamaño y contraste. Los datos secundarios usan un tono más suave que sigue cumpliendo AAA. El espaciado y la alineación a la izquierda siguen un solo eje de lectura.

**Justificación (¿por qué creemos que se cumple?):** el prototipo es coherente con su propósito. Cada elemento responde a una necesidad concreta de usuarios con discapacidad visual, y la conexión al POS garantiza que lo que la app lee sea lo que la caja cobra.

## 6. Ajustes inmediatos a considerar

**Lista de ajustes prioritarios:**

1. **Aplicar la paleta AAA en todas las pantallas** y validar cada combinación de texto, fondo y borde con un medidor de contraste.
2. **Definir una única acción primaria por pantalla** y asegurar el foco visible de 3 px en todos los elementos interactivos.
3. **Agregar etiqueta de texto a todo ícono** y definir las etiquetas accesibles de cada elemento para lector de pantalla.
4. **Representar los estados de conexión con el POS** (conectado, sincronizando, sin conexión, error de pago) con texto y sonido, no solo con color.
5. **Mostrar la confirmación del monto antes del pago** como pantalla propia, con el total en tamaño máximo y botones "Confirmar pago" y "Volver al carrito" claramente diferenciados.

## 7. Recursos necesarios

- [X] **Iconos o imágenes:** un set abierto de trazo grueso (Material Symbols o Phosphor) con texto alternativo para cada imagen.
- [X] **Ayuda técnica:**
  - Pruebas con TalkBack, VoiceOver y NVDA.
  - Documentación o sandbox de la API del POS para validar la sincronización de catálogo, precios y pago.
- [X] **Nuevas ideas de diseño:** modo claro y oscuro, tamaño de texto configurable y comandos de voz.
- [X] **Otra herramienta de prototipado:** Figma no permite probar con lector de pantalla. Para el enlace público conviene una versión en HTML publicada, evaluable con lector de pantalla.
- [X] **Otra cosa:** WebAIM Contrast Checker, axe DevTools y Lighthouse para auditoría de accesibilidad. Idealmente, validación con al menos un usuario con discapacidad visual.

**Notas:** el enlace público debe apuntar siempre a la última versión del prototipo.

## 8. Reflexión final del equipo

Diseñar para discapacidad visual exige que la accesibilidad sea el criterio estructural del diseño y no un ajuste final: cada decisión de color, tamaño y navegación debe poder verificarse con un estándar medible como WCAG. También aprendimos que la conexión con el POS es lo que vuelve útil la interfaz, porque asegura que la información que escucha el usuario coincida con lo que se cobra.

## Verificación contra la pauta de evaluación (nivel alto, 3)

| Criterio | Dónde se cumple | Qué debe verse en el wireframe |
|---|---|---|
| 1. Claridad funcional | Flujo de 9 pasos y retroalimentación (secciones 3 y 5) | Cada pantalla indica qué hacer y qué ocurrió |
| 2. Usabilidad general | Una acción primaria por pantalla, menú de 4 opciones | Sin pasos innecesarios entre escanear y pagar |
| 3. Accesibilidad | Contraste AAA, 44 px, etiquetas, texto al 200 % | Paleta aplicada y etiquetas definidas |
| 4. Jerarquía visual | Tamaños, contraste y alineación (secciones 4 y 5) | Acción principal siempre dominante |
| 5. Consistencia del diseño | Misma barra, botones y tipografía | Ningún elemento cambia de estilo sin motivo |
| 6. Estética funcional | Color con propósito, sin decoración | Sin elementos puramente ornamentales |
| 7. Pertinencia con el propósito | Toda función ligada a catálogo, precio, lectura o pago del POS | Ninguna pantalla sin relación con la compra autónoma |

---

# Entregable 2: Contenido para la presentación

## 1. Paleta de colores accesible

Razones de contraste calculadas con la fórmula de WCAG. AAA exige 7:1 para texto normal y 4,5:1 para texto grande.

### Modo oscuro (principal)

| Rol | HEX | Contraste | Nivel |
|---|---|---|---|
| Fondo | `#0A1A2F` | Base | n/a |
| Superficie (tarjetas) | `#14294A` | 1,20:1 contra fondo; requiere borde | n/a |
| Texto principal | `#F5F7FA` | 16,28:1 sobre fondo; 13,53:1 sobre superficie | AAA |
| Texto secundario | `#C8D3E3` | 11,55:1 sobre fondo; 9,60:1 sobre superficie | AAA |
| Acento primario (botones, foco) | `#FFD60A` | 12,38:1 sobre fondo; 10,29:1 sobre superficie | AAA |
| Texto sobre acento primario | `#0A1A2F` | 12,38:1 sobre `#FFD60A` | AAA |
| Acento secundario (enlaces, información) | `#6FD3FF` | 10,35:1 sobre fondo; 8,60:1 sobre superficie | AAA |
| Error | `#FF9E9E` | 8,85:1 sobre fondo; 7,36:1 sobre superficie | AAA |
| Éxito | `#7DF0A6` | 12,39:1 sobre fondo; 10,30:1 sobre superficie | AAA |
| Bordes y contornos | `#5A7BA6` | 4,01:1 sobre fondo; 3,33:1 sobre superficie | Cumple 3:1 (WCAG 1.4.11) |

### Modo claro (alternativo)

| Rol | HEX | Contraste | Nivel |
|---|---|---|---|
| Fondo | `#FFFFFF` | Base | n/a |
| Superficie | `#EEF3F9` | n/a | n/a |
| Texto principal | `#0A1A2F` | 17,48:1 sobre fondo; 15,66:1 sobre superficie | AAA |
| Acento (botones, enlaces) | `#0B3D91` | 10,04:1 sobre fondo; texto blanco sobre el botón también 10,04:1 | AAA |
| Error | `#A4001F` | 8,08:1 sobre fondo | AAA |
| Éxito | `#005A32` | 8,37:1 sobre fondo | AAA |

### Justificación

- **Navy y amarillo:** el fondo azul muy oscuro con texto casi blanco evita el deslumbramiento del blanco y negro puros, que perjudica a usuarios con astigmatismo y sensibilidad a la luz. El amarillo sobre azul oscuro mantiene un contraste superior a 12:1 y es distinguible con las formas más comunes de daltonismo.
- **Superficie con borde:** el fondo y la superficie no se distinguen entre sí (1,20:1). Por eso toda tarjeta lleva borde `#5A7BA6`, que supera los 3:1 exigidos para componentes de interfaz.
- **Color nunca como único canal (WCAG 1.4.1):** error y éxito van siempre acompañados de ícono con texto y sonido.
- **Foco visible:** anillo de 3 px en `#FFD60A` sobre cualquier elemento interactivo.
- **Dos modos:** hay usuarios con baja visión que ven mejor con fondo claro y otros con fondo oscuro, por lo que el usuario debe poder elegir.

## 2. Contenido estructurado (1 diapositiva)

**Título:** [Nombre del proyecto]: compras autónomas para personas con discapacidad visual

**Problema:**
Una persona ciega o con baja visión no puede leer precios, etiquetas ni pantallas de pago sin ayuda de un tercero.

**Propuesta:**
Sistema de compras asistido que identifica productos, lee su precio y guía el pago por voz y con alto contraste.

**Valor de la conexión al POS:**

- **Catálogo y precios sincronizados:** lo que la app lee es exactamente lo que cobra la caja.
- **Lectura de producto por código de barras** contra el catálogo del comercio, con precio y stock.
- **Pago accesible:** el monto se confirma por voz antes de cobrar. Los datos de tarjeta se procesan solo en el POS.
- **Un sistema global**, conectable a múltiples comercios.

**Público y enfoque en la diversidad:**

- **Ceguera total:** lector de pantalla, voz y vibración.
- **Baja visión:** contraste AAA, texto ampliable al 200 % y modo claro u oscuro.

**Elementos visuales a incluir:**

1. **Esquema de arquitectura en 3 nodos con flechas bidireccionales:** [App del usuario] ↔ [Sistema global (API)] ↔ [POS del comercio]. Etiquetas sobre las flechas: "consulta de producto", "catálogo, precios y stock", "pago". Usar la paleta oscura y trazo grueso.
2. **Dos capturas del wireframe** con la paleta aplicada: pantalla "Escanear producto" y pantalla "Confirmar pago".
3. **Flujo resumido en 5 íconos con texto:** Escanear, Escuchar, Agregar, Revisar, Pagar.
4. **Muestra de la paleta:** 4 cuadros de color con su código HEX.
5. **Texto alternativo** en cada imagen o esquema, para que la diapositiva también sea accesible.

**Tipografía de la diapositiva:** Atkinson Hyperlegible, cuerpo mínimo de 24 pt y títulos de 40 pt.

**Enlace al prototipo:**

`[PEGAR AQUÍ EL ENLACE PÚBLICO DEL PROTOTIPO]`

Incluir un código QR del mismo enlace. Verificar antes de cada entrega que apunte a la última versión.
