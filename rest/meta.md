## Meta
---
Get meta of a specified symbol.

* **URL**

  /realtime/meta

* **Method:**

  `POST`

* **URL Params**

  None

* **Data Params**

  **Interface:**

  ```ts
  interface IMetaReq {
    symbolId: string;
  }
  ```

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content-Type:** `application/json` <br />
    **Interface:**

    ```ts
    interface IMetaRes {
      time: Date;
      date: number;
      mode: string;
      symbol: {
        id: string;
        name: {
          zh: string;
          en: string;
        };
        industry: string;
        category: string;
        sme: boolean;
        index: boolean;
      };
      volume: {
        total: number
      };
      price: {
        ref: number;
        up: number;
        down: number;
        open: number;
        close: number;
      };
      note: {
        index: boolean;
        abnormal: {
          bool: boolean;
          status: string;
          intro: boolean;
          special: boolean;
          since: Date;
        };
        ten: boolean;
        day: {
          buySell: boolean;
          sellBuy: boolean;
        };
        short: boolean;
        lend: boolean;
        duration: number;
      };
      warrant: {
        price: {
          exer: number;
          upper: number;
          lower: number;
        };
        volume: {
          ytd: {
            exer: number;
            cancel: number;
          };
          bal: number;
        };
        ratio: number;
        expiry: Date;
      };
      other: {
        foreign: boolean;
        deal: {
          unit: number;
          currency: string;
        };
      };
      ip: string;
    }
    ```

* **Error Response:**

  * **Code:** 403 Forbidden <br />
    **Content:** None <br />
    **Description:** Login required

  OR

  * **Code:** 404 Not Found <br />
    **Content:** None <br />
    **Description:** `symbolId` does not exist

  OR

  * **Code:** 422 Unprocessable Entity <br />
    **Content:** None <br />
    **Description:** `symbolId` must be provided

{% method %}
* **Sample Call:**

{% sample lang="sh" %}
```sh
curl -H "Content-Type: application/json" -X POST -d '{"date": "20171228"}' https://realtime-api-1.fugle.tw/realtime/work|jq
```

{% sample lang="js" %}
```js
fetch('/realtime/meta', {
  method: 'POST',
  credentials: 'include',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    symbolId: '2330',
  }),
});
```
{% endmethod %}
