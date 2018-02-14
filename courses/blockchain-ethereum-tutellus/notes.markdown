# Blockchain: conceptos básicos y ampliación sobre Ethereum
##### de Miguel Caballero

Curso: [Blockchain: conceptos básicos y ampliación sobre Ethereum]
Autor(es): [Miguel Caballero]
Plataforma: [Tutellus]
Tags: blockchain, bitcoin, ethereum, ico

# Tabla de contenidos

1. Introducción a Blockchain
2. Plataformas descentralizadas
3. Propiedades de una Blockchain
4. Internet del valor Vs. internet de la información
5. Lógica computacional en una Blockchain
6. Tokens asociados a una Blockchain
7. Entendiendo Ethereum (1)
8. Entendiendo Ethereum (2)
9. Entendiendo Ethereum (3)
10. Qué es un Wallet y para qué sirve
11. Conceptos generales de costes: Gas limit y Gwei
12. Creación de un Wallet en Myetherwallet
13. Envío de tokens y ETH desde Myetherwallet
14. Cómo usar Metamask, la extensión para gestionar Wallets
15. Recomendaciones finales

# Introducción a Blockchain

Blockchain es la tecnología usada por Bitcoin que aparece en 2008 como un mÃ©todo de pago basado en la criptografía

La palabra Blockchain no nace con Bitcoin, Satoshi Yamamoto no menciona Blockchain para nada en el paper que diÃ³ luz a Bitcoin

Bitcoin es antecesor o base de Blockchain

Bitcoin nace como alternativa a la banca tradicional para evitar que la crisis financiera de 2007 se repita

# Plataformas descentralizadas

Blockchain estÃ¡ cambiando la forma de realizar transacciones

Una característica es que es una red descentralizada, una base de datos distribuida, y que nadie (persona o grupo) puede controlar o manipular

# Propiedades de una Blockchain

Podemos ver Blockchain como un libro (de contabilidad) donde cada bloque es una pÃ¡gina del libro

en cada bloque se agrupa cierta informaciÃ³n, donde se anotan las transacciones

cada pÃ¡gina hace referencia a lo anterior

las pÃ¡ginas rellenas son inmutables

cada parte (nodo) del Blockchain tiene acceso  a toda la base de dato sy su historial, por lo que no se necesita ningÃºn intermediario para verificar los registros que uno quier

la comunicciÃ³n se hace entre partes, entre nodos, peer-to-peer, nada de tener comunicaciones centralizadas

cada nodo envía informaciÃ³n a los demÃ¡s nodos

"pseudonimato"

hay trazabilidad completa de cada transacciÃ³n

cada usuario/nodo tiene una direcciÃ³n Ãºnica, pero no estÃ¡ obligado a relacionar eso con una persona física

# Internet del valor Vs. internet de la información

en el internet de la informaciÃ³n, el valor estÃ¡ en las aplicaciones, no en el protocolo

la gente conoce google,... en lugar de los protocolos: http, smtp, ...

en internet del valor, son los protocolos (bitcoin, ethereum,...) quien proporciona el valor

# Lógica computacional en una Blockchain

los registros de transacciones son ordenados cronolÃ³gicamente

lo que se graba en Blockchain, permanece para siempre, para bien y para ma

logica computacional: los usuarios pueden configurar algoritmos y reglas que activen automÃ¡ticamente transacciones entre nodos

dapps: aplicaciones distribuidas,

  disponemos un ordenador mundial, distribuido, inmutable,... donde desarrollar dapps (a travÃ©s de los smart contracts)
  
# Tokens asociados a una Blockchain

coin market cap: pagina de capitalizaciones de criptomonedas
  
la mayoría de las criptomonedas son blockchain, estÃ¡n basadas en blockchain
  
cada bloque de la blockchain tiene un determinado tamaÃ±o, lo que hace que guarde cierta cantidad de informaciÃ³n. ese tamaÃ±o influye en la velocidades de transaccion
  
disminuye las tarifas para consolidar una transacciÃ³n
  
perjudica alos mineros, pq cobran menos por minar/cerrar una transacciÃ³n
  
# Entendiendo Ethereum (1)

etherscan.io es una pÃ¡gina donde puedes ver el estado de la blockchain de ethereum

analiza bloques y muestra cierta info almacenado en ellos
  
en cada bloque podemos ver las transacciones que hay almacenadas en ellas: tenemos el hash, el nÃºmero de bloque, de dÃ³nde y hacia dÃ³nde va, los Ethers transmitidos,...
  
el destino puede ser un wallet o un smart contract
  
gas limit: tope de gas/dinero que pones para realizar una transacciÃ³n
  
guoli (gwei, o algo así): es realmente el precio que fijas para esa transacciÃ³n
  
gas * gwei = nos da un valor de Ether, que sería el coste de transacciÃ³n
                             
los fees, no dependen de lo que quieras transmitir, si no del gas y del gwei

# Entendiendo Ethereum (2)

myetherwallet es un walet para trabajar con erc20 (ether)

vesting? habla de enviar ether a un smart contract, y que tiene un período de "vesting" donde el dueÃ±o de contract no puede vender ese ether

hay un apartado de grÃ¡ficas, donde se pueden ver distintas grÃ¡ficas. una de ellas es la de la cola de transacciones pendientes. si estÃ¡ muy alta, si hay muchas transacciones pendientes, quiere decir que son muy complejas/grandes y que los mineros estÃ¡n tardando mucho en consolidarlas. puedes saltarte la cola si pones mÃ¡s gas limit o mÃ¡s gwei, para pagar mÃ¡s a los mineros por la transacciÃ³n

# Entendiendo Ethereum (3)

mÃ¡s graficas en etherscan

grÃ¡fica: los fees de transacciÃ³n

cuanta mÃ¡s alta, signfica que puede haber saturaciÃ³n en la red

proof of work

proof of state: para intentar mejorar la eficiencia de la red, la velocidad de las transacciones

erc20 es un token compatilbe con ethereum

ehterscan.io es el sitio donde mirar quÃ© ha pasado con una transacciÃ³n: si estÃ¡ aceptada o rechazada, quÃ© wallets han intervenido, cuantos mineros la han consolidado, gas, gwei,...

# Qué es un Wallet y para qué sirve

wallet = monedero donde guardar los tokens

hay wallets web, software y hardware

myetherwallet es un servicio muy usado

uno puede tener tantos wallet como quiera

# Conceptos generales de costes: Gas limit y Gwei

para saber el gwei a usar (para que la transacciÃ³n se haga con rapidez) antes de hacer una transacciÃ³n, se recomienda echar un vistazo a etherscan.io, para echar un vistazo a los gwei del momento

si hay muchas transacciones por consolidar, no es buen momento para hacer nuestra transaccion

si hay muchas trx con gwei muy alto, serÃ­a mejor esperar, para no tener que poner un gwei tan alto

# Creación de un Wallet en Myetherwallet

A partir de una contraseÃ±a, MyEtherWallet te genera un fichero JSON que sirve como clave de tu wallet

TambiÃ©n se genera una clave privada, que puedes imprimir, o guardar en fichero de texto,...

El wallet tiene una direcciÃ³n pÃºblica, que es donde puedes enviar tus Ether

La gente suele tener varios wallet: uno para el dÃ­a a dÃ­a, con poco dinero; otro mÃ¡s seguro, donde almacenas mucho mÃ¡s $$$$

MyEtherWallet te permite acceder a tu wallet de distintas formas

MyEtherWallet almacena tokens compatibles ERC20

# Envío de tokens y ETH desde Myetherwallet

Para enviar hace falta: direcciÃ³n de destino, cantidad de token/Ether a enviar, Gas Limit (suele ser de 200K hoy en dia), GWEI (prestar atenciÃ³n a este)

CuidadÃ­n donde guardas la clave privada o el fichero de acceso

# Cómo usar Metamask, la extensión para gestionar Wallets

metamask es una extensiÃ³n de chrome

actÃºa como wallet dentro del navegador

tambiÃ©n estÃ¡ para FF y Opera

metamask puede importar un wallet (de myetherwallet p.e.) solamente proporcionando la clave privada o el fichero json O_o

# Recomendaciones finales

documento en tutellus.io sobre "cÃ³mo comprar tokens"

ahÃ­i enseÃ±an a comprar tokens TUT en la ICO de tutellus.io


