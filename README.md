# Documentación de la API Rutanio

## Introducción
Esta documentación describe los endpoints disponibles en la API de Rutanio, incluyendo los parámetros requeridos y ejemplos de peticiones.

## Autenticación
Todas las peticiones requieren autenticación mediante token JWT. El token debe incluirse en el header `Authorization`:

```
Authorization: Bearer <tu_token_jwt>
```

## Endpoints

### 1. Obtener Token de Autenticación
**Método:** `POST`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/jwt-auth/v1/token`

**Parámetros:**
- `username` (string): Nombre de usuario
- `password` (string): Contraseña

**Ejemplo de petición:**
```json
{
  "username": "tucorreo@dominio.com",
  "password": "tu_contraseña"
}
```

**Respuesta exitosa:**
```json
{
    "token": "eyJ0eXAiOiJKV1QiLCJ....",
    "user_email": "jsagudeloaa@gmail.com",
    "user_nicename": "jsagudeloaagmail-com",
    "user_display_name": "SEBAS AGUDELO",
    "roles": [
        "administrator",
        "tutor_instructor"
    ],
    "store_name": "SEBAS AGUDELO",
    "store_id": 1
}
```

### 2. Listar Servicios
**Método:** `GET`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/wc/v3/products`

**Parámetros opcionales:**
- `Authorization` (string): Token de autenticación

**Ejemplo de respuesta:**
```json
[
  {
    "id": 2390,
    "name": "Curso Introducción A Blockchain",
    "slug": "curso-introduccion-a-blockchain-2",
    "permalink": "https://marketplace.rutanio.com/product/curso-introduccion-a-blockchain-2/",
    "date_created": "2024-02-15T12:44:26",
    "date_created_gmt": "2024-02-15T17:44:26",
    "date_modified": "2024-02-15T12:45:12",
    "date_modified_gmt": "2024-02-15T17:45:12",
    "type": "simple",
    "status": "publish",
    "featured": false,
    "catalog_visibility": "visible",
    "description": "<p>Curso en tecnología Blockchain, donde aprenderá acerca de Blockchain, Protocolos de Consenso, Contratos Inteligentes, Criptoactivos y otros casos de uso Blockchain, Tokens, NFT, defi, Metaverso, Web3.</p>\n",
    "short_description": "<p>Curso en Tecnología Blockchain.</p>\n",
    "sku": "",
    "price": "25",
    "regular_price": "25",
    "sale_price": "",
    "date_on_sale_from": null,
    "date_on_sale_from_gmt": null,
    "date_on_sale_to": null,
    "date_on_sale_to_gmt": null,
    "on_sale": false,
    "purchasable": true,
    "total_sales": 0,
    "virtual": false,
    "downloadable": false,
    "downloads": [],
    "download_limit": -1,
    "download_expiry": -1,
    "external_url": "",
    "button_text": "",
    "tax_status": "taxable",
    "tax_class": "",
    "manage_stock": false,
    "stock_quantity": null,
    "backorders": "no",
    "backorders_allowed": false,
    "backordered": false,
    "low_stock_amount": null,
    "sold_individually": false,
    "weight": "",
    "dimensions": {
        "length": "",
        "width": "",
        "height": ""
    },
    "shipping_required": true,
    "shipping_taxable": true,
    "shipping_class": "",
    "shipping_class_id": 0,
    "reviews_allowed": true,
    "average_rating": "0.00",
    "rating_count": 0,
    "upsell_ids": [],
    "cross_sell_ids": [],
    "parent_id": 0,
    "purchase_note": "",
    "categories": [
        {
            "id": 47,
            "name": "Cursos",
            "slug": "cursos"
        },
        {
            "id": 44,
            "name": "Ofrezco",
            "slug": "ofrezco"
        }
    ],
    "tags": [],
    "images": [],
    "attributes": [],
    "default_attributes": [],
    "variations": [],
    "grouped_products": [],
    "menu_order": 0,
    "price_html": "<span class=\"wcpbc-price wcpbc-price-2390\" data-product-id=\"2390\"><span class=\"woocommerce-Price-amount amount\"><bdi><span class=\"woocommerce-Price-currencySymbol\">&#36;</span>&nbsp;25</bdi></span></span>",
    "related_ids": [
        2384,
        2369,
        2361,
        2383
    ],
    "meta_data": [
        {
            "id": 11591,
            "key": "_wcfm_product_author",
            "value": "597"
        },
        {
            "id": 11592,
            "key": "_wcfm_new_product_notified",
            "value": "yes"
        },
        {
            "id": 11593,
            "key": "_catalog",
            "value": "no"
        },
        {
            "id": 11594,
            "key": "disable_add_to_cart",
            "value": "no"
        },
        {
            "id": 11595,
            "key": "disable_price",
            "value": "no"
        },
        {
            "id": 11596,
            "key": "_wcfmmp_processing_time",
            "value": ""
        },
        {
            "id": 11597,
            "key": "_colombia_price",
            "value": "25"
        }
    ]
  }
]
```

### 3. Crear Cuenta de Usuario Final
**Método:** `POST`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/wp/v2/users`

**Parámetros:**
- `username` (string): Nombre de usuario
- `email` (string): Correo electrónico
- `password` (string): Contraseña
- `roles` (array): Roles del usuario
- `first_name` (string): Nombre del usuario
- `last_name` (string): Apellido del usuario

**Ejemplo de petición:**
```json
{
  "username": "nuevovendedor",
  "email": "nuevovendedor@dominio.com",
  "password": "PasswordSuperSegura123!",
  "roles": ["wcfm_vendor"],
  "first_name": "Nuevo",
  "last_name": "Vendedor"
}
```

**Respuesta exitosa:**
```json
{
    "id": 677,
    "username": "nuevovendedor",
    "name": "Nuevo Vendedor",
    "first_name": "Nuevo",
    "last_name": "Vendedor",
    "email": "nuevovendedor@dominio.com",
    "url": "",
    "description": "",
    "link": "https://marketplace.rutanio.com/store/nuevovendedor",
    "locale": "es_ES",
    "nickname": "nuevovendedor",
    "slug": "nuevovendedor",
    "roles": [
        "wcfm_vendor"
    ],
    "registered_date": "2025-04-29T20:41:03+00:00",
    "capabilities": {
        "level_6": true,
        "level_5": true,
        "level_4": true,
        "level_3": true,
        "level_2": true,
        "level_1": true,
        "level_0": true,
        "read": true,
        "edit_post": true,
        "edit_posts": true,
        "edit_others_posts": true,
        "edit_published_posts": true,
        "delete_posts": true,
        "edit_shop_coupons": true,
        "manage_shop_coupons": true,
        "read_shop_coupons": true,
        "publish_shop_coupons": true,
        "edit_published_shop_coupons": true,
        "delete_shop_coupons": true,
        "delete_published_shop_coupons": true,
        "edit_others_pages": true,
        "edit_published_pages": true,
        "upload_files": true,
        "delete_attachments": true,
        "unfiltered_html": true,
        "assign_product_terms": true,
        "manage_product": true,
        "read_product": true,
        "read_shop_coupon": true,
        "edit_product": true,
        "delete_product": true,
        "edit_products": true,
        "delete_products": true,
        "delete_published_products": true,
        "publish_products": true,
        "edit_published_products": true,
        "view_woocommerce_reports": true,
        "export": true,
        "import": true,
        "manage_product_terms": true,
        "manage_woocommerce": true,
        "publish_shop_orders": true,
        "list_users": true,
        "create_users": true,
        "manage_woocommerce_pos": true,
        "access_woocommerce_pos": true,
        "read_private_posts": true,
        "read_private_products": true,
        "read_private_shop_orders": true,
        "publish_foosales": true,
        "manage_products": true,
        "read_products": true,
        "wcfm_vendor": true
    },
    "extra_capabilities": {
        "wcfm_vendor": true
    },
    "avatar_urls": {
        "24": "https://secure.gravatar.com/avatar/700a0b7afe748321aa4ed63bd2ed848d?s=24&d=mm&r=g",
        "48": "https://secure.gravatar.com/avatar/700a0b7afe748321aa4ed63bd2ed848d?s=48&d=mm&r=g",
        "96": "https://secure.gravatar.com/avatar/700a0b7afe748321aa4ed63bd2ed848d?s=96&d=mm&r=g"
    },
    "meta": {
        "persisted_preferences": []
    },
    "is_super_admin": true,
    "woocommerce_meta": {
        "activity_panel_inbox_last_read": "",
        "activity_panel_reviews_last_read": "",
        "categories_report_columns": "",
        "coupons_report_columns": "",
        "customers_report_columns": "",
        "orders_report_columns": "",
        "products_report_columns": "",
        "revenue_report_columns": "",
        "taxes_report_columns": "",
        "variations_report_columns": "",
        "dashboard_sections": "",
        "dashboard_chart_type": "",
        "dashboard_chart_interval": "",
        "dashboard_leaderboard_rows": "",
        "homepage_layout": "",
        "homepage_stats": "",
        "task_list_tracked_started_tasks": "",
        "help_panel_highlight_shown": "",
        "android_app_banner_dismissed": ""
    },
    "_links": {
        "self": [
            {
                "href": "https://marketplace.rutanio.com/wp-json/wp/v2/users/677"
            }
        ],
        "collection": [
            {
                "href": "https://marketplace.rutanio.com/wp-json/wp/v2/users"
            }
        ]
    }
}
```

### 4. Crear Producto/Servicio
**Método:** `POST`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/wc/v3/products`

**Autenticación:**
Debes incluir el token JWT en el header:
```
Authorization: Bearer TU_TOKEN_JWT
```

**Ejemplo de petición (JSON):**
```json
{
  "name": "Terapia con Sueros Vitaminados",
  "type": "simple",
  "regular_price": "150",
  "description": "<p>Sesión de sueroterapia con vitaminas y minerales para mejorar el sistema inmunológico y la energía.</p>",
  "short_description": "Sueroterapia energizante y revitalizante.",
  "categories": [
    {
      "id": 44
    }
  ],
  "manage_stock": false,
  "status": "publish"
}
```

**Respuesta exitosa (201 - Creado):**
```json
{
  "id": 9999,
  "name": "Terapia con Sueros Vitaminados",
  "slug": "terapia-con-sueros-vitaminados",
  "permalink": "https://marketplace.rutanio.com/product/terapia-con-sueros-vitaminados/",
  ...
}
```

**Resumen de Campos Útiles:**
| Campo | Tipo | Requerido | Descripción |
|-------|------|-----------|-------------|
| name | string | ✅ | Nombre del servicio o producto |
| type | string | ✅ | "simple" o "variable" |
| regular_price | string | ✅ | Precio base en string |
| description | HTML | ❌ | Descripción larga en HTML |
| short_description | HTML | ❌ | Descripción corta |
| categories | array | ❌ | IDs de categorías existentes |
| images | array | ❌ | URLs de imágenes |
| status | string | ❌ | "publish", "draft" |
| manage_stock | boolean | ❌ | true o false |

**Ejemplo en curl:**
```bash
curl -X POST https://marketplace.rutanio.com/wp-json/wc/v3/products \
-H "Content-Type: application/json" \
-H "Authorization: Bearer TU_TOKEN_JWT" \
-d '{
  "name": "Consulta Nutricional",
  "type": "simple",
  "regular_price": "50",
  "description": "<p>Consulta personalizada con nutricionista.</p>",
  "short_description": "Consulta nutricional profesional.",
  "categories": [{"id": 44}],
  "images": [{"src": "https://tusitio.com/img/consulta.jpg"}],
  "manage_stock": false,
  "status": "publish"
}'
```

**Nota:** Puedes obtener los IDs de categorías con:
```
GET https://marketplace.rutanio.com/wp-json/wc/v3/products/categories
```

### 5. Buscar Servicios por Título
**Método:** `GET`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/wc/v3/products`

**Parámetros:**
- `search` (string): Término de búsqueda para filtrar productos por título
- `Authorization` (string): Token de autenticación JWT en el header

**Ejemplo de petición:**
```bash
curl -X GET \
  'https://marketplace.rutanio.com/wp-json/wc/v3/products?search=pez' \
  -H 'Authorization: Bearer TU_TOKEN_JWT'
```

**Respuesta exitosa:**
```json
[
  {
    "id": 2413,
    "name": "\"pez\"",
    "slug": "pez",
    "permalink": "https://marketplace.rutanio.com/product/pez/",
    "price": "150",
    "regular_price": "150",
    "description": "<p>\"desc\"</p>\n",
    ...
    // Resto de campos igual que en el endpoint de listar servicios
  }
]
```

**Notas:**
- Este endpoint devuelve un array de productos cuyo título coincide con el término de búsqueda
- La búsqueda no distingue entre mayúsculas y minúsculas
- Se requiere autenticación con token JWT válido

### 6. Consultar Saldo Actual de Puntos
**Método:** `GET`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/saldo`

**Autenticación:**
Se requiere token JWT (header):
```
Authorization: Bearer <tu_token_jwt>
```

**Respuesta exitosa:**
```json
{
  "user_id": 22,
  "email": "atencion.companiax@gmail.com",
  "saldo": 45
}
```

**Campos:**
- `user_id`: ID interno del usuario autenticado.
- `email`: Email del usuario autenticado.
- `saldo`: Saldo actual de puntos en la cuenta myCred.

### 7. Transferir Puntos Entre Usuarios
**Método:** `POST`  
**Ruta:** `https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/transferir`

**Autenticación:**
Se requiere token JWT (header):
```
Authorization: Bearer <tu_token_jwt>
Content-Type: application/json
```

**Parámetros (body JSON):**
- `destino`: Teléfono o email del usuario destino (debe existir).
- `cantidad`: Cantidad de puntos a transferir (entero positivo).

**Ejemplo de petición:**
```json
{
  "destino": "3101001010",      // Puede ser número de teléfono o email registrado
  "cantidad": 5
}
```

**Respuesta exitosa:**
```json
{
  "status": "ok",
  "de": 2,
  "para": 735,
  "cantidad": 5,
  "nuevo_saldo": 20
}
```


## Ejemplos de Uso
```python
import requests

# Obtener token de autenticación
response = requests.post(
    'https://marketplace.rutanio.com/wp-json/jwt-auth/v1/token',
    json={
        'username': 'tucorreo@dominio.com',
        'password': 'tu_contraseña'
    }
)
token = response.json()['token']

# Listar servicios
response = requests.get(
    'https://marketplace.rutanio.com/wp-json/wc/v3/products',
    headers={'Authorization': f'Bearer {token}'}
)

# Crear cuenta de usuario final
response = requests.post(
    'https://marketplace.rutanio.com/wp-json/wp/v2/users',
    json={
        'username': 'nuevovendedor',
        'email': 'nuevovendedor@dominio.com',
        'password': 'PasswordSuperSegura123!',
        'roles': ['wcfm_vendor'],
        'first_name': 'Nuevo',
        'last_name': 'Vendedor'
    }
)

# Crear producto/servicio
response = requests.post(
    'https://marketplace.rutanio.com/wp-json/wc/v3/products',
    headers={'Authorization': f'Bearer {token}'},
    json={
        'name': 'Terapia con Sueros Vitaminados',
        'type': 'simple',
        'regular_price': '150',
        'description': '<p>Sesión de sueroterapia con vitaminas y minerales para mejorar el sistema inmunológico y la energía.</p>',
        'short_description': 'Sueroterapia energizante y revitalizante.',
        'categories': [{'id': 44}],
        'images': [{'src': 'https://tusitio.com/wp-content/uploads/2024/servicio.jpg'}],
        'manage_stock': False,
        'status': 'publish'
    }
)

# Buscar servicios por título
response = requests.get(
    'https://marketplace.rutanio.com/wp-json/wc/v3/products',
    headers={'Authorization': f'Bearer {token}'},
    params={'search': 'pez'}
)

# Consultar saldo de puntos
response = requests.get(
    'https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/saldo',
    headers={'Authorization': f'Bearer {token}'}
)
print(response.json())  # {'user_id': 22, 'email': 'atencion.companiax@gmail.com', 'saldo': 45}

# Transferir puntos a otro usuario
response = requests.post(
    'https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/transferir',
    headers={'Authorization': f'Bearer {token}'},
    json={
        'destino': '3101001010',  # Puede ser teléfono o email del destinatario
        'cantidad': 5
    }
)
print(response.json())  # {'status': 'ok', 'de': 2, 'para': 735, 'cantidad': 5, 'nuevo_saldo': 20}
```

## Flujo Completo de Uso de Puntos
```python
import requests

# 1. Obtener token de autenticación
res = requests.post(
    'https://marketplace.rutanio.com/wp-json/jwt-auth/v1/token',
    json={
        'username': 'atencion.companiax@gmail.com',
        'password': 'OlSU$wzKKzmj&7#o(bh5Xby&'
    }
)
token = res.json()['token']

# 2. Consultar saldo actual de puntos
res = requests.get(
    'https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/saldo',
    headers={'Authorization': f'Bearer {token}'}
)
print(res.json())  # {'user_id': 2, 'email': 'atencion.companiax@gmail.com', 'saldo': 20}

# 3. Transferir puntos a otro usuario por teléfono
res = requests.post(
    'https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/transferir',
    headers={'Authorization': f'Bearer {token}'},
    json={
        'destino': '3101001010',
        'cantidad': 5
    }
)
print(res.json())  # {'status': 'ok', 'de': 2, 'para': 735, 'cantidad': 5, 'nuevo_saldo': 15}

# 4. Verificar nuevo saldo después de la transferencia
res = requests.get(
    'https://marketplace.rutanio.com/wp-json/rutanio/v1/mycred/saldo',
    headers={'Authorization': f'Bearer {token}'}
)
print(res.json())  # {'user_id': 2, 'email': 'atencion.companiax@gmail.com', 'saldo': 15}
```

## Seguridad y Mejores Prácticas para Puntos

### Autenticación
- Todos los endpoints de puntos requieren autenticación mediante token JWT.
- Nunca almacenes tokens JWT en localStorage o cookies sin protección adecuada.
- Los tokens tienen un tiempo de expiración limitado, prepárate para refrescarlos cuando sea necesario.

### Transferencia de Puntos
- Siempre verifica el saldo antes de intentar una transferencia.
- Implementa confirmaciones antes de realizar transferencias para evitar errores.
- Valida que el destinatario exista antes de mostrar opciones de transferencia en la UI.
- Después de cada transferencia, actualiza el saldo mostrado al usuario.

### Manejo de Errores
- Implementa manejo adecuado para todos los códigos de error posibles (400, 401, 404, 500).
- Muestra mensajes de error amigables para el usuario final.
- Registra los errores para diagnóstico y monitoreo.

### Limitaciones
- No se pueden transferir puntos a uno mismo.
- Solo se pueden transferir cantidades enteras positivas.
- El usuario debe tener saldo suficiente para realizar la transferencia.
- El destinatario debe ser un usuario registrado en el sistema (por teléfono o email).

### Registro de Actividad
- Todas las transferencias de puntos quedan registradas en el sistema.
- Los cambios en el saldo se reflejan inmediatamente.
- Los usuarios pueden consultar su saldo en cualquier momento.
