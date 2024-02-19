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
```ruby
if (e.KeyCode == Keys.Up)
 {

     if (spieler.Y <= anzahlBereiche)
     {
         spieler.Y = hoehe - 35;
         round++;
         alleHindernisse.Clear();
         
         spawnRate-= 1; 
         spawnZaehler = 0;
     }
     else
     {
         spieler.Y = spieler.Y - hoeheJeBereich;

     }


 }
 if (e.KeyCode == Keys.Space)
 {
     if (tmrGameTick.Enabled == true)
     {
         tmrGameTick.Enabled = false;

         //tmrGameTick.Stop();
         return; // verhindert, dass das Paint-Ereignis ausgeführt wird
                 // notwendig, weil dort der Timer gestartet wird.
     }
     else
     {
         tmrGameTick.Enabled = true;
     }
 }
 if (e.KeyCode== Keys.Right) { spieler.X = spieler.X - breiteJeBereich; }
 if(e.KeyCode== Keys.Left) { spieler.X = spieler.X + breiteJeBereich; }
 if(e.KeyCode == Keys.Down)
 {
     if (spieler.Y != hoehe - 35)
     {
         spieler.Y = spieler.Y + hoeheJeBereich;
     }

 }
```
 

### Objekte mit Tasten steuern

### Verhindern, dass ein Spieler aus dem Bild läuft

### Spiel pausieren

### Ihr schönstes Ergebnis





