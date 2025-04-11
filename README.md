# _REPO_


# Documentacion del codigo
Instrucciones: Es relativomante hacerlo con un txt o hacer un readme.md donde se documentara el codigo, o sobre el codigo. Buscar mas informacion acerca de la documentacion del codigo. 

# Links de importacia
- https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/xmldoc/recommended-tags <br>
- https://rjcodeadvance.com/interfaz-grafico-de-usuario-modernista-multi-window-con-c-version-completa/ <br>
- https://learn.microsoft.com/es-es/dotnet/api/system.text.utf8encoding?view=net-8.0 <br>
- https://learn.microsoft.com/es-es/dotnet/api/system.text.utf8encoding?view=net-8.0 <br>
- https://learn.microsoft.com/es-es/visualstudio/ide/reference/options-text-editor-csharp-formatting?view=vs-2022 <br>
-https://learn.microsoft.com/es-es/visualstudio/ide/reference/options-text-editor-csharp-formatting?view=vs-2022 <br>
- https://cs.uns.edu.ar/~ldm/mypage/data/oc/info/guia_para_la_documentacion_de_proyectos_de_software.pdf<br>
- https://www.codemotion.com/magazine/es/dev-life-es/consejos-para-escribir-documentacion-tecnica-como-un-dev-senior/<br>
- https://www.justinmind.com/es/blog/especificacion-funcional-documentacion/<br>
- documento funcional de un codigo de programacion<br>
- https://learn.microsoft.com/es-es/dotnet/api/system.net.sockets.socketerror?view=net-8.0 <br>
- https://rapidapi.com/accujazz/api/rawg-video-games-database/playground/apiendpoint_e4e2766f-1422-4b88-bd10-22acdb7c9a16 <br>
- https://www.igdb.com/api (este es con Twitch) <br>
- https://rawg.io/apidocs <br>
- https://developer.themoviedb.org/docs/getting-started <br>
- https://www.google.com/search?q=api+de+pel%C3%ADculas&client=firefox-b-d&sca_esv=9520d6856541b429&ei=daf3Z5jbLoSSkdUP4OON-A8&oq=apis+series&gs_lp=Egxnd3Mtd2l6LXNlcnAiC2FwaXMgc2VyaWVzKgIIATIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYRzIKEAAYsAMY1gQYR0i_FVAAWABwAXgAkAEAmAFNoAFNqgEBMbgBA8gBAJgCAaACDZgDAIgGAZAGCJIHATGgB-wEsgcAuAcA&sclient=gws-wiz-serp <br>
- https://platzi.com/blog/12-api-gratis-para-desarrolladores-frontend/ <br>
- https://developer.themoviedb.org/reference/configuration-details <br>
- https://dev.to/rtagliavia/creando-una-base-de-datos-de-peliculas-con-la-api-de-omdb-y-react-of4 <br>
- https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/xmldoc/recommended-tags <br>
- how to build an api in java <br>
- https://www.phidgets.com/education/learn/projects/csharp-gui/?srsltid=AfmBOoqPibKaXRZsXqlFlUgKXdJHfVXW-27TWcvf1KP9XUPGiu3VjX8U<br>
- chat c# github<br>
- https://github.com/AKouki/SignalR-Chat<br>
- https://learn.microsoft.com/es-es/dotnet/standard/base-types/regular-expressions<br>
- (*PATTER/REGEX*): https://www.programiz.com/csharp-programming/regex <br>
- <br>

# TODO

<br>
# Documentacion

    Etiquetas generales usadas para varios elementos: estas etiquetas son el conjunto mínimo de cualquier API.
        <summary>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <remarks> **
    Etiquetas usadas en miembros: estas etiquetas se usan al documentar métodos y propiedades.
        <returns>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <param> *: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <paramref>
        <exception> *
        <value>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
    Formato de salida de documentación: estas etiquetas proporcionan instrucciones de formato para las herramientas que generan documentación.
        <para>
        <list>
        <c>
        <code>
        <example> **
    Reutilización de texto de documentación: estas etiquetas proporcionan herramientas que facilitan la reutilización de comentarios XML.
        <inheritdoc> **
        <include> *
    Generación de vínculos y referencias: estas etiquetas generan vínculos a otra documentación.
        <see> *
        <seealso> *
        cref
        href
    Etiquetas para métodos y tipos genéricos: estas etiquetas solo se usan en métodos y tipos genéricos.
        <typeparam> *: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <typeparamref>
---

Codigo Cliente
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading.Tasks;

namespace Chat_Cliente
{
   
    /// <summary>
    /// Class Client
    /// </summary>

    class Client
    {
        #region VARIABLES
        private IPHostEntry host; // Determina el host local
        private IPAddress iPAddress; // Obtiene la direccion IP Local
        private IPEndPoint localEndPoint; // Crea el punto de enlace local

        //VARIABLES PARA EL SOCKET
        Socket c_Socket; // Crea el socket del cliente
        Socket s_Socket; //Crea el socket del servidor

        #endregion

        //Constructor de la clase cliente, donde al igual que al servidor se le pasa el ip y el nº del puerto
        public Client(string ipLocal, int port){
            host = Dns.GetHostEntry(ipLocal); // Determina el host local
            iPAddress = host.AddressList[0]; //Obtiene la direccion IP local 
            localEndPoint = new IPEndPoint(iPAddress, port); // Crea el punto de enlace local

            c_Socket = new Socket(iPAddress.AddressFamily, SocketType.Stream, ProtocolType.Tcp); //Crear el socket del cliente
            }

        //Metodo de conexion para que el cliente se conecte al servidor
        public void Start_Client()
        {
            c_Socket.Connect(localEndPoint); //Conecta el socket al servidor
            Task.Run(() => RecibirMensaje()); //! Enviar mensajes al servidor metodo

            #region ENVIAR VARIOS MENSAJES AL SERVIDOR

            //Al estar dentro de un bucle while se haran varios mensajes hasta que se cumpla la condicion indicada. 
            while (true)
            {
                Console.WriteLine("Escribe tu mensaje para finalizar la conexion 'fin' ");
                string mg = Console.ReadLine(); //Leer el mensaje

                //! Da igual que el cliente escriba "fin" o "FIN" o combinadno mayusculas y minusculas se va a desconectar igualmente (ya que se pasara a minusculas)

                if (mg.ToLower() == "fin") //Compara el mensaje con "fin" para comprobar que el cliente quiera salir
                {
                    Send(mg); //Envia el mensaje al servidor
                    Close_Client(); //Cierra el socket cuando compruebe que es igual a fin
                    break; //Se rompe el bucle
                }
                    Send(mg); //Mientras que no sea "fin" se siguen enviando mensajes al servidor

            } 
            #endregion
        }

        private void RecibirMensaje()
        {
            byte[] buffer = new byte[1024];
            try
            {
                while (true)
                {
                    int  _b = s_Socket.Receive(buffer);
                    if (_b == 0)
                    {
                        Console.WriteLine("Servidor desconectado");
                        break;
                    }
                    string _smg = Encoding.UTF8.GetString(buffer, 0, _b);
                    Console.WriteLine($"> Servidor Mensaje: {_smg}");

                }

            }catch(Exception ex) {
                Console.WriteLine($"Error: {ex.Message}" );
            }

        }



        //Metodo para enviar mensajes al servidor
        public void Send(string mg) {
            byte[] buffer = new byte[1024]; // Crear un buffuer de 1024 bytes para el mensaje
            buffer = Encoding.UTF8.GetBytes(mg); // Codifica el mensaje en UTF8 
            c_Socket.Send(buffer); //Enviar el mensaje al servidor

        }

        //Metodo para cerrar el socket del cliente
        public void Close_Client()
        {
            c_Socket.Shutdown(SocketShutdown.Both); //Cierra el socket
            c_Socket.Close(); //Cierra el socket
        }
    }
}

---

Codigo Server
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Linq;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading.Tasks;

namespace Chat_Server
{

    /// <summary>
    /// Class Server. 
    /// </summary>

    class Server
    {

        #region VARIABLES
        private IPHostEntry host; //  Determina el host local
        private IPAddress ipAddress; // obtiene la IP del Host
        private IPEndPoint localEndPoint; // Crea el EndPoint para la creacion del socket

        //variables para los sockets
        Socket s_socket;  //Socket del servidor
        Socket client_sock;
        #endregion


        //Constructor de la clase server, donde se le pasa la ip y el nº del puerto.
        public Server(string ipLocal, int port) {
            host = Dns.GetHostEntry(ipLocal); // Determina el host local
            ipAddress = host.AddressList[0]; //Obtiene la direccion IP
            localEndPoint = new IPEndPoint(ipAddress, port); //Crea el EndPoint para el socket 


            try //Con el try_catch se controla si hay errores al crear el socket
            {
            s_socket = new Socket(ipAddress.AddressFamily, SocketType.Stream, ProtocolType.Tcp); // Crear el socket
            s_socket.Bind(localEndPoint); // Asociar el socket con el EndPoint
            s_socket.Listen(10); //Escuchar conexiones entrantes
            }catch(SocketException e) //Si hay un error se lanzara el SocketException
            {
                Console.WriteLine($"Se ha producido un error en el servidor: \n {e.Message}");
            }

        }

        //Metodo para iniciar el servidor
        public void Start()
        {
            Console.WriteLine("... SERVIDOR EN ESPERA ...");

            //! Con este bloque del codigo (que esta comentado) se puede recibir un solo mensaje y luego se cerrrara la conexion del servidor
            #region PARA RECIBIR UN SOLO MENSAJE

            /*
            byte[] buffer = new byte[1024];
            string mg;
            client_sock = s_socket.Accept(); //Acepta la conexion del cliente
            client_sock.Receive(buffer); //Recibe el mensaje del cliente
            mg = Encoding.UTF8.GetString(buffer); //Convertir el mensaje a String
            Console.WriteLine("Mensaje recibido: " + mg );
            */
            #endregion

          #region Para recibir varios mensajes y la conexion no se cierre hasta que el cliente la cierre
            #endregion

            while (true) // Con este bucle es para acpetar la conexion del cliente y recibir varios mensajes
            {
                client_sock = s_socket.Accept(); //Acepta la conexion del cliente

                //! Console.WriteLine($"Cliente conectado desde el puerto: {client_sock.RemoteEndPoint.ToString}"); 
                //! ⤴ no pone la forma corecta del puerto, es decir pone: System.Func`1[System.String]

                Console.WriteLine($"Cliente conectado desde el puerto: " +
                    $"{IPAddress.Parse(((IPEndPoint)client_sock.RemoteEndPoint).Address.ToString())} "); //Con esa sintaxis hace que se muestre por conosola el puerto 

                Task.Run(() => HiloCliente(client_sock)); //Manejar la conexion de cliente en un hilo 

                //TODO Implementar el envio de mensajes al cliente


                //Enviar respuesta al cliente
                Console.WriteLine("Enviar respuesta: ");
                String mg = Console.ReadLine();
                Send(mg);
            
            }

        }

        private void Send(string mg)
        {
            byte[] buffer = new byte[1024];
            buffer = Encoding.UTF8.GetBytes(mg);
            client_sock.Send(buffer);
        }

   

        //Metodo para enviar mensajes al cliente


        //Metodo para manejar la conexion del cliente
        private void HiloCliente(Socket client_sock)
        {
            byte[] buffer = new byte[1024]; //Buffer para recibir los mensajes
           
                try //El try_catch para controlar los posibles errores que ocurran
                {
                while (true)
                {
                int _buffer = client_sock.Receive(buffer);
                    if (_buffer == 0) //se cierra si no hay datos
                    {
                        Console.WriteLine("Cliente desconectado");
                        break; 
                        //Se cortara la conexion, pero el servidor se pondra en estado de "pausa" (el estado del hilo del servidor seria ¿dormido?) 
                    }

                    //Recoge el mensaje enviado del cliente y lo convierte a string, para luego pasarlo a minusculas; y asi poder mostrarlo por pantalla
                    string mg = Encoding.UTF8.GetString(buffer, 0, _buffer).ToLower();
                    Console.WriteLine("Mensaje recibido: " + mg);

                    if (mg == "fin") //si el cliente envia "fin" se cierra la conexion
                    {
                        Console.WriteLine("Cliente cerro la conexion");
                        break;
                    }
                }

                }catch(SocketException e) //En caso de error se lanzara la excepcion
                {
                    Console.WriteLine($"Se ha producciodo un error: {e.Message}");
                }
            //TODO Implementar Finally para finalizar la conexion con el cliente
                 finally
                 {
                    client_sock.Close(); //Cerrar la conexion con el cliente
                 }
           
        }
    }
}
