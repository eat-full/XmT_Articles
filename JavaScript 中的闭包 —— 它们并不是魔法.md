���źܶ� JavaScript �ĳ�ѧ�������հ��������ϣ�������ٶ�������һЩ���ѡ�����ͨ����ƪ���£��򵥵�˵һ��ʲô�Ǳհ���������ѧ�߽��һ�����е��ɻ�

һ���������� JavaScript �ĺ��ĸ����ô�հ���ʵ��������⡣Ȼ����ͨ���Ķ�һЩѧ���Ե����»��ߴ���ѧ���Է������Ϣ�����Ǻ������հ���ʲô�ģ���ֻ��е���ɬ�Ѷ���

����ϣ��ͨ��һЩ JavaScript �ľ��庯��ʾ����������������ӣ����ô�Ҹ���һ�±հ���

```
function sayHello(name){
    var text = 'Hello ' + name;
    var sayAlert = function(){ alert(text); }
    sayAlert();
}
```

<input class="codeButton" value="sayHello('Bob');" onclick="sayHello('Bob');" type="button">
<script>
function sayHello(name){
    var text = 'Hello ' + name;
    var sayAlert = function(){ alert(text); }
    sayAlert();
}
</script>

##�հ���ʾ��

���仰�ܽ᣺
1���հ����صĺ������� ���� �ں�������֮����Ȼ�����ã�
2���հ���һ����ջ֡�����ں������غ󲢲��ᱻ�ͷš�

����Ĵ����з�����һ�����������ã�

```
function sayHello2(name){
    var text = 'Hello ' + name; // local variable
    var sayAlert = function(){ alert(text); }
    return sayAlert;
}
```

<input value="var say2 = sayHello2('Jane');
say2();" id="btn2" class="codeButton" onclick="var say2 = sayHello2('Jane');say2();window['say2x'] = say2;" type="button">
<script>
    // Ignore this: it just sets the text for the button: Done this way so button has two lines of text.
    document.getElementById('btn2').value = "var say2 = sayHello2('Jane');\nsay2();" 
</script>
<script>
    function sayHello2(name) {
        var text = 'Hello ' + name;
        var sayAlert = function() { alert(text); }
        return sayAlert;
    }
</script>

������� JavaScript �ĳ���Ա���������Ĵ�����һ����������������η���һ�������ġ�����㲻֪���Ļ�����ô����Ҫ��ѧϰ�հ�֮ǰ�˽�һ�¡�һ��C���Եĳ���Ա���ܻ���Ϊ�������������һ��ָ������ָ�룬���ұ��� `sayAlert` �� `say2` ����һ��ָ������ָ�롣

��C���Ե�ָ���ָ��� JavaScript �ĺ������������У���ʵ�к����ԵĲ�ͬ���� JavaScript �У�������Ϊһ���������ñ���ͬʱ��Ϊһ��ָ������ָ���һ�����ص�ָ��հ���ָ�롣

����Ĵ����д��ڱհ�����Ϊ�������� `function() { alert(text); }` ������һ������ `sayHello2()` �ڲ������ġ��� JavaScript �У����������һ�������ڲ�ʹ�� `function` �ؼ��֣���ʹ�����һ���հ���

��C���Ժ����������У��ں�������֮�����еı��ر��������ٿ��Է��ʣ���Ϊ���ǵĶ�ջ֡�Ѿ����ƻ��ˡ�

���� JavaScript �У����������һ�������ڲ�������һ����������ô�ñ��غ�������������ú���������֮������Ȼ���Է��ʵġ�����������һ����������ӣ��������Ѿ������� `sayHello2()` ֮�����ǵ����� `function say2();`����Ҫע����ǣ����ǵ��ú�����������ʾ�����ı��Ĵ��룬�Ǻ��� `sayHello2()` �ı��ر�����

```
function() { alert(text); }
```

<input class="codeButton" value="alert(say2.toString()); // show code" onclick="if(!window['say2x']) {alert('Click the above button 1st!')} else alert(say2x.toString()); // show code" type="button">

�������İ�ť����ȡ��ӡ���������������� JavaScript ���롣����Կ���ָ������ı��Ĵ��롣����������������ֵΪ `Jane` ���ı�����Ϊ `sayHello2()` �ı��ر�����������һ���հ����С�

JavaScript ������֮�����ڣ�һ������������ͬʱӵ��һ�����صĶԱհ������á�
