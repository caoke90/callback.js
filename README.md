# callback.js

##use demo for jquery

```javascript
var define= $.define
var require= $.require
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
```
