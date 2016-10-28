(function($){
    var loading={}
    var models={}

    $.define=function define(name,args){
        loading[name]=true
        models[name]=args
    }
    $.require=function require(name,callback){
        var next=function(){
            require(name,callback)
        }
        if(loading[name]&&models[name].length==1){
            models[name]=models[name][0]()
            loading[name]=false
        }
        //解析
        if(loading[name]&&models[name].length>1){
            var args=models[name]
            var func=args.pop()
            var len=args.length
            var dataArr=[]
            for(var i=0;i<args.length;i++){
                var model=args[i]
                require(model,function(data){
                    dataArr.push(data)
                    if(--len==0){
                        var sync=args.indexOf("$callback")
                        if(sync==-1){
                            models[name]=func.apply(this,dataArr)
                            loading[name]=false
                            next()
                        }else{
                            dataArr[sync]=function(back){
                                models[name]=back
                                loading[name]=false
                                next()
                            }
                            func.apply(this,dataArr)
                        }
                    }
                })
            }
        }else{
            callback(models[name])
        }
    }

})($);
