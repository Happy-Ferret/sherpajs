# sherpa.js

Sherpa.js is a pure JavaScript library that helps consuming sherpa
API's.

Available as npm package "sherpajs":

	https://www.npmjs.com/package/sherpajs

More information about sherpa:

	https://www.ueber.net/who/mjl/sherpa/

If you're using typescript, take a look at sherpats to generate
typescript from sherpadoc:

	https://github.com/mjl-/sherpats


# Usage

You need to know the baseURL for the API, e.g. "https://www.sherpadoc.org/example/".

	sherpa.load('https://www.sherpadoc.org/example/')
		.then(function(example) {
			example.requestCount()
			.then(function(result) {
				alert('Number of requests: '+result);
			}, function(error) {
				alert('Error: '+JSON.stringify(error));
			});
		}, function(error) {
			alert('Error loading API: '+JSON.stringify(error));
		});

Or if you know the functions you need:

	var sherpaJSON = {functions: ['requestCount']} // loaded from https://www.sherpadoc.org/example/sherpa.json
	var example = sherpa.init('https://www.sherpadoc.org/example/', sherpaJSON);
	example.requestCount()
		.then(function(result) {
			alert('Number of requests: '+result);
		}, function(error) {
			alert('Error: '+JSON.stringify(error));
		});
