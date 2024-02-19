[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/OwH8KTXH)
# GDI+
Eine Sammlung von Tipps und Tricks zum Thema Grafikprogrammierung mit GDI+.

## Klassen / Ereignisse
### Timer
Ein Timer führt in regelmäßigen Abständen ein `Tick`-Event aus. Der [`System.Windows.Forms`.`Timer`](https://learn.microsoft.com/de-de/dotnet/api/system.windows.forms.timer?view=windowsdesktop-8.0&viewFallbackFrom=net-6.0) kann über die Toolbox auf die GUI gezogen werden. 

Anschließend können wir 
- die Zeit zwischen jedem `Tick`-Event einstellen (`+ Interval { get; set; }: int`) und
- den Timer starten (`+ Start():void`) oder
- stoppen (`+ Stop():void`) oder
- den Zustand abfragen. (`+ Enabled{ get; set; }: bool`) (Standard ist ausgeschaltet: `enabled = false`)



## Tipps und Tricks
Ergänzen Sie hier die notwendigen Code-Ausschnitte, um zu zeigen, wie man es macht. 
- Sie können [CodeBlöcke mit Syntax-Highlighting](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting) einsetzen
- Wird es zu unübersichtlich? Sie können auch Unterordner mit Beispiel-Code anlegen und auf die entsprechenden Dateien verlinken. [Inspiration](https://github.com/gsoTH/flaskShowcase/tree/master/datenbanken).
- Die folgende Liste kann gerne ergänzt werden :)

### Bewegung animieren
>Die Methode ` - FrmFrogger_KeyDown´ wird ausgelöst, wenn eine Taste betätigt wird.
```ruby
private void FrmFrogger_KeyDown(object sender, KeyEventArgs e){
//Es wird überprüft, ob die Pfeiltasten nach oben gedrückt wurde.
 if(e.KeyCode == Keys.Down)
 {
     // es wird überprüft, ob der Spieler ganz unten Steht
     if (spieler.Y != hoehe - hoeheJeBereich)
     {
         spieler.Y = spieler.Y + hoeheJeBereich;
     }

 }
}
```
>Alle anderen Pfeiltasten funktionieren genauso, außer einer Ausnahme.
```ruby
 if (e.KeyCode == Keys.Up)
 {

     if (spieler.Y <= anzahlBereiche)
     {
         spieler.Y = hoehe - hoeheJeBereich;
         round++;
         alleHindernisse.Clear();
         
         spawnRate-= 1; 
         spawnZaehler = 0;
     }
     else
     {
         spieler.Y = spieler.Y - hoeheJeBereich;

     }


 }´´´
>Sobald der Spieler sich ganz oben befindet, muss er die Möglichkeit haben, eine neue Runde zu starten. Um dies zu ermöglichen, muss die Variable ` - round´ erhöht werden. Gleichzeitig sollte die `Spawnrate´ verringert werden, um die Häufigkeit der Hinderniserstellung anzupassen. Zudem müssen alle vorhandenen Hindernisse gelöscht werden, um Platz für neue Hindernisse mit unterschiedlichen Eigenschaften in der neuen Runde zu schaffen
 

### Objekte mit Tasten steuern

### Verhindern, dass ein Spieler aus dem Bild läuft

### Spiel pausieren

### Ihr schönstes Ergebnis





