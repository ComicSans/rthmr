---
title: Statische Seiten mit Hexo
date: 2021-02-14 09:58:34
tags: howto, jamstack, hexo, lamp
---

# Übersicht

Klassisch werden kleinere Webseiten  mit einem festen Toolset gehostet: dazu gehören Linux, Apache, MySQL und PHP. Davon leitet sich auch der Name ab, man spricht vom LAMP-Stack. Als Variation tritt manchmal der MAMP-Stack auf, bei dem Linux durch macOS ersetzt wurde. Viele Softwarepakete erfordern diesen Aufbau und entsprechend viele Hosting-Angebote gibt es hier. Wer zum Beispiel ein Wordpress-Blog betreiben will oder ein kleines CMS, der
kommt selten an diesen Angeboten vorbei.

Allen gemein ist der dynamische Aufbau der Webseiten: beim Aufruf der Seite durch den Besucher wird auf Serverseite ein PHP-Prozess gestartet, der Inhalte aus der Datenbank ausliest, HTML-Seiten generiert und diese ausliefert. Ebenfalls können Inhalte über eine Administrationsseite vom Betreiber der Webseiten über das Internet in der Datenbank gespeichert bzw. verändert werden.

Halbwegs neu ist der Ansatz, direkt statische Seiten auszuliefern. Das bedeutet: die Seiten werden nicht dynamisch bei jedem Aufruf neu generiert, sondern einmal erstellt und dann (statisch) gespeichert. Die Benutzung von Datenbank, PHP und ähnlichen Tools entfällt, der Webserver hat nur mit HTML, Javascript und CSS zu tun. Als Begriff hierfür hat sich JAM-Stack etabliert: JavaScript, APIs und Markup.

LAMP-Stack                    | JAM-Stack
------------------------------|------------------------
![LAMP-Stack](lampstack.png)  | ![JAM-Stack](jamstack.png)

## Vorteile des JAM-Stacks

Gerade für kleinere Seiten reicht dieses Vorgehen oft aus. Die Vorteile sind folgende:

### Geschwindigkeit

Da der Generierungs-Schritt bei der Auslieferung der Seiten entfällt, steht die Seite schneller bereit. Der Webserver muss nicht auf die Datenbank zugreifen und serverseitige Skripte auswerten, bevor er alle Inhalte der Seite berechnet hat.

### Sicherheit

Ein Einfallstor für Hacker ist oft die Administrationsoberfläche des CMS oder ein Plugin eines Drittherstellers, welches eine Lücke aufweist. Über die serverseitige Auswertung ist damit ein Zugriff auf das Dateisystem und die Datenbank denkbar. Da im JAM-Stack lediglich HTML-Seiten ausgeliefert werden, ist hier kein solcher Zugriff möglich.

### Kosten

Hostingangebote inkludieren den Preis für Datenbank und Rechenleistung. Erstere fällt nun meist weg und letztere reduziert sich enorm, da keine Skripte ausgeführt werden müssen. Folglich lassen sich kleine und kostenlose Hostinglösungen finden. Diese reichen von [GitHub Pages](https://pages.github.com/) bis hin zu Anbietern wie [Netlify](https://www.netlify.com/).

# Seitengeneratoren

Es haben sich eine ganze Reihe von Generatoren am Markt entwickelt. Die meisten verlassen sich dabei bei der Generierung der Seiten auf Node (und somit JavaScript), manche auf den Programmiersprachen Ruby oder Go. Content wird überlicherweise in Form von [Markdown](https://de.wikipedia.org/wiki/Markdown) bereitgestellt, eine Art vereinfachtes HTML. Auch dieser Text wurde in Markdown geschrieben.

## Übersicht

### Jekyll

[Jekyll](http://jekyllrb.com/) eignet sich für kleinere Projekte und privates Blogging. Content wird in Markdown erstellt, über Liquify-Templates gerendert und benötigt hierfür Ruby. Der eine oder andere mag Jekyll von [GitHub Pages](https://pages.github.com/) her kennen, denn dort stellt es die Basis für die Seitenerstellung.

### Hugo

[Hugo](https://gohugo.io/) wurde in Go geschrieben und war einer der ersten statischen Seitengeneratoren. Er ist bekannt für seine hohe Geschwindigkeit.

### Gatsby

[Gatsby](http://gatsbyjs.org/) basiert auf React und ist somit in der Lage, moderne Obeflächen schnell darzustellen. Eine weitere Stärke ist das reichhaltige Plugin-Ökosystem.

### Hexo

[Hexo](https://hexo.io/) setzt auf NodeJS auf und bringt neben hoher Geschwindigkeit auch eine gewisse Kompatibilität zu älteren Frameworks wie Jekyll mit. Da Node bei modernen Webanwendungen nicht fehlen darf, ist die Einstiegsschwelle zur Benutzung niedrig.

# Hexo

Sehen wir uns im Folgenden an, wie man eine kleine Besipielseite mit Hexo erstellt.

## NodeJS

Als Grundlage benötigen wir Node. Das geht entweder über die Paketverwaltung der Wahl (unter Windows sei [Chocolatey](https://chocolatey.org/) empfohlen).

## Hexo

```bash
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```

Ruft man im Browser nun http://localhost:4000 auf, so begrüßt einen die erste eigene Hexo-Seite.

## Inhalt hinzufügen

Inhalte unterscheiden zwischen "Posts" und "Pages", also Blogbeiträge und festen Seiten wie das Impressum.

Einen neuen Blogbeitrag legt man folgendermaßen an:

```bash
hexo new post "Mein erster Beitrag"
```

Im Anschluss kann im ``source/_posts``-Unterordner die leere Seite begutachtet werden. Die Datei beinhaltet bereits das sogennante ``Front-matter``, Metainformationen zur Seite. Folgende Werte sind möglich:

Wert |	Beschreibung |	Standardwert
--------|-------------|------------
layout |	Das zu verwendende Layout (Post, Pages oder Draft)	|config.default_layout
title |	Seitentitel	| Filename (posts only)
date |	Veröffentlichungsdatum |	File created date
updated | Datum der letzten Änderung |	File updated date
comments |	Kommentare zulassen |	true
tags | Tags |
categories | Kategorien |
permalink |	Vergibt eine feste URL für diesen Beitrag |
excerpt |	Falls gewünscht, kann man hier eine kurze Zusammenfassung der Seite verfassen |
