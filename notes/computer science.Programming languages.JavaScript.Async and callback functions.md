---
id: k3e90rcsyek8wtp94q26rbi
title: Async and callback functions
desc: ''
updated: 1688237518082
created: 1688147957886
---

## Synchronus example

```JS
let pizza;

function orderPizza() {
	console.log("Oder pizza");
	setTimeout(() => {
		pizza = "pizza";
	}, 2000);
	console.log("Pizza was ordered");
};

orderPizza();
console.log(`Eat ${pizza}`);
/* Output
Oder pizza
Pizza was ordered
Eat undefined
*/
```

## Asynchronus example

```JS
let pizza;

function orderPizza() {
	console.log("Oder pizza");
	setTimeout(() => {
		pizza = "pizza";
		console.log(`${pizza} is ready`);
	}, 2000);
	console.log("Pizza was ordered");
};

orderPizza();
console.log("Call Qoli");
console.log(`Eat ${pizza}`);
/* Output
Oder pizza
Pizza was ordered
Call Qoli
Eat undefined
Pizza is ready
*/
```

Asynchronus in the that way we can do multiple things while waiting for others to happen. It still doesn't work, but it's a real life example (call a friend, while you wait for the pizza to be served).

More situations can be:

- Data fetching.

- Calling backend API.

- Loading files.

- Timers and intervals.

## Callback functions

```JS
function orderPizza(callback) {
	setTimeout(() => {
		const pizza = "Pizza";
		callback(pizza);
	}, 2000);
};

function pizzaReady(pizza) {
	console.log(`Eat ${pizza}`);
};

orderPizza(pizzaReady);
console.log("Call Qoli");
/* Output
Call Qoli
Eat Pizza
*/
```

Now it works, using callback to "package" a procedure (order a pizza).

## Callback hell

```JS
function thing1 (callback) {
	callback();
};

function thing2 (callback) {
	callback();
};

function thing3 (callback) {
	callback();
};

thing1(() => {
	thing2(() => {
		thing3();
	});
});
```

[[Promises | computer science.Programming languages.JavaScript.Promises]] comes to solve this problem.

The pizza code with primeses will look like this:

```JS
function orderPizza(callback) {
	return new Promise((resolve, reject) => {
			setTimeout(() => {
				const pizza = "Pizza";
				resolve(pizza);
			}, 2000);
		}
	);
};

function pizzaReady(pizza) {
	console.log(`Eat ${pizza}`);
};

orderPizza()
	.then(pizzaReady)
console.log("Call Qoli");
/* Output
Call Qoli
Eat Pizza
*/
```
