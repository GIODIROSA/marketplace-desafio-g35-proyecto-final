# Marketplace

## Listado de Entidades:

### productos (ED)

    producto_id (PK)
    producto_nombre
    producto_imagen
    producto_descripcion
    producto_precio_unitario
    producto_autores
    producto_stock
    categoria_id (FK)


### usuarios (ED)

    usuario_id (PK)
    usuario_nombre
    usuario_apellido
    usuario_direccion
    usuario_email
    rol_id (FK)
    usuario_contrasenna

### roles (EC)

    rol_id (PK)
    rol_nombre


### categorias (EC)

    categoria_id (PK)
    categoria_nombre

### carrito_compras (ED) - (ET)

    carrito_compra_id (PK)
    fecha_creacion
    usuario_id (FK)


### detalle_carrito (EP)

    detalle_carrito_id (PK)
    carrito_compra_id (FK)
    producto_id (FK)
    detalle_carrito_cantidad

### pedido (ED)

    pedido_id (PK)
    pedido_fecha
    usuario_id (FK)
    estado_id (FK)

### detalle_pedido (EP)

    detalle_pedido_id (PK)
    pedido_id (FK)
    producto_id (FK)
    producto_precio_unitario (FK)
    detalle_cantidad

### estado_pedido (EC)

    estado_id (PK)
    estado_descripcion

## Relaciones

1. Un _usuario_ puede tener varios _productos_ (1 a m)
2. Un _carrito compras_ pertenece a un _usuario_ (m a 1)
3. Un _carrito compras_ puede tener muchos _productos_ (m a m a través de la entidad "detalle_carrito")
4. Un _producto_ puede pertenecer a varias categorías (m a m)
5. Un _detalle carrito_ pertenece a un _carrito compras_ y a un producto (1 a 1 a m)
6. Un _pedido_ pertenece a un usuario (m a 1)
7. Un _pedido_ puede contener varios productos (m a m a través de la entidad "detalle_pedido")
8. Un _usuario_ puede tener varios roles (1 a m)
9. Un _rol_ puede estar relacionado a varios usuarios (m a m)
10. Un _pedido_ puede tener un estado (1 a 1)
11. un _estado pedido_ puede estar relacionado a varios pedido (1 a m)

## Reglas de negocios

### usuarios

1. Un usuario debe tener un correo electrónico único en el sistema
2. La contraseña de un usuario debe estar protegida y almacenarse de manera segura
3. Los usuarios pueden tener uno o varios roles
4. Un usuario debe proporcionar una dirección válida
5. Un usuario puede registrarse en el sistema

### rol

1. Los roles deben tener nombres únicos y descriptivos ("Administrador", "Cliente")
2. Los roles pueden estar relacionados con varios usuarios, y un usuario puede tener varios roles.

### productos

1. Crear el registro del producto
2. Leer el registro de un o varios productos dada la condición en particular
3. Leer todos los registros de la entidad productos
4. Actualizar los datos de un producto dada una condición particular
5. Eliminar los datos de un producto dada una condición particular
6. Cada producto debe tener un nombre unico en el sistema
7. El precio de un producto debe ser un valor válido y no negativo
8. La cantidad de stock de un producto no puede ser negativa

### pedido

1. Un pedido debe estar asoaciado a un usuario
2. Cada pedido debe tener un estado específico, como "pendiente", "en proceso" o "entregado"
3. La fecha de un pedido debe registrarse correctamente
4. La cantidad de productos en un pedido no puede ser negativa
5. El precio total de un pedido debe calcularse correctamente en función de los productos y cantidades incluidas

### estado pedido

1. Los estados de pedido deben ser descriptivos y únicos en el sistema.
2. Cada pedido debe tener un estado específico (1:1)
3. Un estado de pedido puede estar relacionado con varios pedidos (1:n)

### carrito de compras

1. Un carrito de compras puede estar asociado a un usuario
2. Los productos en el carrito deben registrarse correctamente, incluyendo su cantidad y estado
3. Los productos en el carrito no deben tener cantidades negativas
4. Los productos en el carrito deben estar relacionados con los productos disponibles en el sistema
