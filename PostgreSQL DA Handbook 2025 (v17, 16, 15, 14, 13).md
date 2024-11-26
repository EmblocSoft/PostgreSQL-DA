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






















