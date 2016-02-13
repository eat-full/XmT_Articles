JavaScript �еıհ����������Ū�ñȽ���ã�����Ѿ��������������Ա֮������ೡ������Ϊ��Щ������������ۣ�һ�����ǿ�ʼ�е���ʹ�ñհ����������ʱ��������������һ��ͬ�������壺�� for ѭ���ڲ�ʹ�ñհ���

��������������ѭ������ DOM Ԫ��ʱ��Ϊÿһ�� DOM Ԫ�ض�ע��һ���¼���������������������У��ҳ�����ÿ���б�Ԫ���ڱ����ʱ�������������ʾ�������кţ�

```
function attachEventsToListItems( ) {
    var oList = document.getElementById('myList');
    var aListItems = oList.getElementsByTagName('li');
    for(var i = 0; i < aListItems.length; i++) {
        var oListItem = aListItems[i];
        // Here I try to use the variable i in a closure:
        oListItem.onclick = function() {
            alert(i);
        }
    }
}
```

�����Щ�б�Ԫ�أ��鿴�����

<ul id="myList1">
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
    <li>Fourth item</li>
</ul>
<script type="text/javascript">
// <!--
function attachEventsToListItems1( ) {
    var oList = document.getElementById('myList1');
    var aListItems = oList.getElementsByTagName('li');
    for(var i = 0; i < aListItems.length; i++) {
        var oListItem = aListItems[i];
        oListItem.onclick = function() {
            alert(i);
        }
    }
}
attachEventsToListItems1();
// -->
</script>

��ֵ����鷢���ˡ����е���Щ�б�Ԫ���ڱ���������ľ����ʱ����ֻ����ʾ 4�����ԭ����һ�㸴�ӡ����ǽ�һ������������Ϊ�¼������������̳��� `attachEventsToListItems` �������еı��� `i` ��ֵ�������� for ѭ���еı��� `i` ��ֵ��Ȼ�����ȵ��¼�������ִ�е�ʱ��for ѭ���Ѿ�����˵������ú����б��� `i` ��ֵ�Ѿ������ 4���������ĳ�������Ϊ�����������¼��������ĺ����ڱ�ִ��֮ǰ����û��Ϊ���� `i` ����һ���µ�������
  
�������������õİ취��ͨ���� for ѭ��ִ��һ������Ϊ��ǰ�ı��� `i` ����һ���µ�������

```
function attachEventsToListItems( ) {
    var oList = document.getElementById('myList');
    var aListItems = oList.getElementsByTagName('li');
    for(var i = 0; i < aListItems.length; i++) {
        var oListItem = aListItems[i];
        // Watch this:
        oListItem.onclick = (function(value) {
            return function() {
                alert(value);
            }
        })(i);
    }
}
```

<ul id="myList2">
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
    <li>Fourth item</li>
</ul>
<script type="text/javascript">
// <!--
function attachEventsToListItems2( ) {
    var oList = document.getElementById('myList2');
    var aListItems = oList.getElementsByTagName('li');
    for(var i = 0; i < aListItems.length; i++) {
        var oListItem = aListItems[i];
        oListItem.onclick = (function(value) {
            return function() {
                alert(value);
            }
        })(i);
    }
}
attachEventsToListItems2();
// -->
</script>

����������һ��������δ����з�����ʲô���Ҳ�û��ֱ�Ӵ����¼������������Ǵ�����һ���м亯�� (1)������һ������ (2)�������ò������ݽ����ڲ��ĺ�����Ȼ�������ϵ����˺��� (1)���������� `i` ��Ϊ������� (3)��

```
oListItem.onclick = (��function��1(��value��2) {
    return function() {
        alert(value);
    }
})(��i��)3;
```

ͨ�����øú�����Ϊÿһ�εĵ���������һ���µı�����������Ϊ�������������ں���ִ��ʱ�����ġ������Ļ������Ǿ���Ϊ����µ������������ `i`��

���ڣ����������Ҫʹ�ñ�����ֵ���һ���Ҫ���һЩ���顣��סһ�㣬�����ڳ��Դ����¼�������ʱ��ִ�����н麯����������һ��������Ϊ�¼��������ĺ������ú����̳����н麯���ı��������򣬲����ܷ��ĵ�ʹ����ѭ���ڼ������ֵ��

Ϊ��������С���ɣ�������Ҫ���� JavaScript ���ڲ��ĺܶ๤��ԭ����Щԭ�������������ʹ��ʱ�õ��ĸ��Ҫ�ḻ��������ȴ�ǳ�ʵ�ã�ϣ������ϲ����