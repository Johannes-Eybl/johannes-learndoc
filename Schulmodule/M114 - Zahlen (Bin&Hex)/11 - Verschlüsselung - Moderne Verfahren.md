#schule 
#m114


# Lernziele

- Erklären, was eine Hash-Funktion ist und wofür diese eingesetzt wird.
- Aufzeigen, wie ein binärer Schlüssel mit der XOR-Verknüpfung angewendet wird.
- An einem einfachen Beispiel die Funktionsweise der RSA-Verschlüsselung erklären.

# Moderne Verfahren

## Das RSA-Verfahren (Vertraulichkeit)

Bei diesem Verfahren wird mit einem öffentlichen Schlüssel verschlüsselt und mit einem privaten Schlüssel entschlüsselt. Der private Schlüssel wird geheim gehalten und kann nicht geknackt werden (in realischer Zeit).

## Anwendung binärer Schlüssel

Binäre Schlüssell kann man sehr einfach durch die XOR-Verbindung anwenden. Es wird also überall, wo zwei Einsen oder zwei Nullen sind, eine null eingefügt und überall, wo eine Eins und eine Null ist, wird im Chriffrierten Text eine Eins eingefügt. 

![Untitled](Untitled%2011.png)

## Hash-Funktion (Integrität)

Eine Hash-Funktion reduziert eine grosse Datenmenge auf eine kleine Nummer (den Hash-Wert). Wenn in der Datenmenge nur eine kleine Veränderung gemacht wird, ist der Hash-Wert komplett anders. Aus diesem Grund kann der Hash-Wert wie ein Fingerabdruck verwendet werden. 

## Digitale Signatur (Authentizität)

Mithilfe von Hash-Werten kann man die Authentizität von versandten Dokumenten gewährleisten. Der Versender schickt mit dem Dokument einen selbst kalkulierten Hash-Wert . Der Empfänger generiert dann einen eigenen Hash-Wert und vergleicht diesen mit dem gesendeten. So kann garantiert werden, dass Sender und Emfpänger den gleichen Nachrichteninhalt sehen.