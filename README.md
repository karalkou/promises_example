During migrate we have lost part of our code
Implement missing `Parallel` class

Try to do it with minimal amount of code and without complex logic
You free to use any features of ES6 or ES7 if Current version of Google Chrome supporting it.
Do not use any side libraries only native JS.

example on jsbin:
https://jsbin.com/jogekoj/edit?html,output

```javascript
var runner = new Parallel({
	parallelJobs: 2
});

runner
	.job(step1)
	.job(step2)
	.job(step3)
	.job(step4)
	.done(onDone);

function step1(done) {
	console.log('step1');
	setTimeout(done, 100, 'step1');
}

function step2(done) {
	console.log('step2');
	setTimeout(done, 10, 'step2');
}

function step3(done) {
	console.log('step3');
	setTimeout(done, 150, 'step3');
}

function step4(done) {
	console.log('step4');
	setTimeout(done, 50, 'step4');
}

function onDone(results) {
	console.log('onDone', results);
	console.assert(Array.isArray(results), 'result must be an array');
	console.assert(results.length == 4, 'Wrong count of answers');
	console.assert(results[0] === 'step1', 'Wrong answer 1');
	console.assert(results[1] === 'step2', 'Wrong answer 2');
	console.assert(results[2] === 'step3', 'Wrong answer 3');
	console.assert(results[3] === 'step4', 'Wrong answer 4');
}
```

