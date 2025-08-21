#ÜK
#mobileApp

# View

View ist ein Container, der für Styling verwendet wird. Ist vergleichbar mit dem *div* in HTML.

View ist immer auch ein Flex-Container, in dem weitere Components angeordnet werden können.

# SafeAreaView

Wird als äusserste View verwendet und hat gegenüber der normalen View den Vorteil, dass Mindestabstände von den Rändern bereits eingehalten werden und so der Content nicht beispielsweise unter eine Notch oder in der Rundung des Bildschirms landet.

# StatusBar

Dieser Component steuert das Aussehen der Status Bar

# ScrollView

Ist eine View, deren Inhalt gescrollt werden kann. Wird verwendet, wenn der Inhalt der View höher als der Screen ist.

# Image

Wird verwendet, um Bilder anzuzeigen. Speziell ist, dass die AspectRatio angegeben werden kann. So kann das Seitenverhältnis der Bilder gesteuert werden. Wichtig ist, dass nur eine der Grössen angegeben ist und der andere undefinded.

# Text

Wird verwendet, um Text anzuzeigen. Text kann nie ausserhalb der Text-Komponente angezeigt werden.

# TouchableOpacity

Wird verwendet, wenn etwas geklickt werden kann. Es gibt auch *Pressable*, doch im Gegensatz dazu sind bei *TouchableOpacity* bereits Animationen vorhanden!

Ein Unterschied zum Button ist, dass *TouchableOpacity* gestyled werden kann. Buttons haben in React Native *keinen* style-Prop.