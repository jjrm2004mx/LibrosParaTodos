#  Requerimiento de Desarrollo de Software  
## Proyecto: *Libro para Todos*  
### Versión 1.0

---

## 1. Visión del Proyecto

### 1.1 Enunciado de Visión
“**Libro para Todos** es una aplicación móvil que permite a cualquier persona aficionada a la lectura encontrar, comprar, rentar o solicitar en préstamo libros de distintas categorías (ciencias, finanzas, política, etc.), ofreciendo opciones accesibles para todos los presupuestos y superando las limitaciones de los servicios centrados únicamente en la venta de libros.”

---

### 1.2 Público Objetivo
- Lectores con gusto por la lectura en general.
- Personas que requieren libros de categorías específicas.
- Usuarios que buscan alternativas económicas: compra, renta o préstamo.
- Usuarios que desean comparar disponibilidad, precios y formatos.

---

### 1.3 Necesidades a Cubrir
- Acceso a un catálogo amplio y organizado.
- Búsqueda rápida y precisa por diversos criterios.
- Opciones flexibles de adquisición.
- Disponibilidad inmediata o logística eficiente para contenido físico.
- Información detallada del libro con reseñas y valoraciones.

---

### 1.4 Solución Propuesta

#### Funciones Principales
-  **Búsqueda inteligente** con autocompletado.
-  **Filtros avanzados** por categoría, precios, estrellas, formato.
-  **Catálogo visual** con tarjetas de resultados (portada, autor, costo, calificación).
-  **Detalle de libro**: sinopsis, fichas técnicas, reseñas.
-  **Gestión de usuario**: perfil, historial, preferencias, pagos.
-  **Préstamos y rentas P2P entre usuarios**.
-  **Integración con casas editoriales y librerías**.
-  Aplicación optimizada para smartphone (iOS y Android)

---

### 1.5 Propuesta de Valor y Diferenciadores

| Característica | Competidores | Libro para Todos |
|---------------|--------------|-----------------|
| Venta de libros | ✔ | ✔ |
| Renta de libros | Limitado | ✔ |
| Préstamo entre usuarios | ❌ | ✔ |
| Inclusión económica | Limitado | ✔ |
| Comunidad de lectores | Bajo | ✔ |

La plataforma con opciones accesibles a cualquier presupuesto.

---

### 1.6 Objetivo General del Sistema
Desarrollar una aplicación móvil que integre en un solo espacio la **búsqueda, comparación, selección y acceso** a libros en diversas modalidades, impulsando el hábito lector mediante una experiencia económica y socialmente inclusiva.

---

## 1.7 Políticas de Cancelación

### Compra
- Cancelación válida si no se ha descargado contenido digital o enviado libro físico.
- Reembolso al mismo método de pago.

### Renta
- Cancelación antes del inicio del periodo de renta.
- Reembolso parcial según uso.

### Préstamo P2P
- Cancelación hasta antes de la aceptación del propietario.
- Posterior a ello, rigen reglas de devolución y cumplimiento.

### Consideraciones Generales
- Seguimiento del estado de la cancelación.
- Mostrar términos antes de confirmar cualquier operación.

---

## 1.8 Flujo de Préstamo entre Usuarios (P2P)

### Roles
- **Solicitante**
- **Propietario**
- **Sistema**

### Requisitos para ofrecer libros en préstamo/renta
- Cuenta verificada.
- Alta de libros con condiciones claras.
- Aceptación del contrato digital P2P.

### Flujo Simplificado
1. Propietario registra libro disponible.
2. Solicitante envía solicitud.
3. Propietario acepta/rechaza.
4. Sistema genera contrato digital.
5. Entrega digital/física.
6. Notificaciones y seguimiento.
7. Finalización y evaluación mutua.

---

## 1.9 Flujo de Compra y Métodos de Pago

| Método de Pago | Aplicación | Restricciones / Notas |
|----------------|------------|----------------------|
| Tarjeta crédito/débito | Digital y físico | Validación bancaria |
| Meses Sin Intereses (MSI) | Compra según monto mínimo | No aplica a rentas o préstamos |
| Pago en efectivo | Oxxo Pay / Depósito | Entrega posterior a confirmación del pago |

### Seguridad
- PCI-DSS, tokenización, autenticación 3DS.
- Auditoría y antifraude.

---

## 1.10 Integración con Casas Editoriales

### Objetivo
Ampliar catálogo mediante aliados comerciales formales.

### Requisitos
- Registro empresarial validado.
- Publicación de catálogo con metadatos completos.
- Aceptación de términos comerciales y de licenciamiento.

### Beneficios
- Mayor oferta y actualidad del catálogo.
- Ingresos por comisiones comerciales.
- Panel de ventas y analítica para editoriales.
- DRM opcional para proteger contenido digital.

---


