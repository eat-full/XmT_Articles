JavaScript Promises �� ECMAscript 6 �����������ԣ�Ŀ�����ṩһ���������������ֱ�۵ķ����������첽����Ľ�����һֱ�� JavaScript Promises �ĳ���Ϊֹ�������첽����Ľ������ǽ����¼������������磺`image.onload`���ͻص�������ɵġ��¼��������ڶ�����Ԫ�������г�Ч���������������һ����ͼƬ��ȫ������֮���յ�֪ͨ�����߰�ÿ��ͼ����˳���յ�֪ͨ�����������أ��㴫�ݸ������е����һ��������Ϊ�ص����������� jQuery �е� `animate()`���������������֮���ܺܺ������Զ���Ĵ��룬��������Զ��������Ҳ�������첽�������� `animate()`��������Ƕ�׵��ûص������أ������֪����������ص���������

JavaScript Promises �ṩ��һ�����ƣ�ͨ�������³���Ժ͸��ٵĻ���������¼�첽�����״̬��

##JavaScript Promises ֧��

JavaScript Promises �� ECMAscript 6 ��׼�е�һ���֣�����������Ӧ��������������϶��õ�֧�֡�Ŀǰ��promise �Ѿ�������汾�� Chrome��FF��Safari �Ѿ�һЩ�ƶ�������еõ�֧�֣�����ϰ���Եģ�IE ����֧��������ԡ���Ϊ IE ��֧�� promise�������ʹ���� es6-promise.js ��ʹ IE ���� promise��

##�﷨
�õģ�������������ʽ���� promise ��ѧϰ��JavaScript Promises �еĺ��Ĳ��־��� `Promise` ���캯����

```
var mypromise = new Promise(function(resolve, reject){
 // �첽�������д�
 // ���� resolve() ����ʾ����ɹ����
 // ���� reject() ����ʾ����ʧ�� 
})
```

�ù��캯���д��ݽ���һ����������������������������������һ���� `resolve()` �������÷����� promise ��״̬�����ó� fulfilled ��ʱ�򱻵��ã���һ������ `reject()` �� promise ��״̬������Ϊ rejected ��ʱ�򱻵��á�һ�� Promise �������ʼ״̬�� pending����ʾ�첽����ļ�ؼ�û�����(fulfilled)Ҳû��ʧ��(rejected)���������ȿ�һ�� JavaScript Promises ��ʵ���������Ӧ�õģ����������У����� image Ԫ���е� URL ��̬����ͼƬ��

```
function getImage(url){
    return new Promise(function(resolve, reject){
        var img = new Image()
        img.onload = function(){
            resolve(url)
        }
        img.onerror = function(){
            reject(url)
        }
        img.src = url
    })
}
```

`getImage()`��������һ�� Promise ��������¼ͼƬ���ص�״̬��������ã�

```
getImage('doggy.gif')
```

���� promise �������ս��������״̬ pending ת���� fulfilled �� rejected�����յ�״̬ȡ��������ͼƬ�Ƿ���سɹ�����ע�������Ѿ���ͼƬ�� URL ���ݸ��� Promise ���������� `resolve()` �� `reject()`�������������������ϣ��������������󱻴�������ݡ�
 
��Ŀǰ������Promises ���ö����״̬����ʾ�����״̬������������û������ġ����������㿴����������Promise �������Ǹ��򵥡���ֱ�ӵĶ����������������������顣

## then() �� catch()
����ʲôʱ����ʵ������һ�� Promise ����then() �� catch() ����������������Ч�ģ��������������첽�����������һ���Ĺ滮����һ����������ӣ�

```
getImage('doggy.jpg').then(function(successurl){
    document.getElementById('doggyplayground').innerHTML = '<img src="' + successurl + '" />'
})
```

�ڱ��δ����У�һ�� doggy.jpg ������ɣ����ǻ���ͼƬ�� `doggyplayground` �� div ����ʾ���ʼ�� `getImage()` ����������һ�� Promise ����������ǿ��Ե��� `then()` ����ʾ����״̬�Ѿ��� resolved�����Ǵ��ݽ� `resolve()` �����е�ͼƬ�� URL �� `then()` ��������Ϊ������

���ͼƬ����ʧ���ֻᷢ��ʲô�أ�`then()` �����ܹ����ܵڶ������������� rejected ״̬�� Promise ����

```
getImage('doggy.jpg').then(
    function(successurl){
        document.getElementById('doggyplayground').innerHTML = '<img src="' + successurl + '" />'
    },
    function(errorurl){
        console.log('Error loading ' + errorurl)
    }
)
```

�������ṹ�У��������ͼƬ�ɹ�����ִ�� `then()` �еĵ�һ���������������ʧ�ܵĻ����ͻ�ִ�еڶ�������������Ҳ����ʹ�� `catch()` �������������

```
getImage('doggy.jpg').then(function(successurl){
    document.getElementById('doggyplayground').innerHTML = '<img src="' + successurl + '" />'
}).catch(function(errorurl){
    console.log('Error loading ' + errorurl)
})
```

���� `catch()` ���ڵ��� `then(undefined,function)`�������������ȼ��ڣ�

```
getImage('doggy.jpg').then(function(successurl){
    document.getElementById('doggyplayground').innerHTML = '<img src="' + successurl + '" />'
}).then(undefined, function(errorurl){
    console.log('Error loading ' + errorurl)
})
```

##ʹ�õݹ鰴˳���������ʾͼƬ

���������һ��ͼƬ��������Ҫ��˳���������ʾ���ǣ�Ҳ����˵����һ���������ʾ����ͼƬ1��һ������ˣ����ֵ�ͼƬ2�ˣ��Դ����ơ�һ�����ǽ���̸�� chaining promises�����ڴ�֮ǰ����������������һ��ʵ�ֵķ���������ʹ�õݹ�õ�ͼƬ�б�Ȼ��ÿһ�ζ����� `getImage()` ������֮���� `then()` ��������һ�ε��� `getImage()` ֮ǰ����ʾĿǰ��ͼƬ�����ѭ��������ֱ������ͼƬ����������ˣ�
 
```
var doggyplayground = document.getElementById('doggyplayground')
var doggies = ['dog1.png', 'dog2.png', 'dog3.png', 'dog4.png', 'dog5.png']
 
function displayimages(images){
    var targetimage = images.shift()
    if (targetimage){
        getImage(targetimage).then(function(url){
            var dog = document.createElement('img')
            dog.setAttribute('src', url)
            doggyplayground.appendChild(dog)
            displayimages(images)
        }).catch(function(url){
            console.log('Error loading ' + url)
            displayimages(images)
        })
    }
}
 
displayimages(doggies)
```

`displayimages()` �����У�ͨ������ `images.shift()` ��˳��Ļ�ȡ��һ��ͼƬ������ÿһ��ͼƬ���������ȵ��� `getImage()` ����ȡͼƬ��Ȼ���ڷ��غ� Promise ����� `then()` �����н�һ��˵����һ���Ķ������ڱ����о����ڵ��� `displayimages()` ֮ǰ���ý�ͼƬ���� div `doggyplayground` ֮�С���ͼƬ����ʧ�ܵ�ʱ���� `catch()` ������������������� `doggies` ����Ϊ��ʱ���ݹ�ֹͣ��

���� JavaScript Promises ʹ�õݹ飬��һ����˳����һϵ���첽����ķ�������һ������ͨ�õķ�������ͨ��ѧϰ chaining promises �ļ��ɡ� 

##Chaining Promises
�����Ѿ�֪�� `then()` �������Ա�һ�� Promise ��ʵ��������˵���������֮��÷������¡�Ȼ������ʵ�����ǿ��Խ���� `then()` ������������������� promises �������ӵ�һ����ָ��ÿһ�� promise ת��Ϊ resolved ״̬֮��÷������¡�ʹ�� `getImage()` ��������˵������ڻ�ȡ��һ��ͼƬ֮ǰ��ȡһ��ͼƬ��

```
getImage('dog1.png').then(function(url){
    console.log(url + ' fetched!')
    return getImage('dog2.png')
}).then(function(url){
    console.log(url + ' fetched!')
})

//Console log:
// dog1.png fetched
// dog2.png fetched!
```

��ô���﷢ʲô��ʲô�أ�ע���һ�� `then()` �����У�

```
return getImage('dog2.png')
```

���д����ȡͼƬ��dog2.png��������һ�� Promise ����ͨ���� `then()` �з���һ�� Promise ������һ�� `then()` �ͻ�����Ǹ� promise ������֮ǰת��״̬Ϊ resolve��ͬʱ�����µ� Promise �������������Ϊ������ͨ���� `then()` �з�����һ�� promise ���󣬾��Ƕ�� promises ���ӵ�һ��Ĺؼ�һ����

ע�����ǿ����� `then()` �м򵥵ķ���һ����̬��ֵ����ֵ���ᱻ������һ�� `then()` ����������Ϊ���Ĳ�����

�ڿ���������ʾ��֮��������Ȼ��֪����һ��ͼƬû�гɹ�����ʱ����ʲô��ʲô��

```
getImage('baddog1.png').then(function(url){
    console.log(url + ' fetched!')
}).catch(function(url){
    console.log(url + ' failed to load!')
}).then(function(){
    return getImage('dog2.png')
}).then(function(url){
    console.log(url + ' fetched!')
}).catch(function(url){
    console.log(url + ' failed to load!')
})

//Console log:
// baddog1.png failed to load!
// dog2.png fetched!
```

`catch()` �� `(undefined, functionref)` ����ͬ����˼������� `catch()` ֮��ĵ���һ�� `then()` ��Ȼִ�С�ע�⣬���ǽ���һ�� promise ����ķ��ط��������� `then()` �����У���ǰһ�� promise ���֮����Ҫͨ�� `then()` �� `catch()` ����������

�������Ҫ��������3��ͼƬ�����ǽ���ֻ��ҪΪ������������һϵ�е� `then()` `then()` `catch()`��

##����һϵ�е� Promises

��������֪���� chaining promises �Ļ����ĸ�������ֶ��ؽ����� promises ���ӵ�һ��ܿ�ͽ���ò��ɹ�������һ���ܳ�����������ֻ��Ҫһ���ӿ� Promise ����ʼ�ķ�����ͨ��һ���ñ�̷�ʽд������ `then()` �͡�`catch()` ����ֱ�����һ�� promises���� JavaScript Promises �У������ܹ������һ���հ׵� Promise ���󣬲���ת��״̬Ϊ resolved��

```
var resolvedPromise = Promise.resolve()
```

����Ҳ������ `Promise.reject()` ������һ���հ׵���״̬�Ѿ��� rejected �� Promise ������ôΪʲô������Ҫһ�������� Promise �����أ�����һ���Ѿ������� promises ������һ��Ŀհ׵� Promise ������˵����Ϊ״̬�Ѿ��� resolved �� Promise ���󽫻��Զ���ת����һ�� `then()` ��������ʼ�����¼�����

���ǿ���ͨ������ `then()` �� `catch()`����ʹ��״̬�� resolved �� Promise ����������һϵ�е� promise��

```
var sequence = Promise.resolve()
var doggies = ['dog1.png', 'dog2.png', 'dog3.png', 'dog4.png', 'dog5.png']
 
doggies.forEach(function(targetimage){
    sequence = sequence.then(function(){
        return getImage(targetimage)
    }).then(function(url){
        console.log(url + ' fetched!')
    }).catch(function(err){
        console.log(err + ' failed to load!')
    })
})
 
//Console log:
// dog1.png fetched
// dog2.png fetched!
// dog3.png fetched!
// dog4.png fetched!
// dog5.png fetched!
```

���ȣ����Ǵ�����һ��״̬Ϊ resolved �� Promise ���󲢳���Ϊ `sequence`��Ȼ���� froEach() ���� `doggies[]` �����е�Ԫ�أ�ͬʱ�� `then()` �� `catch()` �д���ÿһ���Ѿ�������ɵ�ͼƬ�����յĽ����һ������ `then()` �� `catch()` ���������� `sequence` �ĺ��棬ͬʱ���������ÿ��ͼƬ�������ʱ���ᡣ

����һ������£�ʹ�� `for` ѭ������� `forEach()`��

```
var sequence = Promise.resolve()
var doggies = ['dog1.png', 'dog2.png', 'dog3.png', 'dog4.png', 'dog5.png']
 
for (var i=0; i<doggies.length; i++){
    (function(){
        var capturedindex = i
        sequence = sequence.then(function(){
            return getImage(doggies[capturedindex])
        }).then(function(url){
            console.log(url + ' fetched!')
        }).catch(function(err){
            console.log('Error loading ' + err) 
        })
    }())
}
 
//Console log:
// dog1.png fetched
// dog2.png fetched!
// dog3.png fetched!
// dog4.png fetched!
// dog5.png fetched!
```

�� `for` ѭ�����ڲ���Ϊ����ÿһ��ѭ����ȷ�Ļ�� `i` ��ֵ�����ݽ� `then()` �У�������Ҫ����һ���ⲿ�ıհ�����ȡ `i` ��ֵ��û���ⲿ�ıհ���ÿһ�δ��� `then()` �е� `i` ��ֵ����ֻ�����һ��ѭ�� `i` ��ֵ����˵ `doggies.length-1`��

##����һ�� promises
���ǿ�����һ�� promises ���������� promises ���ӵ�һ�����ʹ�������첽�����Ѿ����֮��������ü򵥣�������ÿһ���������֮����¡����磬����Ĵ�����ʹ�� `getImage()` ����ȡ����ͼƬ�������Ǵ���ڡ�promises �������

```
var twodoggypromises = [getImage('dog1.png'), getImage('dog2.png')]
```

`getImage()` ���õ�ʱ�򷵻�һ�� promise��`twodoggypromises` Ŀǰ���������� promises ������ô���Ƕ���һ�� promises ��ʲô�أ����ǿ���ʹ�þ�̬���� `Promise.all()`��

```
Promise.all(twodoggypromises).then(function(urls){
    console.log(urls) // logs ['dog1.png', 'dog2.png']
}).catch(function(urls){
    console.log(urls)
})
```

`Promise.all()` �д�����һ�����Ե����ģ��������������� promise �����ڽ������� `then()` ����֮ǰ����Ҫ�ȴ����� promises ��ɡ�`then()` �����н��ᴫ��һ�������� promise ����ֵ��ɵ����������

��ô����м�ĳһ�� promise ��״̬����� reject ʱ���ᷢ��ʲô����أ��ڸ�����£����е� `then()` ���ֽ��ᱻ���ԣ�ֻ��ִ�� `catch()` ������������������У����һ������ͼƬ����ʧ�ܣ�ֻ����� `catch()` ������ӡһ�����ʧ�ܵ�ͼƬ�� url��

##�ڵõ�����ͼƬ����ʾͼƬ

���ڵ��˸���ʾͼƬ��ʱ���ˡ�


