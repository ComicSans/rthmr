---
title: Statische Seiten mit Hexo
date: 2021-02-14 09:58:34
tags: howto, jamstack, hexo
---

# Übersicht

Klassisch werden kleinere Webseiten  mit einem festen Toolset gehostet: dazu gehören Linux, Apache, MySQL und PHP. Davon leitet sich auch der Name ab, man spricht vom LAMP-Stack. Als Variation tritt manchmal der MAMP-Stack auf, bei dem Linux durch macOS ersetzt wurde. Viele Softwarepakete erfordern diesen Aufbau und entsprechend viele Hosting-Angebote gibt es hier. Wer zum Beispiel ein Wordpress-Blog betreiben will oder ein kleines CMS, der
kommt selten an diesen Angeboten vorbei.

Allen gemein ist der dynamische Aufbei der Webseiten: beim Aufruf der Seite durch den Besucher wird auf Serverseite ein PHP-Prozess gestartet, der Inhalte aus der Datenbank ausliest, HTML-Seiten generiert und diese ausliefert. Ebenfalls können Inhalte über eine Administrationsseite vom Betreiber der Webseiten über das Internet in der Datenbank gespeichert bzw. verändert werden.

Halbwegs neu ist der Ansatz, direkt statische Seiten auszuliefern. Das bedeutet: die Seiten werden nicht dynamisch bei jedem Aufruf neu generiert, sondern einmal erstellt und dann (statisch) gespeichert. Die Benutzung von Datenbank, PHP und ähnlichen Tools entfällt, der Webserver hat nur mit HTML, Javascript und CSS zu tun. Als Begriff hierfür hat sich JAM-Stack etabliert: JavaScript, APIs und Markup.

LAMP-Stack                    | JAM-Stack
------------------------------|------------------------
![LAMP-Stack](lampstack.png)  | ![JAM-Stack](jamstack.png)

## Vorteile des JAM-Stacks
