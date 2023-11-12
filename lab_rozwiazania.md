# Tytuł
## Poziom 2
### Poziom 3
#### Poziom 4

Lista zadań do wykonania 
* todo 1
* todo 2
  * todo 2.1

 1. Rozdział 1
 2. Rozdział 2  
    2.1 Rozdzial 2.1

    **Listing 1**  
    _Listing 2_  
    **_Listing 3_**  
    Kod......

    ```sql
    SELECT * FROM osoba;
    ```
LAB_04
```sql
use infs_rzepkad
create table postac (
id_postaci int primary key auto_increment,
nazwa varchar(40),
rodzaj enum("wiking","ptak","kobieta"),
data_ur date,
wiek int unsigned);

show tables;

show create table postac;

insert into postac values (default,"Bjorn","wiking","1861-11-09",147);

insert into postac(nazwa, rodzaj, wiek, data_ur) values ("Dawid","wiking","30","1997-04-17");

select * from
postac;

insert into postac values (default,"Drozd","ptak","1980-04-04",30);
insert into postac values (default, "Tesciowa","kobieta","1968-09-05",88);

select * from
postac;

create table walizka (
id_walizki int primary key auto_increment,
pojemnosc int unsigned,
kolor enum("rozowy","czerwony","teczowy","zolty"),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);

show tables;

show create table walizka;

desc walizka;

alter table walizka alter kolor set default "rozowy";

show create table walizka;

desc walizka;

insert into walizka values(default,5,"rozowy",3);

desc walizka;

desc postac;

select * from walizka;

create table izba(
adres_budynku varchar(40) not null,
nazwa_izby varchar(40) not null,
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
wlasciciel int null,
foreign key(wlasciciel) references postac(id_postaci) on delete cascade);

desc izba;

select * from izba;

alter table izba add kolor_izby enum("czarny","czerwony","niebieski")after metraz;

alter table izba alter kolor_izby set default "czarny";

desc izba;

ALTER TABLE izba DROP COLUMN kolor_izby;

desc izba;

create table przetwory (
id_przetworu primary key int auto_increment,
rok_produkcji date,
id_wykonawcy,
zawartosc VARCHAR(150),
dodatek VARCHAR(100),
id_konsumenta,
foreign key(id_wykonawcy, id_konsumenta) references postac(id_postaci) on delete cascade);

alter table przetwory alter rok_produkcji set deafult "1654";

alter table przetwory alter dodatek set deafult "papryczka_chili";

insert into przetwory values ("bigos_z_papryczka_chili", "1654", "default", "bigos", "papryczka_chili", "default"); 
```
