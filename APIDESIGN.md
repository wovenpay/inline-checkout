Proposed inline Js API.
Still trying to simplify it.

```js
const woven = new WovenPay();

const callback = (response) => console.log(response);

const payload = {
  method: "mobile", // Only mobile options will be available. Defaults to "all" if not provided
  amount: 20,
  label: "Valid Shop",
  customer: {
    email: "customer@test.com"
  },
  order: {
    description: "Payment of 100 sweets"
  },
  pubkey: "pk_y9nZvo4LLVtdEHzTDJH8M9",
  reference: "myuniquereference"  
}

woven.checkout(payload);

// Add Event Listeners
woven.on('checkout.closed', callback);
woven.on('checkout.created', callback);
woven.on('checkout.response', callback);
woven.on('checkout.error', callback);

//OR
woven.on(['checkout.error','checkout.response'], callback);


// Forcefully close the checkout form
woven.close(); 
```
