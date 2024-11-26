*** The book, "PostgreSQL Data Analyst DA Handbook - Practical Guide 2025", is published on Amazon, it covers PostgreSQL v13, 14, 15, 16 to the latest v17 ***

Paper book's URL: The "PostgreSQL Data Analyst DA Handbook - Practical Guide 2025" URL:
https://www.amazon.com/PostgreSQL-Handbook-Unlocking-Techniques-Practices/dp/B0DNG6T2S5/

Kindle eBook's URL: The "PostgreSQL Data Analyst DA Handbook - Practical Guide 2025"  URL:
https://www.amazon.com/PostgreSQL-Handbook-Handbook-Unlocking-Techniques-Semi-Structured-ebook/dp/B0DNFL9B66/

Important Note: The following commands are FOR INFORMATION ONLY

###

###


P2.1

INSERT INTO t2 ( my_int, my_real, my_double)
VALUES (1, 1.12345678901234567890, 1.123456789012345678901234567890);
SELECT my_int, my_real, my_double, my_serial FROM t2 WHERE my_int = 1;


P2.2

INSERT INTO t2 (my_int, my_numeric)
VALUES (2, 12345678901234567890.12345678901234567890);
SELECT my_int, my_numeric, my_smallserial, my_bigserial FROM t2 WHERE my_int = 2;


P2.3

INSERT INTO t2 (my_int, my_numeric) VALUES (3, 'Infinity'); 
INSERT INTO t2 (my_int, my_numeric) VALUES (4, '-Infinity'); 
INSERT INTO t2 (my_int, my_numeric) VALUES (5, 'NaN'); SELECT my_int, my_numeric FROM t2;


P2.4

INSERT INTO t2 (my_int, my_money)
VALUES (6, 12345678.912345678901234567890);


P2.5

SELECT my_int, my_money / 5 AS amount FROM t2 WHERE my_int = 6;
SELECT my_int, my_money / 1.5 as amount FROM t2 WHERE my_int = 6;
SELECT my_int, (my_money::NUMERIC / 1.5)::MONEY as amount FROM t2 WHERE my_int = 6;


P2.6

INSERT INTO t2 (my_int, my_char_varying, my_varchar, my_char, my_text) VALUES (7, 'abcdefghijklmnopqrst', 'abcdefghijklmnopqrst', 'abcdefghijklmnopqrstu', 'abcdefghijklmnopqrstuvwxyz');
SELECT my_char_varying, my_varchar, my_char, my_text FROM t2 WHERE my_int = 7;


P2.7

INSERT INTO t2 (my_int, my_char_varying, my_varchar, my_char, my_text) VALUES (8, 'abcdefghijklmnopqrst', 'abcdefghijklmnopqrst', 'abcdefghijklmnopqrst', 'abcdefghijklmnopqrstuvwxyz');
SELECT my_char_varying, my_varchar, my_char, my_text FROM t2 WHERE my_int = 8;
INSERT INTO t2 (my_int, my_char_varying, my_varchar, my_char, my_text) VALUES (9, 'abcdefghijklmnopqrstu', 'abcdefghijklmnopqrstu', 'abcdefghijklmnopqrstu', 'abcdefghijklmnopqrstuvwxyz');
INSERT INTO t2 (my_int, my_char_varying, my_varchar, my_char, my_text) VALUES (9, 'abcdefghijklmnopqrstuvwxyz'::VARCHAR(20), 'abcdefghijklmnopqrstuvwxyz '::VARCHAR(20), 'abcdefghijklmnopqrstuvwxyz '::CHAR(20), 'abcdefghijklmnopqrstuvwxyz');
SELECT my_char_varying, my_varchar, my_char, my_text FROM t2 WHERE my_int = 9;


P2.8

INSERT INTO t2 (my_int, my_bytea) VALUES (10, E'\\xDEADBEEF');
SELECT my_int, my_bytea FROM t2 WHERE my_int = 10;
SET bytea_output = 'hex';
SELECT my_int, my_bytea FROM t2 WHERE my_int = 10; 

SET bytea_output = 'escape';
SELECT my_int, my_bytea FROM t2 WHERE my_int = 10; 


P2.9

INSERT INTO t2 ( my_int,
    my_timestamp_0,
    my_timestamp_3,
    my_timestamp_6,
    my_timestamp_tz_0,
    my_timestamp_tz_3,
    my_timestamp_tz_6,
    my_date,
my_time,
my_time_tz VALUES (
--TIMESTAMP(0)
--TIMESTAMP(3)
--TIMESTAMP(6)
--TIMESTAMP(0) WITH TIME ZONE
--TIMESTAMP(3) WITH TIME ZONE
--TIMESTAMP(6) WITH TIME ZONE
--TIME(6)
--TIME(6) WITH TIME ZONE)
11,
TIMESTAMP '2023-08-03 12:34:56',
TIMESTAMP '2023-08-03 12:34:56.789',
TIMESTAMP '2023-08-03 12:34:56.123456', TIMESTAMPTZ '2023-08-03 12:34:56+00:00', TIMESTAMPTZ '2023-08-03 12:34:56.789+00:00', TIMESTAMPTZ '2023-08-03 12:34:56.123456+00:00', DATE '2023-08-03',
TIME '12:34:56',
TIME '12:34:56+00:00');

\x on
SELECT my_int, my_timestamp_0, my_timestamp_3,my_timestamp_6, my_timestamp_tz_0,my_timestamp_tz_3, my_timestamp_tz_6, my_date, my_time, my_time_tz
FROM t2
WHERE my_int = 11;


P2.10

INSERT INTO t2 (my_int, my_date, my_time, my_time_tz) VALUES (12,'now'::DATE,'allballs'::TIME, 'allballs'::TIME WITH TIME ZONE);
SELECT my_int, my_date, my_time, my_time_tz FROM t2 WHERE my_int = 12;

INSERT INTO t2 ( my_int,
    my_date,
    my_time,
    my_timestamp_tz_0)
VALUES ( 13,
'yesterday'::DATE,
'now'::TIME,
'now'::TIMESTAMP WITH TIME ZONE);

SELECT my_int, my_date, my_time, my_timestamp_tz_0 FROM t2 WHERE my_int = 13;


P2.11

INSERT INTO t2 ( my_int,
    my_timestamp_0,
    my_timestamp_3,
    my_timestamp_6,
    my_timestamp_tz_0,
    my_timestamp_tz_3,
    my_timestamp_tz_6
VALUES ( 14,
--TIMESTAMP(0)
--TIMESTAMP(3)
--TIMESTAMP(6)
--TIMESTAMP(0) WITH TIME ZONE
--TIMESTAMP(3) WITH TIME ZONE
--TIMESTAMP(6) WITH TIME ZONE)
TIMESTAMP '2023-12-31 23:59:59',
TIMESTAMP '2024-01-01 00:00:00.000',
TIMESTAMP '2025-01-01 00:00:00.000000', TIMESTAMPTZ '2023-12-31 23:59:59+08:00', TIMESTAMPTZ '2024-01-01 00:00:00.000+08:00', TIMESTAMPTZ '2025-01-01 00:00:00.000000+08:00');

SELECT
     my_int,
     my_timestamp_3 - my_timestamp_0        AS t1_duration,
     my_timestamp_6 - my_timestamp_0        AS t2_duration,
     my_timestamp_tz_3 - my_timestamp_tz_0  AS t3_duration,
     my_timestamp_tz_6 - my_timestamp_tz_3  AS t4_duration
FROM t2
WHERE my_int = 14;

SELECT
my_int,
EXTRACT(EPOCH FROM (my_timestamp_3 - my_timestamp_0))
 AS t1_duration,
EXTRACT(EPOCH FROM (my_timestamp_6 - my_timestamp_0))
 AS t2_duration,
EXTRACT(EPOCH FROM (my_timestamp_6 - my_timestamp_3))
 AS t3_duration,
EXTRACT(EPOCH FROM (my_timestamp_tz_3 - my_timestamp_tz_0 ))
 AS t4_duration,
EXTRACT(EPOCH FROM (my_timestamp_tz_6 - my_timestamp_tz_0 ))
 AS t5_duration,
EXTRACT(EPOCH FROM (my_timestamp_tz_6 - my_timestamp_tz_3 ))
AS t6_duration FROM t2
WHERE my_int = 14;



P2.12

INSERT INTO t2 ( my_int,
    my_timestamp_0,
my_timestamp_3 VALUES (
--TIMESTAMP(0)
--TIMESTAMP(3))
15,
TIMESTAMP '2023-12-31 23:59:59',
TIMESTAMP '2023-12-31 23:59:59' +
INTERVAL '2 Years 3 Months 17 Days 3 Hours 20 Minutes 8 Seconds');

SELECT FROM t2 WHERE my_int = 15;


SELECT
my_int,
my_timestamp_0,
my_timestamp_3,
my_timestamp_3 - my_timestamp_0 AS t1_duration
FROM t2
WHERE my_int = 15;

SELECT TO_CHAR(INTERVAL '3 Hours 20 Minutes 8 Seconds', 'HH12:MI:SS') AS timing;

SELECT (INTERVAL '1 Year 2 Months 1 Day 3 Hours 20 Minutes 1 Second') AS timing;

SELECT EXTRACT(HOURS FROM INTERVAL '1 Year 2 Months 1 Day 3 Hours 20 Minutes 1 Second') AS timing;

CREATE TABLE event (event_name VARCHAR(100), event_duration INTERVAL(4));

INSERT INTO event (event_name, event_duration) VALUES ('Meeting', INTERVAL '3 hours 30 minutes 15.1234 seconds');

SELECT * FROM event;



P2.13

INSERT INTO t2 ( my_int, my_varchar, my_boolean ) VALUES (16, 'Buy groceries', TRUE);

SELECT
my_int,
my_varchar,
my_boolea
FROM t2
WHERE my_int = 16;

SELECT 'yes'::BOOLEAN AS is_true, NULL::BOOLEAN AS is_false;



P2.14

CREATE TYPE MOOD AS ENUM ('sad', 'ok', happy');

CREATE DOMAIN POSTAL_CODE AS TEXT CHECK(VALUE ~ '^\d{5}$' OR VALUE ~ '^\d{5}-\d{4}$');

CREATE TABLE t3 (
my_int INT,
my_mood MOOD, my_postal_code POSTAL_CODE);

INSERT INTO t3 ( my_int,
my_mood,
my_postal_code ) VALUES (
    1,
    'happy',
    '01234-1234');

SELECT my_int, my_mood, my_postal_code FROM t3 WHERE my_int =1;



P2.15

INSERT INTO t2 (my_int, my_json) --JSON
VALUES (17,'{"title": "DBA Guidebook", "author": "Moss", "published_year": 2023}');

SELECT
   my_int,
   my_json->>'title' AS title,
   my_json->>'author' AS author,
(my_json->>'published_year')::INTEGER AS published_year FROM t2
WHERE my_int = 17;

INSERT INTO t2 (my_int, my_jsonb) 
VALUES (18,'{"title": "DBA Guidebook", "author": "Moss", "published_year": 2023}');


SELECT
   my_int,
   my_jsonb->>'title' AS title,
   my_jsonb->>'author' AS author,
(my_jsonb->>'published_year')::integer AS published_year FROM t2
WHERE my_int = 18;


P2.16

SELECT
   my_int,
   my_json->>'title' AS title,
   my_json->>'author' AS author,
(my_json->>'published_year')::integer AS published_year FROM t2
WHERE my_int = 17;

SELECT
   my_int,
   my_json->'title' AS title,
   my_json->'author' AS author,
(my_json->'published_year') AS published_year FROM t2
WHERE my_int = 17;



P2.17

SELECT
   my_int,
   my_json #> '{title}' AS title,
   my_json #> '{author}' AS author,
   my_json #> '{published_year}' AS published_year
FROM t2
WHERE my_int = 17;



P2.18

SELECT '{"b":2}'::jsonb <@ '{"a":1, "b":2}'::jsonb AS checked;

SELECT '{"a":1, "b":2}'::jsonb ? 'b' AS checked;

SELECT '{"a":1, "b":2}'::jsonb @> '{"b":2}'::jsonb AS checked;


P2.19

INSERT INTO t2 (my_int, my_json) VALUES (18, to_json('{"title": "SQL Certification"}'::json));

SELECT
my_int,
my_json #> '{title}' AS title FROM t2
WHERE my_int = 18;

SELECT array_to_json('{{1,5},{99,100}}'::int[]) AS checked;

INSERT INTO t2 (my_int, my_jsonb) VALUES (
19, jsonb_build_object(
        'title', 'Data Visualization',
        'author', 'Antonia',
        'published_year', '2023'::jsonb
));


SELECT
   my_int,
   my_jsonb #> '{title}' AS title,
   my_jsonb #> '{author}' AS author,
   my_jsonb #> '{published_year}' AS published_year
FROM t2
WHERE my_int = 19;


SELECT
   my_int,
   my_jsonb->>'title' AS title,
   my_jsonb->>'author' AS author,
(my_jsonb->>'published_year') AS published_year FROM t2
WHERE my_int = 19;

SELECT 
my_int, my_jsonb FROM t2
WHERE my_int = 20;

SELECT
   my_int,
   my_jsonb->0->>'title'  AS title,
   my_jsonb->1->>'author' AS author,
(my_jsonb->2->>'published_year ')::int AS published_year FROM t2
WHERE my_int = 20;

INSERT INTO t2 (my_int, my_jsonb)
VALUES (
21,
to_jsonb('{"title": "DBA Guidebook", "author": "Moss", "published_year": 2023}'::jsonb));

SELECT
   my_int,
   my_jsonb->>'title' AS title,
   my_jsonb->>'author' AS author,
   (my_jsonb->>'published_year')::int AS published_year
FROM t2
WHERE my_int = 21;

INSERT INTO t2 (my_int, my_jsonb)
VALUES (
22,
array_to_json(ARRAY[jsonb_build_object(
'title', 'DBA Guidebook', 'author', 'Moss', 'published_year', 2023)]));

SELECT
   my_int,
   (my_jsonb #> '{0,title}') AS title,
   (my_jsonb #> '{0,author}') AS author,
((my_jsonb #> '{0,published_year}')::int) AS published_year FROM t2
WHERE my_int = 22;

INSERT INTO t2 (my_int, my_jsonb) VALUES (
23, row_to_json(
(SELECT r F
FROM (SELECT 'DBA Guidebook' AS title,
'Moss' AS author,
2023 AS published_year) AS r)));

SELECT
   my_int,
   my_jsonb->>'title' AS title,
   my_jsonb->>'author' AS author,
   (my_jsonb->>'published_year')::int AS published_year
FROM t2
WHERE my_int = 23;


INSERT INTO t2 (my_int, my_jsonb) VALUES (
24,
json_object(
ARRAY['title', 'author', 'published_year'], ARRAY['DBA Guidebook', 'Moss', '2023'])::jsonb);

SELECT
   my_int,
   my_jsonb->>'title' AS title,
   my_jsonb->>'author' AS author,
   (my_jsonb->>'published_year')::int AS published_year
FROM t2
WHERE my_int = 24;



P2.20

SELECT my_int, jsonb_each(my_jsonb) FROM t2 WHERE my_int =24;


P2.21

INSERT INTO t2 (my_int, my_xml) VALUES (25, '<root><element>Example XML</element></root>');

SELECT my_int, my_xml FROM t2 WHERE my_int=42;



P2.22

CREATE TABLE t4 (my_int INT, my_varchar_array VARCHAR[], my_int_array INT[3], my_numeric_array NUMERIC[], my_boolean_array BOOLEAN[], my_date_array DATE[]);

INSERT INTO t4 (my_int, my_varchar_array) VALUES (1, '{"value1", "value2", "value3"}');
INSERT INTO t4 (my_int, my_int_array) VALUES (2, '{1, 2, 3}');
INSERT INTO t4 (my_int, my_numeric_array) VALUES (3, '{1.23, 4.56, 7.89}');
INSERT INTO t4 (my_int, my_boolean_array) VALUES (4, '{true, false, true}');
INSERT INTO t4 (my_int, my_date_array)VALUES (5, '{"2023-05-01", "2023-05-15", "2023-06-01"}');

SELECT my_varchar_array[1] FROM t4 WHERE my_int = 1; Result:

SELECT my_int_array[2] FROM t4 WHERE my_int = 2; 

SELECT my_numeric_array[3] FROM t4 WHERE my_int = 3; 

SELECT my_boolean_array[1] FROM t4 WHERE my_int = 4; 

SELECT my_date_array[2] FROM t4 WHERE my_int = 5; 



P2.23

CREATE TABLE t5 ( my_int my_int4range my_numrange my_tsrange my_tstzrange my_varchar my_value
INT,
INT4RANGE,
NUMRANGE,
TSRANGE,
TSTZRANGE,
VARCHAR,
NUMERIC);

INSERT INTO t5 (my_int, my_tsrange, my_varchar, my_value)
VALUES (1, '[2023-08-01 00:00:00, 2023-08-02 00:00:00)', 'USD/EUR', 1.221);

INSERT INTO t5 (my_int, my_tsrange, my_varchar, my_value)
VALUES (2, '[2023-08-02 00:00:00, 2023-08-03 00:00:00)', 'USD/EUR', 1.222);

INSERT INTO t5 (my_int, my_tsrange, my_varchar, my_value)
VALUES (3, '[2023-08-03 00:00:00, 2023-08-04 00:00:00)', 'USD/EUR', 1.223);

SELECT my_varchar AS Currency, my_value AS rate FROM t5 WHERE my_tsrange @> '2023-08-03'::TIMESTAMP;

SELECT my_varchar AS Currency, my_value AS rate FROM t5 WHERE my_tsrange @> '2023-08-02'::TIMESTAMP;

SELECT my_varchar AS Currency, my_value AS rate FROM t5 WHERE my_tsrange @> '2023-08-01'::TIMESTAMP;

INSERT INTO t5 (my_int, my_tstzrange, my_varchar, my_value)
VALUES (4, '[2023-08-01 00:00:00+8, 2023-08-02 00:00:00+8)', 'USD/EUR', 1.224);

INSERT INTO t5 (my_int, my_tstzrange, my_varchar, my_value)
VALUES (5, '[2023-08-02 00:00:00+8, 2023-08-03 00:00:00+8)', 'USD/EUR', 1.225);

INSERT INTO t5 (my_int, my_tstzrange, my_varchar, my_value)
VALUES (6, '[2023-08-03 00:00:00+8, 2023-08-04 00:00:00+8)', 'USD/EUR', 1.226);

SELECT my_varchar AS Currency, my_value AS rate FROM t5
WHERE my_tstzrange @> '2023-08-01'::TIMESTAMP WITH TIME ZONE;

SELECT my_varchar AS Currency, my_value AS rate FROM t5
WHERE my_tstzrange @> '2023-08-02'::TIMESTAMP WITH TIME ZONE;

SELECT my_varchar AS Currency, my_value AS rate FROM t5
WHERE my_tstzrange @> '2023-08-03'::TIMESTAMP WITH TIME ZONE;



P2.24

INSERT INTO t5 (my_int, my_int4range, my_varchar, my_value) VALUES (11, '[0, 1)', 'New Born', 50000);

INSERT INTO t5 (my_int, my_int4range, my_varchar, my_value) VALUES (12, '[1, 7)', 'Kid', 100000);

INSERT INTO t5 (my_int, my_int4range, my_varchar, my_value) VALUES (13, '[7, 18)', 'Young', 150000);

INSERT INTO t5 (my_int, my_int4range, my_varchar, my_value) VALUES (14, '[18, 60)', 'Adult', 200000);

INSERT INTO t5 (my_int, my_int4range, my_varchar, my_value) VALUES (15, '[60, 150)', 'Old', 250000);

SELECT my_varchar, my_value FROM t5 WHERE my_int4range @> 18;

INSERT INTO t5 (my_int, my_numrange, my_varchar, my_value) VALUES (21, '[0.00, 50.00)', 'Low Price Range', 0.05);

INSERT INTO t5 (my_int, my_numrange, my_varchar, my_value) VALUES (22, '[50.00, 150.00)', 'Mid-Price Range', 0.08);

INSERT INTO t5 (my_int, my_numrange, my_varchar, my_value) VALUES (23, '[150.00, 1000]', 'High Price Range', 0.10);

SELECT my_varchar, my_numrange, my_value AS extra_discount FROM t5 WHERE my_numrange @> '50'::NUMERIC;

SELECT my_varchar, my_numrange, my_value AS extra_discount FROM t5 WHERE my_numrange @> '49.99999'::NUMERIC;

SELECT my_varchar, my_numrange, my_value AS extra_discount FROM t5 WHERE my_numrange @> '150.00'::NUMERIC;



P2.25

INSERT INTO t2 (my_int, my_uuid, my_varchar) VALUES (26, 'a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11', 'Data validation Job');

INSERT INTO t2 (my_int, my_inet, my_varchar) VALUES (27, '192.168.0.1', 'Database server IP');

INSERT INTO t2 (my_int, my_cidr, my_varchar) VALUES (28, '192.168.0.0/24', 'CIDR Range');

INSERT INTO t2 (my_int, my_macaddr, my_varchar) VALUES (29, '08:00:2b:01:02:03', 'MAC Address');

INSERT INTO t2 (my_int, my_macaddr8, my_varchar) VALUES (30, '08:00:2b:01:02:03:04:05', 'MAC Address 8');



P2.26

INSERT INTO t2 (my_int, my_text, my_tsvector)
VALUES (31,'Using dedicated data types for UUID, CIDR, INET, MACADDR, and MACADDR8 can lead to better data management',
to_tsvector('english', 'Using dedicated data types for UUID, CIDR, INET, MACADDR, and MACADDR8 can lead to better data management'));

INSERT INTO t2 (my_int, my_text, my_tsvector)
VALUES (32,'As database systems evolve, they can introduce optimizations and enhancements specific to these data types. Storing the data in dedicated columns will allow you to take advantage of such improvements without needing to change your data model.',to_tsvector('english', 'As database systems evolve, they can introduce optimizations and enhancements specific to these data types. Storing the data in dedicated columns will allow you to take advantage of such improvements without needing to change your data model.'));

INSERT INTO t2 (my_int, my_text, my_tsvector)
VALUES (33,'Storing MAC addresses alongside network configuration settings for various devices to ensure proper configuration and connectivity.', to_tsvector('english', 'Storing MAC addresses alongside network configuration settings for various devices to ensure proper configuration and connectivity.'));

SELECT my_text, my_tsvector FROM t2 WHERE my_int =31;

SELECT my_int, my_text FROM t2 WHERE my_tsvector @@ to_tsquery('english', 'data & types') ORDER BY ts_rank_cd(my_tsvector, to_tsquery('english', 'better & data')) DESC;


SELECT my_int, my_text FROM t2 WHERE my_tsvector @@ to_tsquery('english', 'data & types') ORDER BY ts_rank_cd(my_tsvector, to_tsquery('english', ' improvements & enhancements')) DESC;


P3

CREATE TABLE category (
category_id SERIAL PRIMARY KEY, category_description TEXT);

CREATE TABLE category_designer (
category_id INT REFERENCES category(category_id), designer_name TEXT,
PRIMARY KEY (category_id, designer_name));


INSERT INTO category (category_description) VALUES
    ('Category A'),
    ('Category B'),
    ('Category C');

INSERT INTO category_designer (category_id, designer_name) VALUES
    (1, 'Antonia'),
    (1, 'Arthur'),
    (2, 'Eddy');

INSERT INTO category (category_description) VALUES
    ('Category A'),
    ('Category B'),
    ('Category C');

INSERT INTO category-designer (category_id, designer_dame) VALUES
    (1, 'Antonia'),
    (1, 'Arthur'),
    (2, 'Eddy');

SELECT
    p.product_name,
    c.category_description,
    string_agg(cd.DesignerName, ', ') AS Designers
FROM product p
JOIN category c ON p.category_id = c.category_id
LEFT JOIN category_designer cd ON c.category_id = cd.category_id GROUP BY p.product_name, c.category_description;

    
CREATE DATABASE about_x;

\c about_x

CREATE SCHEMA car;
CREATE SCHEMA space; CREATE SCHEMA common;


P3.1

CREATE TYPE ENUM_TITLE AS ENUM ('Mr.', 'Ms.', 'Mrs.', 'Dr.', 'Prof.');

CREATE TABLE common.shareholder (
    shareholder_id VARCHAR(10) PRIMARY KEY,
    title       ENUM_TITLE,
    first_name  VARCHAR(30) NOT NULL,
    middle_name VARCHAR(30),
last_name
    email
    phone
    address_1
    address_2   VARCHAR(30),
    address_3   VARCHAR(30),
    address_4   VARCHAR(30),
    city        VARCHAR(30) NOT NULL,
    country     VARCHAR(30) NOT NULL,
    postal_code VARCHAR(8) NOT NULL);
    
CREATE INDEX shareholder_idx_01 ON common.shareholder (shareholder_id);

CREATE INDEX shareholder_idx_02 ON common.shareholder (first_name, last_name, shareholder_id);

INSERT INTO common.shareholder (
shareholder_id, title, first_name, middle_name, last_name, email, phone, address_1, address_2, address_3, address_4,
city, country, postal_code)
VALUES('S000000001','Mr.', 'Elon', 'Reeve', 'Musk','Elon.musk@x.com', '+1-010101010101', 'Unit 1 X Corp Building', NULL, NULL, NULL, 'Los Angeles', 'USA', '912345');



P3.2

CREATE TABLE common.shareholder_registry (
company VARCHAR(50) NOT NULL, shareholder_id VARCHAR(10) NOT NULL, shares BIGINT NOT NULL, PRIMARY KEY (shareholder_id, company), FOREIGN KEY (shareholder_id)
REFERENCES common.shareholder (shareholder_id));

CREATE INDEX share_reg_idx_01 ON common.shareholder_registry (company, shareholder_id);

INSERT INTO common.shareholder_registry (company, shareholder_id, shares) VALUES ('xSpace Inc', 'S000000001', 100000000);
INSERT INTO common.shareholder_registry ( company, shareholder_id, shares) VALUES ('E Car Inc', 'S000000001', 200000000);
INSERT INTO common.shareholder_registry ( company, shareholder_id, shares)VALUES ('X Inc', 'S000000001', 300000000);

SELECT s.title, s.first_name, s.last_name, sr.shares FROM common.shareholder s
JOIN common.shareholder_registry sr
ON s.shareholder_id = sr.shareholder_id;



P3.3

CREATE TABLE space.space_travel_schedule (
trip_id VARCHAR(10) PRIMARY KEY, destination VARCHAR(100) NOT NULL, departure_from VARCHAR(100) NOT NULL, departure_dtm TIMESTAMP(0) NOT NULL, return_dtm TIMESTAMP(0) NOT NULL, price MONEY NOT NULL);

CREATE INDEX space_idx_01 ON space.space_travel_schedule (trip_id);

CREATE INDEX space_idx_02 ON space.space_travel_schedule (destination, trip_id);

INSERT INTO space.space_travel_schedule (
 trip_id, destination, departure_from,
departure_dtm, return_dtm, price) VALUES (
 'S000000001', 'Moon', 'Los Angeles, USA',
 '2024-12-31 23:59:59', '2025-01-31 00:00:00', 1000000.00);


P3.4

customer_id VARCHAR(20) PRIMARY KEY, title ENUM_TITLE,
first_name VARCHAR(30) NOT NULL, middle_name VARCHAR(30),
VARCHAR(30) NOT NULL, VARCHAR(30), VARCHAR(30),
last_name
email
phone
address_1   VARCHAR(30),
address_2   VARCHAR(30),
address_3   VARCHAR(30),
address_4   VARCHAR(30),
city        VARCHAR(30),
country     VARCHAR(30),
postal_code VARCHAR(8),
tweeter_account_id VARCHAR(64));

CREATE INDEX customer_idx_01 ON car.customer (customer_id);


Result:
INSERT 0 1
192
Practice 3.4: CREATE TABLE “Customer” under “space” schema
-- Create the Customer table under the car schema CREATE TABLE car.customer (
customer_id VARCHAR(20) PRIMARY KEY, title ENUM_TITLE,
first_name VARCHAR(30) NOT NULL, middle_name VARCHAR(30),
VARCHAR(30) NOT NULL, VARCHAR(30), VARCHAR(30),
last_name
email
phone
address_1   VARCHAR(30),
address_2   VARCHAR(30),
address_3   VARCHAR(30),
address_4   VARCHAR(30),
city        VARCHAR(30),
country     VARCHAR(30),
postal_code VARCHAR(8),
tweeter_account_id VARCHAR(64));

CREATE INDEX customer_idx_01 ON car.customer (customer_id);
-- Insert sample data INSERT INTO car.customer (
 customer_id, title, first_name, middle_name, last_name,
 email, phone,
 address_1, address_2, address_3, address_4,
 city, country, postal_code,
tweeter_account_id) VALUES (
 'C230000001', 'Mr.', 'Thomas', 'S', 'Bright',
 'thomas@thomassbright.org', '+01-123456789',
 'Unit 1, First Street', NULL, NULL, NULL,
 'Los Angeles', 'USA', '923456',
 '@thomassbright');


P3.5

CREATE TABLE space.space_trip (
trip_id VARCHAR(10) PRIMARY KEY, customer_id VARCHAR(10) NOT NULL, fee MONEY NOT NULL, amount_paid MONEY NOT NULL,
FOREIGN KEY (customer_id) REFERENCES car.customer(customer_id) );

CREATE INDEX trip_idx_01 ON space.space_trip (trip_id, customer_id);

CREATE INDEX trip_idx_02 ON space.space_trip (customer_id, trip_id);

INSERT INTO space.space_trip (trip_id, customer_id, fee, amount_paid) VALUES ('S000000001', 'C230000001', '1,000,000.00', '900,000.00');

SELECT st.trip_id, sch.destination, sch.departure_dtm, c.first_name, c.last_name,
st.amount_paid FROM space.space_trip st
JOIN car.customer c ON st.customer_id = c.customer_id
JOIN space.space_travel_schedule sch ON st.trip_id = sch.trip_id;



P3.6

CREATE TABLE car.category (
    category_id VARCHAR(20) PRIMARY KEY,
    description TEXT NOT NULL);

CREATE INDEX category_idx_01 ON car.category (category_id);

INSERT INTO car.category (category_id, description) VALUES ('CT000001', 'Advanced model');



P3.7

CREATE TABLE car.category_designer (
category_id VARCHAR(20) REFERENCES car.category (category_id), designer VARCHAR(50) NOT NULL,
PRIMARY KEY (category_id, designer));

CREATE INDEX category_designer_idx_01 ON car.category_designer (category_id, designer);

INSERT INTO car.category_designer (category_id, designer) VALUES ('CT000001', 'Arthur');

INSERT INTO car.category_designer (category_id, designer) VALUES ('CT000001', 'Antonia');



P3.8

CREATE TABLE car.product (
product_id VARCHAR(20) PRIMARY KEY, 
product_name TEXT NOT NULL,
sku VARCHAR(20) NOT NULL, 
origin VARCHAR(20) NOT NULL, 
color VARCHAR(20) NOT NULL,
category_id VARCHAR(20) NOT NULL,
price MONEY NOT NULL,
FOREIGN KEY (category_id) REFERENCES car.category(category_id));

CREATE INDEX product_idx_01 ON car.product (product_id);

CREATE INDEX product_idx_02 ON car.product (category_id, product_id);

CREATE INDEX product_idx_03 ON car.product (origin, product_id);

INSERT INTO car.product (product_id, product_name, sku, origin, color,category_id, price)
VALUES ( 'P00000001', 'Model K', 'S0001-20841-2233-331', 'USA', 'Black', 'CT000001', 39999.99);

SELECT category_id, designer FROM car.category_designer; 

SELECT
    p.product_id, p.product_name, p.price, p.sku, p.category_id,
    c.description AS category_description,
    ARRAY_AGG(cd.designer) AS designers
FROM car.product p
JOIN car.category c ON p.category_id = c.category_id
JOIN car.category_designer cd ON p.category_id = cd.category_id
GROUP BY p.product_id, p.product_name, p.price, p.sku, p.category_id, c.description;

SELECT
    p.product_id,
    p.product_name,
    p.price,
    p.sku,
    p.category_id,
    c.description AS category_description,
    cd.designer AS designers
FROM car.product p
JOIN car.category c ON p.category_id = c.category_id
JOIN car.category_designer cd ON p.category_id = cd.category_id;



P3.9

CREATE TABLE car.order_header (
order_no VARCHAR(20) NOT NULL,
customer_idVARCHAR(20) REFERENCES car.customer (customer_id),
order_dtm TIMESTAMP(0),
delivery_address_1 VARCHAR(30), 
delivery_address_2 VARCHAR(30), 
delivery_address_3 VARCHAR(30), 
delivery_address_4 VARCHAR(30), 
discount_rate NUMERIC(5,2), 
order_net_total MONEY,
PRIMARY KEY (order_no, customer_id)
);

CREATE INDEX order_header_idx_01 ON car.order_header (order_no, customer_id);

INSERT INTO car.order_header (order_no, customer_id, order_dtm, delivery_address_1,discount_rate, order_net_total) VALUES (
'OR2023000001', 'C230000001', '2023-08-03 12:00:00','123 Main St', 0.10, 71999.98);


P3.10

CREATE TABLE car.order_detail (
order_no VARCHAR(20) NOT NULL,
product_id VARCHAR(20) REFERENCES car.product (product_id), qty NUMERIC(11,2),
unit_price NUMERIC(15,2),
amount NUMERIC(15,2),
PRIMARY KEY (order_no, product_id));

CREATE INDEX order_detail_idx_01 ON car.order_detail (order_no, product_id);

INSERT INTO car.order_detail (order_no, product_id, qty, unit_price, amount)
VALUES ('OR2023000001', 'P00000001', 2, 39999.99, 79999.98);


P3.11

ALTER TABLE car.customer
ADD CONSTRAINT customer_tweeter_account_id_unique UNIQUE (tweeter_account_id);

CREATE TABLE car.tweet (
tweet_message_id VARCHAR(64) PRIMARY KEY, 
tweeter_account_id VARCHAR(64) REFERENCES car.customer(tweeter_account_id),
content TEXT,
publish_dtm TIMESTAMP(6),
image BYTEA,
video VARCHAR(100),
url VARCHAR(100));

CREATE INDEX tweet_idx_01 ON car.tweet (tweet_message_id, tweeter_account_id);

INSERT INTO car.tweet (
 tweet_message_id, tweeter_account_id,
 content,
 publish_dtm, image, video, url)
VALUES (
'T000000001', '@thomassbright',
 'Excited to share our latest electric car model!',
 '2023-08-03 12:00:00.000000', NULL, NULL, NULL);



P3.12

CREATE TABLE t6 (
id INT PRIMARY KEY,
name VARCHAR(50), description VARCHAR(100));

CREATE TABLE t7 (
id INT PRIMARY KEY,
t6_id INT,
details VARCHAR(200),
FOREIGN KEY (t6_id) REFERENCES t6(id));

INSERT INTO t6 (id, name, description)
VALUES (1, 'Item A', 'Description for Item A'), (2, 'Item B', 'Description for Item B'), (3, 'Item C', 'Description for Item C'), (4, 'Item D', 'Description for Item D'), (5, 'Item E', 'Description for Item E');

INSERT INTO t7 (id, t6_id, details) VALUES (1, 1, 'Details for Item A'), (2, 2, 'Details for Item B'), (3, 1, 'Details for Item A'), (4, 3, 'Details for Item C'), (5, 2, 'Details for Item B');



P3.13

ALTER TABLE t6 ADD COLUMN new_column VARCHAR(50);

INSERT INTO t6 (id, name, description, new_column) VALUES (6, 'Item F', 'Description for Item F', '600'), (7, 'Item G', 'Description for Item G', '700'), (8, 'Item H', 'Description for Item H', '800');

ALTER TABLE t6 ALTER COLUMN new_column SET DATA TYPE INT USING new_column::INT;

ALTER TABLE t6 RENAME COLUMN new_column TO new_int;

SELECT * FROM t6;



P3.14

DROP TABLE t6;



P3.15

DROP TABLE t6 CASCADE;



P3.16

CREATE INDEX CONCURRENTLY tweet_idx_02 ON car.tweet (publish_dtm, tweeter_account_id, tweet_message_id);



P3.17

ALTER INDEX car.tweet_idx_02 RENAME TO tweet_idx_02a;

ALTER INDEX car.tweet_idx_02a SET (fillfactor = 80);

DROP INDEX car.tweet_idx_02a;

CREATE INDEX CONCURRENTLY tweet_idx_02 ON car.tweet (publish_dtm, tweet_message_id, tweeter_account_id);



P3.18

CREATE VIEW space_trip_details AS
SELECT st.trip_id, sch.destination, sch.departure_dtm,
       c.first_name, c.last_name,
st.amount_paid FROM space.space_trip st
JOIN car.customer c ON st.customer_id = c.customer_id
JOIN space.space_travel_schedule sch ON st.trip_id = sch.trip_id;

SELECT * FROM space_trip_details LIMIT 1;

DROP VIEW space_trip_details;

CREATE VIEW space_trip_details AS
SELECT st.trip_id, sch.destination, sch.departure_dtm, sch.return_dtm,
       c.first_name, c.last_name,
st.amount_paid FROM space.space_trip st
JOIN car.customer c ON st.customer_id = c.customer_id
JOIN space.space_travel_schedule sch ON st.trip_id = sch.trip_id;

SELECT * FROM space_trip_details LIMIT 1;

DROP VIEW space_trip_details;


P3.19

COMMENT ON COLUMN car.order_header.order_no IS 'Unique identifier for each order.';

COMMENT ON COLUMN car.order_header.discount_rate IS 'Percentage discount applied to the whole order.';

COMMENT ON COLUMN car.order_header.order_net_total IS 'Total net amount of the order after discounts, = SUM(order_detail.amount) - SUM(order_detail.amount) * order_header.discount_rate ';




P4.1

INSERT INTO car.tweet ( tweet_message_id, tweeter_account_id, content,
publish_dtm, image, video, url)
VALUES (
'T000000002', 'C230000001',
'Data manipulation in a database refers to the process of adding,
   altering, retrieving, or deleting data stored within the database.',
  '2023-08-05 15:00:00.000000', NULL, NULL, NULL);



P4.2 

INSERT INTO car.tweet ( tweet_message_id, tweeter_account_id, content,
  publish_dtm,
  image,
  video,
  url)
VALUES (
'T000000002',
'@thomassbright',
'Data manipulation in a database refers to the process of adding,
   altering, retrieving, or deleting data stored within the database. ',
  '2023-08-05 15:00:00.000000',
  NULL,
  'https://www.youtube.com/watch?v=T000000002',
  'https://twitter.com/your_username/status/T000000002' );

SELECT * FROM car.tweet WHERE tweet_message_id ='T000000003';

SELECT
     c.customer_id,
     c.first_name,
     c.last_name,
     oh.order_no,
     oh.order_dtm,
     od.product_id,
     od.unit_price,
     p.product_name,
     p.price AS unit_price,
     cat.category_id,
     cat.description AS category_description,
     od.qty AS total_quantity
FROM car.customer AS c
JOIN car.order_header AS oh ON c.customer_id = oh.customer_id JOIN car.order_detail AS od ON oh.order_no = od.order_no
JOIN car.product AS p ON od.product_id = p.product_id
JOIN car.category AS cat ON p.category_id = cat.category_id ORDER BY c.customer_id, oh.order_no, od.product_id;



P4.3

UPDATE car.order_detail
SET unit_price = 34999.99,
amount = qty * 34999.99
WHERE order_no = 'OR2023000001' AND product_id = 'P00000001'

SELECT * FROM car.order_detail
WHERE order_no = 'OR2023000001' AND product_id = 'P00000001';

SELECT COUNT(1) FROM car.tweet;

DELETE FROM car.tweet
WHERE tweet_message_id = 'T000000001';



P4.4

SELECT * FROM car.tweet WHERE tweet_message_id = 'T000000003';

MERGE INTO car.tweet AS target USING (
SELECT
'T000000003' AS tweet_message_id,
'@thomassbright' AS tweeter_account_id,
'Check out MERGE as it is cool!' AS content,
TIMESTAMP '2023-08-04 10:30:00.000000' AS publish_dtm, NULL::bytea AS image, 'https://www.youtube.com/watch?v=your_video_id' AS video, 'https://twitter.com/your_username/status/your_tweet_id' AS url
) AS source
ON (target.tweet_message_id = source.tweet_message_id) WHEN MATCHED THEN
UPDATE SET
        content = source.content,
        publish_dtm = source.publish_dtm,
        image = source.image,
        video = source.video,
        url = source.url
WHEN NOT MATCHED THEN
INSERT (tweet_message_id, tweeter_account_id, content,
publish_dtm, image, video, url)
VALUES (source.tweet_message_id, source.tweeter_account_id,
            source.content,
            source.publish_dtm, source.image, source.video,
            source.url);
            
SELECT * FROM car.tweet WHERE tweet_message_id = 'T000000003';

MERGE INTO car.tweet AS target USING (
SELECT
'T000000003' AS tweet_message_id,
'@thomassbright' AS tweeter_account_id,
'Check out MERGE as it is cool!' AS content,
TIMESTAMP '2023-09-02 11:30:00.000000' AS publish_dtm, NULL::bytea AS image, 'https://www.youtube.com/watch?v=T000000003' AS video, 'https://twitter.com/your_username/status/T000000003' AS url
) AS source
ON (target.tweet_message_id = source.tweet_message_id) WHEN MATCHED THEN
UPDATE SET
        content = source.content,
        publish_dtm = source.publish_dtm,
        image = source.image,
        video = source.video,
        url = source.url
WHEN NOT MATCHED THEN
INSERT (tweet_message_id, tweeter_account_id, content,
publish_dtm, image, video, url)
VALUES (source.tweet_message_id, source.tweeter_account_id,
            source.content,
            source.publish_dtm, source.image, source.video,
            source.url);


SELECT * FROM car.tweet WHERE tweet_message_id = 'T000000003';


P4.5

CREATE TABLE car.tweet_shared ( 
tweet_message_id VARCHAR(64) PRIMARY KEY, 
tweeter_account_id VARCHAR(64) REFERENCES  car.customer(tweeter_account_id),
content TEXT,
publish_dtm TIMESTAMP(6),
image BYTEA,
video VARCHAR(100),
url VARCHAR(100));

TRUNCATE car.tweet;

INSERT INTO car.tweet (
tweet_message_id, tweeter_account_id, content, publish_dtm, image, video, url)
VALUES (
'T000000001', '@thomassbright',
 'Excited to share our latest electric car model!',
 '2023-08-03 12:00:00.000000', NULL, NULL, NULL);

INSERT INTO car.tweet (
tweet_message_id, tweeter_account_id, content, publish_dtm, image, video, url)
VALUES (
'T000000002', '@thomassbright',
 'Advanced Table Synchronization!',
 '2023-09-01 10:22:00.000000', NULL,
 'https://www.youtube.com/watch?v=T000000002',
 'https://twitter.com/your_username/status/T000000002');

INSERT INTO car.tweet (
tweet_message_id, tweeter_account_id, content, publish_dtm, image, video, url)
VALUES (
'T000000003', '@thomassbright',
'let us check the result!',
 '2023-09-02 11:22:00.000000', NULL,
 'https://www.youtube.com/watch?v=T000000003',
 'https://twitter.com/your_username/status/T000000003');

INSERT INTO car.tweet_shared (
tweet_message_id, tweeter_account_id, content, publish_dtm, image, video, url)
SELECT
    source.tweet_message_id,
    source.tweeter_account_id,
    source.content,
    source.publish_dtm,
    source.image,
    source.video,
source.url
FROM car.tweet source
ON CONFLICT (tweet_message_id) DO UPDATE
SET
tweeter_account_id = excluded.tweeter_account_id, content = excluded.content,
publish_dtm = excluded.publish_dtm,
image = excluded.image,
video = excluded.video,
url = excluded.url;

DELETE FROM car.tweet_shared target
WHERE NOT EXISTS (SELECT 1 FROM car.tweet source WHERE target.tweet_message_id = source.tweet_message_id);

SELECT * FROM car.tweet;

SELECT * FROM car.tweet_shared;

DELETE FROM car.tweet WHERE tweet_message_id = 'T000000001';

UPDATE car.tweet SET
publish_dtm = '2023-09-03 10:22:00.000000',
content = 'Advanced Table Synchronization – Updated!'
WHERE tweet_message_id = 'T000000002';

INSERT INTO car.tweet_shared (
tweet_message_id, tweeter_account_id, content, publish_dtm, image,
video, url)
SELECT
    source.tweet_message_id,
    source.tweeter_account_id,
    source.content,
    source.publish_dtm,
    source.image,
    source.video,
source.url
FROM car.tweet source
ON CONFLICT (tweet_message_id) DO UPDATE
SET
tweeter_account_id = excluded.tweeter_account_id, content = excluded.content,
publish_dtm = excluded.publish_dtm,
image = excluded.image,
video = excluded.video,
url = excluded.url;

DELETE FROM car.tweet_shared target
WHERE NOT EXISTS (
SELECT 1
FROM car.tweet source
WHERE target.tweet_message_id = source.tweet_message_id
);

SELECT * FROM car.tweet;

SELECT * FROM car.tweet_shared;



P4.6

BEGIN;

INSERT INTO car.order_header (order_no, customer_id, order_dtm, delivery_address_1, discount_rate, order_net_total)
VALUES ('O00000002', 'C230000001', '2023-08-15 14:00:00', '456 Elm St', 0.05, 113999.97);

INSERT INTO car.order_detail (
order_no, product_id, qty, unit_price, amount) 
VALUES ('O00000002', 'P00000001', 3, 39999.99, 119999.97);

COMMIT;

SELECT * FROM car.order_detail;

SELECT order_no, customer_id, order_dtm, delivery_address_1 FROM car.order_header;



P4.7

BEGIN; -- Start the transaction

UPDATE car.customer
SET address_1 = '789 Oak St' WHERE customer_id = 'C230000001';

UPDATE car.order_header
SET delivery_address_1 = '789 Oak St' WHERE order_no = 'O00000002';

COMMIT;

SELECT customer_id, address_1 FROM car.customer;

SELECT order_no, customer_id, delivery_address_1 FROM car.order_header WHERE order_no = 'O00000002';



P4.8

TRUNCATE t6;



P4.9

TRUNCATE t7 CASCADE; 
TRUNCATE t6 CASCADE;


P4.10

CREATE OR REPLACE FUNCTION prevent_null_content()
RETURNS TRIGGER AS $$
BEGIN
    IF NEW.content IS NULL THEN
        RAISE EXCEPTION 'Content cannot be null';
END IF;
RETURN NEW;
END;
$$ LANGUAGE plpgsql;


CREATE TRIGGER check_content_before_insert BEFORE INSERT ON car.tweet FOR EACH ROW EXECUTE FUNCTION prevent_null_content();

CREATE OR REPLACE FUNCTION prevent_null_content_update()
RETURNS TRIGGER AS $$
BEGIN
    IF NEW.content IS NULL THEN
        RAISE EXCEPTION 'Content cannot be set to null';
END IF;
RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER check_content_before_update BEFORE UPDATE ON car.tweet FOR EACH ROW EXECUTE FUNCTION prevent_null_content_update();

INSERT INTO car.tweet( tweet_message_id, tweeter_account_id, content, publish_dtm, image, video, url)
VALUES ('T000000001', '@user123', NULL, '2023-08-05 15:00:00', NULL, NULL, 'https://twitter.com/user123/status/123456');

SELECT * FROM car.tweet;

UPDATE car.tweet
SET content = NULL
WHERE tweet_message_id = 'T000000002';



P5.1

SELECT c.customer_id, c.first_name, c.last_name, SUM(oh.order_net_total) AS total_amount
FROM car.customer c
JOIN car.order_header oh ON c.customer_id = oh.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name;



P5.2

INSERT INTO car.product (product_id, product_name, sku, origin, color, category_id, price)
VALUES ('P00000002', 'Classic Watch', 'S0002-12345', 'Switzerland', 'Silver', 'CT000001', 599.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000003', 'Leather Bag', 'S0003-67890', 'Italy', 'Brown',
'CT000003', 249.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000004', 'Wireless Headphones', 'S0004-56789', 'USA', 'Black',
'CT000004', 149.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000005', 'Smartphone', 'S0005-23456', 'China', 'Gold',
'CT000001', 699.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000006', 'Laptop', 'S0006-34567', 'USA', 'Silver', 'CT000001',
999.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000007', 'Sports Shoes', 'S0007-45678', 'Germany', 'Blue',
'CT000001', 89.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000008', 'HD Television', 'S0008-78901', 'Japan', 'Black',
'CT000001', 799.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000009', 'Designer Sunglasses', 'S0009-89012', 'Italy',
'Brown', 'CT000001', 199.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000010', 'Fitness Tracker', 'S0010-90123', 'USA', 'Black',
'CT000001', 49.99);

INSERT INTO car.product (product_id, product_name, sku, origin, color,
category_id, price)
VALUES ('P00000011', 'Coffee Maker', 'S0011-01234', 'Switzerland',
'Silver', 'CT000001', 79.99);

SELECT p.category_id,
MAX(p.price::NUMERIC) AS max_price, 
MIN(p.price::NUMERIC) AS min_price, 
AVG(p.price::NUMERIC) AS avg_price, COUNT(product_id),
VARIANCE(p.price::NUMERIC) AS variance_price, 
STDDEV(p.price::NUMERIC) AS stddve_price, 
STDDEV_POP(p.price::NUMERIC) AS stddve_pop_price, 
STDDEV_SAMP(p.price::NUMERIC) AS stddve_samp_price
FROM car.product p GROUP BY p.category_id ORDER BY p.category_id;




P5.3

SELECT
SUM(amount) AS total_amount,
REGR_COUNT(qty, amount) AS num_valid_rows, 
REGR_AVGX(qty, amount) AS regr_avg_qty, 
REGR_AVGY(qty, amount) AS regr_avg_amount, 
REGR_SLOPE(qty, amount) AS regr_slope, 
|REGR_INTERCEPT(qty, amount) AS regr_intercept, 
REGR_R2(qty, amount) AS regr_r_squared, 
REGR_SXX(qty, amount) AS regr_sum_squares_x, 
REGR_SYY(qty, amount) AS regr_sum_squares_y, 
REGR_SXY(qty, amount) AS regr_sum_products_xy, 
VAR_POP(amount) AS var_pop_amount, 
VAR_SAMP(amount) AS var_samp_amount,
CORR(qty, amount) AS correlation_qty_amount, COVAR_POP(qty, amount) AS covar_pop_qty_amount, COVAR_SAMP(qty, amount) AS covar_samp_qty_amount
FROM car.order_detail;



P5.4

SELECT
p.product_id,
p.product_name,
p.price,
p.sku,
p.category_id,
c.description AS category_description, ARRAY_AGG(cd.designer) AS designers, STRING_AGG(cd.designer, ', ') AS concatenated_designers, BOOL_AND(p.price::numeric > 0) AS all_positive_prices, BOOL_OR(p.price::numeric > 100) AS any_price_above_100, EVERY(p.price::numeric > 50) AS all_prices_above_50
FROM car.product p
JOIN car.category c ON p.category_id = c.category_id
JOIN car.category_designer cd ON p.category_id = cd.category_id
WHERE p.product_id = 'P00000001'
GROUP BY p.product_id, p.product_name, p.price, p.sku, p.category_id, c.description;


P5.5

SELECT oh.order_no, oh.order_net_total
FROM car.order_header oh
WHERE oh.order_net_total::numeric > (SELECT AVG(order_net_total::numeric) FROM car.order_header);



P5.6

WITH OrderCounts AS (
SELECT customer_id, COUNT(*) AS order_count FROM car.order_header
GROUP BY customer_id
)
SELECT c.customer_id, c.first_name, c.last_name, COALESCE(oc.order_count, 0) AS order_count
FROM car.customer c
LEFT JOIN OrderCounts oc ON c.customer_id = oc.customer_id;



P5.7

INSERT INTO car.customer (customer_id, title, first_name, middle_name, last_name, email, phone, address_1, address_2, address_3, address_4, city, country, postal_code, tweeter_account_id)
VALUES
('C00000002', 'Ms.', 'Jane', '', 'Johnson', 'jane@example.com', '+9876543210', '456 Elm St', '', '', '', 'Townsville', 'Countryland', '54321', '@janejohnson'),
('C00000003', 'Dr.', 'Michael', '', 'Williams', 'michael@example.com', '+1122334455', '789 Oak St', '', '', '', 'Villagetown', 'Countryland', '67890', '@drmike'),
('C00000004', 'Prof.', 'Emily', '', 'Brown', 'emily@example.com', '+5544332211', '101 Pine St', '', '', '', 'Citytown', 'Countryland', '45678', '@profemily'),
('C00000005', 'Mrs.', 'Daniel', '', 'Miller', 'daniel@example.com', '+3344556677', '222 Maple St', '', '', '', 'Suburbville', 'Countryland', '98765', '@mrsdaniel');

INSERT INTO car.category (category_id, description) VALUES
    ('CT000002', 'Car Charger'),
    -- Add 3 more records with different categories
    ('CT000003', 'Battery'),
    ('CT000004', 'Accessory'),
    ('CT000005', 'Cleaning Kid');

INSERT INTO car.product (product_id, product_name, sku, origin, color, category_id, price)
VALUES
    ('P00000002', 'Quick Charge', 'SKU002', 'China', 'Blue', 'CT000002', '$699.99'),
    -- Add 3 more records with different products
    ('P00000003', 'Super Battery Pack', 'SKU003', 'Italy', 'Brown', 'CT000003',
'$19999.99'),
    ('P00000004', 'Car Cam', 'SKU004', 'UK', 'Various', 'CT000004', '$399.99'),
    ('P00000005', 'Easy Clean', 'SKU005', 'France', 'Red', 'CT000005', '$69.99');

INSERT INTO car.category_designer (category_id, designer) VALUES
    ('CT000002', 'Peter'),
    -- Add 3 more records with different designers
    ('CT000003', 'Thomas'),
    ('CT000004', 'Eddie'),
    ('CT000005', 'Gary');

INSERT INTO car.order_header (order_no, customer_id, order_dtm, delivery_address_1, discount_rate, order_net_total)
VALUES
('OR00000001', 'C00000001', '2023-08-01', '123 Main St', 0.1, (4*39999.99) - (4*39999.99)* 0.1), ('OR00000002', 'C00000002', '2023-08-02', '456 Elm St', 0.05, (5*699.99) - (5*699.99) * 0.05), ('OR00000003', 'C00000003', '2023-08-03', '789 Oak St', 0.2, (1*19999.99) - (1*19999.99) * 0.2), ('OR00000004', 'C00000004', '2023-08-04', '101 Pine St', 0.15, (3*399.99) - (3*399.99) * 0.15), ('OR00000005', 'C00000005', '2023-08-05', '222 Maple St', 0.1, (2*69.99) - (2*69.99) * 0.1);

INSERT INTO car.order_detail (order_no, product_id, qty, unit_price, amount) VALUES
    ('OR00000001', 'P00000001', 4, 39999.99, 159999.96),
    ('OR00000002', 'P00000002', 5, 699.99, 3499.95),
    ('OR00000003', 'P00000003', 1, 19999.99, 19999.99),
    ('OR00000004', 'P00000004', 3, 399.99, 1199.97),
    ('OR00000005', 'P00000005', 2, 69.99, 139.98);


SELECT c.customer_id, c.first_name, c.last_name, oh.order_no, SUM(oh.order_net_total)
OVER (PARTITION BY c.customer_id
ORDER BY oh.order_no) AS cumulative_total
FROM car.customer c
JOIN car.order_header oh ON c.customer_id = oh.customer_id WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
ORDER BY c.customer_id, oh.order_no;

SELECT DISTINCT p.category_id,
SUM(od.amount) OVER (PARTITION BY p.category_id) AS
cumulative_total_by_category
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id JOIN car.order_header oh ON od.order_no = oh.order_no WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
ORDER BY p.category_id;

SELECT DISTINCT cd.designer, SUM(od.amount)
OVER (PARTITION BY cd.designer ORDER BY cd.designer) AS
cumulative_total_by_designer
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category_designer cd ON p.category_id = cd.category_id JOIN car.order_header oh ON od.order_no = oh.order_no
WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
ORDER BY cd.designer;



P5.8

INSERT INTO car.order_header (order_no, customer_id, order_dtm, delivery_address_1, discount_rate, order_net_total)
VALUES
('2200000001', 'C00000001', '2022-07-01', '123 Main St', 0.1, (5 * 39999.99) - (5 * 39999.99) * 0.1),
('2200000002', 'C00000002', '2022-07-02', '456 Elm St', 0.05, (2 * 699.99) - (2 * 699.99) * 0.05),
('2200000003', 'C00000003', '2023-07-03', '789 Oak St', 0.2, (4 * 19999.99) - (4 * 19999.99) * 0.2),
('2200000004', 'C00000004', '2022-07-04', '101 Pine St', 0.15, (1 * 399.99) - (1 * 399.99) * 0.15),
('2200000005', 'C00000005', '2022-07-05', '222 Maple St', 0.1, (1 * 69.99) - (1 * 69.99) * 0.1);

INSERT INTO car.order_detail (order_no, product_id, qty, unit_price, amount)
VALUES
    ('2200000001', 'P00000001', 3, 39999.99, 119999.97),
    ('2200000002', 'P00000002', 2, 699.99, 1399.98),
    ('2200000003', 'P00000003', 4, 19999.99, 79999.96),
    ('2200000004', 'P00000004', 1, 399.99, 399.99),
    ('2200000005', 'P00000005', 1, 69.99, 69.99);


SELECT
p.product_name, EXTRACT(YEAR FROM oh.order_dtm) AS order_year, SUM(od.amount) AS total_sales,
LAG(SUM(od.amount)) OVER (PARTITION BY p.category_id ORDER BY
EXTRACT(YEAR FROM oh.order_dtm)) AS previous_year_sales, LEAD(SUM(od.amount)) OVER (PARTITION BY p.category_id ORDER BY
EXTRACT(YEAR FROM oh.order_dtm)) AS next_year_sales FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id JOIN car.order_header oh ON od.order_no = oh.order_no GROUP BY EXTRACT(YEAR FROM oh.order_dtm), p.product_id ORDER BY p.product_id, order_year;



P5.9

SELECT designer, total_sales, ROW_NUMBER() OVER (ORDER BY total_sales DESC) AS sales_rank
FROM (
    SELECT cd.designer, SUM(od.amount) AS total_sales
    FROM car.order_header oh
    JOIN car.order_detail od ON oh.order_no = od.order_no
    JOIN car.product p ON od.product_id = p.product_id
    JOIN car.category_designer cd ON p.category_id = cd.category_id
    WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
GROUP BY cd.designer ) AS designer_sales ORDER BY sales_rank;



P5.10

SELECT
p.product_name,
SUM(od.amount) AS total_sales,
RANK() OVER (ORDER BY SUM(od.amount) DESC) AS sales_rank, DENSE_RANK() OVER (ORDER BY SUM(od.amount) DESC) AS dense_sales_rank
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category_designer cd ON p.category_id = cd.category_id JOIN car.order_header oh ON od.order_no = oh.order_no
WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
GROUP BY p.product_name
ORDER BY sales_rank;



P5.11

SELECT DISTINCT ON (cd.designer) cd.designer, FIRST_VALUE(oh.order_dtm) OVER (PARTITION BY cd.designer
ORDER BY oh.order_dtm) AS first_order_date, LAST_VALUE(oh.order_dtm) OVER (PARTITION BY cd.designer
ORDER BY oh.order_dtm ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS last_order_date,
SUM(od.amount) OVER (PARTITION BY cd.designer) AS total_amount
FROM car.order_header oh
JOIN car.order_detail od ON oh.order_no = od.order_no
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category_designer cd ON p.category_id = cd.category_id WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
ORDER BY cd.designer, last_order_date;


P5.12

SELECT p.product_name, EXTRACT(YEAR FROM oh.order_dtm) AS order_year,
SUM(od.amount) AS total_sales,
NTILE(3) OVER (PARTITION BY EXTRACT(YEAR FROM oh.order_dtm) ORDER BY
SUM(od.amount) DESC) AS sales_quartile
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id
JOIN car.order_header oh ON od.order_no = oh.order_no WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
GROUP BY p.product_name, EXTRACT(YEAR FROM oh.order_dtm) ORDER BY sales_quartile, total_sales DESC;

SELECT p.product_name, EXTRACT(YEAR FROM oh.order_dtm) AS order_year, SUM(od.amount) AS total_sales,
NTILE(4) OVER (PARTITION BY EXTRACT(YEAR FROM oh.order_dtm) ORDER BY
SUM(od.amount) DESC) AS sales_quartile
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id
JOIN car.order_header oh ON od.order_no = oh.order_no WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
GROUP BY p.product_name, EXTRACT(YEAR FROM oh.order_dtm) ORDER BY sales_quartile, total_sales DESC;



P5.13

SELECT p.product_name, EXTRACT(YEAR FROM oh.order_dtm) AS order_year, SUM(od.amount) AS total_sales,
PERCENT_RANK() OVER (PARTITION BY EXTRACT(YEAR FROM oh.order_dtm)
ORDER BY SUM(od.amount)) AS percent_rank,
CUME_DIST() OVER (PARTITION BY EXTRACT(YEAR FROM oh.order_dtm) ORDER
BY SUM(od.amount)) AS cume_dist
FROM car.order_detail od
JOIN car.product p ON od.product_id = p.product_id
JOIN car.order_header oh ON od.order_no = oh.order_no WHERE EXTRACT(YEAR FROM oh.order_dtm) = 2023
GROUP BY p.product_name, EXTRACT(YEAR FROM oh.order_dtm) ORDER BY order_year, percent_rank;



P5.14

SELECT
    c.city,
c.country,
ct.description AS category, cd.designer,
SUM(od.amount) AS total_sales_amount
FROM car.order_detail od
JOIN car.order_header oh ON od.order_no = oh.order_no
JOIN car.customer c ON oh.customer_id = c.customer_id
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category ct ON p.category_id = ct.category_id
JOIN car.category_designer cd ON ct.category_id = cd.category_id GROUP BY c.city, c.country, ct.description, cd.designer
ORDER BY c.country, c.city, ct.description, cd.designer;




P5.15

SELECT
    c.city,
c.country,
ct.description AS category, cd.designer,
SUM(od.amount) AS total_sales_amount
FROM car.order_detail od
JOIN car.order_header oh ON od.order_no = oh.order_no
JOIN car.customer c ON oh.customer_id = c.customer_id
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category ct ON p.category_id = ct.category_id
JOIN car.category_designer cd ON ct.category_id = cd.category_id GROUP BY
ROLLUP ( c.city, c.country, ct.description, cd.designer) ORDER BY c.country, c.city, ct.description, cd.designer;



P5.16

SELECT
    c.country,
c.city,
ct.description AS category, SUM(od.amount) AS total_sales_amount
FROM    car.order_detail od
JOIN    car.order_header oh ON od.order_no = oh.order_no
JOIN    car.customer c ON oh.customer_id = c.customer_id
JOIN    car.product p ON od.product_id = p.product_id
JOIN    car.category ct ON p.category_id = ct.category_id
JOIN
car.category_designer cd ON ct.category_id = cd.category_id
GROUP BY
GROUPING SETS (c.city, c.country, ct.description)
ORDER BY
    c.country, c.city, ct.description;



P5.17

SELECT
    c.country, c.city, ct.description AS category,
    SUM(od.amount) AS total_sales_amount
FROM car.order_detail od
JOIN car.order_header oh ON od.order_no = oh.order_no
JOIN car.customer c ON oh.customer_id = c.customer_id
JOIN car.product p ON od.product_id = p.product_id
JOIN car.category ct ON p.category_id = ct.category_id
JOIN car.category_designer cd ON ct.category_id = cd.category_id GROUP BY CUBE (c.city, c.country, ct.description)
ORDER BY c.country, c.city, ct.description;



P5.18

CREATE TABLE car.tweet_comment (
    comment_id VARCHAR(64),
    comment_dtm TIMESTAMP(6),
    comment JSON,
    tweet_message_id VARCHAR(64) REFERENCES car.tweet(tweet_message_id));


INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES
    ('tweet001', '@thomassbright', 'Excited about our new product launch! #innovation', '2023-07-01 10:00:00.000000'),
    ('tweet002', '@thomassbright', 'Check out the features of our Super Battery Pack. #technology', '2023-07-02 12:30:00.000000'),
    ('tweet003', '@thomassbright', 'Thrilled to see the positive reviews for our latest product. #customerfeedback', '2023-07-03 15:45:00.000000'),
    ('tweet004', '@thomassbright', 'Join us for an interactive webinar on our new products. #webinar', '2023-07-04 09:15:00.000000'),
    ('tweet005', '@thomassbright', 'Our Super Battery Pack is now available for purchase! #productlaunch', '2023-07-05 11:30:00.000000'),
    ('tweet006', '@thomassbright', 'Exciting times ahead as we expand our product lineup. #growth', '2023-07-06 14:00:00.000000'),
    ('tweet007', '@thomassbright', 'Stay tuned for a special discount on our products. #specialoffer', '2023-07-07 16:20:00.000000'),
    ('tweet008', '@thomassbright', 'Thank you to all our loyal customers for your support! #gratitude', '2023-07-08 18:45:00.000000'),
    ('tweet009', '@thomassbright', 'Learn how our Super Battery Pack is changing the industry. #innovation', '2023-07-09 20:10:00.000000'),
    ('tweet010', '@thomassbright', 'Visit our website to explore the full range of our products. #website', '2023-07-10 22:30:00.000000');

INSERT INTO car.tweet_comment (comment_id, comment_dtm, comment, tweet_message_id)
VALUES
    ('comment006', '2023-09-02 11:30:00.000000', '{"text": "Looking forward to the results!"}', 'T000000003'),
    ('comment007', '2023-09-03 12:00:00.000000', '{"text": "Thanks for the update!"}', 'T000000002'),
    ('comment008', '2023-07-01 10:30:00.000000', '{"text": "This is awesome!"}', 'tweet001'),
    ('comment009', '2023-07-02 13:00:00.000000', '{"text": "I want one too!"}', 'tweet002'),
    ('comment010', '2023-07-03 16:30:00.000000', '{"text": "Impressive product!, I ordered Super Battery Pack"}', 'tweet002'),
    ('comment011', '2023-07-03 16:30:00.000000', '{"text": "Impressive product!, I ordered Super Battery Pack"}', 'tweet002');


P5.19

SELECT comment_dtm, c.comment->>'text' as comments FROM car.tweet_comment c;

SELECT comment_dtm, c.comment->>'text' as comments FROM car.tweet_comment c
WHERE LOWER(c.comment->>'text') LIKE '%battery%';

SELECT p.product_id FROM car.product p
JOIN car.tweet_comment c ON POSITION('battery' IN LOWER(p.product_name)) > 0 WHERE LOWER(c.comment->>'text') LIKE '%battery%';

SELECT
  oh.order_dtm,
  p.product_name,
  od.product_id,
  od.amount
FROM car.order_header oh
JOIN car.order_detail od ON oh.order_no = od.order_no JOIN car.product p ON od.product_id = p.product_id WHERE od.product_id IN (
SELECT p.product_id
FROM car.product p
JOIN car.tweet_comment c ON POSITION('battery' IN
LOWER(p.product_name)) > 0
WHERE LOWER(c.comment->>'text') LIKE '%battery%');

SELECT
     tc.comment_text AS tweet_comment, tc.comment_dtm,
oh.order_dtm, p.product_name, od.product_id, od.amount FROM car.order_header oh
JOIN car.order_detail od ON oh.order_no = od.order_no
JOIN car.product p ON od.product_id = p.product_id
JOIN (
SELECT DISTINCT p.product_id, c.comment->>'text' AS comment_text, c.comment_dtm
FROM car.product p
JOIN car.tweet_comment c ON POSITION('battery' IN LOWER(p.product_name)) > 0
WHERE LOWER(c.comment->>'text') LIKE '%battery%' ) tc ON tc.product_id = od.product_id
WHERE od.product_id IN (
SELECT p.product_id
FROM car.product p
JOIN car.tweet_comment c ON POSITION('battery' IN
LOWER(p.product_name)) > 0
WHERE LOWER(c.comment->>'text') LIKE '%battery%');


P5.21

SELECT regexp_replace(url, E'[^https?://[^\s]+]', '', 'g') AS full_urls FROM car.tweet
WHERE url ~ E'https?://[^\s]+';


P5.22

INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES ('T20230907123456789', '@thomassbright', 'I have compared the products and found this one is interesting, feel free to contact me by email if you want know my comparison result, my email is thomas@mythomasbrighttest.com.', '2023-08-01 12:00:00');

SELECT
REGEXP_MATCHES(content, E'[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}', 'g') AS email_addresses
FROM car.tweet WHERE content ~ E'[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,4}';



P5.23

SELECT comment_id, array_length(regexp_split_to_array(json_extract_path_text(comment, 'text')::text, E'\\s+'), 1) AS word_count
FROM car.tweet_comment
ORDER BY array_length(regexp_split_to_array(json_extract_path_text(comment, 'text')::text, E'\\s+'), 1) DESC;



P5.24

WITH tweet_word_counts AS ( SELECT tweet_message_id,
ARRAY_LENGTH(REGEXP_SPLIT_TO_ARRAY (content, E'\\s+'), 1)
AS word_count FROM car.tweet
)
SELECT tweet_message_id, word_count FROM tweet_word_counts
ORDER BY word_count DESC;


WITH tweet_word_counts AS ( SELECT tweet_message_id,
ARRAY_LENGTH(REGEXP_SPLIT_TO_ARRAY (content, E'\\s+'), 1)
AS word_count FROM car.tweet
)
SELECT tweet_message_id, word_count FROM tweet_word_counts
ORDER BY word_count DESC
LIMIT 10;


P5.25

SELECT * FROM car.tweet WHERE content ~ E'#\\w+';


P5.26

SELECT * FROM car.tweet WHERE content ~ E'@[A-Za-z0-9_]+';


P5.27

SELECT tweet_message_id, comment->>'text' AS comment
FROM car.tweet_comment WHERE TO_TSVECTOR('english', comment->>'text') @@ TO_TSQUERY('Super');


SELECT tweet_message_id, comment->>'text' AS comment FROM car.tweet_comment
WHERE comment::text ILIKE '%Super%';



P5.28

INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES ('tweet011', '@thomassbright', E'\\x48656c6c6f20776f726c6421', '2023-08-01 12:00:00');

INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES ('tweet012', '@thomassbright', E'\\x5468697320697320616e6f7468657220747765657421', '2023-08-02 12:00:00');

INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES ('tweet013', '@thomassbright', 'This is a regular text tweet.', '2023-08-03 12:00:00');

INSERT INTO car.tweet (tweet_message_id, tweeter_account_id, content, publish_dtm)
VALUES ('tweet014', '@thomassbright', E'\\x48657861646563696d616c20646174612069732068657821', '2023-08-04 12:00:00');

SELECT tweet_message_id, tweeter_account_id, content FROM car.tweet WHERE content ~ E'\\\\x[0-9A-Fa-f]+';


P5.29

SELECT date_trunc('hour', publish_dtm) AS tweet_hour, count(*) AS tweet_count
FROM car.tweet
GROUP BY tweet_hour
ORDER BY tweet_hour;


P5.30

SELECT
COUNT(*) AS total_tweets,
SUM(CASE WHEN image IS NOT NULL THEN 1 ELSE 0 END)
AS tweets_with_images,
SUM(CASE WHEN image IS NULL THEN 1 ELSE 0 END)
AS tweets_without_images FROM car.tweet;



P5.31

SELECT tweeter_account_id, COUNT(*) AS tweet_count FROM car.tweet
GROUP BY tweeter_account_id
ORDER BY tweet_count DESC;



P5.32

SELECT tweet_message_id, content FROM car.tweet;

SELECT product_name FROM car.product;

TRUNCATE car.tweet_comment;

INSERT INTO car.tweet_comment (comment_id, comment_dtm, comment, tweet_message_id)
SELECT
'comment_id_for_tweet_' || tweet_message_id, current_timestamp, -- or the desired timestamp JSON_BUILD_OBJECT('text', 'This tweet mentioned product: ' ||
product_name),
     tweet_message_id
FROM car.tweet AS tweet
JOIN car.product AS product
ON tweet.content ILIKE '%' || product.product_name || '%';

SELECT * FROM car.tweet_comment;



P5.33

CREATE TABLE space.dw_orders AS
SELECT
    t.trip_id,
    c.customer_id,
    t.destination,
    t.departure_from,
    t.departure_dtm AS travel_departure_dtm,
    t.return_dtm AS travel_return_dtm,
    t.price AS travel_price,
    o.order_no,
    o.order_dtm AS order_date,
    o.delivery_address_1 AS delivery_address,
    o.discount_rate,
    o.order_net_total AS order_total
FROM space.space_travel_schedule t
JOIN space.space_trip s ON t.trip_id = s.trip_id
JOIN car.customer c ON s.customer_id = c.customer_id
JOIN car.order_header o ON c.customer_id = o.customer_id;

CREATE INDEX dw_orders_idx_01 ON space.dw_orders (order_no, customer_id);

SELECT * FROM space.dw_orders;

COPY ( SELECT
        t.trip_id,
        c.customer_id,
        t.destination,
        t.departure_from,
        t.departure_dtm AS travel_departure_dtm,
        t.return_dtm AS travel_return_dtm,
        t.price AS travel_price,
        o.order_no,
        o.order_dtm AS order_date,
        o.delivery_address_1 AS delivery_address,
        o.discount_rate,
        o.order_net_total AS order_total
FROM space.space_travel_schedule t
JOIN space.space_trip s ON t.trip_id = s.trip_id
JOIN car.customer c ON s.customer_id = c.customer_id
JOIN car.order_header o ON c.customer_id = o.customer_id)
TO 'C:\Users\tony\dw_order.csv' WITH CSV HEADER;



P5.34

SELECT
   trip_id, destination, departure_from,
CASE
WHEN price::numeric >= 1000000 THEN 'Expensive' WHEN price::numeric >= 500000 THEN 'Moderate' ELSE 'Affordable'
END AS price_category
FROM space.space_travel_schedule;

SELECT
order_no,
COALESCE(delivery_address_1, delivery_address_2, delivery_address_3, delivery_address_4, 'N/A') AS delivery_address
FROM car.order_header
LIMIT 1;

SELECT
order_no, delivery_address_1, delivery_address_2, delivery_address_3, delivery_address_4
FROM car.order_header LIMIT 1;



P5.35

SELECT
    p.product_id,
    p.product_name,
    p.sku,
    p.origin,
    p.color,
    p.category_id,
    p.price,
    SUM(CASE WHEN od.qty IS NOT NULL THEN od.qty ELSE 0 END) AS total_qty,
    SUM(CASE WHEN od.amount IS NOT NULL THEN od.amount ELSE 0 END) AS
total_amount
FROM car.product p
LEFT JOIN car.order_detail od ON p.product_id = od.product_id GROUP BY
    p.product_id,
    p.product_name,
    p.sku,
    p.origin,
    p.color,
    p.category_id,
    p.price;


SELECT product_id, 'product_name' AS attribute, product_name AS value FROM car.product
UNION ALL
SELECT product_id, 'sku' AS attribute, sku AS value
FROM   car.product
UNION ALL
SELECT product_id, 'origin' AS attribute, origin AS value FROM car.product
UNION ALL
SELECT product_id, 'color' AS attribute, color AS value FROM car.product
UNION ALL
SELECT product_id, 'category_id' AS attribute, category_id AS value FROM car.product
UNION ALL
SELECT product_id, 'qty' AS attribute, qty::text AS value
FROM car.order_detail
WHERE qty IS NOT NULL
UNION ALL
SELECT product_id, 'amount' AS attribute, amount::text AS value FROM car.order_detail
WHERE amount IS NOT NULL;













