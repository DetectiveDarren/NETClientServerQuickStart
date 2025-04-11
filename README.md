Explica aquí os métodos e variables dos seguintes scripts:
 
 - HelloWorldManager.cs
 OnGUI(): dibuja una interfaz gráfica sencilla que permite al usuario iniciar el juego como Host, Cliente o Servidor.
 
 StartButtons(): muestra botones en pantalla para seleccionar el modo de inicio (Host, Cliente o Servidor).
 
 StatusLabels(): muestra etiquetas que indican el estado actual de la conexión de red.
 
 - HelloWorldPlayer.cs
 Position: almacena la posición del jugador y se sincroniza en la red.
 
 OnNetworkSpawn(): se ejecuta al generar el objeto en la red; si el jugador es el propietario, llama al método Move().
 
 Move(): solicita al servidor una nueva posición aleatoria para el jugador mediante SubmitPositionRequestRpc().
 
 SubmitPositionRequestRpc(): es un RPC que se envía al servidor para asignar una nueva posición aleatoria al jugador.
 
 GetRandomPositionOnPlane(): genera y devuelve una posición aleatoria en el plano de juego.
 
 Update(): actualiza la posición del jugador en cada frame según el valor de la variable de red Position.
 
 - NetworkTransformTest.cs
 Update(): si el objeto se ejecuta en el servidor, calcula una nueva posición en un patrón circular y actualiza la posición del objeto.
 
 - RPCTest.cs
 OnNetworkSpawn(): se llama cuando el objeto de red se genera, si no es el servidor, inicia la cadena de llamadas RPC llamando a TestServerRpc(0).
 
 TestServerRpc(int value): es un RPC que se ejecuta en el servidor cuando es llamado por un cliente, muestra en el registro el valor recibido y llama a TestClientRpc(value) para enviar el valor a todos los clientes.
 
 TestClientRpc(int value): es un RPC que se ejecuta en todos los clientes cuando es llamado por el servidor, muestra en el registro el valor recibido y, si es un cliente, llama a TestServerRpc(value + 1) para enviar de vuelta al servidor el valor incrementado, creando una cadena de llamadas entre el cliente y el servidor.
 
 Explica os seguintes compoñentes do GameObject `NetworkManager`:
 
 - Network Manager: es el componente que maneja el estado de red en un juego multi-jugador.
 
 - Unity Transport: es el transporte recomendado que maneja la transmisión de datos entre el cliente y el servidor.
 
 - Hello World Manager: su función principal es proporcionar una interfaz de usuario simple para iniciar el juego en diferentes modos de red y mostrar el estado actual de la conexión en la pantalla.
 
 
 Explica os seguintes compoñentes do Prefab `Player`:
 
 - Network Object: permite que el objeto sea reconocido y gestionado por el NetworkManager, asegurando que su estado se sincronice correctamente entre el servidor y los clientes.
 
 - Hello World Player: gestiona la lógica específica del jugador en el contexto de la red, como la solicitud de cambios de posición y la recepción de actualizaciones de posición desde el servidor.
 
 - Rpc Test: demuestra el uso de los RPC para la comunicación entre el cliente y el servidor, permitiendo el intercambio de mensajes y la ejecución de funciones de forma remota.
 
 - Network Transform: se encarga de sincronizar la posición, rotación y escala de un objeto a través de la red, asegura que todos los clientes vean el objeto en la misma posición y orientación, manteniendo la coherencia del estado del juego en entornos multijugador.
