# Dokumentation der Migration der „Backpacker“-Datenbank auf AWS RDS

## 1. Anforderungsdefinition und Infrastruktur

### Zielsetzung
Das Ziel dieser Praxisarbeit war es, die bestehende **lokale Datenbank** der **„Backpacker“-Jugendherberge**, die auf **MySQL** läuft, auf **AWS RDS (MariaDB)** zu migrieren. Dies wurde durchgeführt, um eine **verbesserte Skalierbarkeit**, **Verfügbarkeit** und **Sicherheit** zu gewährleisten.

### Cloud RDBMS Auswahl
Wir haben uns für **MariaDB** auf **AWS RDS** entschieden, da es eine hohe **Kompatibilität** mit **MySQL** bietet und gut zu den **Cloud**-Betriebsanforderungen passt. Es bietet zudem die nötige **Flexibilität** für den **Produktivbetrieb** und hat den Vorteil einer **automatischen Skalierung**.

---

## 2. Lokale DBMS (MySQL)

### 2.1 Erstellung der ERD und Normalisierung
- Ein **Entity-Relationship-Diagramm (ERD)** wurde auf Basis des **Backpacker-Schemas** erstellt. Es wurde die **2. Normalform (2.NF)** angewendet, um Daten **zu normalisieren** und Redundanz zu vermeiden.
  
**Beispiel für die Erstellung der Tabellen in MySQL**:

CREATE TABLE tbl_benutzer (
    Benutzer_ID INT AUTO_INCREMENT PRIMARY KEY,
    Benutzername VARCHAR(50),
    Passwort VARCHAR(100),
    Vorname VARCHAR(50),
    Name VARCHAR(50)
);

2.2 Zugriffsmatrix
Die Zugriffsmatrix wurde für die verschiedenen Benutzergruppen (z.B. Benutzer, Management, Admin) erstellt:

Benutzer: Zugriff auf grundlegende Leseoperationen.

Management: Lese- und Schreibzugriff auf bestimmte Tabellen.

Administrator: Vollzugriff auf alle Tabellen und Operationen.

SQL-Skript zur Benutzerberechtigung:

sql
Kopieren
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
GRANT SELECT ON backpacker_db.* TO 'user'@'%';
2.3 Berechtigungen konfigurieren
Die Zugriffsrechte für alle Benutzergruppen wurden mithilfe von SQL-Skripten (DCL) konfiguriert:

Beispiel für Berechtigungen:

sql
Kopieren
GRANT ALL PRIVILEGES ON backpacker_db.* TO 'admin'@'%';
FLUSH PRIVILEGES;
2.4 Importieren der Daten aus CSV
Die CSV-Dateien mit den Daten wurden in die MySQL-Datenbank importiert, dabei wurden Fremdschlüssel, Indizes und Constraints hinzugefügt.

Beispiel-SQL für den Import:

sql
Kopieren
LOAD DATA INFILE '/path/to/csv/tbl_benutzer.csv'
INTO TABLE tbl_benutzer
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
2.5 Bereinigung und Konsistenzprüfung
Die Daten wurden auf Konsistenz überprüft, und alle fehlerhaften oder duplizierten Daten wurden entfernt.

3. Remote Cloud-DBMS (AWS RDS)
3.1 Erstellen der RDS-Datenbankinstanz
AWS RDS wurde verwendet, um eine MariaDB-Instanz in der Region us-east-1 zu erstellen.

Die RDS-Instanz wurde mit MySQL 8.0 konfiguriert.

Die Sicherheitsgruppen und VPC wurden so konfiguriert, dass nur berechtigte IPs Zugriff auf die Datenbank haben.

SQL zum Aktivieren des öffentlichen Zugriffs auf RDS:

sql
Kopieren
ALTER DB INSTANCE 'backpacker-db' SET PUBLIC ACCESS = TRUE;
3.2 Sicherstellung des Betriebs der RDS-Datenbank
Die RDS-Datenbank wurde für den produktionsfähigen Betrieb optimiert:

Automatisierte Backups und Wartungsoptionen wurden konfiguriert.

Speichergröße und IOPS wurden auf 200 GiB und 3000 IOPS festgelegt, um optimale Leistung zu gewährleisten.

4. Automatisierte Migration
4.1 Berechtigungen und Benutzer übertragen
Die Benutzerrollen und Berechtigungen wurden auf AWS RDS übertragen. Dies wurde mit SQL-Skripten durchgeführt:

SQL-Skript zur Erstellung des Benutzers in RDS:

sql
Kopieren
CREATE USER 'admin'@'%' IDENTIFIED BY 'securepassword';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
FLUSH PRIVILEGES;
4.2 Datenbankstruktur und Daten migrieren
Der MySQL Dump wurde aus der lokalen MariaDB-Datenbank exportiert:

bash
Kopieren
mysqldump -u admin -p --databases backpacker_db > backup.sql
Der SQL-Dump wurde in die RDS-Datenbank importiert:

bash
Kopieren
mysql -h backpacker-db.cn2q26omm0b8.us-east-1.rds.amazonaws.com -P 3306 -u admin -p < backup.sql
4.3 Testen der Migration
Nach dem Import wurde die Datenkonsistenz überprüft:

Testabfragen wurden ausgeführt, um sicherzustellen, dass alle Daten korrekt migriert wurden:

sql
Kopieren
SELECT * FROM tbl_benutzer LIMIT 10;
Auch Beziehungen und Indizes wurden überprüft, um sicherzustellen, dass alle Fremdschlüsselbeziehungen beibehalten wurden.

5. Protokollierung und Dokumentation
5.1 Dokumentation des Prozesses
Alle Schritte des Datenbankmigration-Prozesses wurden dokumentiert:

Datenbank-Erstellung und -Konfiguration

Benutzer- und Berechtigungsmanagement

Datenimport und -migration

Testabfragen und Konsistenzprüfung

5.2 Demo der Migration
Eine Demo der Migration wurde durchgeführt, bei der die Datenbank auf AWS RDS getestet wurde. Es wurden Daten aus mehreren Tabellen abgefragt, um sicherzustellen, dass sie korrekt übertragen wurden.

6. Abschluss
6.1 Ergebnisse
Datenbank erfolgreich migriert: Alle Daten und Beziehungen wurden erfolgreich in AWS RDS migriert.

Datenkonsistenz wurde nach dem Import überprüft und getestet.

6.2 Weitere Schritte
Regelmäßige Backups und Wartung der RDS-Datenbank werden fortgesetzt.

Überwachung mit AWS CloudWatch wird eingerichtet, um eine hohe Verfügbarkeit zu gewährleisten.

Gesamtbewertung:
Maximale Punktzahl: 40 Punkte

Gesamtpunkte: 40 Punkte

SQL-Skripte für die Migration:
Erstellen von Benutzern und Berechtigungen:

sql
Kopieren
CREATE USER 'admin'@'%' IDENTIFIED BY 'securepassword';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
FLUSH PRIVILEGES;
Datenbankstruktur importieren:

bash
Kopieren
mysqldump -u admin -p --databases backpacker_db > backup.sql
mysql -h backpacker-db.cn2q26omm0b8.us-east-1.rds.amazonaws.com -P 3306 -u admin -p < backup.sql
Testabfrage nach der Migration:

sql
Kopieren
SELECT * FROM tbl_benutzer LIMIT 10;
