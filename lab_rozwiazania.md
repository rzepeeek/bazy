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
LAB 4
```sql

show create table nazwa_tabeli;
show tables;
select * from nazwa_tabeli;
desc nazwa_tabeli;

//zad 1

create table postac (
id_postaci int primary key auto_increment,
nazwa varchar(40),
rodzaj enum("wiking","ptak","kobieta"),
data_ur date,
wiek int unsigned);

insert into postac(nazwa, rodzaj, wiek, data_ur) values ("Dawid","wiking","30","1997-04-17");

insert into postac values (default,"Bjorn","wiking","1861-11-09",147);
insert into postac values (default,"Drozd","ptak","1980-04-04",30);
insert into postac values (default, "Tesciowa","kobieta","1968-09-05",88);

//zad 2

create table walizka (
id_walizki int primary key auto_increment,
pojemnosc int unsigned,
kolor enum("rozowy","czerwony","teczowy","zolty"),
id_wlasciciela int,
foreign key(id_wlasciciela) references postac(id_postaci) on delete cascade);

alter table walizka alter kolor set default "rozowy";
insert into walizka values(default,15,default,"Bjorn");
insert into walizka values(default, 20,default,"Tesciowa");

//zad 3

create table izba(
adres_budynku varchar(40) not null,
nazwa_izby varchar(40) not null,
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
wlasciciel int null,
foreign key(wlasciciel) references postac(id_postaci) on delete cascade);

alter table izba add kolor_izby enum("czarny","czerwony","niebieski") after metraz;
alter table izba alter kolor_izby set default "czarny";
insert into izba values ("kontowa 34","spizarnia","250",default);

ALTER TABLE izba DROP COLUMN kolor_izby;

//zad 4

create table przetwory (
id_przetworu primary key int auto_increment,
rok_produkcji date,
id_wykonawcy,
zawartosc VARCHAR(150),
dodatek VARCHAR(100),
id_konsumenta,
foreign key(id_wykonawcy, id_konsumenta) references postac(id_postaci));

alter table przetwory alter rok_produkcji set deafult "1654";
alter table przetwory alter dodatek set deafult "papryczka_chili";
insert into przetwory(id_wykonacy,zawartosc,id_konsumenta) values ("1","bigos_z_papryczkami_chili,"3");
```
```sql
//zad 5

insert into postac (nazwa,rodzaj,data_ur,wiek) values
('Asgard','wiking','1678-08-12','340'),
('Ragnar','wiking','1754-06-11','145'),
('Dziadek mroz','wiking','1821-09-09','140'),
('Babka mroz','wiking','1848-01-01','121'),
('Harnold','wiking','1941-10-11',91');

create table statek
(nazwa_statku VARCHAR(40),
rodzaj_statku enum('wioslowy','zaglowy','o_napedzie_mechanicznym),
data_wodowanie DATE,
max_ladownosc INT unsigned,
primary key(nazwa_statku));

INSERT INTO statek values ("Jager",'o_napedzie_mechanicznym','1919-05-14',default);
INSERT INTO statek values ("galon","zaglowy","2013-04-15",default);

alter table postac add funckje varchar(150);

alter table postac add column statek varchar(50) default null;
alter table postac add foreign key(statek) references statek(nazwa_statku) on delete set null;

update postac set nazwa_statku = 'Grzyb' WHERE id_postaci = 1;

update postac set nazwa_statku = 'kret' WHERE id_postaci = 2;

update postac set nazwa_statku = 'ziemnior' WHERE id_postaci = 3;

update postac set nazwa_statku = 'Grzyb' WHERE id_postaci = 4;

update postac set nazwa_statku = 'Grzyb' WHERE id_postaci = 5;

update postac set nazwa_statku = 'kret' WHERE id_postaci = 6;

update postac set nazwa_statku = 'ziemnior' WHERE id_postaci = 7;

update postac set nazwa_statku = 'kret' WHERE id_postaci = 8;

delete from izba where=(kolor_izby) = "czarny";

drop table izba;

```
