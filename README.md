## puffsjs

A highly optimised, light-weight JS utility for [PUFFScoin](http://www.puffscoin.leafycauldronapothecary.com/) based on [`web3.js`](https://github.com/puffscoin/web3.js), but lighter, async only and using `BN.js`.

Only **106 kB** minified!

## Install

```
npm install --save puffsjs
```

## CDN

```
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/puffsjs@0.3.4/dist/ethjs.min.js"></script>
```

Note, exports to `window.Eth` global.

## Usage

```js
const Puffs = require('puffsjs');
const eth = new Puffs(new Puffs.HttpProvider('https://ropsten.infura.io'));

eth.getBlockByNumber(45300, true, (err, block) => {
  // result null { ...block data... }
});

const puffsValue = Puffs.toWei(72, 'puffs');

// result <BN: 3e733628714200000>

const tokenABI = [{
  "constant": true,
  "inputs": [],
  "name": "totalSupply",
  "outputs":[{"name": "","type": "uint256"}],
  "payable": false,
  "type": "function",
}];

const token = eth.contract(tokenABI).at('0x6e0E0e02377Bc1d90E8a7c21f12BA385C2C35f78');

token.totalSupply().then((totalSupply) => {
  // result <BN ...>  4500000
});

// token.transfer( ... ).then(txHash => eth.getTransactionSuccess(txHash)).then(receipt => console.log(receipt));
```

## About

A simple module for building dApps and applications that use PUFFScoin.

Please see our complete [`user-guide`](docs/user-guide.md) for more information.

## Guides

You'll find more detailed information on using `puffsjs` and tailoring it to your needs in our guides:

- [User guide](docs/user-guide.md) - Usage, configuration, FAQ and complementary tools.
- [Developer guide](docs/developer-guide.md) - Contributing to `puffsjs` and writing your own code and coverage.


## Licence

This project is licensed under the MIT license, Copyright (c) 2016 Nick Dodson. For more information see LICENSE.md.

```
The MIT License

Copyright (c) 2016 Nick Dodson. nickdodson.com

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
