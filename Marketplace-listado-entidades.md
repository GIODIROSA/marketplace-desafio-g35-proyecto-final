# Marketplace

## Listado de Entidades:

### productos (ED)

    producto_id (PK)
    producto_nombre
    producto_imagen
    producto_descripcion
    producto_precio
    producto_autores
    producto_stock
    producto_categoria
    producto_estado


### usuarios (ED)

    usuario_id (PK)
    usuario_nombre
    usuario_apellido
    usuario_direccion
    usuario_email 
    usuario_contrasenna 
    usuario_rol 

### pedido (ED)

    pedido_id (PK)
    pedido_fecha
    pedido_medio_pago
    pedido_total 
    usuario_id (FK)
    pedido_estado

### detalle_pedido (EP)

    detalle_id (PK)
    detalle_cantidad
    detalle_total 
    pedido_id (FK)
    producto_id (FK)
    producto_precio (FK)

## Relaciones

1. Relación entre Usuarios y Pedidos (m a 1):

Cada usuario puede realizar varios pedidos, pero cada pedido pertenece a un solo usuario. Esto se representa con la clave foránea usuario_id en la tabla de Pedidos que hace referencia al usuario_id en la tabla de Usuarios.

2. Relación entre Pedidos y Detalles de Pedido (1 a m):

Cada pedido puede tener varios detalles de pedido, pero cada detalle de pedido pertenece a un solo pedido. Esto se refleja en la clave foránea producto_id en la tabla de Detalle_Pedido, que hace referencia al pedido_id en la tabla de Pedidos.
Relación entre Productos y Detalles de Pedido (m a m):

Cada producto puede estar presente en varios detalles de pedido, y un detalle de pedido puede contener un solo producto. Esto se implementa a través de la tabla Detalle_Pedido, que tiene una clave foránea (producto_id) que referencia al producto_id en la tabla de Productos.

3. Relación entre Usuarios y Roles (m a m):

Cada usuario puede tener varios roles, y cada rol puede estar asociado a varios usuarios. Esto se logra a través de la tabla de Usuarios que tiene una columna usuario_rol que puede contener el nombre del rol.

## Reglas de negocios

1. Productos en el Carrito de Compras:

Regla de Negocio: Los productos en el carrito de compras deben estar relacionados con los productos disponibles en el sistema. Esto implica que al agregar un producto al carrito, el sistema debe verificar si ese producto existe en la base de datos y está disponible para su compra. Si el producto no existe o no está disponible, no debe permitirse agregarlo al carrito.

2. Usuarios:

Regla de Negocio: Un usuario debe tener un correo electrónico único en el sistema. Garantiza que cada usuario se registre con un correo electrónico único, evitando duplicados en la base de datos.

3. Pedidos:

Regla de Negocio: Cada pedido debe estar asociado a un usuario. Asegura que todos los pedidos estén vinculados a un usuario específico, lo que facilita el seguimiento y la gestión de los pedidos.

4. Detalle de Pedido:

Regla de Negocio: La cantidad de productos en un pedido no puede ser negativa. Evita la inserción de cantidades negativas en un pedido, lo cual no tendría sentido en el contexto de un sistema de pedidos.
