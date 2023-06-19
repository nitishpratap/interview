# What is polyfill?

A polyfill is code that implements a feature on web browsers that do not support the feature.
There are so many polyfills available, but I will cover only famous array polyfill code below.

## Polyfill of forEach() method.
```javascript
Array.prototype.myForEach = function(callback){
    for(let i=0; i<this.length; i++){
      callback(this[i],i,this)
    }
}
```
## Polyfill of map() method.
```javascript
Array.prototype.myMap = function(callback){
    const arr = [];
    for(let i=0; i<this.length; i++){
       arr.push(callback(this[i],i,this));
     }
     return arr;
}
```
## Polyfill of filter() method.
```javascript
Array.prototype.myFilter = function(callback){
    const arr = [];
    for(let i=0; i<this.length; i++){
       if(callback(this[i],i,this)){
            arr.push(this[i]);
       }
    }
    return arr;
}
```
## Polyfill of find() method.
```javascript
Array.prototype.myFind = function(callback){
    for(let i=0; i<this.length; i++){
      const res = callback(this[i],i,this);
        if(res){
          return this[i];
        }
     }
     return undefined;
}
```
## Polyfill of reduce() method
```javascript
Array.prototype.myReduce=function(){
   const callback = arguments[0];
   let currentVal = arguments[1];
   for(let i=0; i<this.length; i++){
     let result = callback(currentVal, this[i], i ,this); 
        currentVal = result;
   }
   return currentVal;
}
var logicAlbums = [ ‘Bobby Tarantino’, ‘The Incredible True Story’, ‘Supermarket’, ‘Under Pressure’, ]
var withReduce = logicAlbums.myReduc(function(a, b) { return a + ‘ , ‘ + b}, ‘Young Sinatra’)

```
## Polyfill of every() method
```javascript
Array.prototype.myEvery = function(callback){
   for(let i=0; i<this.length; i++){
     if(!callback(this[i],i,this)){
       return false;
     }
   }
   return true;
}

```

## Polyfill of some() method
```javascript
Array.prototype.mySome = function(callback){
   for(let i=0; i<this.length; i++){
     if(callback(this[i],i,this)){
       return true;
     }
   }
   return false;
}
```
