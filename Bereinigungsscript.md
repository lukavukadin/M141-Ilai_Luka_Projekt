``` 
-- Vorname
SELECT * FROM tbl_personen 
WHERE Vorname NOT REGEXP '[A-Za-z]';

SELECT * FROM tbl_buchung 
WHERE Personen_FS IN (148, 486, 1394, 1721, 2183, 2521, 3429, 3756);

DELETE FROM tbl_buchung 
WHERE Buchungs_ID IN (101, 117, 548, 732);

START TRANSACTION;

DELETE FROM tbl_personen 
WHERE Personen_ID IN (148, 486, 1394, 1721, 2183, 2521, 3429, 3756);

COMMIT;

-- Titel
SELECT * FROM tbl_personen 
WHERE Titel NOT REGEXP '^(Herr|Frau|Herrn|Miss)$';

-- Name
SELECT * FROM tbl_personen 
WHERE Name REGEXP '[0-9]';

SELECT * FROM tbl_buchung 
WHERE Personen_FS IN (371, 915, 1031, 1808, 2406, 2950, 3066, 3843);

SELECT * FROM tbl_positionen 
WHERE Buchungs_FS IN (811, 812);

DELETE FROM tbl_positionen 
WHERE Buchungs_FS IN (811, 812);

DELETE FROM tbl_buchung 
WHERE Personen_FS = 1808;

DELETE FROM tbl_personen 
WHERE Personen_ID IN (371, 915, 1031, 1808, 2406, 2950, 3066, 3843);

-- Ort
SELECT * FROM tbl_personen;

SELECT * FROM tbl_personen 
WHERE Ort REGEXP '^(Zrich|Glcks|Kln|Schnengrund)';

START TRANSACTION;

UPDATE tbl_personen 
SET Ort = 'Glücksburg' 
WHERE Ort = 'Glcksburg';

UPDATE tbl_personen 
SET Ort = 'Schönengrund' 
WHERE Ort = 'Schnengrund';

UPDATE tbl_personen 
SET Ort = 'Köln' 
WHERE Ort = 'Kln';

UPDATE tbl_personen 
SET Ort = 'Zürich 2' 
WHERE Ort = 'Zrich 2';

COMMIT;

SELECT * FROM tbl_personen 
WHERE Ort REGEXP '^[0-9]';

SELECT * FROM tbl_positionen 
WHERE Buchungs_FS IN (6, 106, 162, 285, 305, 384, 402, 415, 431, 532, 543, 577, 599, 600, 601, 602, 605, 689, 744, 768, 816, 833, 851, 903, 913, 954, 970, 971);

SELECT * FROM tbl_buchung 
WHERE Personen_FS IN (7, 76, 80, 91, 159, 161, 279, 287, 313, 336, 340, 347, 547, 591, 595, 623, 659, 689, 690, 760, 808, 809, 818, 888, 937, 948, 978, 1000, 1006, 1014, 1020, 1057, 1102, 1111, 1119, 1160, 1263, 1373, 1441, 1443, 1451, 1469, 1514, 1525, 1531, 1536, 1543, 1546, 1611, 1633, 1676, 1732, 1757, 1765, 1812, 1828, 1849, 1857, 1928, 1939, 1980, 2000, 2010, 2042, 2088, 2106, 2111, 2115, 2126, 2194, 2196, 2314, 2322, 2348, 2371, 2375, 2382, 2582, 2626, 2630, 2658, 2694, 2724, 2725, 2795, 2843, 2844, 2853, 2923, 2972, 2983, 3013, 3035, 3041, 3049, 3055, 3092, 3137, 3146,_
