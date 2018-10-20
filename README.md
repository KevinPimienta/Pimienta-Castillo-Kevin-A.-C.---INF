# Pimienta-Castillo-Kevin-A.-C.---INF
Proyecto 3
class Blackjack
    {
        static string[] cartas = new string[11];
        static string toma0matiene = "";
        static int total = 0, posi = 1, totaldelvato = 0;
        static Random cartaalea = new Random();
        static void Main(string[] args)
        {
            Console.ForegroundColor = ConsoleColor.Black;
            Console.BackgroundColor = ConsoleColor.White;
            Console.Clear();
            Inicio();
        }
        /*
         Inicio le da al crupier un total, nos da dos cartas y nos pide tomar o nos mantener.*/
        static void Inicio()
        {
            totaldelvato = cartaalea.Next(15, 22);
            cartas[0] = Trato();
            cartas[1] = Trato();
            
            do{
                Console.WriteLine("Juego: Blackjack.");
                Console.WriteLine("Se te dio " + cartas[0] + " y " + cartas[1] + ". \nTu total es " + total + ".\nTe gustaria tomar o mantener?");
                toma0matiene = Console.ReadLine();

            } while (!toma0matiene.Equals("tomar") && !toma0matiene.Equals("mantener"));
            Juego();
        }
        /*
         Aqui se quiere ver  si eligieron tomar o mantener, y si se quedaron ver si ganaron y preguntar si quieren o no volver a jugar.*/
        static void Juego()
        {
            if (toma0matiene.Equals("tomar"))
            {
                Tomar();
            }
            else if (toma0matiene.Equals("mantener"))
            {
                if (total > totaldelvato && total <= 21)
                {
                    Console.WriteLine("\nFelicidades. Ganaste el juego. El total del crupier fue de: " + totaldelvato + ".\nTe gustaria jugar de nuevo? s/n");
                    JugarDeNuevo();
                }
                else if (total < totaldelvato)
                {
                    Console.WriteLine("\nHas perdido. El total del crupier fue de: " + totaldelvato + ".\nTe gustaria jugar de nuevo? s/n ");
                    JugarDeNuevo();
                }
            }
            Console.ReadLine();
        }
        /*
         * Hacemos una variable string llamada Carta para 
         * devolver. Luego se lo asignaremos a Cartas[]. 
         * Despues creamos un numero aleatorio entre 1 y 14. Luego, 
         * cambiamos ese numero entero y dependiendo de su resultado asignamos un valor a 
         * la Carta y agregamos una cantidad  a "total". Despues devolvemos 
         * Carta.
         */
        static string Trato()
        {
            string Carta = "";
            int cartas = cartaalea.Next(1, 14);
            switch (cartas)
            {
                case 1:
                    Carta = "Dos"; total += 2;
                    break;
                case 2:
                    Carta = "Tres"; total += 3;
                    break;
                case 3:
                    Carta = "Cuatro"; total += 4;
                    break;
                case 4:
                    Carta = "Cinco"; total += 5;
                    break;
                case 5:
                    Carta = "Seis"; total += 6;
                    break;
                case 6:
                    Carta = "Siete"; total += 7;
                    break;
                case 7:
                    Carta = "Ocho"; total += 8;
                    break;
                case 8:
                    Carta = "Nueve"; total += 9;
                    break;
                case 9:
                    Carta = "Diez"; total += 10;
                    break;
                case 10:
                    Carta = "Jack"; total += 10;
                    break;
                case 11:
                    Carta = "Reina"; total += 10;
                    break;
                case 12:
                    Carta = "Rey"; total += 10;
                    break;
                case 13:
                    Carta = "As"; total += 11;
                    break;
                default:
                    Carta = "2"; total += 2;
                    break;
            }
            return Carta;
        }
        /*
         Agregamos otra carta a nuestra mano y vemos si es Blackjack, perdio o aun hay menos de 21.*/
        static void Tomar()
        {
            posi += 1;
            cartas[posi] = Trato();
            Console.WriteLine("\nTu nuevo total es " + total + ".");
            if (total.Equals(21))
            {
                Console.WriteLine("\nTienes Blackjack. El total del crupier fue de: " + totaldelvato + ".\nTe gustaria jugar de nuevo? s/n");
                JugarDeNuevo();
            }
            else if (total > 21)
            {
                Console.WriteLine("\nTe pasaste. Has perdido. El total del crupier fue de: " + totaldelvato + ".\nTe gustaria jugar de nuevo? s/n");
                JugarDeNuevo();
            }
            else if (total < 21)
            {
                
                do{
                    Console.WriteLine("\nTe gustaria tomar o mantener?");
                    toma0matiene = Console.ReadLine().ToLower();
                } while (!toma0matiene.Equals("tomar") && !toma0matiene.Equals("mantener"));
                Juego();
            }
        }
        /*Con base a la respuesta de jugar o no de nuevo te dice que reinicies el juego o lo cierres*/
        static void JugarDeNuevo()
        {
            string jugardenuevo = "";
            
            do{

                jugardenuevo = Console.ReadLine().ToLower();
            } while (!jugardenuevo.Equals("s") && !jugardenuevo.Equals("n"));
            if (jugardenuevo.Equals("s"))
            {
                Console.WriteLine("\nPrsiona Enter para reincir el juego.");
                Console.ReadLine();
                Console.Clear();
                totaldelvato = 0;
                posi = 1;
                total = 0;
                Inicio();
            }
            else if (jugardenuevo.Equals("n"))
            {
                Console.WriteLine("\nPresiona Enter para acabar.");
                Console.ReadLine();
                Environment.Exit(0);
            }
        }
    }
