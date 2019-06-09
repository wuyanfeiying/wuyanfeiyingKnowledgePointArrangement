> ## vue的双向数据绑定原理
1. Vue.js采用的使 “数据劫持+发布/订阅模式”的方式，通过 Object.defineProperty()来劫持各个属性的 setter/getter,在数据变动时发布消息给订阅者（wacther）,触发相应的监听回调。

2. 简单实现
```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <title>双向绑定最最最初级demo</title>
            <meta charset="UTF-8">
        </head>
        <body>
            <div id='app'>
            <input type='text' id='txt'>   
            <p id='show-txt'></p>
            </div>
        </body>
        <script>
            var obj = {} ;
            Object.defineProperty(obj,'txt,{
                get: function(){
                    return obj
                },
                set: function(newValue){
                    document.getElementById('txt'.value = newValue) ; 
                    document.getElementById('show-text').innerHTML = newValue ;
                }
            })

            document.addEventListener('keyup',function(e){
                obj.txt = e.target.value ; 
            })
        </script>
    </html>
```