#schule 
#m114

# Lernziele

- Anhand von Samplingrate und Samplingtiefer erklären, wie Audiosignale digitalisiert werden.
- Aufzeigen, wie durch psychoakustische Effekte Audio-Dateien reduziert werden können.
- Den Kompressionsfaktor und die Kompressionsrate für Multimedia-Dateien berechnen.

# Definition von Reduktion

Reduktion ist kompression mit Verlust. Man verwendet Reduktion, wenn die gegebenen Daten in einer Genauigkeit vorliegen, die die Präzision der menschlichen Sinne überschreitet. In so einem Fall bemerkt der Nutzer nicht, dass die Datenmenge unvollständig ist..

Der zweite Schritt in der Anwendung von Reduktion ist das Kürzen der Informationsdichte auf ein angemessenes Mass für die gegebene Anwendung. Ein Videocall braucht beispielsweise nicht die gleiche Auflösung wie eine Netflix-Serie. 

Zuletzt werden die übrig gebliebenen Daten mit einem verlustfreien Verfahren komprimiert.

# Audio-Dateien

## Aufnahme

Die Aufnahme von Audio ist schlussendlich nichts anderes als die Messung von Schalllwellen, also Luftdruckschwankungen. Wenn man diese Schwankungen aufnehmen will, sind folgende zwei Faktoren von besonderer Bedeutung:

### Samplingrate

Gibt an, wie häufig das analoge Signal abgetastet wird, also wie häufig eine digitale Messung gemacht wird. Die Grösse eine unkompremierten Audiodatei ist  proportional zur Samplingrate

### Samplingtiefe

Die Samplingtiefe beschreibt die präzision, mit der die digitalen Messungen vorgenommen werden. Wie auch die Samplingrate ist die Samplingtiefe proportional zur Grösse der Audiodatei.

.wav ist ein Dateiformat, das Audiodateien ohne Komprimierung abspeichert. Die Sampling-Rate und Tiefe sind einstellbar. 

In einer CD sind Dateien mit eine Samplingrate von 44.1kHz und einer Samplingtiefe von 16 Bit.

# Psychoakustische Reduktion

Bei der psychoaukustischen Reduktion handelt es sich um verschiedene Kompressionsverfahren, bei dem Töne, die sich ausserhalb des menschlichen Hörvermögens befinden, entfernt werden. 

## Hörschwelle

Töne, die sich unterhalb der Hörschwelle befinden, sind zu leise um wahrgenommen zu werden. 

## Maskierung von Nebenfrequenzen

Bei der Maskierung von Nebenfrequenzen werden leise Töne gelöscht, die zeitgleich mit lauten Tönen erklingen. Das Gehör kann beim Wahrnehmen von lauten Tönen keine leiseren Töne hören, weshalb sie von einer Audiodatei gelöscht werden können.

## Nachmaskierung

Wenn ein lauter Ton erklingt, fällt es dem Gehör schwer, kurz darauf erklingende leise Töne wahrzunehmen. Also können, wie bei der Maskierung, auch leise Töne, die kurz nach einem leuten Ton gespielt werden, von der Audiodatei entfernt werden.

# Bild-Dateien

Bilddateien speichern jeden Pixel und seinen Farbwert ab. Die Dateigrösse ist direkt von der Auflösung und der genauigkeit der Farbinformation abhängig.

### Schwarzweiss-Grafiken

Bei einem Schwarzweiss-Bild muss jeder Pixel nur ein Bit gespeichert werden.

### Graustufen

Üblicherweise werden Graustufen in 16 verschiedene Töne eingeteilt. Das bedeutet, dass jeder Pixel 4 Bit (2^4=16) an Informationen benötigt.

### Farbige Bilder

Farbige Bilder haben verschieden tiefe Farbinformationen, je nach dem, welches Dateiformat verwendet wird. Gifs haben beispielsweise nur 256 Farben pro Pixel, was in 8 Bit gespeichert werden kann. 

Das True-Color Format hingegen hat über 16 Millionen mögliche Farben, jeder Pixel benötigt 24Bit speicher. 

## Reduktion von Bilddateien

Das beliebteste Verfahren zur Reduktion von Bilddateien ist das JPEG-Format. Blöd gesagt werden dabei Pixel zu grossen Einheiten zusammengefasst, besonders bei Flächen, die wenig Kontrast besitzen.