# Box-Model Intro, main-Tag, semantische-Tags

## Einführung - Alles ist eine Box

Als Webentwickler begegnen wir ständig Boxen auf Webseiten. Jedes Element, sei es ein Text, ein Bild oder ein Formularfeld, wird im Web als eine rechteckige Box behandelt. Um dies zu verdeutlichen, können wir die Entwicklerwerkzeuge unseres Browsers verwenden.

1. Öffnen Sie die Webseite google.com in Ihrem Browser.
2. Klicken Sie mit der rechten Maustaste auf einen beliebigen Bereich der Seite und wählen Sie "Element untersuchen" (oder ähnliche Option je nach Browser).
3. Die Entwicklerwerkzeuge sollten sich nun öffnen und den HTML-Code für die Seite anzeigen. Finden Sie die CSS-Regel für das `<body>`-Element und fügen Sie die folgende Regel hinzu: `border: 1px solid red !important;`
4. Beachten Sie, wie nun alle Elemente auf der Seite durch eine rote Linie umrandet sind. Jedes Element ist eine Box!

## Inhalte enthalten

### Die Standard-Box: das `<main>`-Tag

Das `<main>`-Tag ist ein Block-Level-Element und wird verwendet, um den Hauptinhalt einer Webseite zu definieren. Es repräsentiert den zentralen Inhalt der Seite und sollte nur einmal pro Dokument verwendet werden.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            main {
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <main>
            <h1>Willkommen auf meiner Webseite</h1>
            <p>Hier ist der Hauptinhalt der Seite.</p>
        </main>
    </body>
</html>
```

### Unseren Inhalt einschließen (Engl. "Shrink Wrapping"): Alles in einem `<main class="container">` platzieren

Manchmal möchten wir unseren Inhalt in einer begrenzten Breite zentrieren. Hierfür können wir eine Container-Box erstellen und unseren Inhalt darin einschließen.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .container {
                width: 80%;
                margin: 0 auto;
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <main class="container">
            <h1>Willkommen auf meiner Webseite</h1>
            <p>Hier ist der Hauptinhalt der Seite.</p>
        </main>
    </body>
</html>
```

### Breite ändern und zentrieren: CSS `width` und `margin: auto`

Um die Breite eines Elements zu ändern und es horizontal zu zentrieren, können wir die `width`-Eigenschaft und `margin: auto` verwenden.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .box {
                width: 200px;
                margin: auto;
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <p>Dieser Inhalt ist 200px breit und horizontal zentriert.</p>
        </div>
    </body>
</html>
```

### Die Höhe begrenzen: CSS `height` NUR in spezifischen Situationen verwenden

Die Verwendung der `height`-Eigenschaft sollte sparsam erfolgen, da sie die Höhe eines Elements festlegt und dessen Inhalt möglicherweise abschneidet. In den meisten Fällen sollte die Höhe eines Elements durch den Inhalt bestimmt werden.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .box {
                width: 200px;
                height: 100px; /* Beispielhöhe */
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <p>Dieser Inhalt hat eine festgelegte Höhe von 100px.</p>
        </div>
    </body>
</html>
```

### Inhalt mit der `vh`-Einheit in voller Höhe anzeigen

Die `vh`-Einheit erlaubt es uns, die Höhe eines Elements in Bezug auf die Höhe des Viewports festzulegen. Dies ist nützlich, wenn Sie ein Element haben möchten, das die gesamte sichtbare Höhe des Bildschirms einnimmt.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .full-height {
                height: 100vh;
                background-color: lightblue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <div class="full-height">
            <p>Dieser Inhalt nimmt die volle Höhe des Viewports ein.</p>
        </div>
    </body>
</html>
```

### Die Flusskontrolle - die `overflow`-Eigenschaft

Die `overflow`-Eigenschaft bestimmt, wie ein Element reagieren soll, wenn sein Inhalt die festgelegten Abmessungen überschreitet.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .box {
                width: 200px;
                height: 100px;
                border: 1px solid blue;
                padding: 20px;
                overflow: scroll; /* Andere mögliche Werte: hidden, auto */
            }
        </style>
    </head>
    <body>
        <div class="box">
            <p>
                Dieser Inhalt wird durch die `overflow: scroll`-Eigenschaft
                scrollbar, wenn er die Box-Abmessungen überschreitet.
            </p>
        </div>
    </body>
</html>
```

## Block-Level-Semantik

Block-Level-Elemente beginnen immer in einer neuen Zeile und nehmen die gesamte verfügbare Breite ein.

-   `<section>`, `<article>` und `<aside>` sind semantische Elemente, die verwendet werden, um den Inhalt zu strukturieren.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            section,
            article,
            aside {
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <section>
            <h2>Über uns</h2>
            <p>Informationen über unser Unternehmen.</p>
        </section>

        <article>
            <h2>Artikelüberschrift</h2>
            <p>Dies ist ein Artikel über ein bestimmtes Thema.</p>
        </article>

        <aside>
            <h3>Werbung</h3>
            <p>Hier ist ein Werbebanner.</p>
        </aside>
    </body>
</html>
```

-   `<header>` und `<footer>` sind Block-Level-Elemente, die typischerweise am Anfang bzw. Ende eines Abschnitts oder einer Seite verwendet werden.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            header,
            footer {
                background-color: lightblue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <header>
            <h1>Meine Webseite</h1>
            <nav>
                <!-- Navigationselemente hier einfügen -->
            </nav>
        </header>

        <main>
            <p>Hier ist der Hauptinhalt der Seite.</p>
        </main>

        <footer>
            <p>&copy; 2023 Meine Webseite. Alle Rechte vorbehalten.</p>
        </footer>
    </body>
</html>
```

-   `<div>` ist ein generisches Block-Level-Element, das verwendet wird, um Inhalte zu gruppieren und zu gestalten.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Meine Webseite</title>
        <style>
            .box {
                border: 1px solid blue;
                padding: 20px;
            }
        </style>
    </head>
    <body>
        <div class="box">
            <h2>Überschrift</h2>
            <p>Dies ist ein Abschnitt des Inhalts.</p>
        </div>

        <div class="box">
            <h2>Weitere Überschrift</h2>
            <p>Dies ist ein weiterer Abschnitt des Inhalts.</p>
        </div>
    </body>
</html>
```
