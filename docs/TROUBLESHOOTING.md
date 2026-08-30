# Guía de Troubleshooting - Google Customer Reviews

## 🔍 Problemas Comunes y Soluciones

### ❌ El widget no aparece en la página de confirmación

**Causas posibles:**
1. Merchant ID incorrecto
2. Dominio no verificado en Google Merchant Center
3. No está usando HTTPS
4. Orden no tiene datos completos
5. Google API no cargó

**Soluciones:**

```
✅ Paso 1: Verifica tu Merchant ID
   - Ve a Google Merchant Center
   - Copia exactamente tu Merchant ID
   - Asegúrate que coincida en tu sección

✅ Paso 2: Habilita Modo Depuración
   - En la sección GCR, activa "Modo Depuración"
   - Abre DevTools (F12) → Console
   - Busca mensajes "[GCR]"

✅ Paso 3: Verifica HTTPS
   - Tu tienda DEBE estar en HTTPS
   - Google no carga en HTTP

✅ Paso 4: Valida datos de orden
   - Confirma que el cliente tiene email
   - Verifica que tiene país de envío
   - Revisa que haya al menos un producto
```

---

### ❌ Error: "Merchant ID no configurado"

**Solución:**

1. Ve a **Tienda Online > Temas > Personalizar**
2. Selecciona la sección **Google Customer Reviews**
3. Ingresa tu **Merchant ID** (debe ser un número)
4. Haz clic en **Guardar**

**Ejemplo correcto:**
```
Merchant ID: 5838265930
```

**Ejemplo incorrecto:**
```
Merchant ID: "5838265930"  ❌ No uses comillas
Merchant ID: US-5838265930 ❌ No agregues prefijos
```

---

### ❌ Error: "Email inválido"

**Mensaje en consola:**
```
[GCR Error] Email inválido: cliente@ejemplo
```

**Solución:**

El email del cliente debe estar completo y válido.

**Formatos válidos:**
```
✅ cliente@ejemplo.com
✅ usuario@tienda.co.uk
✅ info@negocio.mx
```

**Formatos inválidos:**
```
❌ cliente@ejemplo      (sin dominio)
❌ cliente.ejemplo.com  (sin @)
❌ @ejemplo.com         (sin usuario)
```

---

### ❌ Error: "Código de país inválido"

**Mensaje en consola:**
```
[GCR Error] Código de país inválido: USA
```

**Solución:**

El código debe ser ISO 2 letras MAYÚSCULAS.

**Códigos válidos:**
```
US = Estados Unidos
MX = México
AR = Argentina
BR = Brasil
ES = España
FR = Francia
GB = Reino Unido
CA = Canadá
```

**Códigos inválidos:**
```
❌ USA    (3 letras)
❌ us     (minúsculas)
❌ E.U.   (formato incorrecto)
```

---

### ❌ Error: "Formato de fecha inválido"

**Mensaje en consola:**
```
[GCR Error] Formato de fecha inválido. Use YYYY-MM-DD
```

**Solución:**

La fecha debe estar en formato ISO 8601: **YYYY-MM-DD**

**Formatos válidos:**
```
✅ 2026-09-05
✅ 2026-12-31
✅ 2027-01-01
```

**Formatos inválidos:**
```
❌ 09/05/2026  (formato DD/MM/YYYY)
❌ 2026/09/05  (slashes en lugar de guiones)
❌ 09-05-2026  (orden incorrecto)
❌ Septiembre 5, 2026 (texto)
```

---

### ❌ Error: "GTIN inválido"

**Mensaje en consola:**
```
[GCR Error] GTIN inválido: ABC123. Debe ser numérico, 8-14 dígitos
```

**Solución:**

El GTIN debe ser:
- Numérico (solo números)
- Entre 8 y 14 dígitos
- Único por producto

**Si no tienes GTIN:**

1. Ve a **Productos**
2. Selecciona el producto
3. Ve a **Código de barras**
4. Ingresa un GTIN válido o dejalo vacío

**Formatos válidos:**
```
✅ 5901234123457  (13 dígitos)
✅ 00012345        (8 dígitos)
✅ N52MNHZLZ (si es alfanumérico, se saltará)
```

**Formatos inválidos:**
```
❌ SKU-12345      (contiene letras)
❌ 123            (muy corto, menos de 8)
❌ 123456789012345 (muy largo, más de 14)
```

---

### ⏳ Los datos tardaron en aparecer

**Comportamiento normal:**

Google tarda 24-48 horas en indexar nuevas órdenes y mostrar métricas en el dashboard.

**Qué hacer:**

1. Espera 24 horas
2. Coloca órdenes de prueba adicionales
3. Verifica en Google Merchant Center después de 48 horas

---

### 🔧 Cómo Habilitar Modo Depuración

**Para ver qué está pasando:**

1. Ve a **Tienda Online > Temas > Personalizar**
2. Abre la sección **Google Customer Reviews**
3. Marca **Modo Depuración**
4. Guarda cambios
5. Abre DevTools (F12) en la página de orden
6. Ve a la pestaña **Console**
7. Verás mensajes como:

```
[GCR] Inicializando Google Customer Reviews
[GCR] Datos de orden extraídos: {
  orderId: "66688480641328",
  email: "cliente@ejemplo.com",
  countryCode: "US",
  deliveryDate: "2026-09-05",
  productsCount: 2
}
[GCR] Renderizando con payload: {...}
[GCR] Survey renderizado exitosamente
```

---

### 📋 Checklist de Verificación

Antes de reportar un problema:

```
□ ¿Tu Merchant ID es correcto?
□ ¿Estás usando HTTPS?
□ ¿La orden tiene cliente con email?
□ ¿La orden tiene país de envío?
□ ¿Los productos tienen GTIN o barcode?
□ ¿Habilitaste el Modo Depuración?
□ ¿Revisaste la consola de DevTools?
□ ¿Esperaste 24 horas desde la primera orden?
□ ¿Tu dominio está verificado en Google Merchant Center?
□ ¿Activaste Google Customer Reviews en tu cuenta?
```

---

### 🆘 Aún hay problemas

**Recopila esta información:**

1. Captura de pantalla de DevTools Console (Modo Depuración activo)
2. Tu Merchant ID (escondiendo dígitos si es necesario)
3. URL de tu tienda
4. Código de país de la orden de prueba
5. El Payload completo del error

**Luego:**

- Contacta a [Google Support](https://support.google.com/merchants)
- O revisa [Shopify Community](https://community.shopify.com)

---

### 📞 Recursos de Ayuda

- [Google Customer Reviews Official Help](https://support.google.com/merchants/answer/7050000)
- [Google Merchant Center Status](https://status.google.com)
- [Shopify Theme Development](https://shopify.dev/themes)
- [Liquid Documentation](https://shopify.dev/api/liquid)