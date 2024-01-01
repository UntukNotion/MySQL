https://docs.google.com/presentation/d/1v4HllRI-BNj4EdJFLh4_jISq_dcosHoAVo5-LME-ghY/edit?pli=1#slide=id.p

### MySQL Cheat Sheet

## Database
```
SHOW DATABASES;

CREATE DATABASE nama_database;

USE nama_database;

DROP DATABASE nama_database;
```

## Tipe Data
```
Integer
    Tinyint
    Smallint
    Mediumint
    Int
    Bigint

Floating Point
    Float
    Double

DECIMAL(jumlah_digit, digit_belakang_koma) // customize float

Char
Varchar   // lebih direkomendasikan dibanding char
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
```

## Engine
```
SHOW ENGINES;
```

## Table
```
SHOW TABLES;

CREATE TABLE nama_table (
kolom_1,
kolom_2
) ENGINE = InnoDB;         // tanpa menulis engine juga, secara default innodb

DESCRIBE nama_tabel;
DESC nama_tabel;

SHOW CREATE TABLE nama_tabel;

TRUNCATE nama_tabel;

DROP TABLE nama_tabel;

ALTER TABLE nama_tabel
    ADD COLUMN ... DATATYPE,
    DROP COLUMN ...,
    RENAME COLUMN ... TO ...,
    MODIFY ... DATATYPE AFTER ...,
    MODIFY ... DATATYPE FIRST;

DROP TABLE nama_tabel;
```

## Default Value
```
// DEFAULT
Tipe Data lain = Null & Not Null
Tipe Data time = CURRENT_TIMESTAMP

INSERT INTO nama_table(kolom_1, kolom_2) VALUES ("nilai1a", "nilai2a") ("nilai1b", "nilai2b"), ("nilai1c", "nilai2c");

SELECT * FROM nama_table;

SELECT kolom_1, kolom_2 FROM nama_table;
```

## Primary Key
```
CREATE TABLE nama_table (
kolom_1,
kolom_2,
PRIMARY KEY (kolom_1)
) ENGINE = InnoDB;

ALTER TABLE nama_table
ADD PRIMARY KEY (id);
```

## Where
```
SELECT * FROM nama_table WHERE kolom_syarat = "syarat";
```

## Update
```
UPDATE nama_table SET nama_kolom = "nilai_baru" WHERE nama_kolom_acuan = "nilai_kolom";
UPDATE nama_table SET nama_kolom = "nilai_baru", nama_kolom_lain = "nilai_baru" WHERE nama_kolom_acuan = "nilai_kolom";
```

## Delete
```
DELETE FROM nama_table WHERE nama_kolom = "nilai_kolom";
```

## Alias
```
SELECT nama_kolom as 'nama_alias' from nama_table;
SELECT p.nama_kolom as 'nama_alias' from nama_table as p;
```

Where juga bisa menggunakan logika if else pemrograman, bisa juga menggunakan () sebagai prioritas

## Like
```
SELECT * FROM nama_table WHERE nama_kolom LIKE '%b%';
SELECT * FROM nama_table WHERE nama_kolom LIKE 'b%';
SELECT * FROM nama_table WHERE nama_kolom LIKE '%b';
```

## Null Operator
```
SELECT * FROM nama_table WHERE nama_kolom IS NULL;
SELECT * FROM nama_table WHERE nama_kolom IS NOT NULL;
```

## Between
```
SELECT * FROM nama_table WHERE nama_kolom BETWEEN 101010 AND 101010;
SELECT * FROM nama_table WHERE nama_kolom NOT BETWEEN 101010 AND 101010;
```

## In
```
SELECT * FROM nama_table WHERE nama_kolom IN ('nilai1', 'nilai2');
```

## Order by
```
SELECT * FROM nama_table ORDER BY nama_kolom ASC, kolom_lain DESC;
```

## Limit
```
SELECT * FROM nama_table WHERE nama_kolom <>= kondisi ORDER BY nama_kolom LIMIT 2;
SELECT * FROM nama_tabel LIMIT 10;
SELECT * FROM nama_tabel LIMIT 10, 5;
```

## Distinct
```
SELECT DISTINCT nama_kolom FROM nama_table;
```

## Aritmatik Operator
```
% atau MOD
*
+
-
/
SELECT 10 + 10 AS hasil;
SELECT kolom_satu, kolom_dua, DIV 1000 AS 'Price in K' FROM nama_table;
```

## Matematikal Function
```
ABS()
COS()
PI()
SIN()
TAN()
```

## Auto Increment
```
SELECT LAST_INSERT_ID(); // mendapatkan id terakhir
```

## String Function
```
LOWER()
LENGTH()
UPPER()
CONCAT()
TRIM()
```

## Date Time Function
```
EXTRACT()
YEAR()
MONTH()
DATE()
DAYNAME()
```

## Flow Control Function
```
// CASE
SELECT id, CASE nama_kolom WHEN "nilai satu lama" THEN "nilai satu baru" WHEN "nilai dua lama" THEN "nilai dua baru" ELSE "nilai lainnya" END FROM nama_table;

// IF()
SELECT id, price, IF(price <= 15000, 'Murah', IF(price <= 20000, 'Mahal', 'Mahal Banget')) AS 'Mahal?' FROM nama_table;

IFNULL(nama_kolom, "nilai baru")
```

## Aggregate Function
```
COUNT()
SUM()
AVG()
MIN()
MAX()
```

## Grouping
```
SELECT category, COUNT(id) AS 'Total Product' FROM nama_table GROUP BY category;
```

## Having Clause
```
HAVING dan WHERE adalah kata kunci yang sama
bedanya HAVING untuk alias
```

## Constraint
```
UNIQUE KEY
CREATE TABLE nama_table (id INT NOT NULL AUTO_INCREMENT, UNIQUE KEY nama_unik (nama_kolom));
ALTER TABLE nama_table ADD CONSTRAINT nama_unik UNIQUE (nama_kolom);
ALTER TABLE nama_table DROP CONSTRAINT nama_unik;
```

## Check Constraint
```
CREATE TABLE nama_table (id INT NOT NULL AUTO_INCREMENT, price INT UNSIGNED NOT NULL, CONSTRAINT price_check CHECK(price >= 1000));
ALTER TABLE nama_table ADD CONSTRAINT price_check CHECK(price >= 1000);
ALTER TABLE nama_table DROP CONSTRAINT price_check;
```

## Foreign Key
```
CREATE TABLE nama_table (
id INT NOT NULL AUTO_INCREMENT, id_product VARCHAR(10) NOT NULL
CONSTRAINT fk_wishlist_product FOREIGN KEY (id_product) REFERENCE products (id)
) ENGINE = InnoDB; // kriteria id_product harus sama dengan id pada table product

ALTER TABLE nama_table ADD CONSTRAINT fk_wishlist_product FOREIGN KEY (id_product) REFERENCE products (id);
ALTER TABLE nama_table DROP CONSTRAINT fk_wishlist_product;

Behavior Foreign Key = {
    RESTRICT = {
        ON DELETE = "Ditolak",
        ON UPDATE = "Ditolak"
    },
    CASCADE = {
        ON DELETE = "Data akan dihapus",
        ON UPDATE = "Data akan ikut diubah"
    },
    NO ACTION = {
        ON DELETE = "Data dibiarkan",
        ON UPDATE = "Data dibiarkan"
    },
    SET NULL = {
        ON DELETE = "Diubah jadi NULL",
        ON UPDATE = "Diubah jadi NULL"
    }
}

Mengubah Behavior
ALTER TABLE nama_table ADD CONSTRAINT fk_wishlist_product
FOREIGN KEY (id_product) REFERENCE products (id) ON DELETE CASCADE ON UPDATE CASCADE;  // On Delete dan On Update diubah berbarengan
```

## Join
```
Dua Table
SELECT * FROM wishlist JOIN products ON (wishlist.id_product = products.id);
SELECT wishlist.id, products.id, products.name, wishlist.description FROM wishlist JOIN products ON (wishlist.id_product = products.id);
SELECT w.id, p.id, p.name, w.description FROM wishlist AS w JOIN products AS p ON (w.id_product = p.id);
SELECT w.id AS wishlist_id, p.id AS prod_id, p.name AS prod_name, w.description AS wishlist_desc FROM wishlist AS w JOIN products AS p ON (w.id_product = p.id);

Tiga Table
SELECT c.email, p.id, p.name, w.description FROM wishlist AS w JOIN products AS p ON (w.id_product = p.id) JOIN customers AS c ON (w.id_customer = c.id);
```

## One to One Relationship
```
- Harus memiliki Foreign Key
- Harus memiliki Unique Key agar data tidak duplikat
```

## One to Many Relationship
```
- Harus memiliki Foreign Key'
- Tidak harus memiliki Unique key
```

## Many to Many Relationship
```
- Harus memiliki Table perantara (ketiga)
- Table ketiga harus reference ke table lainnya
```

## Melihat data 
```
SELECT * FROM orders JOIN orders_detail ON (orders_detail.id_order = orders.id) JOIN products ON (orders_detail.id_product = products.id);
```

## Join
```
Inner Join
Left Join
Right Join
Cross Join
```

## Subqueries
```
SELECT * FROM products WHERE price > (SELECT AVG(price) FROM products);
SELECT MAX(cp.price) FROM (SELECT price FROM categories JOIN products ON (products.id_category = categories.id)) as cp;
```

## Union
```
(query table satu) UNION (query table dua); // jika dua table terdapat data duplikat maka akan dihapus
(query table satu) UNION ALL (query table dua); // jika dua table terdapat data duplikat maka akan ditampilkan
SELECT DISTINCT email FROM customers WHERE email IN (SELECT DISTINCT email FROM guestbooks);  // intersect adalah inner join
SELECT DISTINCT customers.email FROM customers INNER JOIN guestbooks ON (guestbooks.email = customers.email); // intersect juga
SELECT DISTINCT customers.email, guestbooks.email FROM customers LEFT JOIN guestbooks ON (customers.email = guestbooks.email) WHERE guestbooks.email IS NULL; // minus adalah left join
```

## Transaction (Locking Otomatis)
```
START TRANSACTION
COMMIT
ROLLBACK
```

## Locking Manual
```
SELECT FOR UPDATE; // hasil select akan keluar jika user lain selesai transaction
```

## Lock Table (Satu table saja)
```
LOCK TABLE produts READ;  // user lain hanya bisa read
LOCK TABLE produts WRITE; // user lain tidak bisa read dan write
UNLOCK TABLES;
```

## Lock Instance (Satu Database)
```
LOCK INSTANCE FOR BACKUP; // hanya bisa READ, DDL dan DML tidak bisa
UNLOCK INSTANCE;
```

## BackUp Database
```
perintah
mysqldump nama_database --user --root --password --result-file=/path/file/tujuan/nama_file.sql
mysqldump nama_database --user=nama_pengguna --password=kata_sandi --result-file=/path/file/tujuan/nama_file.sql
```

Restore hasil backup
```
mysql --user=nama_pengguna --password=kata_sandi nama_database < /path/file/tujuan/nama_file.sql
```
