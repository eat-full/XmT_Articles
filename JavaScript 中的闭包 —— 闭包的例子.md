##�����ıհ�ʾ��

��һ�£����Ǽ�˵����һ�±հ��ĸ�������㽫�����������հ���

�Ҹ�����Ϊ������ͨ���Ķ����˽�հ���ʱ�������Ƿǳ���ɬ���������ģ���������ѧϰ��һЩ�հ���ʾ��֮�������ͨ�����������ť�˽⵽�հ�����ι����ġ��ҽ��������˽�հ���ι���֮ǰ���úõ�����һ�±����ṩ�����ӡ��������û����ȫ���ձհ�֮ǰ�Ϳ�ʼʹ�ñر��ˣ�����ܻ������ܶ����벻���� bug��

###ʾ��һ

����˵���ˣ����ر������Ǹ��Ƴ����ģ�������һ�����á�����һ�����������ⲿ�������ڵ�ʱ�򣬽���ջ֡�������ڴ��еķ�����

```
function say667() {
    // Local variable that ends up within closure
    var num = 666;
    var sayAlert = function() { alert(num); }
    num++;
    return sayAlert;
}
```

<input value="var sayNumba = say667();
sayNumba();" id="btn3" class="codeButton" onclick="var sayNumba = say667();sayNumba();window['say3x'] = sayNumba;" type="button">
<script>
    // Ignore this: it just sets the text for the button: Done this way so button has two lines of text.
    document.getElementById('btn3').value = "var sayNumba = say667();\nsayNumba();" 
</script>

###ʾ����

����ʾ���е�����ȫ�ֺ�����ͬһ���հ�ӵ��һ�����������ã�������Ϊ���Ƕ��ڵ��� `setupSomeGlobals()`֮��������
 
```
function setupSomeGlobals() {
    // Local variable that ends up within closure
    var num = 666;
    // Store some references to functions as global variables
    gAlertNumber = function() { alert(num); }
    gIncreaseNumber = function() { num++; }
    gSetNumber = function(x) { num = x; }
}
```

<input class="codeButton" value="setupSomeGlobals();" onclick="setupSomeGlobals();document.getElementById('example4setup').style.display='';" type="button">

�����е������������ж�ͳһ�հ��ķ���Ȩ�ޣ������������������ʱ�򣬸ñհ����� setupSomeGlobals() �ı��ر�����

��һ����Ҫע����ǣ��������һ�ε�� setupSomeGlobals()�����д���һ���µıհ����ϵ� gAlertNumber, gIncreaseNumber, gSetNumber �������ô����µıհ����º�����д������ JavaScript �У����ۺ�ʱ����һ�������ڲ�������һ�����������ⲿ������ÿһ�ε���ʱ���ڲ��ĺ����ᱻ������������

###ʾ����

��������������ѧ�����ױհ�����������Ҫ����ȥ��������������һ��ѭ���ж�����һ�����������Ահ��ı��ر������������벻����

```
function buildList(list) {
    var result = [];
    for (var i = 0; i < list.length; i++) {
        var item = 'item' + list[i];
        result.push( function() {alert(item + ' ' + list[i])} );
    }
    return result;
}
 
function testList() {
    var fnlist = buildList([1,2,3]);
    // using j only to help prevent confusion - could use i
    for (var j = 0; j < fnlist.length; j++) {
        fnlist[j]();
    }
}
```

<input class="codeButton" onclick="testList();" value="testList();" type="button">
<script>
    function buildList(list) {
        var result = [];
        for (var i = 0; i < list.length; i++) {
          var item = 'item' + list[i];
          result.push( function() {alert(item + ' ' + list[i])} );
        }
        return result;
    }
    function testList() {
        var fnlist = buildList([1,2,3]);
        // using j only to help prevent confusion - could use i
        for (var j = 0; j < fnlist.length; j++) {
          fnlist[j]();
        }
    }
    </script>

`result.push( function() {alert(item + ' ' + list[i])}` ��һ��ѭ����3�Σ�ÿһ�ζ���һ��������������������� `result` �����С�����㲻��Ϥ�������������ܾ��ù����������ģ�

```
pointer = function() {alert(item + ' ' + list[i])};
result.push(pointer);
```

ע�⣬��������ʾ����ʱ�򣬾������ݡ�item3 undefined��������3�Ρ�������Ϊ������ǰһ������һ����buildList ������ֻ��һ�����ر����ıհ�����������������һ�� `fnlist[j]();` �б����õ�ʱ������ʹ����ͬһ���հ�����������ʹ���˵�ǰ�հ��� `i` ������ `item` ������ֵ������ `i` ��ֵ��3�������ڵ�ѭ����ɵ�ʱ�򣬱��� `i` ��ֵ��3���ұ��� `item` ��ֵ�� `item3`����

###ʾ����
����˵���˱հ��а����κ����ⲿ�����˳�֮ǰ���ⲿ�����������ı��ر�������һ��Ҫע��ľ��ǣ����� `alice` ʵ�����������������������ġ����������������������������������������õ�ʱ�����ǿ��Է��ʱ��� `alice` �ģ���Ϊ���� `alice` �ڱհ��С���ô `sayAlice()();` ����ֱ�ӵ����˴Ӻ��� `sayAlice()` �з��صĺ������á�

```
function sayAlice() {
    var sayAlert = function() { alert(alice); }
    // Local variable that ends up within closure
    var alice = 'Hello Alice';
    return sayAlert;
}
```

<input class="codeButton" value="sayAlice()();" onclick="sayAlice()();" type="button">
<input class="codeButton" value="alert(alice); // ע��: ���� alice ����һ��ȫ�ֱ��������Բ������κη�Ӧ" onclick="alert(alice);" type="button">
<script>
    function sayAlice() {
      var sayAlert = function() { alert(alice); }
      // Local variable that ends up within closure
      var alice = 'Hello Alice';
      return sayAlert;
    }
</script>
    
С��ʾ��ע����� `sayAlert` Ҳ�ڱհ��ڲ������ҿ��Ա������ں��� `sayAlice` �������������������ʣ����߿��Ա��ڲ������ݹ�ķ��ʡ�
    
###ʾ����
���һ��ʾ��˵����ÿһ�κ������ö���Ϊ���ر�������һ�������ıհ���������ÿһ�κ�����������һ���հ���������ÿһ�κ������õ�ʱ��Ż����һ���հ���

```
 function newClosure(someNum, someRef) {
    // Local variables that end up within closure
    var num = someNum;
    var anArray = [1,2,3];
    var ref = someRef;
    return function(x) {
        num += x;
        anArray.push(num);
        alert('num: ' + num + 
            '\nanArray ' + anArray.toString() + 
            '\nref.someVar ' + ref.someVar);
    }
}
```

<input value="closure1 = newClosure(40, {someVar : 'closure 1'});
closure2 = newClosure(1000, {someVar : 'closure 2'});" id="btn6" class="codeButton" onclick="closure1 = newClosure(40, {someVar : 'closure 1'});closure2 = newClosure(1000, {someVar : 'closure 2'});document.getElementById('example6setup').style.display='';" type="button">
<script>
    // Ignore this: it just sets the text for the button: Done this way so button has two lines of text.
    document.getElementById('btn6').value = "closure1 = newClosure(40, {someVar : 'closure 1'});\nclosure2 = newClosure(1000, {someVar : 'closure 2'});" 
</script>
<div id="example6setup" style="display: none;">
        <input class="codeButton" value="closure1(5);" onclick="closure1(5);" type="button">
        <br>
        <input class="codeButton" value="closure2(-10);" onclick="closure2(-10);" type="button">
</div>
<script>
    function newClosure(someNum, someRef) {
      // Local variables that end up within closure
      var num = someNum;
      var anArray = [1,2,3];
      var ref = someRef;
      return function(x) {
          num += x;
          anArray.push(num);
          alert('num: ' + num + 
               '\nanArray ' + anArray.toString() + 
               '\nref.someVar ' + ref.someVar);
        }
    }
</script>