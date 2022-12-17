# AnastasiaTshnkva-Deriv-Hackathon

Your task is to create a simple Payout Currency Converter using Deriv's 
WebSocket endpoint. The requirements of this task are as the following: 
​ 
1. Create a page with an input field, a dropdown and a table. 
2. Dropdown 
   - List out all the available payout currencies. The selected item in the 
dropdown is the `base_currency` 
3. Input Field 
   - This sets the value of the `base_currency`. 
   - Must be valid currency value. 
4. Table 
   - List out all of the currencies from `exchange_rates` call. 
   - 2 Columns: `Currency` and `Value`. 
      - `Currency` is the currency code (Example: `USD`, `AUD`, etc). 
      - `Value` is the converted value of the `base_currency` entered in the `Input 
Field` to the specified `currency`. 
      - This value must be update on every change on the `Input Field`. 
5. Formatting 
   - Round the USD, AUD and GBP exchange rate values to `2` decimal 
places. Leave the remaining exchange rate values as it is. 
​ 
- You need to initiate a connection to deriv websocket, the `ws` endpoint is: 
`wss://ws.binaryws.com/websockets/v3?app_id=1089`.<br> 
  Note: `1089` can be used as the `app_id`. Registering a new `app_id` is not 
needed. 
​ 
- An example of how you can initiate a websocket connection to deriv 
websocket: 
  Please keep in mind that the `onopen` and `onmessage` event listeners that 
listed below are just examples of how to send message and get response 
with deriv ws connection. You need to find the needed parameters from 
documentation links which provided in the next sections. 
​ 
  ```javascript 
  var ws = new 
WebSocket('wss://ws.binaryws.com/websockets/v3?app_id=1089'); 
   
  ws.onopen = function(evt) { 
      ws.send(JSON.stringify({ticks:'R_100'})); 
  }; 
   
  ws.onmessage = function(msg) { 
     var data = JSON.parse(msg.data); 
     console.log('ticks update: %o', data); 
  }; 
  ``` 
 
​ 
- List of payout currencies can be obtained using the `payout_currencies` 
WebSocket API call. Please check the API Playground for `payout_currencies` 
WebSocket API call - https://api.deriv.com/api-explorer/#payout_currencies 
 
writer.editor.GO_TO_TOPwriter.editor.GO_TO_BOTTOM
