Proposed inline Js API.
Still trying to simplify it.

```js

const pubkey = "pk_y9nZvo4LLVtdEHzTDJH8M9";

const woven = new WovenPay(pubkey);

const callback = (response) => console.log(response);

const payload = {
  method: "mobile" // Only mobile options will be available not cards. For cards only use method: "card". Defaults to "all" if not provided
  amount: 20,
  label: "Valid Shop",
  customer: {
    email: "customer@test.com"
  },
  order: {
    description: "Payment of 100 sweets"
  },
  reference: "myuniquereference"  
}

woven.checkout(payload, [callback]? optional);

// Add Event Listeners
woven.on('checkout.closed', callback);
woven.on('checkout.created', callback);
woven.on('checkout.response', callback);
woven.on('checkout.error', callback);

// Forcefully close the checkout form
woven.close(); 
```
