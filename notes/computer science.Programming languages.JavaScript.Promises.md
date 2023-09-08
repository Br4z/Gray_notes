---
id: ckv6947pckyqyjmqlv8jplq
title: Promises
desc: ''
updated: 1688237534335
created: 1687824824586
---

The `Promise` object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

A `Promise` is in one of these states:

- pending: initial state, neither fulfilled nor rejected.
- fulfilled: meaning that the operation was completed successfully.
- rejected: meaning that the operation failed.

```JS
function getWeather() {
	return new Promise(function(resolve, reject) {
			setTimeout(() =>
				resolve("Sunny"), 100
			);
		}
	);
};

function getWeatherIcon(weather) {
	return new Promise(function (resolve, reject) {
			setTimeout(() => {
				switch (weather) {
					case "sunny":
						resolve("Sunny icon");
						break;
					default:
						reject("No icon found");
				};
			}, 100);
		}
	);
};

function onSuccess(data) {
	console.log(`Success ${data}`);
}

function onReject(data) {
	console.log(`Rejected ${data}`);
}

function onFinally() {
	console.log("I'm always executed")
}

getWeather()
	.then(getWeatherIcon)
	.then(onSuccess)
	.catch(onReject)
	.finally(onFinally)
```
