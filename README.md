# OriginStamp TypeScript Fetch Client

[![Build Status](https://travis-ci.com/OriginStampTimestamping/originstamp-client-typescript-fetch.svg?branch=master)](https://travis-ci.com/OriginStampTimestamping/originstamp-client-typescript-fetch)

![](https://resources.originstamp.com/images/logo/originstamp-logo-landscape-mc_248x53.png)


> A TypeScript Fetch implementation of the OriginStamp API. For endpoint documentation see [OriginStamp Documentation](https://docs.originstamp.com).

For more information, please visit [https://originstamp.com](https://originstamp.com).

## Install

```
npm install originstamp-client-fetch@2.0.0 --save
```

## Specifications

Environment

* Node.js
* Webpack
* Browserify

Language level

* ES5 - you must have a Promises/A+ library installed
* ES6

Module system

* CommonJS
* ES6 module system

It can be used in both TypeScript and JavaScript. In TypeScript, the definition should be automatically resolved
via `package.json`. ([Reference](http://www.typescriptlang.org/docs/handbook/typings-for-npm-packages.html))

## Getting Started

The following contains an example for Angular (can be easily transferred to other TypeScript/JavaScript projects):

```typescript
import {Component} from '@angular/core';
import {APIKeyApi, BulkApi, ProofApi, SchedulerApi, TimestampApi, WebhookApi} from 'originstamp-client-fetch';

@Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.css']
})
export class AppComponent {

    constructor() {
        this.test();
    }

    private test(): void {
        const hash = '<INPUT_HASH>';
        const seedId = '<SEED_ID>';
        const authorization = '<YOUR_API_KEY>';


        const apiKeyApi = new APIKeyApi();
        apiKeyApi.getApiKeyUsage(authorization).then(result => {
            console.log(result);
        });

        const schedulerApi = new SchedulerApi();
        schedulerApi.getActiveCurrencies(authorization).then(result => {
            console.log(result);
        });

        const timestampApi = new TimestampApi();
        timestampApi.createTimestamp(authorization, {
            hash: hashString,
            comment: 'comment',
            notifications: null
        }).then(result => {
            console.log(result);
        });

        timestampApi.getHashStatus(authorization, hashString).then(result => {
            console.log(result);
        });

        timestampApi.getSeedStatus(authorization, seedId).then(result => {
            console.log(result);
        });

        const proofApi = new ProofApi();
        proofApi.getProof(authorization, {proofType: 1, hash_string: hashString, currency: 0}).then(result => {
            console.log(result);
        });

        const bulkApi = new BulkApi();
        bulkApi.createBulkTimestamp(authorization, {
            timestamps: [{
                hash: hashString,
                comment: 'comment',
                notifications: null
            }]
        }).then(result => {
            console.log(result);
        });
        bulkApi.getSeedStatus(authorization, seedId).then(result => {
            console.log(result);
        });

        const webhookApi = new WebhookApi();
        // ...
    }
}
```

For more information on the requests and the DTOs, we refer to our [JavaScript Client](https://www.npmjs.com/package/originstamp-client-javascript).

## Author

mail@originstamp.com
