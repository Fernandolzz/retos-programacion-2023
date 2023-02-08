# Reto #6: Piedra, Papel, Tijera, Lagarto, Spock
#### Dificultad: Media | Publicación: 06/02/23 | Corrección: 13/02/23

## Enunciado

```
/*
 * Crea un programa que calcule quien gana más partidas al piedra,
 * papel, tijera, lagarto, spock.
 * - El resultado puede ser: "Player 1", "Player 2", "Tie" (empate)
 * - La función recibe un listado que contiene pares, representando cada jugada.
 * - El par puede contener combinaciones de "🗿" (piedra), "📄" (papel),
 *   "✂️" (tijera), "🦎" (lagarto) o "🖖" (spock).
 * - Ejemplo. Entrada: [("🗿","✂️"), ("✂️","🗿"), ("📄","✂️")]. Resultado: "Player 2".
 * - Debes buscar información sobre cómo se juega con estas 5 posibilidades.
 */
```
#### Tienes toda la información extendida sobre los retos de programación semanales en **[retosdeprogramacion.com/semanales2023](https://retosdeprogramacion.com/semanales2023)**.

Sigue las **[instrucciones](../../README.md)**, consulta las correcciones y aporta la tuya propia utilizando el lenguaje de programación que quieras.

> Recuerda que cada semana se publica un nuevo ejercicio y se corrige el de la semana anterior en directo desde **[Twitch](https://twitch.tv/mouredev)**. Tienes el horario en la sección "eventos" del servidor de **[Discord](https://discord.gg/mouredev)**.

//Definir un array de permutaciones ganadoras
var a_ganador = arrayOf(
    arrayOf("Tijera", "Papel"),
    arrayOf("Tijera", "Lagarto"),
    arrayOf("Papel", "Piedra"),
    arrayOf("Papel", "Spock"),
    arrayOf("Piedra", "Tijera"),
    arrayOf("Piedra", "Lagarto"),
    arrayOf("Lagarto", "Papel"),
    arrayOf("Lagarto", "Spock"),
    arrayOf("Spock", "Tijera"),
    arrayOf("Spock", "Piedra"),
)

//Definir las variables de condiciones de victoria
var nJugador1 = 0
var nJugador2 = 0
var nEmpate = 0


fun main(){
    game(arrayOf(arrayOf("Piedra","Papel"), arrayOf("Spock","Spock"), arrayOf("Tijera","Lagarto")))
}

fun game(arrayList: Array<Array<String>>) {

    for (value in 0 until arrayList.count()) {

        //Definir la condición de empate
        if (arrayList[value][0]==arrayList[value][1]){
            nEmpate +=1
        }

        //Definir el bucle que recorre las condiciones ganadoras en ambos sentidos para dar puntos al jugador correspondiente
        for (x in 0 until a_ganador.count()) {
            if (a_ganador[x][0] == arrayList[value][0] && a_ganador[x][1]==arrayList[value][1]) {
                nJugador1+=1
            }
            if (a_ganador[x][0] == arrayList[value][1] && a_ganador[x][1]==arrayList[value][0]){
                nJugador2+=1
            }
        }
    }

    /*La condición de "TIE" se cumple ambos jugadores tienen el mismo valor
    */
    if (nJugador2== nJugador1){
        println("Tie")
    }
    //Se descarta la condición de empate si el valor de un jugador supera al otro
    if(nJugador1> nJugador2){
        println("Player 1")
    }
    if(nJugador2> nJugador1){
        println("Player 2")
    }

}
