# BajaScript V2
## What is BajaScript
+ JavaScript data API
+ Interact with a Niagara station
  + Resolve and Subscribe
  + Database queries
  + Tags and Relations
+ Extensible
+ Not a UI framework

## Resolve and Subscribe
```javascript
var sub = new baja.Subscriber();

sub.attach('changed', function(prop) {
  if(prop.getName() === 'out') {
    console.log('changed: ' + this.get(prop));
  }
});

baja.Ord.make('station:|slot:/Ramp').get({ subscriber: sub});
```

## Database Queries
...

## Tags and Relations
...

## Unit Database support
...

## Promises
### What is a Promise?
+ A unit of asynchronous work
+ Can be fulfilled or rejected
+ Bring try/catch/finally semantics to asynchronous code
+ Can be orchestrated / grouped together

visit [bluebirdjs.com](http://bluebirdjs.com) to get more about Promises 

### Example
```javascript
Promise.join(
  baja.Ord.make('station:|slot:/Services').get(),
  baja.Ord.make('station:|slot:/Drivers').get()
).spread(function (services, drivers) {
  console.log('resolved both components');
  console.log(services.getNavOrd());
  console.log(drivers.getNavOrd());
});
```

### try/catch/finally
```javascript
Promise.try(function () {
  return baja.Ord.make('station:|slot:/Schwervices').get();
})
.catch(function (err) {
  console.log('failed to resolve Services: ' + err);
})
.finally(function () {
  console.log('this runs no matter what');
});
```

## Offline support
...

## RequireJS
```javascript
require(['baja!'], function(baja) {
  baja.outln('now bajascript is running.');
});
```
