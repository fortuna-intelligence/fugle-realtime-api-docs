## Tick

Get tick of a specified symbol.

* **URL**

  /realtime/tick

* **Method:**

  `POST`

* **URL Params**

  None

* **Data Params**

  **Interface:**

  ```ts
  interface ITickReq {
    symbolId: string;
  }
  ```

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content-Type:** `application/json` <br />
    **Interface:**

    ```ts
    interface ITickRes {
      time: Date;
      date: number;
      mode: string;
      symbol: {
        id: string;
        index: boolean;
      };
      buy5: [number, number][];
      sell5: [number, number][];
      ticks: {
        time: Date;
        status: string[];
        value: [number, number];
        total: [number, number];
        serial: string;
      }[];
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
    **Description:** `symbold` must be provided

{% method %}
* **Sample Call:**

{% sample lang="sh" %}
```sh
curl -H "Content-Type: application/json" -X POST -d '{"date": "20171228"}' https://realtime-api-1.fugle.tw/realtime/work|jq
```

{% sample lang="js" %}
```js
fetch('/realtime/tick', {
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
