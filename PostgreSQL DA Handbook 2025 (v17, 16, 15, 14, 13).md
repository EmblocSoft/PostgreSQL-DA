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

