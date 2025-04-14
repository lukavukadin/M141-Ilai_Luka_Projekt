# Backpacker LB3 Migration: Projekt M141 - DB-Systeme in Betrieb nehmen

## Projektübersicht

In diesem Projekt geht es darum, die bestehende Access-Datenbank einer Jugendherberge auf ein leistungsfähigeres MySQL-Datenbankmanagementsystem zu migrieren. Die Aufgaben umfassen:
- Die Migration der Datenstruktur (DDL-Skripte) und der Daten (CSV-Dateien) von einer Access-Datenbank auf MySQL.
- Die Konsolidierung und Bereinigung der Daten nach dem Import.
- Die Migration der Datenbank auf ein Cloud-DBMS (z.B. MariaDB auf AWS), um sie in einer sicheren und skalierbaren Umgebung für den produktiven Betrieb bereitzustellen.

## Ziele des Projekts

1. **Migration der Datenbank** von einer Access-Datenbank zu MySQL.
2. **Konsolidierung und Bereinigung der Daten**, um Inkonsistenzen zu beheben.
3. **Testen der Performance und Sicherheit** der Datenbank sowohl lokal als auch in der Cloud.
4. **Cloud-Migration**, um die Daten in eine skalierbare und sichere Cloud-Datenbank zu überführen.
5. **Erstellung von Testprotokollen und Skripten**, die den gesamten Prozess dokumentieren.

## Projektstruktur

Die Projektdateien sind wie folgt organisiert:

- **DDL-Skripte**: Enthalten die Struktur der Datenbank, die auf MySQL übertragen wird.
- **CSV-Dateien**: Beinhaltet die Daten, die in die neue Datenbank importiert werden.
- **SQL-Skripte**: Dienen zum Testen der Migration und zur Bereinigung der Daten.
- **Testprotokolle**: Dokumentieren die Tests und Ergebnisse der Migration, sowohl lokal als auch in der Cloud.

## Setup-Anleitung

### Lokale MySQL-Datenbank einrichten

1. Installiere [XAMPP](https://www.apachefriends.org/index.html), um eine lokale MySQL-Datenbankumgebung zu haben.
2. Importiere die **DDL-Skripte** in eine neue MySQL-Datenbank.
3. Importiere die **CSV-Daten** in die entsprechenden Tabellen.

### Cloud-DBMS einrichten

1. Erstelle ein AWS-Konto und richte eine MariaDB-Datenbank in der Cloud ein.
2. Konfiguriere die Cloud-Datenbank und migriere die Daten von der lokalen MySQL-Datenbank.
3. Teste die Datenbank und stelle sicher, dass sie sicher und performativ läuft.

## Testen

- Führe die bereitgestellten Testskripte aus, um sicherzustellen, dass die Migration sowohl lokal als auch in der Cloud funktioniert.
- Überprüfe die Konsistenz der Daten und die korrekte Implementierung der Zugriffsberechtigungen gemäß der Zugriffsmatrix.

## Abschluss

Das Projekt wird bis zum **08. Mai 2025** abgeschlossen sein. Eine Demo der finalen Lösung wird ebenfalls bereitgestellt, um die funktionierende Migration und den produktiven Betrieb der Datenbank in der Cloud zu demonstrieren.

## Kontakt

Wenn du Fragen zum Projekt hast, kannst du dich an Ilai oder Luka unter Ilai.luise@edu.tbz.ch / luka.vukadin@edu.tbz.ch wenden.
