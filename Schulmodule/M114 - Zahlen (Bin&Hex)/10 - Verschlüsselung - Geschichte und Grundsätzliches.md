#schule 
#m114


# Lernziele

- Den Unterschied zwischen symmetrischer und asymmetrischer Verschlüsselung erklären.
- Den Begriff “Steganographie” erklären.
- Exemplarisch monoalphabetische Chriffren dechiffrieren

# Ziele beim Schutz von Informationen

1. Vertraulichkeit
    
    Die Informationen können nur von Befugten eingesehen werden
    
    Wird durch sichere Verschlüsselung erreicht
    
2. Integrität
    
    Die Informationen sind unverfälscht und vollständig
    
    Wir durch eine gute Hash-Funktion erreicht
    
3. Authentizität
    
    Sender und Empfänger sind einander klar bekannt
    
    Wird durch eine gute Funktion für digitale Signatur erreicht.
    

# Steganographie

Es handelt sich und die Kunst von versteckten Informationen in einem Trägermedium (container). Nur Sender und Empfänger sollen von dem Vorhandensein versteckter Informationen bescheid wissen.

Damit dieses Prinzip aber funktionieren kann, muss der Empfänger eine Anleitung zum Auffinden der Informationen haben.

# Geschichte der Verschlüsslung

## Monoalphabetische Chiffren

Bei dieser sehr alten Art der Verschlüsselung wird für jeden Buchstaben des Alphabets genau ein geheimes Zeichen verwendet (immer das selbe)

## Caesar-Chiffre

Bei dieser Art der Verschlüsselung werden Buchstaben um eine bestimmte Anzahl stellen im Alphabet verschoben. Das erlaubt den Nutzern das Ändern des Codes, in dem sie die anzahl der Stellen anpassen.

## Geheimschrift der Mary Stuart

Diese Verschlüsselungsmethode ist grundsätzlch eine monoalphabetische Verschlüsselung mit extra Steps, die da lauten wie folgt:

1. Es gibt Zeichen, die keine Bedeutung haben
2. Es gibt ein Zeichen für doppelt vorkommende Buchstaben
3. Es gibt Zeichen, die ganze, häufig vorkommende Wörter darstellen (zb. “not”, “when”, “is”, “what”)

## Kryptoanalyse von monoalphabetischen Chiffren

Kryptoanalyse bedeutet das knacken von Verschlüsselungen

Bei monoalphabetischen Chiffren ist das knacken sehr einfach. Jede Sprache hat Buchstaben, die häufiger vorkommen als andere. Sobald man also weis, in welcher Sprache der verschlüsselte Text geschrieben worden ist, kann man viele der monoalphabetischen Chiffren bereits knacken. Besonders bei längeren Texten ist das der Fall.

Anhand der verwendeten Sprache kann man auch weitere statistische Schlüsse ziehen. Zum Beispiel hat jeder Buchstabe bestimmte Nachbarn, die ihm besonders häufig folgen.

# Symmetrische und asymmetrische Verschlüsselung

## Symmetrische Verschlüsselung

Bei der symmetrischen Verschlüsselung verwenden so wohl Sender als auch Empfänger den selben Schlüssel. Dieser Schlüssel muss also zwischen den beiden Parteien ausgetauscht werden und ist auf dem Weg ungeschützt!

Monoalphabetische Verschlüsselungsverfahren haben beispeilsweise eine symmetrische Verschlüsselung.

## Asymmetrische Verschlüsselung

Diese Art der Verschlüsselung besitzt einen Schlüssel zum verschlüsseln  (Public Key) und einen weiteren zum entschlüsseln (Private Key). Dadurch muss man nur den Public Key teilen, um verschlüsselte Nachrichten empfangen zu können.

## Hybride Verfahren

Die beiden oben genannten Verschlüsselungen haben je Vor- und Nachteile:

- Symmetrische Verfahren sind wegen dem Schlüsselaustausch nicht sicher, doch dafür effizienter und schneller.
- Asymmetrische Verfahren sind zwar sicher, aber ineffizient und langsam.

Aus diesem Grund versucht man, beide verfahren mit auf hybride Weise zu kombinieren.

Es wird ein gemeinsamer, symmetrischer Schlüssel auf assymetrische weise Versendet. Sobald beide Parteien diesen symmetrischen Schlüssel besitzen, können die mit symmetrischer Verschlüsselung kommunizieren. 

Dadurch ist nur der Verbindungsaufbau langsam (aber sicher) und die restliche Kommunikation kann auf schnelle Weise vorangehen und dabei eine gewährleistete Sicherheit haben!