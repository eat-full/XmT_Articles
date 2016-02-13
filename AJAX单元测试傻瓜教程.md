Ajax ���󾭳����׷������󣬿ͻ��˷��͵����ݳ����⣬�������˷��ص��������󶼻ᵼ�� Ajax ��������㲻�ܱ�֤����������������ǹ���������Ajax������Ҫ���û������뷢�͸������������ط�������Ӧ����ˣ��������ݵ���ȷ����������Ҫ��
��������Ajax���첽�ģ���������ͬʱ���뱣֤�����ԣ�������β�����Ajax�����������ͨ�ŵ�ʱ�������е�Ԫ�����أ�
��Ҫ�£������ǿ�һ�������������ӣ�ѧϰһ����ζ�Ajax������е�Ԫ���ԡ�
##����
�����ǿ�ʼ��Ԫ����֮ǰ��������Ҫ��װ��������Ĺ��ߡ�
- �½�һ��Ŀ¼��������ű�Ҫ���ļ�
- ʹ�� `npm install mocha chai sinon` ��װ `Mocha`, `Chai`, `Sinon`

###����������
Ϊ��ʹ����򵥣����ǽ�ֱ��������������в��ԡ�������ϲ�����������еĲ��ԵĻ����������еĽ��Ҳ�����������еĽ����ȫһ�¡�
���ǽ���ʹ�����µ��ļ���Ϊ�������������ҽ�������Ϊ`test.html`��

```
<!DOCTYPE html>
<html>
    <head>
        <title>Mocha Tests</title>
        <link rel="stylesheet" href="node_modules/mocha/mocha.css">
    </head>
    <body>
        <div id="mocha"></div>
        <script src="node_modules/mocha/mocha.js"></script>
        <script src="node_modules/sinon/pkg/sinon-1.12.2.js"></script>
        <script src="node_modules/chai/chai.js"></script>
        <script>mocha.setup('bdd')</script>
        <script src="testApi.js"></script>
        <script src="test.js"></script>
        <script>
            mocha.run();
        </script>
    </body>
</html>
```

ע��`mocha.js`,`mocha.css`,`sinon-1.17.1.js`,`chai.js`���ļ�·������Ϊ������`npm`��װ���ǵģ��������Ƕ���`node_modules`Ŀ¼�¡����� `Sinon`���������Ҫ�����ļ�����ƥ�䰲װ�İ汾����������ʹ�õ��ǰ汾��1.17.1��ͬʱҲע��`testApi.js`,`test.js`�������ļ����������ļ���Ϊ�ҵ�ʵ��ģ��Ͳ����������ҽ����ڽ�������һ�������ǡ�

###ʵ��ģ��
�����������ǽ�����һ��������ģ�飬��ģ�齫�ᷢ��һЩAjax�������ǽ�������������չʾ��ζ�Ajax���е�Ԫ���ԡ�
���ǽ����ļ�����Ϊ`testApi.js`��

```
var testApi = {
    get: function(callback) {
        var xhr = new XMLHttpRequest();
        xhr.open('GET', 'http://jsonplaceholder.typicode.com/posts/1', true);

        xhr.onreadystatechange = function() {
            if(xhr.readyState == 4) {
                if(xhr.status == 200) {
                    callback(null, JSON.parse(xhr.responseText));
                }
                else {
                    callback(xhr.status);
                }
            }
        };

        xhr.send();
    },

    post: function(data, callback) {
        var xhr = new XMLHttpRequest();
        xhr.open('POST', 'http://jsonplaceholder.typicode.com/posts', true);

        xhr.onreadystatechange = function() {
            if(xhr.readyState == 4) {
                callback();
            }
        };

        xhr.send(JSON.stringify(data));
    }
};
```

��δ��뿪����Ӧ�ú���Ϥ������д������������һ��������ʹ��`GET`������ȡ���ݣ���һ��������ʹ��`POST`������������������ݣ���Щ��������ͨ�� Ajax��������������ʹ����[JSONPlaceholder API](http://http://jsonplaceholder.typicode.com/ "JSONPlaceholder API")������һ����ѵ�����REST���������ʹ�����ṩ��ģ�����ݣ��ǳ��ʺϿ��ٲ��ԡ�

###�����������
֮��������Ҫ����һ����ܣ����������ÿ���龰�Ĳ��Լ������ļ�������Ϊ`test.js`��

```
chai.should();

describe('TestAPI', function() {
  //Tests etc. go here
});
```

`Mocha`��ʹ��`describe`������һ�������������ò�����������������Ӳ��Դ���ĵط���
`chai.should()`����������ʹ�� "should style" ���ԡ�����ζ�����ǿ������ɵ���֤���ǵĲ��Խ�����磺`someValue.should.equal(12345)`��

##����GET����
���ǵ�ʾ��ģ������һ��`get`�������ú������Ա��������ط��������͹��������ݡ����ǽ��ᴴ��һ�����Ժ�����֤���ɷ�����ȡ��������һ��JSON���ݡ����Ǹ�`GET`��������`XMLHttpRequest`�����ģ��������ǲ��Ե�ʱ��û�з������������ǵ����ݣ��������ǲ�����ķ���һ�� Http ������ô������β��ܱ�����ķ��������أ�������ܵõ����ص������أ�
���ż������ʱ��͵��� Sinon �����ˡ�����һ��ʼ�ھ���`test.html`�������� Sinon �Ŀ⣬���� Sinon�����ǾͿ���ģ���������Ӧ�����ǿ��Խ�XMLHttpRequest��һ�����������棬���ǳ�֮Ϊ fake XMLHttpRequest���������Ǿ����ڲ��������ɿ���Ajax�����ˡ�
������Ҫ��΢����һ�����ǵĲ���������ܣ������Ǹ���֮���`test.js`�ļ���

```
chai.should();

describe('TestAPI', function() {
    beforeEach(function() {
        this.xhr = sinon.useFakeXMLHttpRequest();

        this.requests = [];
        this.xhr.onCreate = function(xhr) {
            this.requests.push(xhr);
        }.bind(this);
    });

    afterEach(function() {
        this.xhr.restore();
    });


    //Tests etc. go here
});
```

`beforeEach`��`afterEach`�������ǵ�����һ����������ÿһ�εĲ���ǰ�Ͳ��Ժ󱻵��á���ÿһ������֮ǰ������ʵ������һ�� fake XMLHttpRequest ���ҽ�ÿһ���������� fake request ������һ�������У���Щֵ���洢��`this.xhr`��`this.request`�У��������ǾͿ����ڸò����е�����������ʹ���ˡ�

��ÿһ�β���֮������ʹ����`this.xhr.restore`���ָ���ʼ��XMLHttpRequest����

���ڣ����ǿ��Կ�ʼ��`test.js`��д�����ǵĵ�һ�����Լ���

```
it('should parse fetched data as JSON', function(done) {
    var data = { foo: 'bar' };
    var dataJson = JSON.stringify(data);

    testApi.get(function(err, result) {
        result.should.deep.equal(data);
        done();
    });

    this.requests[0].respond(200, { 'Content-Type': 'text/json' }, dataJson);
});
```

���Ƕ�����һ������`data`������JSON�汾`dataJson`��Ϊ���ǽ�Ҫ���ݵ����ݡ���һ�������ǵ�����`testApi.call`,�����Ļص�����������ʹ����`result.should.deep.equal`����֤����ǲ���������������������һ�¡����ǻ�������`done()`�����������Ǹ��� Mocha ���첽��������ˡ������Ҫע��`done`�ǲ��Ժ����е�һ��������
������ǵ�����`this.requests[0].respond`���㻹�ǵ�֮ǰ��`beforeEach`����ô������ÿһ�εĲ��Կ�ʼ֮ǰ�������е� fake XMLHttpRquest ������`this.requests`�С������ǵĲ��Ե���`testApi.get`ʱ����������һ������������󱻴�����`this.requests`��������У�`this.requests[0]`�ʹ������������
ͨ����˵��XMLHttpRequest û��`respond`�����������`respond`������Ӧһ�� fake request�������ڸ���Ӧ������״̬��Ϊ`200`����˼�ǳɹ���Ӧ��ͬʱ�����ǽ���Ӧͷ�е�`Content-Type`����Ϊ`text/json`��������Ϊ���Ǵ��ݵ��� JSON ���ݡ�`respond`�����е����һ��������ʾ��Ӧ�壬���ǽ�������Ϊ֮ǰ�����õ�`dataJson`������
fake XMLHttpRequest ģ����һ�� GET �������Ӧ���ڵõ���Ӧ֮��`testApi.get`�еĻص��������ᱻ���á��ûص������У����ǽ���Ӧ�еõ��Ľ����`data`�������Աȣ�

```
testApi.get(function(err, result) {
    result.should.deep.equal(data);
    done();
});
```

��Ϊ֮ǰ���Ǵ�����`data`��`dataJson`�����������ݵ����ݣ����������Ӧ��ȷ����Ӧ������Ӧ�ñ�������һ������
���ڣ����ǿ�������������������ǵĲ����ˣ���`test.html`�ļ�����Ӧ�ÿ��Կ������ڲ���ͨ������Ϣ��

##����POST����
�����ǵ�ʾ���л���һ����������������ݵ�`post`���������͵������� JSON ��ʽ�ġ����������Ǿ�Ҫ��ɶԸú����Ĳ��ԡ�

```
it('should send given data as JSON body', function() {
    var data = { hello: 'world' };
    var dataJson = JSON.stringify(data);

    testApi.post(data, function() { });

    this.requests[0].requestBody.should.equal(dataJson);
});
```

�ͺ�֮ǰһ�����������ȶ�����һ����������`data`������ JSON ��ʽ�ı���`dataJson`��֮�����ǵ�����`testApi.post`����֮ǰ���� GET ����һ���ĵط��ǣ���һ������ֻ��Ҫ��֤Ҫ�����͵������Ƿ���ȷ��ת������ JSON ��ʽ����Ϊ����ֻ��Ҫ��֤ POST �����з�������������ȷ�ģ�������ǵĻص������ǿյġ�
�öδ��������һ��ʹ����һ��������ȷ���������ݵ���ȷ�ԡ���֮ǰһ��������ʹ���� fake XMLHttpRequest��������һ������Ҫ֤����Я������ȷ�����ݡ�POST ������Я�������ݴ���� fake XMLHttpRequest �� `requestBody`�����У����ǽ�����`dataJson`���Ƚ�����֤���ǵ���Ϊ��

##�������
��Ϊ���һ��ʾ�������������ǲ���һ��ʧ�ܵ�������Ϊ���������п��ܳ��ֺܶ����⣬ͬʱ������Ҳ���ܳ������⣬�������ǲ�Ӧ����������վ���û��Ծ���Ĵ�����Ϣ�е��ɻ����Դ�����Էǳ���Ҫ��
ʾ��ģ���еĻص���������������������һ���������Ǵ�����Ϣ���ڶ�����������ÿһ�� Http ������Ӧ�õ��Ľ�����������£�

```
it('should return error into callback', function(done) {
    testApi.get(function(err, result) {
        err.should.exist;
        done();
    });

    this.requests[0].respond(500);
});
```

�����Ǵ�����ԣ�������һ�����ǲ���Ҫ�κ����ݡ����ǵ�����`testApi.get`��������ص�����������֤ error �����Ĵ��ڡ�Ϊ��ģ����Ӧ�������һ���е� fake XMLHttpRequest ������һ���ڲ������������״̬�� 500 ���������������

##�ܽ�
Ajax����Ĳ����Ǻ���Ҫ�ģ��������֤��ÿһ����������ȷ�ģ���ô��Ӧ�ó����е��������־�����ȫ����ÿһ�� Ajax ����õ������ݡ�
����������ʹ�� JQuery Ajax�����Եķ��������ӵķ�����һģһ���ġ���ͬ������ʹ�� Sinon �е� fake XMLHttpRequests��
��Ȼ��Sinon �в���ֻ�� fake XMLHttpRequest�� ������ fake Server ����ģ���������Ӧ������Ȥ�Ļ�����ȥ Sinon �Ĺ����˽⡣