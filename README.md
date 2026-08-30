# Google Customer Reviews - Shopify Integration

Integración completa de Google Customer Reviews para Shopify con manejo de errores, validación de datos y soporte dinámico para múltiples órdenes.

## 📋 Características

- ✅ Integración automática con datos de órdenes
- ✅ Validación de datos en tiempo real
- ✅ Manejo robusto de errores
- ✅ Soporte para múltiples productos por orden
- ✅ Sección personalizada reutilizable
- ✅ Compatible con Shopify Liquid
- ✅ Documentación completa

## 🚀 Inicio Rápido

### Requisitos Previos

- Tienda Shopify activa
- Merchant ID de Google Customer Reviews (ejemplo: 5838265930)
- Acceso a Theme Editor

### Instalación

#### Opción 1: Usar la Sección Personalizada (Recomendado)

1. Ve a tu admin de Shopify
2. Dirígete a **Tienda Online > Temas > Personalizar**
3. Abre **Configuración de la página** (engranaje)
4. Agrega la sección `google-customer-reviews.liquid` a tu tema
5. Configura tu Merchant ID

#### Opción 2: Integración Directa en order.liquid

1. Descarga `order.liquid` de este repositorio
2. Reemplaza el archivo en tu tema
3. Actualiza el `merchant_id` con tu valor

## 📁 Estructura de Archivos

```
google-customer-reviews-shopify/
├── README.md
├── INSTALLATION.md
├── CONTRIBUTING.md
├── sections/
│   └── google-customer-reviews.liquid
├── templates/
│   └── order.liquid (opcional)
├── config/
│   └── settings.json
└── docs/
    └── TROUBLESHOOTING.md
```

## ⚙️ Configuración

### Merchant ID

Tu Merchant ID es único y se obtiene de Google Merchant Center.

**Ejemplo:** `5838265930`

### Datos Dinámicos

La integración captura automáticamente:

- `order.name` - Número de orden
- `order.email` - Email del cliente
- `order.shipping_address.country_code` - Código de país (ej: US, MX, AR)
- `order.fulfillments[0].estimated_delivery_at` - Fecha estimada de entrega
- `order.line_items[].barcode` - GTIN de productos

## 🔧 Validación de Datos

El sistema valida automáticamente:

| Campo | Validación | Ejemplo |
|-------|-----------|----------|
| **order_id** | No vacío | `66688480641328` |
| **email** | Formato válido | `cliente@ejemplo.com` |
| **delivery_country** | Código ISO 2 letras | `US`, `MX`, `AR` |
| **estimated_delivery_date** | Formato YYYY-MM-DD | `2026-09-05` |
| **gtin** | Numérico (8-14 dígitos) | `N52MNHZLZ` |

## 🛡️ Manejo de Errores

El código incluye:

- ✅ Validación de campos requeridos
- ✅ Verificación de tipos de datos
- ✅ Fallback si datos están vacíos
- ✅ Logs de error en consola
- ✅ Reintentos automáticos

## 📝 Ejemplo de Uso

```javascript
// Configuración básica
{
  "merchant_id": 5838265930,
  "order_id": "{{ order.name }}",
  "email": "{{ order.email }}",
  "delivery_country": "{{ order.shipping_address.country_code }}",
  "estimated_delivery_date": "{{ order.fulfillments[0].estimated_delivery_at | date: '%Y-%m-%d' }}",
  "products": [...]
}
```

## 🐛 Troubleshooting

Si tienes problemas:

1. Verifica que tu Merchant ID sea correcto
2. Asegúrate que tu dominio esté verificado en Google Merchant Center
3. Comprueba la consola del navegador para errores
4. Valida que los datos de la orden estén completos

Ver más en [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md)

## 📞 Soporte

- Google Customer Reviews Help: https://support.google.com/merchants/answer/7050000
- Shopify Liquid: https://shopify.dev/api/liquid

## 📄 Licencia

MIT License - Libre para usar y modificar

## 👤 Autor

Integración creada para Nexo Style Store