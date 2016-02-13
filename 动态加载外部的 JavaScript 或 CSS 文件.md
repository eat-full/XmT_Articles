��ͳ����ҳ���м����ⲿ�� JavaScript �ļ����磺.js���� CSS �ļ����磺.css���ķ�������ҳ��� head ��ǩ��������á�

```
<head>
<script type="text/javascript" src="myscript.js"></script>
<link rel="stylesheet" type="text/css" href="main.css" />
</head>
```

�����ַ���Ϊҳ�������ļ�����ҳ�����Դһ��ͬ�����ء��ںܶ�����£����ַ����ܺܺõ��������ǵ����󣬵������첽 Ajax �����ģʽ�У����� JavaScript/ CSS �ļ��ķ�ʽҲ���Խ��Խ���ڱ��̳��У���������һ����ζ�̬�ļ���  JavaScript/ CSS �ļ���

�����֮��Ϊ����һ��ҳ���м���һ�� .js �� .css �ļ�������ζ��Ҫʹ�� DOM ���������ȴ���һ���µ� ��script�� �� ��link�� Ԫ�أ�Ϊ�������ú��ʵ����ԣ����ʹ�� `element.appendChild()` �����ĵ��ṹ���к��ʵ�λ������Ԫ�ء����������ƺ���Щ��������������һ�¾����ʾ����

```
function loadjscssfile(filename, filetype){
    if (filetype=="js"){ //����ļ������ⲿ�� JavaScript �ļ�
        var fileref=document.createElement('script')
        fileref.setAttribute("type","text/javascript")
        fileref.setAttribute("src", filename)
    }
    else if (filetype=="css"){ //����ļ������ⲿ�� CSS �ļ�
        var fileref=document.createElement("link")
        fileref.setAttribute("rel", "stylesheet")
        fileref.setAttribute("type", "text/css")
        fileref.setAttribute("href", filename)
    }
    if (typeof fileref!="undefined")
        document.getElementsByTagName("head")[0].appendChild(fileref)
}
 
loadjscssfile("myscript.js", "js") //��̬���غ���Ӹ� .js �ļ�
loadjscssfile("javascript.php", "js") //�� ��javascript.php�� �ļ���Ϊ JavaScript �ļ���̬����
loadjscssfile("mystyle.css", "css") ////��̬���غ���Ӹ� .css �ļ�
```

��Ϊ�ⲿ�� JavaScript �� CSS �ļ��ڼ������ǿ������κ��Զ�����ļ���չ����β�ģ����磺��`javascript.php`�����������Ĳ��� `filetype` ������ߺ�������Ҫ�����ļ����͡���֪���ļ�����֮�󣬺�����ʹ�ú��ʵ� DOM ���������� Html Ԫ�أ���Ϊ���Ƿ�����ʵ����ԣ����ս�����ӵ� head Ԫ���ڡ����ڣ�������Ҫ����һ�£���������� head Ԫ���з����ļ������ã�

```
document.getElementsByTagName("head")[0].appendChild(fileref)
```

����ͨ������ҳ��� head Ԫ�أ�Ȼ����� `appendChild()`�����´�����Ԫ�����ӵ� head ��ǩ��ĩβ�������⣬��Ӧ����ʶ���Ѿ����ڵ�Ԫ���ǲ�����´�����Ԫ�ز����κ�Ӱ��ġ�Ҳ����˵����������ε��� `loadjscssfile("myscript.js", "js")` �������� head Ԫ�ص�ĩ�˽����������µ� script Ԫ�أ���ָ��ͬһ�� JavaScript �ļ������������Ч�ʽǶ������Ļ�����Ϊ���ҳ�����һ�������Ԫ��ʱ�����˷��˽�������������ڴ档������һ���򵥷�������ֹΪҳ���������ͬ���ļ����÷������Ǽ�¼ÿһ��ͨ�� `loadjascssfile()` �������ļ���ֻ�����µ��ļ���

```
var filesadded="" //�Ѿ����ص��ļ����б�
 
function checkloadjscssfile(filename, filetype){
    if (filesadded.indexOf("["+filename+"]")==-1){
        loadjscssfile(filename, filetype)
        filesadded+="["+filename+"]" //���Ѿ����ص��ļ���������Ѽ����ļ��б���ʽ�� ��[filename1],[filename2],etc��
    }
    else
        alert("file already added!")
}
 
checkloadjscssfile("myscript.js", "js") //�ɹ�����
checkloadjscssfile("myscript.js", "js") //������ļ��������ļ����ᱻ����
```

�Ҹոմ��Ե����˼�⣬һ���ļ��ڱ�����֮���Ƿ�������һ�����ڴ���Ѵ����ļ��б�ı��� `filesadded` �С�

�ڱ����У��ҽ���������һ����ζ�̬�ļ��� JavaScript �� CSS �ļ���������Щ����£�����Ҫ�����Ƴ����滻һ���Ѿ���ӽ�ҳ��� .js �� .css �ļ��������ô���أ�����һ���һ�����ҵĽ̳̣������ڴ���