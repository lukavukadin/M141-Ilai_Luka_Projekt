# Dokumentation der Projektarbeit

## 1. Definition der Infrastruktur

### 1.1 Anforderungsdefinition
Die Aufgabenstellung beinhaltete die Bereinigung einer lokalen MySQL-Datenbank und deren Migration auf eine AWS Cloud-Datenbank. Zunächst haben wir die Datenbank auf einem lokalen Server eingerichtet und dann die Daten bereinigt. Abschließend haben wir das System in der Cloud mit den entsprechenden Sicherheitsvorkehrungen und Berechtigungen konfiguriert.

### 1.2 Evaluation Cloud RDBMS
Für das Projekt wurde MySQL als relationales Datenbankmanagementsystem (RDBMS) sowohl lokal als auch in der Cloud verwendet. Die Wahl fiel auf MySQL aufgrund seiner Verbreitung und der Verfügbarkeit als Managed Service auf AWS.

### 1.3 Link zu Repository/Datenpool
Der Link zum Repository und dem Datenpool wurde auf der Projektplattform bereitgestellt.

---

## 2. Lokale DBMS

### 2.1 Setup der lokalen Datenbank
Für das Projekt haben wir XAMPP verwendet, um MySQL lokal zu betreiben. Die Struktur der Datenbank wurde aus einer bereitgestellten DDL-Datei in phpMyAdmin importiert.

### 2.2 Datenbereinigung
Die Datenbank war mit Fehlern behaftet, die wir manuell und automatisiert bereinigt haben. Fehler wie Zahlen im Vornamen, fehlerhafte Orte und ungültige Daten wurden identifiziert und korrigiert.

#### Manuelle Bereinigung
Einige der fehlerhaften Datensätze wurden manuell mit Excel bearbeitet und anschließend wieder in die Datenbank importiert.

#### Automatisierte Bereinigung mit SQL-Skripten
Einige Fehler wurden mit SQL-Skripten automatisch korrigiert. Weitere Details und das vollständige Bereinigungsskript sind in der Datei [Bereinigungsscript.md](M141-Ilai_Luka_Projekt/Bereinigungsscript.md) zu finden.

---

## 3. Remote Cloud-DBMS

### 3.1 Setup der Cloud-Datenbank
Nach der Bereinigung der lokalen Datenbank haben wir die Daten auf AWS migriert. Zunächst mussten wir eine MySQL-Instanz auf AWS RDS (Relational Database Service) einrichten. Dabei haben wir eine Sicherheitsgruppe erstellt, die nur den Zugang über den SSH-Port 22 erlaubte.

### 3.2 Sicherstellung des Betriebs
Wir haben die MySQL-Instanz auf AWS gesichert, indem wir die notwendigen Konfigurationen für den produktiven Betrieb durchgeführt haben. Hierzu gehörten die Anpassung der Konfigurationsdateien und das Setzen von Berechtigungen.

### 3.3 Verbindung mit der Cloud-Datenbank
Wir haben MySQL Workbench verwendet, um eine Verbindung zu unserer AWS-Datenbank aufzubauen. Dafür haben wir den Endpoint der RDS-Instanz kopiert und uns mit den entsprechenden Zugangsdaten verbunden. Nach der Verbindung haben wir das SQL-Skript zur Erstellung der Datenbank, das wir ursprünglich in phpMyAdmin verwendet hatten, in MySQL Workbench eingefügt und ausgeführt.

---

## 4. Automatisierte Migration

### 4.1 Berechtigungen
Die Berechtigungen für die Benutzer wurden nach der Migration auf die Cloud-Datenbank automatisiert übertragen. Hierbei haben wir verschiedene Benutzerrollen erstellt und ihnen entsprechende Berechtigungen zugewiesen. Details zur Erstellung der Benutzer und der Zugriffsmatrix sind in der Datei [Zugriffsmatrix.md](M141-Ilai_Luka_Projekt/Zugriffsmatrix.md) zu finden.

## 5. Protokollierung
Die gesamten Schritte von der Bereinigung der lokalen Datenbank bis zur Migration auf AWS und der Einrichtung der Cloud-Datenbank wurden dokumentiert. Testprotokolle wurden erstellt und alle SQL-Skripte sind versioniert und im Repository verfügbar.

## 6. Abschluss und Demo
Im letzten Schritt haben wir eine Demo durchgeführt, bei der wir drei Benutzer in der AWS-Cloud-Datenbank erstellt haben. Die Demo beinhaltete die Demonstration des Zugriffs auf die Datenbank und die Ausführung von SQL-Abfragen. Die Demo dauerte 10-15 Minuten und wurde erfolgreich abgeschlossen.


