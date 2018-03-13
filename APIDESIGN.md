Proposed inline Js API.
Still trying to simplify it.

```js

const pubkey = "pk_y9nZvo4LLVtdEHzTDJH8M9";

const woven = new WovenPay(pubkey);

const callback = (ev) => console.log(ev);

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

// Create your own checkout button
let btn = document.createElement("button");
btn.addEventListener("click", function () {
  woven.checkout(payload, [callback]? optional);
});

// Add Event Listeners
woven.on('checkout.closed', callback);
woven.on('checkout.loaded', callback);
woven.on('checkout.complete', callback);
woven.on('checkout.error', callback);

// Forcefully close the checkout form
woven.close(); 
```
