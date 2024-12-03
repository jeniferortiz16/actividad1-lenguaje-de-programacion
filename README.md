# actividad1-lenguaje-de-programacion
create database UNIempresa

create table empleados(
numero_empleado int primary key identity(1,1) not null,
nombre varchar(30) not null,
apellido_paterno varchar(30) not null,
apellido_materno varchar(30) not null,
fecha_nacimiento date not null,
RFC AS (upper(substring(nombre,1,2) + substring(apellido_paterno,1,2) + substring(apellido_materno,1,1) + format(fecha_nacimiento, 'yyMMdd'))),
centro_trabajo varchar(30) not null,
puesto varchar(30) not null,
descripcion_puesto varchar(30) not null,
directivo bit not null
);
insert into empleados (nombre, apellido_paterno, apellido_materno, fecha_nacimiento, centro_trabajo, puesto, descripcion_puesto, Directivo)
values
('Rodolfo', 'Castillo', 'Morales', '1988-02-21', 'La Primavera Ropa', 'Gerente Ropa', 'Gestiona la administracion', 1),
('Ana', 'Luz', 'Martinez', '1985-12-23', 'Tiendas Angel Flores Cajas', 'Cajero', 'Recibe pagos de clientes', 0),
('Susana', 'Arias', 'Coria', '1981-05-01', 'Tiendas Angel Flores Muebles', 'Vendedor', 'Vende articulos a clientes', 0),
('Antonio', 'Ortiz', 'Garcia', '1979-09-15', 'La Primavera Muebles', 'Gerente Suplente', 'Gestiona la administracion', 1),
('Victor', 'Avila', 'Olivo', '1990-10-08', 'Tiendas Angel Flores Ropa', 'Inventarista', 'Controla el inventario', 0),
('Marcela', 'Velazquez', 'Ruiz', '1992-01-30', 'La Primavera Cajas', 'Director Financiero', 'Dirige actividades financieras', 1);

create table directivo(
numero_empleado int primary key identity(1,1),
nombre varchar(30) not null,
apellido_paterno varchar(30) not null,
apellido_materno varchar(30) not null,
fecha_nacimiento date not null,
RFC AS (upper(substring(nombre,1,2) + substring(apellido_paterno,1,2) +
substring(apellido_materno,1,1) +
format(fecha_nacimiento, 'yyMMdd'))),
centro_supervisa int not null,
prestacion_combustible bit not null
);
insert into directivo (nombre, apellido_paterno, apellido_materno, fecha_nacimiento, centro_supervisa, prestacion_combustible)
values
('Rodolfo', 'Castillo', 'Morales', '1988-02-21', '49001', 1),
('Antonio', 'Ortiz', 'Garcia', '1979-09-15', '49002', 0),
('Marcela', 'Velazquez', 'Ruiz', '1992-01-30', '49003', 1),
('Juan', 'Torres', 'Vieyra', '1981-06-06', '202', 0),
('Lorena', 'Cortes', 'Vega', '1995-08-31', '201', 1);

create table centro(
numero_centro int primary key,
nombre_centro varchar(30) not null,
ciudad varchar(30) not null
);
insert into centro (numero_centro, nombre_centro, ciudad)
values
('000201', 'Tiendas Angel Flores Ropa', 'Culiacan'), 
('000202', 'Tiendas Angel Flores Muebles', 'Culiacan'),
('000203', 'Tiendas Angel Flores Cajas', 'Culiacan'),
('049001', 'La Primavera Ropa', 'Culiacan'),
('049002', 'La Primavera Muebles', 'Culiacan'),
('049003', 'La Primaver Cajas', 'Culiacan');
