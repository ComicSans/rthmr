---
title: Infrastructure as Code (IaC)
date: 2022-04-20 09:20:37
tags:
- Software Design
---

__Infrastructure as Code__ (IaC) beschreibt IT-Infrastruktur in Form von maschinenlesbarem Code. Die Infrastruktur wird also ähnlich wie Software programmiert. Dieses Konzept geht mit DevOps und Cloud-Computing Hand in Hand.

 Die Vorteile von IaC liegen in der Geschwindigkeit der Bereitstellung, den niedrigeren Kosten und der guten Skalierbarkeit. Hinzu kommt eine hohe Flexibilität. Grundlage für effizientes Infrastructure as Code bilden virtualisierte Umgebungen und das Cloud Computing, da sich hier Ressourcen ohne die Notwendigkeit eines manuellen Zugriffs auf die eigentlichen physischen Hardwareressourcen verwalten lassen. Doch auch On-Premise ist der Einsatz von toolgestützter Bereitstellung möglich.

 Ein weiterer Vorteil liegt in der wiederholbaren Bereitstellung von Hardware: durch erneutes Ausführen des Bereitstellungsskript stellt reproduzierbar und verlässlich eine identische Umgebung bereit. Die Duplikation von Umgebungen ist nützlich für Testszenarien und die einfache Bereitstellung von Abnahmeumgebungen.

## Warum IaC?

In der Bereitstellung von Software wird die Hardware traditionell manuell bereitgestellt und gewartet. Hierbei kann es zu Abweichungen zwischen verschiedenen Umgebungen und in der Folge zu unerwarteten Problemen kommen, da im Laufe der Zeit diese Umgebungen auseinanderlaufen, sei es durch unterschiedliche Wartungszyklen, verschiedene Teams oder abweichenden Anforderungen. Das macht die Herstellung eines reproduzierbaren Zustands unmöglich. Solche Insellösungen werden als "Schneeflocken" beschrieben: alle irgendwie ähnlich, aber nie ganz gleich und nie zu reproduzieren.

Inkonsistenzen führen zu Deployment-Problemen.

Die Vermeidung von Inkonsistenzen und das automatisierter, reproduzierbare Bereitstellen ist das Ziel von IaC. Durch die Definition eines gewünschten Zielzustands unabhängig vom Ausgangszustand der Umgebung erreicht man eine einheitliche, schnell zu reproduzierende Struktur (Idempotenz).

## Gängige Tools zur Programmierung der Infrastruktur

Zur Programmierung der Infrastruktur verwendet man Tools wie [Terraform](https://www.terraform.io/), [Chef](https://www.chef.io/), [Puppet](https://puppet.com/) oder [Ansible](https://www.ansible.com/). Neben diesen  anbieterübergreifend nutzbaren Open-Source-Tools gibt es auch spezifische Tools für die jeweiligen Cloud-Umgebungen.

Um Infrastrktur zu programmieren benötigt man eine Abstraktionsschicht zwischen physikalischer Hardware und dem gewählten Tool. In der Regel handelt es sich bei diesen Abstraktionsschichten um verschiedene Formen der Virtualisierung. Es werden Schnittstellen oder Tools bereitgestellt, über die sich die einzelnen Ressourcen mithilfe einer definierten Code-Sprache programmieren lassen.

Bei allen Tools erstellt man eine menschenlesbare und dokumentierte Grundkonfiguration, ein Konfigurationsmodell mit einer definierten Version. Die Deployment-Pipeline wertet dieses Modell aus und stellt den Zielzustand im Zielsystem her.

Bei Änderungen an der gewünschten Konfiguration wird die Quelle der Information bearbeitet, das Konfigurationsmodell und nie das Ziel direkt.

## Deklarativ vs. imperativ

Die Programmierung muss deklarativ oder imperativ erfolgen. Die _deklarative Programmierung_ gibt die genaue Zielumgebung vor, während die _imperative Programmierung_ die auszuführenden Aktionen definiert, um eine gewünschte Zielumgebung zu erstellen. 

Dies kann zu unerwarteten Problemen führen:

Eine imperative Formulierung ("erstelle drei VMs!") beschreibt die Aktionen unabhängig vom Ausgangszeitpunkt. Die deklarative Formulierung ("es sollen drei VMs sein!") beschreibt den Zielzustand. Angenommen, es existieren bereits zwei VMs so erstellt der Imperativ in Summe fünf VMs, die Deklaration die gewünschten drei.

Mehr findet sich [hier](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/infrastructure-as-code).