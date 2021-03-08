---
title: Chocolatey
date: 2021-03-08 10:59:31
tags: tools
---

Eine Paketverwaltung ermöglicht die komfortable Verwaltung von Software, die in Form von Programmpaketen vorliegt. Dazu gehören Installieren, Aktualisieren und Deinstallieren diese Pakete.

Typischerweise liegen diese Pakete in einem zentralen Repository. Änderungen, welche die Paketverwaltung zur Installation des Pakets vornehmen muss, werden von dieser aus dem Paket ausgelesen und umgesetzt. Erkennt die Paketverwaltung dabei, dass noch weitere Software für das Funktionieren benötigt wird (sogenannte Abhängigkeit, z. B. eine Programmbibliothek), aber noch nicht installiert ist, warnt sie entweder oder versucht, die fehlende Software mit den ihr zur Verfügung stehenden Mitteln, ebenfalls aus dem Repository, nachzuladen und vorweg zu installieren.

## Welche Paketverwaltungen gibt es?

Paketverwaltungen sind unter Linux der übliche Weg, um Software zu installieren. Hier seien folgende erwähnt:

- Debian Package Manager + Advanced Packaging Tool (APT) – für deb- oder RPM-basierte Linux-Distributionen
- NuGet – für Visual Studio
- gem – für Ruby-Pakete via RubyGems
- brew - für macOS
- emerge und Portage – für Gentoo
- das Ports-System unter BSD-Distributionen (z. B. FreeBSD, OpenBSD)
- npm – für Webentwicklung
- Chocolatey – ein freier Paketmanager für Windows-Betriebssysteme

## Chocolatey

Wir werden uns hier vorerst nur eines davon ansehen: [Chocolatey](https://chocolatey.org/). Es ist die einzige Paketverwaltung für Windows-Anwendungen aus der obigen Liste - und nimmt damit einen besonderen Platz ein. Technisch basiert sie auf NuGet.

Unter Linux ist die Installation von Software mittels Software-Repository der gängige Weg. Unter Windows wird üblicherweise eine Setup-Datei auf den Rechner übertragen und dort ausgeführt. Chocolatey automatisiert diesen Prozess. Somit ist es möglich, schnell mehrere Anwendungen zu installieren oder zu aktualisieren.

### Beispiel

Chocolatey lässt sich einfach [installieren](https://chocolatey.org/install) und wird dann über die PowerShell gestartet. Wir wollen als Beispiel Notepad++ installieren. Vorausgesetzt wird eine abgeschlossene Installation von Chocolatey, sonst geht logischerweise der Aufruf von ``choco.exe``nicht.

Wir benötigen die PowerShell. Da für die Installation Admin-Berechtigungen nötig sind, kann man diese gleich passend starten (Rechtsklick -> "als Adminsitrator ausführen").

{% code %}
choco.exe install notepadplusplus
{% endcode %}

## Pakete

Aktuell sind mehr als 8000 Pakete im der zentralen [Verzeichnis](https://chocolatey.org/packages) verfügbar. Um einen besseren Überblick zu bekommen, kann man die graphische Oberfläche mit Hilfe von ``choco.exe install chocolateygui`` nachinstallieren, um Pakete komfortabel verwalten zu können.
