<h1 align="center">Crafting-SK - Documentation</h1>
<p align="center">Crafting-Sk est un skript permettant d'avoir une table de craft custom.</p><br />

## 🏹 Plus d'informations ?
Vous souhaitez avoir des informations sur comment télécharger et installer ce code ?
Rendez vous sur cette page : [README.md](https://github.com/MaxouLeKangou/Crafting-SK/blob/main/README.md)

## 👨‍💻 crafting table
- **_Cette partie si dessous, est le design de la table de craft._**
```
function craft(p: player):
    open virtual chest inventory with size 6 named "&8Table de craft" to {_p}
    set slot 0,1,2,3,4,5,6,7,8,9,10,14,15,16,17,18,19,23,25,26,27,28,32,33,34,35,36,37,38,39,40,41,42,43 and 44 of {_p}'s current inventory to black glass pane named " "
    set slot 24 of {_p}'s current inventory to item frame named "&cRecette requise"
    set slot 45,46,47,48,50,51,52 and 53 of {_p}'s current inventory to red glass pane named " "
    set slot 49 of {_p}'s current inventory to barrier named "&c&nRetour en jeu"
```
- **_Cette partie si dessous, va vous permettres de gérer vos crafts._**
```
inventory click:
    while name of current inventory = "&8Table de craft":
        set slot 24 of current inventory to item frame named "&cRecette requise"
        set slot 45,46,47,48,50,51,52 and 53 of current inventory to red glass pane named " "

        clicked item = item frame, black glass pane, red glass pane or light green glass pane:
            cancel event
        name of event-item = "&c&nRetour en jeu":
            close player's inventory

        slot 11 and 20 of current inventory = brick named "&cRubis":
            slot 29 of current inventory = stick:
                slot 12,13,21,22,30 and 31 of current inventory = air:
                    set slot 24 of current inventory to diamond sword named "&cLame en Rubis"
                    set slot 45,46,47,48,50,51,52 and 53 of current inventory to light green glass pane named " "
                    clicked slot = 24:
                        set player's cursor to clicked item
                        remove 2 brick named "&cRubis" from current inventory
                        remove 1 stick from current inventory
                        stop

        wait tick
```
- **_Cette partie si dessous, va vous permettres de récupérer vos items à la fermeture de la table de craft._** ⚠️**LES ITEMS DROPS AU SOL**
```
inventory close:
    name of current inventory = "&8Table de craft":
        set slot 0,1,2,3,4,5,6,7,8,9,10,14,15,16,17,18,19,23,24,25,26,27,28,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52 and 53 of current inventory to air
        loop all items in current inventory:
            drop loop-item
```
