```
-- Erstellen der Benutzerrollen
CREATE ROLE Benutzer;
CREATE ROLE Management;

-- Benutzer 1 (Standard User) erstellen
CREATE USER Angela IDENTIFIED BY '1234';
GRANT Benutzer TO Angela;

-- Benutzer 2 (Manager) erstellen
CREATE USER Livia IDENTIFIED BY '1234';
GRANT Management TO Livia;

-- Benutzer 3 (Admin) erstellen
CREATE USER Peter IDENTIFIED BY '1234';
GRANT Management TO Peter;

-- Zuweisen von Tabellenrechten für Benutzer

-- Berechtigungen für den Benutzer
GRANT SELECT, INSERT, UPDATE ON tbl_personen TO Angela;
GRANT SELECT, INSERT, UPDATE ON tbl_buchung TO Angela;
GRANT SELECT, INSERT, UPDATE ON tbl_positionen TO Angela;

-- Berechtigungen für den Manager
GRANT SELECT, INSERT, UPDATE, DELETE ON tbl_positionen TO Livia;
GRANT SELECT, INSERT, UPDATE, DELETE ON tbl_buchung TO Livia;
GRANT SELECT, INSERT, UPDATE, DELETE ON tbl_land TO Livia;
GRANT SELECT, INSERT, UPDATE, DELETE ON tbl_leistung TO Livia;

-- Berechtigungen für den Admin
GRANT ALL PRIVILEGES ON tbl_personen TO Peter;
GRANT ALL PRIVILEGES ON tbl_benutzer TO Peter;
GRANT ALL PRIVILEGES ON tbl_buchung TO Peter;
GRANT ALL PRIVILEGES ON tbl_positionen TO Peter;
GRANT ALL PRIVILEGES ON tbl_land TO Peter;
GRANT ALL PRIVILEGES ON tbl_leistung TO Peter;

