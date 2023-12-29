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

Limit
SELECT * FROM nama_table WHERE nama_kolom <>= kondisi ORDER BY nama_kolom LIMIT 2;
SELECT * FROM nama_tabel LIMIT 10;
SELECT * FROM nama_tabel LIMIT 10, 5;

Distinct
SELECT DISTINCT nama_kolom FROM nama_table;

Aritmatik Operator
% atau MOD
*
+
-
/
SELECT 10 + 10 AS hasil;
SELECT kolom_satu, kolom_dua, DIV 1000 AS 'Price in K' FROM nama_table;

Matematikal Function
ABS()
COS()
PI()
SIN()
TAN()

Auto Increment
digunakan pada kolom pada pembuatan table
lebih sering digunakan pada kolom id
SELECT LAST_INSERT_ID(); // mendapatkan id terakhir

String Function
LOWER()
LENGTH()
UPPER()
CONCAT()
TRIM()

Date Time Function
EXTRACT()
YEAR()
MONTH()
DATE()
DAYNAME()

Flow Control Function
CASE 
SELECT id, CASE nama_kolom WHEN "nilai satu lama" THEN "nilai satu baru" WHEN "nilai dua lama" THEN "nilai dua baru" ELSE "nilai lainnya" END FROM nama_table;

IF()
SELECT id, price, IF(price <= 15000, 'Murah', IF(price <= 20000, 'Mahal', 'Mahal Banget')) AS 'Mahal?' FROM nama_table;

IFNULL(nama_kolom, "nilai baru")


Aggregate Function
COUNT()
SUM()
AVG()
MIN()
MAX()

Grouping
SELECT category, COUNT(id) AS 'Total Product' FROM nama_table GROUP BY category;

Having Clause
HAVING dan WHERE adalah kata kunci yang sama
bedanya HAVING untuk alias

Constraint
UNIQUE KEY
CREATE TABLE nama_table (id INT NOT NULL AUTO_INCREMENT, UNIQUE KEY nama_unik (nama_kolom));
ALTER TABLE nama_table ADD CONSTRAINT nama_unik UNIQUE (nama_kolom);
ALTER TABLE nama_table DROP CONSTRAINT nama_unik;

Check Constraint
CREATE TABLE nama_table (id INT NOT NULL AUTO_INCREMENT, price INT UNSIGNED NOT NULL, CONSTRAINT price_check CHECK(price >= 1000));
ALTER TABLE nama_table ADD CONSTRAINT price_check CHECK(price >= 1000);
ALTER TABLE nama_table DROP CONSTRAINT price_check;
