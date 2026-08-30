# Guía de Instalación - Google Customer Reviews

## 📋 Tabla de Contenidos

1. [Requisitos Previos](#requisitos-previos)
2. [Paso 1: Obtener Merchant ID](#paso-1-obtener-merchant-id)
3. [Paso 2: Elegir Método de Instalación](#paso-2-elegir-método-de-instalación)
4. [Paso 3: Instalar Sección Personalizada](#paso-3-instalar-sección-personalizada-recomendado)
5. [Paso 4: Verificar Funcionamiento](#paso-4-verificar-funcionamiento)

---

## Requisitos Previos

✅ Tienda Shopify Plus o estándar
✅ Acceso a Theme Editor
✅ Google Merchant Center account
✅ Dominio verificado en Google Search Console
✅ HTTPS habilitado en tu tienda

---

## Paso 1: Obtener Merchant ID

### Si ya tienes Google Customer Reviews configurado:

1. Dirígete a [Google Merchant Center](https://merchantcenter.google.com)
2. Ve a **Growth** → **Reviews** → **Google Customer Reviews**
3. Busca tu **Merchant ID** (ej: 5838265930)

### Si es tu primera vez:

1. Accede a Google Merchant Center
2. Configura tu tienda
3. Verifica tu sitio
4. Activa Google Customer Reviews
5. Copia tu Merchant ID

---

## Paso 2: Elegir Método de Instalación

### Método A: Sección Personalizada (Recomendado ⭐)

**Ventajas:**
- Fácil de configurar
- Reutilizable en múltiples páginas
- Sin tocar código
- Actualizaciones simples

**Desventajas:**
- Requiere agregar a la página de confirmación manualmente

### Método B: order.liquid (Integración Directa)

**Ventajas:**
- Se aplica automáticamente a todas las órdenes
- Menos pasos

**Desventajas:**
- Requiere acceso a archivos de tema
- Más técnico

---

## Paso 3: Instalar Sección Personalizada (Recomendado)

### 3.1 Descarga la Sección

Copia el contenido de `sections/google-customer-reviews.liquid`

### 3.2 Sube a tu Tema

1. Accede a tu admin de Shopify
2. Ve a **Tienda Online > Temas**
3. Haz clic en tu tema activo
4. Haz clic en **...** (tres puntos)
5. Selecciona **Editar código**
6. Ve a **Secciones** (lado izquierdo)
7. Haz clic en **Agregar un archivo nuevo**
8. Nombra el archivo: `google-customer-reviews.liquid`
9. Pega el código completo
10. Haz clic en **Guardar**

### 3.3 Configura en tu Página de Orden

1. Ve a **Tienda Online > Temas > Personalizar**
2. Selecciona tu tema
3. Haz clic en **Página de confirmación de pedido**
4. Haz clic en **Agregar sección**
5. Busca y selecciona **Google Customer Reviews**
6. Ingresa tu **Merchant ID**
7. Haz clic en **Guardar**

---

## Paso 4: Verificar Funcionamiento

### 4.1 Prueba en Desarrollo

1. Coloca una orden de prueba en tu tienda
2. Completa el pago
3. Deberías ver un widget de encuesta en la página de confirmación

### 4.2 Verifica en Consola

1. Abre DevTools (F12)
2. Ve a la pestaña **Console**
3. Busca mensajes como:
   - ✅ `GCR initialized successfully`
   - ✅ `Survey rendered`

4. Si hay errores, anota el mensaje

### 4.3 Valida en Google Merchant Center

1. Ve a Google Merchant Center
2. **Growth** → **Reviews** → **Google Customer Reviews**
3. Busca **Opt-in metrics** o **Active surveys**
4. Deberías ver tráfico registrado

---

## Alternativa: Instalación Manual en order.liquid

Si prefieres la integración directa:

### 1. Accede a tu archivo order.liquid

1. Admin Shopify → **Tienda Online > Temas**
2. Haz clic en **...** → **Editar código**
3. Ve a **Plantillas** → **order.liquid**

### 2. Pega el código

Copia todo el contenido de `templates/order.liquid` del repositorio y reemplaza el archivo actual.

### 3. Actualiza Merchant ID

Busca esta línea:
```liquid
"merchant_id": 5838265930,
```

Y reemplaza `5838265930` con **tu Merchant ID**.

### 4. Guarda

Haz clic en **Guardar**.

---

## 🔍 Troubleshooting

### El widget no aparece

**Solución:**
- ✅ Verifica que tu Merchant ID sea correcto
- ✅ Asegúrate de estar en HTTPS
- ✅ Abre DevTools y revisa la consola para errores
- ✅ Espera 24-48 horas para que Google indexe

### El email/país está vacío

**Solución:**
- ✅ Asegúrate de que el cliente completó su información de envío
- ✅ Verifica que el país tenga código ISO válido

### Los productos no aparecen

**Solución:**
- ✅ Verifica que los productos tengan código de barras (GTIN)
- ✅ El GTIN debe ser único y válido

---

## 📞 Soporte Adicional

- [Google Customer Reviews Help](https://support.google.com/merchants/answer/7050000)
- [Shopify Themes Documentation](https://shopify.dev/themes)
- [Shopify Liquid Reference](https://shopify.dev/api/liquid)