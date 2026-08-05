

# WHALEVAULT :: *Extensión Segura de Almacén de Claves Cross-Chain para Graphene*

El código base de git se subirá pronto. Mientras tanto, descomprima la última versión para inspeccionar el código base.

Para los desarrolladores que buscan integrar **WhaleVault** en sus sitios, la aplicación de demostración debería proporcionarle 
todo lo que necesita: https://github.com/alexpmorris/crypto-playpen/tree/master/whalevault

Puede encontrar una descripción general más detallada de WhaleVault en: 
https://wlsworld.vip/@alexpmorris/whalevault-secure-graphene-cross-chain-key-store-extension

## Instalación
Asegúrese de instalar la extensión solo directamente desde:
- Chrome Web Store: https://chrome.google.com/webstore/detail/hcoigoaekhfajcoingnngmfjdidhmdon
- Complementos de Firefox: https://addons.mozilla.org/en-US/firefox/addon/whalevault/

O directamente desde el repositorio oficial de GitHub: https://github.com/alexpmorris/whalevault/releases

Para su propia seguridad y protección, **¡NO INSTALE DESDE NINGÚN OTRO LUGAR!**

Como precaución adicional, solo debe permitir el **"acceso al sitio"** a la extensión WhaleVault en Chrome para aquellos sitios web de confianza que lo requieran.


---
No es seguro ni confiable usar sus claves privadas o contraseñas maestras directamente en un sitio web, incluso si es operado por una parte de confianza, ya que también incentiva a los hackers a encontrar vulnerabilidades en el sitio y explotarlas. Sin embargo, así es como funcionan muchos sitios y servicios basados en Graphene. Este vector de ataque aumenta con el tipo de clave requerida. Las contraseñas maestras ofrecen la mayor recompensa potencial, otorgando al atacante control completo sobre la cuenta.

En Ethereum, nunca tiene que ingresar su clave privada en un sitio web para usar un dApp. Simplemente usa una extensión del navegador como MetaMask, y los sitios web de dApps pueden interactuar con la extensión para firmar y transmitir transacciones de manera segura a la blockchain en su nombre.

WhaleVault busca llevar la seguridad y facilidad de uso de MetaMask a todas las blockchains basadas en Graphene, accesibles a través de una única extensión unificada.

WhaleVault es una forma mejor y más segura de acceder a todas sus cuentas de Graphene de manera cross-chain desde navegadores basados en Chrome (incluidos Brave, Opera, Yandex Mobile y Kiwi Mobile), Firefox y Firefox Android. Las blockchains de Graphene compatibles de forma nativa incluyen WhaleShares wlsWorld, BitShares, EOS/Vaulta, Steem, Hive, Blurt, Telos, Golos/CyberWay, Peerplays y Scorum.

La extensión inyecta la API de WhaleVault en el contexto de JavaScript de cada sitio web, de modo que cualquier sitio web que autorice pueda solicitar una firma o cifrar/descifrar un memo de manera segura sin tener acceso directo a ninguna de sus claves privadas.

Dado que agrega funcionalidad al contexto normal del navegador, WhaleVault requiere permiso para leer y escribir cualquier página web que desee acceder a la extensión. Siempre puede "ver el código fuente" de WhaleVault de la misma manera que lo haría con cualquier extensión de Chrome o complemento de Firefox, o desde el repositorio oficial de GitHub: https://github.com/alexpmorris/whalevault

Para aquellos que no usan Steem Keychain y/o Hive Keychain, WhaleVault también actuará como un polyfill para Steem Keychain, Hive Keychain y Blurt Keychain, permitiendo transacciones fluidas y seguras con cualquier aplicación o billetera que los soporte. ¡Esto incluye soporte para Steem-Engine y Hive-Engine, todo desde una sola extensión!

WhaleVault es un fork multi-chain creado por @alexpmorris a partir de la extensión de navegador Steem Keychain. Steem Keychain (repositorio en https://github.com/MattyIce/steem-keychain) fue creado originalmente por @yabapmatt, desarrollado por @stoodkev y financiado por @aggroed. ¡Muchas gracias a ellos por crear una gran plantilla sobre la cual construir WhaleVault!

## Características
La extensión WhaleVault incluye las siguientes características:
- Almacenar una cantidad ilimitada de claves de cuenta de Graphene, cifradas con AES
- Firmar transacciones de forma segura en múltiples formatos para múltiples fines
- Cifrar/descifrar memos de forma segura
- Interactuar de forma segura con sitios basados en Graphene como WhaleShares, STEEM, 
  BitShares y EOS, que se han integrado con WhaleVault
- Gestionar las preferencias de confirmación de transacciones por cuenta y por sitio web
- Se bloquea automáticamente al cerrar el navegador o manualmente usando el botón de bloqueo
- Feed de noticias/alertas con advertencias de dominio para alertar a los usuarios sobre 
  hackeos, estafas y otros intentos de phishing potenciales en sitios de criptomonedas

## Integración en Sitios Web
Actualmente, los sitios web pueden solicitar a la extensión WhaleVault que realice las siguientes funciones / operaciones de transmisión:
- Enviar un handshake para asegurarse de que la extensión está instalada
- Cifrar/Descifrar mensajes cifrados por una clave privada
- Firmar transacciones de forma segura en múltiples formatos para múltiples fines,
  incluida la verificación de identidad para fines de inicio de sesión
- Los métodos disponibles pueden devolver callbacks o promises

## Instalación
Asegúrese de instalar la extensión solo directamente desde:
- Chrome Web Store: https://chrome.google.com/webstore/detail/hcoigoaekhfajcoingnngmfjdidhmdon
- Complementos de Firefox: https://addons.mozilla.org/en-US/firefox/addon/whalevault/

O directamente desde el repositorio oficial de GitHub: https://github.com/alexpmorris/whalevault/releases

Para su propia seguridad y protección, **¡NO INSTALE DESDE NINGÚN OTRO LUGAR!**

Como precaución adicional, solo debe permitir el **"acceso al sitio"** a la extensión WhaleVault en Chrome para aquellos sitios web de confianza que lo requieran.

## Bibliotecas Utilizadas
`jquery.js` (v3.3.1), `whale-1.0.0.js` (v1.0.0 beta, mantenido por el autor) y las bibliotecas `eosjs-*.js` (v20.0.0), compiladas directamente desde nodejs a través de webpack: https://github.com/EOSIO/eosjs/releases/tag/20.0.0

## Ejemplo

Un ejemplo de una página web que interactúa con la extensión se incluye en la carpeta "example" del repositorio. Puede probarlo ejecutando un servidor HTTP local y yendo a http://localhost:1337/main.html en su navegador.

```
cd example
node node_serve.js  //static server via nodejs
py3_serve  //static server via python3
```

NOTA: En localhost, solo se ejecutará en el puerto 1337.

## Documentación de la API

La extensión WhaleVault inyectará un objeto JavaScript "whalevault" en todas las páginas web abiertas en el navegador mientras la extensión esté en ejecución. Por lo tanto, puede verificar si el usuario actual tiene la extensión instalada utilizando el siguiente código:

```
if (window.whalevault) {
    // WhaleVault extension installed...
} else {
    // WhaleVault extension not installed...
}
```

### Handshake

Además, puede solicitar un "handshake" a la extensión para garantizar aún más que está instalada y que su página puede conectarse a ella:

*como callback:*
```
window.whalevault.requestHandshake("appId", function(response) {
    console.log('whalevault: Handshake received!');
    console.log(response);
});
```

*como promise:*
```
var response = await window.whalevault.promiseHandshake("appId");
```

### Firmar Transacciones

WhaleVault generalmente se incrusta directamente en bibliotecas. Por ejemplo, funciona de forma nativa con las últimas bibliotecas `wlsjs` o `smokejs` simplemente estableciendo lo siguiente:

* wlsjs: `wlsjs.config.whalevault = window.whalevault;`
* smokejs: `steem.config.whalevault = window.whalevault;`
* steemjs: `steem.config.whalevault = window.whalevault;`
  * requiere el fork de steemjs disponible aquí: https://github.com/alexpmorris/steem-js/tree/master/dist


Sin embargo, WhaleVault también puede intentar transmitir la tx sin la necesidad de bibliotecas de chain adicionales estableciendo la `url` de la chain en el objeto de firma. Si la tx es aceptada, en lugar de recibir una firma, recibiría la respuesta de la chain a la tx.

Aquí hay un ejemplo de una `transfer op` para whaleshares:

```
var ops = [ 
  ['transfer', 
   { from: 'user', 
     to: 'recip', 
     amount: '5.000 WLS', 
     memo: 'sample xfer'
   }
  ]
];

whalevault.requestSignBuffer('demo', 'wls:user', 
                             { url: 'https://pubrpc.wlsworld.vip', operations: ops }, 
                             'Active', 'transfer', 'tx', 
                             function(response) { console.log(response); });
```
