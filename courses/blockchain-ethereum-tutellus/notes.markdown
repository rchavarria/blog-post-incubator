# Blockchain: conceptos básicos y ampliación sobre Ethereum
##### de Miguel Caballero

- Curso: [Blockchain: conceptos básicos y ampliación sobre Ethereum]
- Autor(es): [Miguel Caballero]
- Plataforma: [Tutellus]
- Tags: blockchain, bitcoin, ethereum, ico

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

Blockchain es la tecnología usada por Bitcoin que aparece en 2008 como un método de pago basado en la criptografía

La palabra Blockchain no nace con Bitcoin, Satoshi Yamamoto no menciona Blockchain para nada en el paper que dió luz a Bitcoin

Bitcoin es antecesor o base de Blockchain

Bitcoin nace como alternativa a la banca tradicional para evitar que la crisis financiera de 2007 se repita

# Plataformas descentralizadas

Blockchain está cambiando la forma de realizar transacciones

Una característica es que es una red descentralizada, una base de datos distribuida, y que nadie (persona o grupo) puede controlar o manipular

# Propiedades de una Blockchain

Podemos ver Blockchain como un libro (de contabilidad) donde cada bloque es una pÃ¡gina del libro

en cada bloque se agrupa cierta información, donde se anotan las transacciones

cada página hace referencia a lo anterior

las páginas rellenas son inmutables

cada parte (nodo) del Blockchain tiene acceso  a toda la base de dato sy su historial, por lo que no se necesita ningún intermediario para verificar los registros que uno quier

la comunicción se hace entre partes, entre nodos, peer-to-peer, nada de tener comunicaciones centralizadas

cada nodo envía información a los demás nodos

"pseudonimato"

hay trazabilidad completa de cada transacción

cada usuario/nodo tiene una dirección única, pero no está obligado a relacionar eso con una persona física

# Internet del valor Vs. internet de la información

en el internet de la información, el valor está en las aplicaciones, no en el protocolo

la gente conoce google,... en lugar de los protocolos: http, smtp, ...

en internet del valor, son los protocolos (bitcoin, ethereum,...) quien proporciona el valor

# Lógica computacional en una Blockchain

los registros de transacciones son ordenados cronológicamente

lo que se graba en Blockchain, permanece para siempre, para bien y para ma

logica computacional: los usuarios pueden configurar algoritmos y reglas que activen automáticamente transacciones entre nodos

dapps: aplicaciones distribuidas,

disponemos un ordenador mundial, distribuido, inmutable,... donde desarrollar dapps (a través de los smart contracts)
  
# Tokens asociados a una Blockchain

coin market cap: pagina de capitalizaciones de criptomonedas
  
la mayoría de las criptomonedas son blockchain, están basadas en blockchain
  
cada bloque de la blockchain tiene un determinado tamaño, lo que hace que guarde cierta cantidad de información. ese tamaño influye en la velocidades de transaccion
  
disminuye las tarifas para consolidar una transacción
  
perjudica alos mineros, pq cobran menos por minar/cerrar una transacción
  
# Entendiendo Ethereum (1)

etherscan.io es una página donde puedes ver el estado de la blockchain de ethereum

analiza bloques y muestra cierta info almacenado en ellos
  
en cada bloque podemos ver las transacciones que hay almacenadas en ellas: tenemos el hash, el número de bloque, de dónde y hacia dónde va, los Ethers transmitidos,...
  
el destino puede ser un wallet o un smart contract
  
gas limit: tope de gas/dinero que pones para realizar una transacción
  
gwei: es realmente el precio que fijas para esa transacción
  
gas * gwei = nos da un valor de Ether, que sería el coste de transacción
                             
los fees, no dependen de lo que quieras transmitir, si no del gas y del gwei

# Entendiendo Ethereum (2)

myetherwallet es un walet para trabajar con erc20 (ether)

vesting? habla de enviar ether a un smart contract, y que tiene un período de "vesting" donde el dueño de contract no puede vender ese ether

hay un apartado de gráficas, donde se pueden ver distintas gráficas. una de ellas es la de la cola de transacciones pendientes. si está muy alta, si hay muchas transacciones pendientes, quiere decir que son muy complejas/grandes y que los mineros estÃ¡n tardando mucho en consolidarlas. puedes saltarte la cola si pones más gas limit o más gwei, para pagar más a los mineros por la transacción

# Entendiendo Ethereum (3)

más graficas en etherscan

gráfica: los fees de transacción

cuanta más alta, signfica que puede haber saturación en la red

proof of work

proof of state: para intentar mejorar la eficiencia de la red, la velocidad de las transacciones

erc20 es un token compatilbe con ethereum

ehterscan.io es el sitio donde mirar qué ha pasado con una transacción: si está aceptada o rechazada, qué wallets han intervenido, cuantos mineros la han consolidado, gas, gwei,...

# Qué es un Wallet y para qué sirve

wallet = monedero donde guardar los tokens

hay wallets web, software y hardware

myetherwallet es un servicio muy usado

uno puede tener tantos wallet como quiera

# Conceptos generales de costes: Gas limit y Gwei

para saber el gwei a usar (para que la transacción se haga con rapidez) antes de hacer una transacción, se recomienda echar un vistazo a etherscan.io, para echar un vistazo a los gwei del momento

si hay muchas transacciones por consolidar, no es buen momento para hacer nuestra transaccion

si hay muchas trx con gwei muy alto, sería mejor esperar, para no tener que poner un gwei tan alto

# Creación de un Wallet en Myetherwallet

A partir de una contraseña, MyEtherWallet te genera un fichero JSON que sirve como clave de tu wallet

También se genera una clave privada, que puedes imprimir, o guardar en fichero de texto,...

El wallet tiene una dirección pública, que es donde puedes enviar tus Ether

La gente suele tener varios wallet: uno para el día a día, con poco dinero; otro más seguro, donde almacenas mucho más $$$$

MyEtherWallet te permite acceder a tu wallet de distintas formas

MyEtherWallet almacena tokens compatibles ERC20

# Envío de tokens y ETH desde Myetherwallet

Para enviar hace falta: dirección de destino, cantidad de token/Ether a enviar, Gas Limit (suele ser de 200K hoy en dia), GWEI (prestar atención a este)

Cuidadín donde guardas la clave privada o el fichero de acceso

# Cómo usar Metamask, la extensión para gestionar Wallets

metamask es una extensión de chrome

actúa como wallet dentro del navegador

también está para FF y Opera

metamask puede importar un wallet (de myetherwallet p.e.) solamente proporcionando la clave privada o el fichero json O_o

# Recomendaciones finales

documento en tutellus.io sobre "cómo comprar tokens"

ahíi enseñan a comprar tokens TUT en la ICO de tutellus.io

# Referencias

[Blockchain: conceptos básicos y ampliación sobre Ethereum]: https://app.tutellus.com/cuaderno/blockchain-conceptos-basicos-y-ampliacion-sobre-ethereum-18512
[Miguel Caballero]: https://twitter.com/mcaballero
[Tutellus]: https://www.tutellus.com
