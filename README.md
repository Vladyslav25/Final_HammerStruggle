# Final_HammerStruggle | 5.2020, 15 Monate

Leider ist die LFS bei GitHub zu klein um den Sourcecode hier hoch zu laden. Daher kann der Sourcecode über folgenden Link runtergeladen werden: https://drive.google.com/drive/folders/1XUxTZVD2xW_Cy4JFb78SrJ_IcbsPo3En?usp=sharing

Was habe ich gelernt:
 - Unreal Engine 4
  - Blueprints
  - Visual Scripting
  - Animation as FSM
  - UI
  - Game Logic
  - Collision
- Behaviour Trees

Diese Abgabe ist ein Gruppenprojekt gewesen. Wir hatten 3 Monate Zeit, von der Idee bis zum fertigen Spiel.
Wir waren zu 4 in dieser Gruppe: 2 Programmierer und 2 Artist. Leider ist ein Gruppenmitglied, welcher Programmierer war, kurz nach der Fertigstellung der Alpha Version krank geworden und somit musste das meiste von mir alleine programmiert werden. Trotz dessen wurden alle nötigen Features implementiert.

Ressourcen:
Der Spieler besitzt ein Array aus Structs wo auch die Menge der jeweiligen Ressource gespeichert wird. Die Ressource besitzt als Variabel den Index, wo sie im Array beim Spieler hinzugefügt werden muss.
  - Wood: 0
  - Stone: 1
  - Iron: 2
  - Copper: 3
  - Marbel: 4
  - Silver: 5
  - Gem: 6
  - Gold: 7
In diesem Struct wird auch das Sprite als auch die Beschreibung für die UI-Bindings gespeichert. Damit bei Änderungen alles Zentral beim Spieler ist.

AI:
Es gibt zwei Arten von AI. Eine die Nahkampfangriffe ausführen kann und eine die noch zusätzlich werfen kann. Jede dieser Art besitzt einen eigenen Behaviour Tree und Animations-FSM, aber beide besitzen denselben Vater-Blueprint. So kann ich im Blueprint das Aussehen und das Verhalten beim Tot für beide gleichzeitig anpassen.

Player Animation:
Bei der Playeranimation wird über ein Enum die benötigte Animation ausgewählt. Dabei spielt der Oberkörper die Attack-Animation ab und der Unterkörper folgt weiter der Lauf bzw. der Idle Animation, welche geblendet werden, weiter.
Das wechseln der Waffen von dem Rücken in die Hand wird über Sockets gemacht.

Damage:
Der Schaden wird über die von Unreal Engine implementierte Damage Funktion ausgelöst. Dabei wird in der Animation ein ShpereTrace gemacht. Wenn dieser Trifft wird dem Getroffenen Schaden erteilt.

Player Upgrades:
Die Kosten für die Player Upgrades werden durch Transformiere Funktionen berechnet. Die Funktionen sind so implementiert, dass man flexibel die Transformation anpassen könnte. 

Brunnen:
Der Brunnen wird freigeschaltet sobald der Spieler die erste seltene Ressource eingesammelt hat. Dort hat er die Möglichkeit den Kristall aufzuladen, welcher dann einen Golem in der Nähe verstärkt und eine bestimmte Ressource spawnen lässt. Ich habe den Brunnen in der Schmiede mit dem Trigger um die UI zu öffnen, als auch die Lampe in ein Blueprint gepackt umso einfachere auf die Lampe zu referenzieren.

Golem Spawner:
Die Anzahl, die HP, der Schaden und die Ressource, die beim Sterben gedropt wird, der Golems ist abhängig von der Anzahl an Upgrades die der Spieler gemacht hat, als auch von der Rundenanzahl. Die Werte werden über eine Formel errechnet, welche auch von den Entwicklern flexibel angepasst werden kann. 

Round Controller:
Der Round Controller entscheidet, wann eine Runde endet und wann eine Runde weiter geht. Dieser besitzt Referenzen zu den Türen und zu dem Golem Spawner. Wenn der Spieler die Schmieder verlässt, beginnt die nächste Runde, die Schmiede schließt sich und der Spanwer spawnt die Golems. Sobald die Golems besiegt sind, schließt dieser die Türen des Spawnbereiches, wenn sich er Spieler nicht drinnen befindet. Und öffnet die Türen der Schmiede. Usw.

