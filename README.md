mysql cheat sheet

Database
show databases;
create database nama_database;
use nama_database;
drop database nama_database;

Tipe Data
Integer
	Tinyint
	Smallint
	Mediumint
	Int
	Bigint
Floating Point
	Float
	Double
DECIMAL(jumlah_digit, digit_belakang_koma)
Char
Varchar
Text
	Tinytext
	Text
	Mediumtext
	Longtext
Enum("data_1", "data_2")
Date YYYY-MM-DD
Datetime YYYY-MM-DD HH:MM:SS
Timestamp YYYY-MM-DD HH:MM:SS
Time HH:MM:SS
Year YYYY
Boolean

Engine
SHOW ENGINES;

Table
SHOW TABLES;
CREATE TABLE nama_table (kolom_1, kolom_2) ENGINE = InnoDB;
DESCRIBE nama_tabel;
DESC nama_tabel;
SHOW CREATE TABLE nama_tabel;
TRUNCATE nama_tabel;
DROP TABLE nama_tabel;
ALTER TABLE nama_tabel ADD COLUMN ... DATATYPE, DROP COLUMN ..., RENAME COLUMN ... TO ..., MODIFY ... DATATYPE AFTER ..., MODIFY ... DATATYPE FIRST;
DROP TABLE nama_tabel;

Default Value
DEFAULT
Tipe Data lain
	Null & Not Null
Tipe Data time
	CURRENT_TIMESTAMP

INSERT INTO nama_table(kolom_1, kolom_2) VALUES ("nilai1a", "nilai2a") ("nilai1b", "nilai2b"), ("nilai1c", "nilai2c");

SELECT * FROM nama_table;

SELECT kolom_1, kolom_2 FROM nama_table;

Primary Key
CREATE TABLE nama_table (kolom_1, kolom_2, PRIMARY KEY (kolom_1)) ENGINE = InnoDB;
ALTER TABLE nama_table ADD PRIMARY KEY (id);

Where
SELECT * FROM nama_table WHERE kolom_syarat = "syarat";

Update
UPDATE nama_table SET nama_kolom = "nilai_baru" WHERE nama_kolom_acuan = "nilai_kolom";
UPDATE nama_table SET nama_kolom = "nilai_baru", nama_kolom_lain = "nilai_baru" WHERE nama_kolom_acuan = "nilai_kolom";

Delete
DELETE FROM nama_table WHERE nama_kolom = "nilai_kolom";

Alias
SELECT nama_kolom as 'nama_alias' from nama_table;
SELECT p.nama_kolom as 'nama_alias' from nama_table as p;

Where juga bisa menggunakan logika if else pemrograman, bisa juga menggunakan () sebagai prioritas

Like
SELECT * FROM nama_table WHERE nama_kolom LIKE '%b%';
SELECT * FROM nama_table WHERE nama_kolom LIKE 'b%';
SELECT * FROM nama_table WHERE nama_kolom LIKE '%b';

Null Operator
SELECT * FROM nama_table WHERE nama_kolom IS NULL;
SELECT * FROM nama_table WHERE nama_kolom IS NOT NULL;

Between
SELECT * FROM nama_table WHERE nama_kolom BETWEEN 101010 AND 101010;
SELECT * FROM nama_table WHERE nama_kolom NOT BETWEEN 101010 AND 101010;


In
SELECT * FROM nama_table WHERE nama_kolom IN ('nilai1', 'nilai2');

Order by
SELECT * FROM nama_table ORDER BY nama_kolom ASC, kolom_lain DESC;

