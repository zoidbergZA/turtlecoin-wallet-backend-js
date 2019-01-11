# turtlecoin-wallet-backend

Provides an interface to the TurtleCoin network, allowing wallet applications to be built.

* Downloads blocks from the network, either through a traditional daemon, or a blockchain cache for increased speed
* Processes blocks, decrypting transactions that belong to the user
* Sends and receives transactions

## Building

`git clone https://github.com/zpalmtree/turtlecoin-wallet-backend.git`

`cd turtlecoin-wallet-backend`

`npm install -g yarn` (Skip this if you already have yarn installed)

`yarn build`

Generated javascript files will be written to the dist/lib/ folder.

## Running tests

`yarn test`

## Building documentation

`yarn docs`

## Contributing

Please run `yarn style` to ensure your changes adhere to the tslint rules before committing.

You can try running `yarn style --fix` to automatically fix issues.

## Quick Start

### Javascript

```javascript
const WB = require('turtlecoin-wallet-backend');

(async () => {
    const daemon = new WB.ConventionalDaemon('127.0.0.1', 11898);
    
    const wallet = WB.WalletBackend.createWallet(daemon);

    console.log('Created wallet');

    await wallet.init();

    console.log('Initialized wallet');

    wallet.start();

    console.log('Started wallet');

    /* After some time...
    wallet.stop();
    */

})().catch(err => {
    console.log('Caught promise rejection: ' + err);
});
```

### Typescript

```typescript
import { WalletBackend, ConventionalDaemon } from 'turtlecoin-wallet-backend';

(async () => {
    const daemon: ConventionalDaemon = new ConventionalDaemon('127.0.0.1', 11898);
    
    const wallet: WalletBackend = WalletBackend.createWallet(daemon);

    console.log('Created wallet');

    await wallet.init();

    console.log('Initialized wallet');

    wallet.start();

    console.log('Started wallet');

    /* After some time...
    wallet.stop();
    */

})().catch(err => {
    console.log('Caught promise rejection: ' + err);
});
```

## Documentation

You can view the documentation here: https://turtlecoin.github.io/turtlecoin-wallet-backend-js/

Alternatively, open up docs/index.html in your web browser.
