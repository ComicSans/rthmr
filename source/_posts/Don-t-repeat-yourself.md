---
title: Don't repeat yourself
date: 2021-03-20 10:40:03
tags: Software Design Principles CleanCode
---

Don’t repeat yourself (DRY, englisch für "wiederhole dich nicht") ist ein Prinzip, das darauf abzielt, Redundanz zu vermeiden oder zumindest zu reduzieren. Es handelt sich hierbei um ein Prinzip von Clean Code.

Warum ist das wichtig? Naja, Duplikate (seien sie absichtlich entstanden oder nicht) entwicklen sich schnell zum Albtraum wenn es um die spätere Wartung oder die Erweiterung bestehenden Codes geht. Richtig schlimm wird es, wenn diese Duplikate langsam ein Eigenleben entwicklen und sich selbstständig weiterentwicklen.

Wichtig ist die Feststellung, dass sich der Begriff "Duplikat" hier nicht auf doppelten Code bezieht, sondern auf dupliziertes _Wissen_:

> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

Oder auf Deutsch: es gibt genau eine Stelle, an der die Wahrheit zu finden ist.

Ein gewisses Maß an Redundanz lässt sich nie vermeiden. Wichtig ist aber, dass eine Authorität benannt wird, die das Wissen vorgibt. Das kann eine Methode sein, die von allen Stellen aufgerufen wird (ein Logger  beispielsweise). Oder ein Interface, das die Struktur der implementierenden Klassen vorgibt. Oder eine generierte Schnittstellendatei.

Schauen wir uns ein kurzes Beispiel an:

{% code %}
cars = ['BMW', 'Volkswagen', 'Ford']

print cars[0], 'is a car manufacturer'
print cars[1], 'is a car manufacturer'
print cars[2], 'is a car manufacturer'
{% endcode %}

Wir erhalten, vielleicht wenig überraschend, folgendes Ergebnis:

{% code %}
BMW is a car manufacturer
Volkswagen is a car manufacturer
Ford is a car manufacturer
{% endcode %}

Das Ergebnis is unzweifalhaft richtig. Dennoch haben wir das Wissen, wie ein Array-Eintrag ausgegeben wird, dupliziert (nochmal der Hinweis: das Problem ist nicht die textuelle Wiederholung, sondern dass jede Zeile selbst definiert, wie der Text auszugeben ist).

Springen wir in die Zukunft und lassen die drei Hersteller Raketen statt Autos bauen. Dann müssten wir an drei Stellen den Text ändern.

Wir können das leicht vermeiden (hier mit Typescript):

{% code %}
cars = ['BMW', 'Volkswagen', 'Ford']

cars.forEach( (car) => console.log(car + " is a car manufacturer"));
{% endcode %}

Das ist kürzer. Der Hauptvorteil aber ist: der String wird nur einmal definiert. Und lässt sich so später zentral austauschen.
