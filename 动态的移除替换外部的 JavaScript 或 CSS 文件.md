��һ���У����Ǽ򵥽�������ζ�̬�����ⲿ JavaScript �� CSS �ļ������������Ǽ���ѧϰ��ζ�̬���Ƴ�/�滻�ⲿ�� JavaScript �� CSS �ļ���

�κ��ⲿ�� JavaScript �� CSS �ļ����������ֶ����صĻ��Ƕ�̬���صģ������Դ�ҳ�����Ƴ���Ȼ���Ƴ�֮��Ľ�����ܲ��������������ġ�

##��̬�Ƴ�һ���ⲿ�� JavaScript �� CSS �ļ�

Ϊ�˴�ҳ�����Ƴ�һ���ⲿ�� JavaScript �� CSS �ļ����ؼ���һ����������ͨ�� DOM ������ `removeChild()` �����������Ǵ��ĵ�ģ�������Ƴ���һ��ͨ�õķ�������ͨ���ⲿ�ļ����ļ������Ƴ�������Ȼ��������������������ͨ�� CSS ���������ǵ���һ�㣬�������ĺ�����������ļ������Ƴ��κ� JavaScript �� CSS �ļ���

```
function removejscssfile(filename, filetype){
    var targetelement=(filetype=="js")? "script" : (filetype=="css")? "link" : "none" //ȷ��Ԫ������
    var targetattr=(filetype=="js")? "src" : (filetype=="css")? "href" : "none" //ȷ��Ԫ���е��������
    var allsuspects=document.getElementsByTagName(targetelement)
    for (var i=allsuspects.length; i>=0; i--){ //�ӽڵ��б������������Ҫ���Ƴ���Ԫ��
    if (allsuspects[i] && allsuspects[i].getAttribute(targetattr)!=null && allsuspects[i].getAttribute(targetattr).indexOf(filename)!=-1)
        allsuspects[i].parentNode.removeChild(allsuspects[i]) //ͨ������ parentNode.removeChild() ���Ƴ�Ԫ��
    }
}
 
removejscssfile("somescript.js", "js") //�Ƴ�ҳ�������г��ֵ� ��somescript.js�� ��Ԫ��
removejscssfile("somestyle.css", "css") //�Ƴ�ҳ�������г��ֵ� ��somestyle.css�� ��Ԫ��
```

�ú���һ��ʼ�͸�����Ҫɾ�����ļ����ͣ�������һ��ҳ�������� "script" �� "link" Ԫ�صļ��ϡ�����������ʱҲ������Ӧ�ı仯��`scr` �� `href`����֮�󣬺���������һ��ѭ�����Ӻ���ǰ���������е�Ԫ�أ�����ļ����Ƿ�ƥ�䡣��������Ӻ���ǰ�ı���˳������һЩҪ˵���ĵط������һ���Ѿ���֤����Ԫ�ر�ɾ���ˣ���ô��������ÿһ�ζ��ᱻ��һ��Ԫ���ƻ���Ϊ���ټ�����ȷ�ı����µļ��ϣ����÷������ˣ��һ��С�ֶΣ�����ʱ�������� undefined Ԫ�أ��������Ҫ�� if ����м�� `allsuspects[i]`�������Ϊ��ɾ��ȷ������Ԫ�أ��͵����� DOM ���� `parentNode.removeChild()`��

��ô������ɾ��һ���ⲿ JavaScript �� CSS �ļ�ʱ�ᷢ��ʲô���أ�������ȫ������������������� JavaScript �У����һ��Ԫ�ش��ĵ��ṹ����ɾ��ʱ�������Ѿ����ع����ⲿ JavaScript �ļ��еĴ�����Ȼ��������������ڴ��С�Ҳ����˵������Ȼ���Է��ʱ������������ⲿ JavaScript �ļ��м��ؽ����Ķ������������ͨ���Ƴ��ⲿ JavaScript �ļ����������ڴ棬���ϵķ����ǲ����еġ������ⲿ�� CSS �ļ��������Ƴ�һ���ļ�ʱ���ļ������е� CSS ����Ҳ�����Ƴ���

##��̬�滻һ���ⲿ�� JavaScript �� CSS �ļ�

```
function createjscssfile(filename, filetype){
    if (filetype=="js"){ //����ļ������ⲿ JavaScript �ļ�
        var fileref=document.createElement('script')
        fileref.setAttribute("type","text/javascript")
        fileref.setAttribute("src", filename)
    }
    else if (filetype=="css"){ //����ļ������ⲿ CSS �ļ�
        var fileref=document.createElement("link")
        fileref.setAttribute("rel", "stylesheet")
        fileref.setAttribute("type", "text/css")
        fileref.setAttribute("href", filename)
    }
    return fileref
}
 
function replacejscssfile(oldfilename, newfilename, filetype){
    var targetelement=(filetype=="js")? "script" : (filetype=="css")? "link" : "none" //ȷ��Ԫ������
    var targetattr=(filetype=="js")? "src" : (filetype=="css")? "href" : "none" //ȷ���������
    var allsuspects=document.getElementsByTagName(targetelement)
    for (var i=allsuspects.length; i>=0; i--){ //��������ڵ��б��е�Ԫ�ز�ƥ��Ҫɾ����Ԫ��
        if (allsuspects[i] && allsuspects[i].getAttribute(targetattr)!=null && allsuspects[i].getAttribute(targetattr).indexOf(oldfilename)!=-1){
            var newelement=createjscssfile(newfilename, filetype)
            allsuspects[i].parentNode.replaceChild(newelement, allsuspects[i])
        }
    }
}
 
replacejscssfile("oldscript.js", "newscript.js", "js") //�� "newscript.js" �ļ��滻���д��� "oldscript.js" �ļ���Ԫ��
replacejscssfile("oldstyle.css", "newstyle", "css") //�� "newscript.css" �ļ��滻���д��� "oldscript.css" �ļ���Ԫ��
```

ע��һ�º��� `createjscssfile()`������ʵ����������һ���������ܵ� `loadjscssfile()`�������ڷ���ֵ�������޸ģ������Ƿ����½���Ԫ�ض����ǽ������ӵ�ҳ���С��� `replacejscssfile()` �е��� `parentNode.replaceChild()` �����µ�Ԫ������ɵ�Ԫ���Ƿǳ��򵥺ͷ���ġ�

##�ܽ�
�����Ĵ��� web Ӧ���У��ܹ������������첽������Ӧ�� JavaScript/CSS �ļ����������Ǿ���֮�ͣ�������ĳЩ����£��Ѿ��Ǳر��ļ����ˡ�ϣ�����ܴ���������ҵ������Ȥ��
