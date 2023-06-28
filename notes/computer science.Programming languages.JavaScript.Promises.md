---
id: ckv6947pckyqyjmqlv8jplq
title: Promises
desc: ''
updated: 1687824954108
created: 1687824824586
---

```JS
function getWeather() {
	return new Promise(function(resolve, reject) {
		setTimeout(() =>
		resolve("Sunny"), 100);
	});
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
			}}, 100)
	});
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
