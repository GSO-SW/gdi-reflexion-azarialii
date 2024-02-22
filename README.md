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

Dieser Code wird jedes Mal ausgeführt, wenn ein Timer namens tmrGameTick abläuft.
spawnZaehler wird bei jedem Durchlauf um 1 erhöht.
Wenn spawnZaehler gleich spawnRate ist, wird ein neues Hindernis erzeugt.
Ein zufälliger Bereich (zufall) wird ausgewählt, in dem das Hindernis erscheinen soll.
Abhängig von der aktuellen Runde (round) wird das Hindernis mit unterschiedlichen Eigenschaften erstellt

```ruby
Private void tmrGameTick_Tick(object sender, EventArgs e)
        {

            spawnZaehler++;
            if(spawnZaehler == spawnRate)
            {
                Random rnd = new Random();
                spawnZaehler = 0;

                int zufall = rndBahn.Next(1, anzahlBereiche-1);
                int yWertDerBahn = alleBahnen[zufall].Top;
                if(round == 0)
                {
                    alleHindernisse.Add(new Hindernis(breite, yWertDerBahn, 60, hoeheJeBereich, 10, Color.Red));
                }
                else if (round == 1)
                {
                    alleHindernisse.Add(new Hindernis(breite, yWertDerBahn, 60, hoeheJeBereich, 40, Color.Blue));
                }
                else if(round == 2)
                {
                    if (rnd.Next() % 2 == 0)
                    {
                        alleHindernisse.Add(new Hindernis(breite, yWertDerBahn, 60, hoeheJeBereich, 10, Color.PowderBlue));

                    }
                    else
                    {
                        alleHindernisse.Add(new Hindernis(breite, yWertDerBahn, 60, hoeheJeBereich, 80, Color.Black));

                    }

                }
                else if(round == 3)
                {
                    alleHindernisse.Add(new Hindernis(breite, yWertDerBahn, 60, hoeheJeBereich, 20, Color.Blue));
                }

            }
}
```
### Objekte mit Tasten steuern
>Die Methode (`- FrmFrogger_KeyDown`) wird ausgelöst, wenn eine Taste betätigt wird.
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


 }
```

>Sobald der Spieler sich ganz oben befindet, muss er die Möglichkeit haben, eine neue Runde zu starten. Um dies zu ermöglichen, muss die Variable (`- round`) erhöht werden. Gleichzeitig sollte die (`Spawnrate`) verringert werden, um die Häufigkeit der Hinderniserstellung anzupassen. Zudem müssen alle vorhandenen Hindernisse gelöscht werden, um Platz für neue Hindernisse mit unterschiedlichen Eigenschaften in der neuen Runde zu schaffen
 
### Spiel pausieren
- Wenn die Leertaste gedrückt wird und der Timer aktiviert ist (`tmrGameTick.Enabled == true`), wird der Timer deaktiviert (tmrGameTick.Enabled = false;).
- Wenn die Leertaste gedrückt wird und der Timer deaktiviert ist, wird er aktiviert (`tmrGameTick.Enabled = true;`). Das Spiel wird fortgesetzt. 
```ruby
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
```

### Ihr schönstes Ergebnis
> Werden zwei neuen Forms erstellt(`FrmMenu`: wird am anfagang angezeit,`FrmOption`)
> Dieser Code definiert für die Click-Ereignisse der beiden Buttons (b_Start und b_options).Beim Klicken auf die Buttons wird ein neues Form erstellt.
Das neue Formular wird mit der Methode ShowDialog() angezeigt, und das alte wird mit `Close()`geschlossen.
```ruby
  private void b_Start_Click(object sender, EventArgs e)
  {
     FrmFrogger frm= new FrmFrogger();
      frm.ShowDialog();
      this.Close();
  }
  private void b_options_click(object sender, EventArgs e)
  {
      FrmOption frmOption = new FrmOption();
      frmOption.ShowDialog();
      this.Close();
      this.Hide();

  }
```
![image](https://github.com/GSO-SW/gdi-reflexion-azarialii/assets/145339205/e1f67b86-0909-4d9b-adda-339e12346de2)






