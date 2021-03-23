# Basededatos
create database films;

use films;

create table profile(
  profile_id int not null,
  name varchar(500),
  primary key(profile_id)
);

create table gender(
  gender_id int not null,
  name varchar(500) not null,
  primary key(gender_id)
);

create table movie(
  movie_id int not null auto_increment,
  name varchar(500) not null,
  description longtext,
  image varchar(500) not null,
  create_at datetime not null,
  release_date date,
  actors varchar(500),
  gender_id int not null,
  rating int,
  primary key(movie_id),
  foreign key(gender_id) references gender(gender_id) 
);

create table users(
  users_id int not null auto_increment,
  name varchar(500) not null,
  email varchar(100) not null,
  password varchar(500) not null,
  create_at datetime not null,
  profile_id int not null,
  primary key(user_id),
  foreign key(profile_id) references profile(profile_id),
  UNIQUE (email)
);

insert into gender(gender_id, name) values (1, 'Acción');
insert into gender(gender_id, name) values (2, 'Aventura');
insert into gender(gender_id, name) values (3, 'Comedia');
insert into gender(gender_id, name) values (4, 'Terror');
insert into gender(gender_id, name) values (5, 'Animado');
insert into gender(gender_id, name) values (6, 'Suspenso');

-- profile
insert into profile(profile_id, name) values (1, 'Administrador');
insert into profile(profile_id, name) values (2, 'Cliente');

-- user
insert into users (users_id, name, email, create_at, password, profile_id)
  values (1, 'Alexander Ocampo', 'wilfer.ocampo@est.iudigital.edu.co', now(), '70328265', 1);

insert into users (users_id, name, email, create_at, password, profile_id)
  values (2, 'Adriana Aguilar', 'adriana.a@iudigital.edu.co', now(), '123456', 2);
  
