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
