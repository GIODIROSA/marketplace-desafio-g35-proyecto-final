# Modelado de Datos

### Pasos a seguir

1. Identificar las entidades del sistema
2. Identificar los atributos de las entidades
3. Identificar las llaves primarias y secundarias
4. Asignar una nomenclatura adecuada a las entidades y sus atributos
5. Identificar las entidades pivote del sistema
6. Identificar los catálogos del sistema.
7. Identificar los tipos de relaciones del sistema
8. Crear el Modelo Entidad-Relación del sistema.
9. Crear el Modelo Relacional de la base de datos del sistema
10. Identificar los tipos de datos de los atributos de las entidades del sistema
11. Identificar los atributos que puedan ser únicos en el sistema.
12. Identificar las reglas de negocios (Operaciones CRUD) del sistema.

## Glosario

- PK: _primary key_
- FK: _foreing key_
- UQ: _Unique attribute_
- ED: _Entidad de Datos_
- EP: _Entidad Pivote_
- EC: _Entidad Catálogo_}
- ET: _Entidad Transitoria_

## Teoría

1. productos: Esta tabla almacena información sobre los carteles disponibles en la tienda en línea. Incluye un identificador único, nombre, descripción, precio, y la cantidad en stock. La relación principal aquí es con la tabla "detalle_carrito" a través de "poster_id."


2. usuarios: Esta tabla almacena información sobre los usuarios de la tienda en línea. Incluye un identificador único, nombre, apellido, dirección, correo electrónico y contraseña. La tabla de relación "usuarios_roles" establece los roles de los usuarios.

3. roles: Almacena los roles disponibles en el sistema, como "usuario" o "administrador." La tabla de relación "usuarios_roles" conecta los roles a los usuarios.

4. usuarios_roles: Esta tabla crea una relación de muchos a muchos entre usuarios y roles. Un usuario puede tener varios roles.

5. categorias: Almacena las categorías de productos. Aunque no tiene relaciones directas con otras tablas en este modelo, podría usarse para organizar productos en categorías en futuras expansiones.

6. carrito_compras: Registra los carritos de compras de los usuarios, con un identificador único, el usuario que lo posee y la fecha de creación. La relación principal es con "detalle_carrito" a través de "carrito_compra_id."

7. detalle_carrito: Registra los detalles de los productos en el carrito de compras, incluyendo la cantidad. La relación principal es con "productos" a través de "poster_id."

8. pedido: Almacena información sobre los pedidos realizados por los usuarios. Incluye un identificador único, el usuario que hizo el pedido, la fecha y el estado del pedido. La relación principal es con "detalle_pedido" a través de "pedido_id."

9. detalle_pedido: Registra los detalles de los productos en un pedido, incluyendo la cantidad y el precio unitario. La relación principal es con "productos" a través de "poster_id."

10. estado_pedido: Almacena los diferentes estados que un pedido puede tener, como "pendiente" o "entregado."