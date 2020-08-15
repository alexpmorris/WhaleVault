# WHALEVAULT :: *Secure Graphene Cross-Chain Key Store Extension*

git codebase will be uploaded soon.  In the meantime, unzip latest release to inspect codebase.

For developers looking to integrate **WhaleVault** into their sites, the demo app should provide you 
with all you need: https://github.com/alexpmorris/crypto-playpen/tree/master/whalevault

A more detailed overview of WhaleVault may be found at: 
https://whaleshares.io/@alexpmorris/whalevault-secure-graphene-cross-chain-key-store-extension

## Installation
Make sure you only install the extension directly from:
- Chrome Web Store: https://chrome.google.com/webstore/detail/hcoigoaekhfajcoingnngmfjdidhmdon
- Firefox Add-ons: https://addons.mozilla.org/en-US/firefox/addon/whalevault/

Or directly from the official github repo: https://github.com/alexpmorris/whalevault/releases

For your own safety and security, **DO NOT INSTALL FROM ANYWHERE ELSE!**

As an additional precaution, you should only allow **"site access"** to the WhaleVault extension in Chrome for those trusted websites that require it.


---
It's not safe or secure to use your private keys or master passwords directly on a website, even if operated by a trusted party, as it also incentivizes hackers to find site vulnerabilities and exploit them.  Yet this is how many graphene-based sites and services still operate.  This attack vector increases with the type of key required.  Master passwords offer the greatest potential reward, granting an attacker complete control over the account.

On Ethereum, you never have to enter your private key into a website to use a dApp.  You just use a browser extension like MetaMask, and dApp websites can interface with the extension to securely sign and broadcast transactions to the blockchain on its behalf.

WhaleVault aims to bring the security and ease-of-use of MetaMask to all graphene-based blockchains, accessible through a single unified extension.

WhaleVault, based on Steem Keychain, is a better, safer cross-chain way to access all your graphene accounts from both desktop and mobile browsers such as Chrome, Firefox, Brave, and Yandex.  Graphene blockchains supported out-of-the-box include WhaleShares, BitShares, Eos, Steem, Hive, Blurt, Smoke, Telos, Worbli, Golos, Peerplays, Scorum, and Vice.  WhaleVault is also the "key vault of choice" for ShareBits.

The extension injects the WhaleVault API into each website's javascript context, so that any website that you authorize can safely and securely request a signature or encrypt/decrypt a memo without ever having direct access to any of your private keys.

Because it adds functionality to the normal browser context, WhaleVault requires permission to read and write any web page that wishes to access the extension. You can always "view source" of WhaleVault the way you would any Chrome extension or Firefox Add-on, or from the official GitHub repo: https://github.com/alexpmorris/whalevault

For those not using Steem Keychain and/or Hive Keychain, WhaleVault will also act as a polyfill for Steem Keychain, Hive Keychain, and Blurt Keychain for seamlessly and securely transacting with any app or wallet that supports them.  That includes Steem-Engine and Hive-Engine support, all from a single extension!

WhaleVault is a multi-chain fork by @alexpmorris of the Steem Keychain browser extension.  Steem Keychain (repo at https://github.com/MattyIce/steem-keychain) was originally created by @yabapmatt, developed by @stoodkev, and funded by @aggroed. Many thanks to them for creating a great template upon which to build WhaleVault!

## Features
The WhaleVault extension includes the following features:
- Store an unlimited number of Graphene account keys, encrypted with AES
- Securely sign transactions in multiple formats for multiple purposes
- Securely encrypt/decrypt memos
- Securely interact with Graphene-based sites such as WhaleShares, STEEM, 
  BitShares, and EOS, that have integrated with WhaleVault
- Manage transaction confirmation preferences by account and by website
- Locks automatically on browser shutdown or manually using the lock button
- News/alerts feed with domain warnings for alerting users to related 
  crypto site hacks, scams, and other potential phishing attempts

## Website Integration
Websites can currently request the WhaleVault extension to perform the following functions / broadcast operations:
- Send a handshake to make sure the extension is installed
- Encrypt/Decrypt messages encrypted by a private key
- Securely sign transactions in multiple formats for multiple purposes,
  including identity verification for login purposes
- Methods available can return either callbacks or promises

## Installation
Make sure you only install the extension directly from:
- Chrome Web Store: https://chrome.google.com/webstore/detail/hcoigoaekhfajcoingnngmfjdidhmdon
- Firefox Add-ons: https://addons.mozilla.org/en-US/firefox/addon/whalevault/

Or directly from the official github repo: https://github.com/alexpmorris/whalevault/releases

For your own safety and security, **DO NOT INSTALL FROM ANYWHERE ELSE!**

As an additional precaution, you should only allow **"site access"** to the WhaleVault extension in Chrome for those trusted websites that require it.

## Libraries Used
`jquery.js` (v3.3.1), `whale-1.0.0.js` (v1.0.0 beta, maintained by author), and the `eosjs-*.js` libraries (v20.0.0), built directly from nodejs via webpack: https://github.com/EOSIO/eosjs/releases/tag/20.0.0

## Example

An example of a web page that interacts with the extension is included in the "example" folder in the repo. You can test it by running a local HTTP server and going to http://localhost:1337/main.html in your browser.

```
cd example
node node_serve.js  //static server via nodejs
py3_serve  //static server via python3
```

NOTE: On localhost, it will only run on port 1337.

## API Documentation

The WhaleVault extension will inject a "whalevault" JavaScript object into all web pages opened in the browser while the extension is running. You can therefore check if the current user has the extension installed using the following code:

```
if (window.whalevault) {
    // WhaleVault extension installed...
} else {
    // WhaleVault extension not installed...
}
```

### Handshake

Additionally, you can request a "handshake" from the extension to further ensure it's installed and that your page is able to connect to it:

*as callback:*
```
window.whalevault.requestHandshake("appId", function(response) {
    console.log('whalevault: Handshake received!');
    console.log(response);
});
```

*as promise:*
```
var response = await window.whalevault.promiseHandshake("appId");
```

### Signing Transactions

WhaleVault is generally embedded directly into libraries.  For example, it works out-of-the-box with the latest `wlsjs` or `smokejs` libraries simply by setting the following:

* wlsjs: `wlsjs.config.whalevault = window.whalevault;`
* smokejs: `steem.config.whalevault = window.whalevault;`
* steemjs: `steem.config.whalevault = window.whalevault;`
  * requires steemjs fork available here: https://github.com/alexpmorris/steem-js/tree/master/dist


However, WhaleVault can also attempt to transmit the tx without the need for additional chain libraries by setting the chain's `url` in the signing object.  If the tx is accepted, instead of receiving a signature, you would receive the chain's response to the tx.

Here is an example of a `transfer op` for whaleshares:

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
                             { url: 'https://pubrpc.whaleshares.io', operations: ops }, 
                             'Active', 'transfer', 'tx', 
                             function(response) { console.log(response); });
```
