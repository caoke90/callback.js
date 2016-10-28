# callback.js

##use demo for jquery

```javascript
var define= $.define
var require= $.require
define("hello",[function(a){
    return "hello"
}])
define("world",["hello","$callback",function(hello,callback){
    console.log(hello)
    setTimeout(function(){
        callback("world")
    },1000)

}])
define("demo",["$callback","hello","world",function(callback,hello,world){
    console.log(hello)
    console.log(world)
    setTimeout(function(){
        callback("demo sync")
    },1000)

}])
require("demo",function(demo){
    console.log(demo)
})
```

##demo for m3m4

```javascript
m3m4(function(define,require){
    define("a",[function(a){
        return "a"
    }])
    define("b",["a","$callback",function(a,callback){
        console.log(a)
        setTimeout(function(){
            callback("b sync")
        },1000)
 
    }])
    define("c",["$callback","a","b",function(callback,a,b){
        console.log(b)
        console.log(a)
        setTimeout(function(){
            callback("c sync")
        },1000)
 
    }])
    require("c",function(c){
        console.log(c)
    })
})
```
