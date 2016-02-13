2014�꣬Angular�Ŷӷ��������� ECMAScript ���Ե���չ�汾 AtScript��Ϊ��ʹ AtScript �ܹ����������Աʹ�ã�ӵ�����õĿ������飬angular�Ŷ����������������ͼ���ע���﷨(annotations)��������ȥ�ˣ����Ŷ������� AtScript ת���֧�� annotations �� decorators �������Ե� TypeScript.

���ǣ�annotations �� decorators ������ʲô�أ������� TypeScript �������������������أ�����������һ��һ�� annotations ��ת������Լ����� decorators �Ĳ�֮ͬ����

##Annotation

�����ȴ� Annotations ��ʼ��ǰ���ᵽ��Angular �Ŷӿ������� JavaScript ���﷨�� AtScript���������µ��������� Type Annotations������ע�ͣ�, Field Annotations���ֶ�ע�ͣ� and MetaData Annotations��Ԫ����ע�ͣ����������ȴ� metadata annotations ˵��������һ�� Angular2 ��������ӣ�����ͨ�������ӿ�һ�� metadata annotations ���׳�ʲô����

```
@Component({
  selector: 'tabs',
  template: `
    <ul>
      <li>Tab 1</li>
      <li>Tab 2</li>
    </ul>
  `
})
export class Tabs {

}
```

��������������һ�� `Tabs` ���ࡣ����ӵ��һ�� annotations ���� `@Component`����������Ƴ����е� annotations����������һ���յ����ǲ��Ǿ�û���κ������������أ���ˣ�`@Component` ����Ϊ `Tabs` ������һЩ metadata���Ӷ�ʹ���������һЩ��������塣��ʵ����� annotations �����ã�������һ�������ķ�ʽ��Ϊ���������� metadata��

`@Component` ��Ϊһ�� annotations�������� Angular�������������Ǹ��� `Tabs` ��һ�������annotations ������ô�򵥵�һ����������Ȼ�ܼ򵥣�������Ȼ��һЩ�µ����⣺

1����Щ annotations ���������ģ���ЩӦ�ò��� JavaScript ���Դ��Ķ����ɣ�
2��˭�������������� `@Component`��
3��������� AtScript �е�һ���֣���ô����ת���� JavaScript ����ʲô���ӵģ����������������ʹ������ô?

���ϵ���������һ��һ���Ľ�������ȣ�annotations ���������ģ��ص��������֮ǰ��������Ҫ���һ�μ򵥴��롣`@Component` ��Ҫ���Ǵ� Angular2 ���ļ�����������ˣ�

```
import {Component} from "angular2/core";
```

������һ������ͽ���ˣ����е� annotations �������� Angular2������������һ����� annotations �� Angular2 �����е����ӣ�

```
export class Component extends DirectiveMetadata {

  constructor() {
    ...
  }
}
```

���ǿ��Կ��� `Component` ʵ������ Angular �ܹ��е�һ���࣬��ô�ڶ�������Ҳ����ˡ����ǵ�һ�£�annotations Ҳ��һ���࣬��ôһ���򵥵�������θı���һ�������Ϊ���أ�Ϊʲô����ֻҪ����Щ��֮ǰ���� `@` ��Ǿ���ʹ����Щ����Ϊ annotations ���أ���ʵ�����ǲ������ԡ�annotations ��Ŀǰ�������������Ч�ģ�������Ҫ����ת�������������Ӳ���������������С�

����������������������ѡ���� Babel, Traceur, TypeScript �ȵȣ�����ֻ�� Traceur ʵ���� annotations����������һ��������������� Traceur ����֮������ӣ�

```
var Tabs = (function () {
  function Tabs() {}

  Tabs.annotations = [
    new Component({...})
  ];

  return Tabs;
})
```

���գ��౻�������һ��������Ҳ����˵��һ���������е� annotations ���ն�����һ��ʵ�����ҷ������ `annotations` �����С��ղ���˵���� annotations����ʵ����˵�������Ͻ����� annotations ����Ĳ�����ʱ�����ͻᱻ������� `parameters` �����У�

```
class MyClass {

  constructor(@Annotation() foo) {
    ...
  }
}
```

����� JavaScript ֮��

```
var MyClass = (function () {
  function MyClass() {}

  MyClass.parameters = [[new Annotation()]];

  return MyClass;
})
```

������ annotation ��������һ��Ƕ�������У�������Ϊһ�����������в�ֹһ�� annotation��

���ˣ���������֪������Щ metadata annotations ��ʲô������ת��֮������ӣ�����������Ȼ��֪���� Angular2 �У� `@Component` ����ν�һ����������ת����һ������ġ�ʵ���ϣ���Щ�������� Angular �Լ���ɵġ�annotations ����һ�α���ӽ������е� metadata����Ҳ����Ϊʲô `@Component` �ǿ����� Angular2 ���ҵ�ʵ�ֵ�Դ��ġ�Angular2 �л��кܶ������� annotation������Ҳֻ�� Angular ��������Щ annotation �ľ������á�

������һ���ǳ�����˼���£�Angular ϣ���� metadata �������е� `annotations` �� `parameters` �����С���� Traceur ���� annotation ת������Щ�ض��������У�Angular2 �Ͳ���֪�����Ļ�ȡ metadata��AtScript Annotations ����һ���ǳ������ʵ�֣�ʹ annotation �ܹ���ʵ�ʵ����á�

�����Ϊ����Գ�������ѡ���� metadata ��������е�λ�ã����������ǲ��Ǹ���һЩ�أ�������������˵һ�� decorator ������һ�������Ľ�ɫ��

##Decorator
Decorator ���� Yehuda Katz Ϊ ECMAScript 2016 �����һ�������׼��Ŀ�ľ���Ϊ��Ҫ�����Ӧ�ó����ʱ��ע�ͺ�����������ԡ����������ǲ�����Щ�� annotation �ɵ��£�����������ôһ����...����������һ�� decorator ��ʲô����

```
@decoratorExpression
class MyClass { }
```

���Կ���������ȫ�� AtScript �е� annotations ����һ��������ȷʵ���񣬵���ʵ���ǻ��������ԵĲ�𡣴�ʹ���ߵĽǶ�������decorator �ĳ�����Ǹ� "AtScript annotation" ���ġ�����������һ������һ�δ���ת���� JavaScript ֮������ӣ�

```
function decoratorExpression(target) {
   // Add a property on target
   target.annotated = true;
}
```

���ڿ��Ժ�����Ŀ�����decorator ��һ��������Ϊ `target` ������һ�� `annotated` �����ԣ�����������Ϊ `true`������һ����Ҫ�����ε� `target` �Ŀɷ���Ȩ�޸����ˡ��ǲ��ǿ�����һЩ���ߣ����ڲ��Ǳ�������������� annotation �����ģ����������Լ����������Ķ��� decoration �� annotation����ʵ����һ�仰�ܽ᣺���� decorator�����Ǿ��ܹ���һ�� annotation��

��Ȼ���� decorator ���кܶ����ݣ��������Ѿ������˱��ĵķ�Χ�ˡ��ҽ�������Ȥ�Ķ��߿��Կ�һ�� Yehuda �Ľ��飨https://github.com/wycats/javascript-decorators�����˽������й��ڸ����Ե����ݡ�

##�ܽ�
��������֪����������Angular �Ŷ��Ѿ��������Ƿ��� ��AtScript�� ת��֧�� ��TypeScript������Ϊ�����ֹ��߶��ǽ��ͬһ�����⡣���⣬TypeScript �Ѿ��� 1.5 �汾�о��Ѿ�֧�� annotation �� decorator �ˡ���AtScript Annotation�� �� decorator ������һ���ġ���һ��ʹ���ߵĽǶ���˵������ӵ����ͬ���﷨������֮��Ψһ�Ĳ�ͬ���������ǲ��ܿ�����ν� annotation ��Ϊ metadata ��ӽ����ǵĴ��롣Ȼ�� decorator ����һ�������� annotation �ӿڡ����ԣ�����ֻ��Ҫ��ע�������� decorator �ϣ���Ϊ���Ѿ���Ϊ��һ�ֱ�׼����ϣ������������Щ�� annotation �� decorator ֮����ã�Ķ��ߵõ�һЩ������

