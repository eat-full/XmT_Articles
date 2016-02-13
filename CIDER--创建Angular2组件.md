##ǰ��
Angular2�������ڳ�����﷨�ж���Angular1.x�ɺܴ������2.x�汾�з�����1.x�汾�кܶ�����ԡ�˵ʵ����Angular2����һ��ȫ�µĶ������������Ѿ����˽�Angular 1.x�ˡ�

�ھ�����һ��ʱ����������֮�����ܽ������һ�׷���������������Ĵ�����ø��Ӽ򵥡����׷����Ĺؼ����� CIDER����������ͨ��һ��ʾ��Ϊ��ҽ���һ����μ򵥵Ĵ���һ��Angular2�������
 
##CIDER
1������һ���ࣨCreate��
2����������(Import)
3��װ�������(Decorate)
4��������������Enhance��
5������������ظ����ϲ��裨Repeat��

�ҽ���һ��Angular2�����̵̳�ʾ������ Tour of Heroes Tutorial(https://angular.io/docs/ts/latest/tutorial/)������չʾһ������Ĵ������̡�

##����һ����
��������ĵ�һ�������ǽ�Ҫ����һ����Ϊ AppComponent ���ࡣ

```
class AppComponent {
  public title = 'Tour of Heroes';
}
```

##�����������
�ڶ�������Ҫ�����е��������뵽�ļ��С�Component �� AppComponent �������е�Ψһ������

```
import {Component} from 'angular2/angular2';

class AppComponent {
  public title = 'Tour of Heroes';
}
```

##װ�������
���������Ѿ��������������Angular2������������ʱ��װ��һ�������࣬������һ��Angular2�����������á����Ǵ������Angular2�������Ǹո�д�õ� AppComponent ����Ϊһ�����ʹ�ã��������� `my-app` Ԫ�ذ���һ��

```
import {Component} from 'angular2/angular2';
class Hero {
  id: number;
  name: string;
}
@Component({
  selector: 'my-app',
  templateUrl:'my-template.html'
})
class AppComponent {
  public title = 'Tour of Heroes';
  public hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };
}
```

�ڱ��δ����У���Ϊ�˵õ������������ʽ��֧�֣�ʹ���� `templateUrl` ���ԡ���Ҳ����ʹ�� `template` ���ԣ��ڸ������ж���ģ��� HTML �ṹ��

```
<h1>{{title}}</h1>

<h2>{{hero.name}} details!</h2>

<div><label>id: </label>{{hero.id}}</div>

<div><label>name: </label>{{hero.name}}</div>
```

##����������
���ڣ������Ѿ��춨��һ������Ļ����ˣ���ʱ�����������ǵ�����ˡ����Ǵ���ʹ�����Ǹոն���õ�ģ���ļ����������м���һ��`input`Ԫ�أ�������ʾ��

```
<h1>{{title}}</h1>

<h2>{{hero.name}} details!</h2>

<div><label>id: </label>{{hero.id}}</div>

<div>
  <label>name: </label>
  <div><input [(ng-model)]="hero.name" placeholder="name"></div>
</div>
```

Ϊ�˶�`input`Ԫ�ؽ���˫�����ݰ󶨣�������Ҫ����һ��`FORM_DIRECTIVES`ָ��������������ģ���з���`ng-model`���������Ǻ���Ҫ��һ����������Ҫ��`FORM_DIRECTIVES`�������η��е�`directives`�����У���������һ���������͡�
 
```
import {Component, FORM_DIRECTIVES} from 'angular2/angular2';
class Hero {
  id: number;
  name: string;
}
@Component({
  selector: 'my-app',
  templateUrl:'my-template.html',
  directives: [FORM_DIRECTIVES]
})
class AppComponent {
  public title = 'Tour of Heroes';
  public hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };
}
```

##����������ظ����ϲ���
�ոգ����ǳ�ɫ�����������ǵ������Ϊ�������һ���Ա��������Ĺ��ܣ��������Ҫ��Ϊһ����Ʒ������Ȼ��ԶԶ���������ǻ������Ϊ���������������ǵ�������Խ��Խ���ӣ�����Ҳ���Խ�һ���������Ϊ�ɼ������֣�����ÿ�����ֳ����һ�����������������һ�ο�ʼ��CIDER�Ĺ��̡������������һ��ӵ�и�����֤�ı������뽫��Ԫ�ش����������ж�����������������Ҫ����һ���µ�������װ��ı������������е�������������һ�ֵ�CIDER�ֿ�ʼ�ˡ�

##���䣺����һ�����������
��Ϊһ���������������Ҫ��һЩ����Ĳ������������ǵ�Ӧ�ó�������Ϊ����������������С����ȣ�������Ҫ����һ����Ϊ `bootstrap`��������Ȼ�������ļ��ĵײ����� `bootstrap(AppComponent)`����ֻ��Ҫ�����Ӧ�ó����е���һ�ξͿ����ˣ�����ҪΪÿ����������� `bootstrap` ������
 
```
import {bootstrap, Component, FORM_DIRECTIVES} from 'angular2/angular2';
class Hero {
  id: number;
  name: string;
}
@Component({
  selector: 'my-app',
  templateUrl:'my-template.html',
  directives: [FORM_DIRECTIVES]
})
class AppComponent {
  public title = 'Tour of Heroes';
  public hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };
}
bootstrap(AppComponent);
```

##β��
OK������һ�����������ô�򵥣�ϣ�����ϴ�������ķ����ܶ�����ѧϰAngular2�ĵ�·���𵽰������ã�ͬʱ��Ҳ���Բ鿴�������й�Angular2�����£�ϣ��������һЩ������