# proy-bases
Poyecto Final de Bases de Datos



CREATE DATABASE proy_final
    WITH
    OWNER = postgres
    ENCODING = 'UTF8'
    LC_COLLATE = 'Spanish_Colombia.1252'
    LC_CTYPE = 'Spanish_Colombia.1252'
    LOCALE_PROVIDER = 'libc'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
	
CREATE TABLE cliente (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100),
    apellido VARCHAR(100),
    correo_electronico VARCHAR(100) UNIQUE,
    contrasena VARCHAR(100),
    direccion_envio VARCHAR(200),
    telefono VARCHAR(20),
    genero VARCHAR(10),
    fecha_nacimiento DATE,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    metodo_pago_preferido VARCHAR(50),
    estado_cliente VARCHAR(20),
    historial_compras JSONB,
    nivel_afiliacion VARCHAR(50));
	
CREATE TABLE productos (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100),
    descripcion TEXT,
    precio NUMERIC(10, 2),
    categoria VARCHAR(50),
    talla VARCHAR(10),
    color VARCHAR(50),
    cantidad_stock INTEGER
);

CREATE TABLE pedidos (
    id SERIAL PRIMARY KEY,
    id_cliente INTEGER REFERENCES clientes(id),
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    estado VARCHAR(50),
    metodo_pago VARCHAR(50),
    total NUMERIC(10, 2)
);
