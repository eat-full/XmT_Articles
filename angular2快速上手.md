Ŀǰangular2�Ѿ�������beta�棬����ζ�����Ѿ������˿������ȶ�Ӧ�õ�׼���ˡ���angular1.x��ȣ������������߸��Եı仯��angular2�Ĺٷ���վ�ϣ���һ��5���ӿ��ٿ�ʼ�̳�(angular.io)������Ȥ�����ѿ���ȥ��һ�£���������ٵ��˽�angular2���ڱ����У��ҽ���ͨ������һ���򵥵�С��վ����Ϊ���չʾangular2�������ԣ�����������angular2��ȫ�����硣

##��������
������������Ҫ�ķ�������angular2��Ӧ�ó���һ����ͨ��systemjs(https://github.com/systemjs/systemjs)������һ������webpack��https://webpack.github.io/����Ϊ�˼�������ڱ����н���ʹ��systemjs��
�����ʹ��ES5��EcmaScript 2015 ���� TypeScript���������angular2Ӧ�ã�angular2���Ŷӵ��Ƽ���ʹ��TypeScript��������ʹ��TypeScript֮ǰ����Ҫ���һЩ���ù�������Ȼ���о�����Щ�����������������㻹�ǻ�е�����Ӧ�ֵģ���Ĵ���Ҳ��������������ˡ�
�����Ƚ�����angular2�����Ľ̳�(https://angular.io/docs/ts/latest/tutorial/)��ʹ�õĹ���Tour of Heroes��https://github.com/johnpapa/angular2-tour-of-heroes������ʼ���ǵ����̡�
�����ͨ��git����������̣�������������֮�󣬵�һ����Ӧ������`npm i`��������ʼ����Ŀ��
###tsconfig.js
��Ϊ��������TypeScript��д���ǵĳ������������ȵ������ǵĹ���������TypeScript�����߱�������β���JavaScript�ļ������������ļ��е����������������ҾͲ�׸���ˣ���ֻ������������Ҫ�����ԣ�һ����`"target":"ES5"`��`"module":"system"`��`target`���Խ�����TypeScript���������ECMAScript�汾Ϊ<br>ES5</br>��`"module":"system"`��Ϊ����������<br>system</br>�ĸ�ʽ���������ǵ�ģ�顣

```
{
  "compilerOptions": {
    "target": "ES5",
    "module": "system",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "moduleResolution": "node",
    "removeComments": false,
    "noImplicitAny": true,
    "suppressImplicitAnyIndexErrors": true
  },
  "exclude": [
    "node_modules"
  ]
}
```

###package.json
�����Ѿ������˸���α���TypeScript�ļ���������������ҪΪ�������һ��package.json�ļ���

```

```

##��������
Angular2�ж�������˵�����ص�һ����ǡ��Ҹ���������ҵ�Ӧ�ã��������ڶ����ص�һ����ǡ��ðɣ��Ҹ���������ҵ�Ӧ�ó��򣿣���

�������ǵ�Ӧ�õĵ�һ���¾����ڹ��̵�`index.html`�ļ������ñ�Ҫ����Դ������angular����Դ��֮�⣬����Ҫ��һ������`system.src.js`�������������ǵ�ģ���������

```
<script src="node_modules/angular2/bundles/angular2-polyfills.js"></script>
<script src="node_modules/systemjs/dist/system.src.js"></script>
<script src="node_modules/rxjs/bundles/Rx.js"></script>
<script src="node_modules/angular2/bundles/angular2.dev.js"></script>
<script src="node_modules/angular2/bundles/router.dev.js"></script>
```

���Ǵ���ͨ��ʹ��`systemjs`���������ǵ�����ģ�顣

```
<script>
    System.config({ packages: { app: { format: 'register', defaultExtension: 'js' } } });
    System.import('app/boot')
        .then(null, console.error.bind(console));
</script>
```

��`boot.ts`�ļ��У�����������3�������`bootstrap`��`ROUTER_PROVIDERS`��`AppComponent`��Ȼ��ʵ���������ǵ�Ӧ�ò�ָ�������ǵĸ������`AppComponent`��ע����`ROUTER_PROVIDERS`��Ϊһ����ģ�顣

```
import {bootstrap} from 'angular2/platform/browser';
import {ROUTER_PROVIDERS} from 'angular2/router';
import {AppComponent} from './app.component';

bootstrap(AppComponent, [
  ROUTER_PROVIDERS
]);
```

�ص�֮ǰ��`index.html`�ļ��У�`<app>Loading...</app>`��һ�о�������Ӧ�õ���ڱ�ǡ�Angular�Ѿ�ʵ������`AppComponent`���ҽ�����ģ�����뵽��`app`Ԫ���С�

```
<body>
    <app>Loading...</app>
</body>
```

�ڽ�������α��롢���ú�����һ��angular2��Ӧ�ó���֮�������ǿ�һ��angular2���������ɲ��֣��Ա������ܸ��õ����`AppComponent`��`app`֮�����ϵ��

##���(Component)
Angular�е������angular��������ĸ���֮һ��һ���������һ����ͼ��View������һƬΪ�û�չʾ��Ϣ����Ӧ�û���������ҳ��һ����˵��һ���������һ�����ڿ�����ͼģ���JavaScript�ࡣ
���ã��й�������ĸ������ݣ������ȥ�Ķ��ҵġ�CIDER:����һ��Angular2��������㽫���˽⵽��δ�����ʹ����������

###App ���
�����齨�ĵ�һ���¾�����дһ���ࣨclass��,��������������һ�������Ľ�����

```
export class AppComponent {}
```

������������Ӧ���������ǵ�����ģ�顣�ڱ����У����ǽ���Ҫ��`angular2/core`������`Component`��

```
import {Component} from 'angular2/core';
```

֮��������Ҫװ��(decorate)���ǵ��ࡣͨ�����`@Component`��Ԫ�������������ǵ�Ӧ�ó���������Ҫһ����ô����`AppComponent`�����ǽ�ʹ��`selector`����Ϊ���ǵ����ȡһ��HTMLԪ�ص����֣������Ϳ���ͨ������õ�HTMLԪ�ص�������ʹ������ˡ�ͬʱ����Ҫͨ��`templateUrl`��`styleUrls`Ϊ�������ģ�����ʽ��������ǽ�`ROUTER_DIRECTIVES`���ָ��ͨ��`directives`����ע�뵽�����ȥ��

```
@Component({
  selector: 'app',
  templateUrl: 'app/app.component.html',
  styleUrls: ['app/app.component.css'],
  directives: [ROUTER_DIRECTIVES]
})
export class AppComponent {}
```

�����ʾ���У����ǻ�������Ϊ���ǵ��������·�ɹ��ܣ�������ǽ���ʹ��`RouterConfig`ģ�飬����`@RouterConfig`��װ�����ǵ������Ϊ���ܹ�·�ɣ�������Ҫ���ļ��е��������`RouterConfig`��`ROUTER_DIRECTIVES`��`AboutComponent`��`ExperimentsComponent`��`HomeComponent`��

```
import {RouteConfig, ROUTER_DIRECTIVES} from 'angular2/router';
import {AboutComponent} from './about/about.component';
import {ExperimentsComponent} from './experiments/experiments.component';
import {HomeComponent} from './home/home.component';
```

������Ҫ·��ģ��������·�ɹ����Լ������������Ϊ·�ɵ�Ŀ�ꡣ����������Ҫ��`@RouterConfig`�д���һ��·�ɵĶ��壬������Ӧ�ó���·�ɵ�·����·�ɵ����ֺ�ÿ��·������Ӧ�����������Ϊ`home`·�ɵ�����`useAsDefault`����Ϊ`true`��������ΪĬ��·�ɡ�

```
@RouteConfig([
  {path: '/home',        name: 'Home',        component: HomeComponent, useAsDefault: true },
  {path: '/about',       name: 'About',       component: AboutComponent },
  {path: '/experiments', name: 'Experiments', component: ExperimentsComponent }
])
```

Ȼ�����ǽ�`StateService`��`ExperimentService`���뵽���ǵ�����в�����`component`���η���`providers`�����С����������� AppComponent �Ĵ��롣

```
import {Component} from 'angular2/core';
import {RouteConfig, ROUTER_DIRECTIVES} from 'angular2/router';
import {AboutComponent} from './about/about.component';
import {ExperimentsComponent} from './experiments/experiments.component';
import {HomeComponent} from './home/home.component';
import {StateService} from './common/state.service';
import {ExperimentsService} from './common/experiments.service';

@Component({
  selector: 'app',
  templateUrl: 'app/app.component.html',
  styleUrls: ['app/app.component.css'],
  directives: [ROUTER_DIRECTIVES],
  providers: [StateService, ExperimentsService],
})
@RouteConfig([
  {path: '/home',        name: 'Home',        component: HomeComponent, useAsDefault: true },
  {path: '/about',       name: 'About',       component: AboutComponent },
  {path: '/experiments', name: 'Experiments', component: ExperimentsComponent }
])
export class AppComponent {}
```

###Home ���
����� App ���֮�����Ǽ�����д���ǵ� Home ��������Ȼ����ȶ���һ�� `HomeComponent` �࣬ͬʱ������Ϊ����ı�������ݶ����������ԡ�

```
export class HomeComponent {
  title: string = 'Home Page';
  body:  string = 'This is the about home body';
}
```

Ȼ��������ʵ�����ģ�顣

```
import {Component} from 'angular2/core';
```

֮��װ�����ǵ��ಢ����`selector`��`templateUrl`���ԡ�

```
@Component({
    selector: 'home',
    templateUrl: 'app/home/home.component.html'
})
```

Ȼ�����ǽ�Ϊ���ǵ�������� StateService ��ʹ�������洢״̬����·��֮���״̬��Angular2�е�����ע�뷢���ڸ���Ĺ��캯���У�������ǽ��ڹ��캯����ע�� StateService��Angular��ÿ������������������ڵĹ��ӣ�lifecycle hooks�������ǿ��԰�˳��ʹ�����ǡ��ڱ�����У��������������ʼ����ʱ��� StateService �л�ȡ���������ǵ���Ϣ����ʱ��������Ҫʹ��`ngOnInit`���ӡ����й���������������ڵ���ϸ���ݿ��Բο������̳̣�https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html����

```
import {Component} from 'angular2/core';
import {StateService} from '../common/state.service';

export class HomeComponent {
  title: string = 'Home Page';
  body:  string = 'This is the about home body';
  message: string;

constructor(private _StateService: StateService) { }

ngOnInit() {
    this.message = this._StateService.getMessage();
  }

updateMessage(m: string): void {
    this._StateService.setMessage(m);
  }
}
```

##����(Service)
���������ܻ���Ҫ������ͬ��һ�����ݣ������ǲ�������ɵ��һ����һ����һ��ĸ���ճ��ͬ���Ĵ��롣���ʱ�򣬷���Service�������ˡ�������Ҫ����һ����һ���ҿ����ظ�ʹ�õ����ݷ��񣬲�ѧ�Ὣ�÷���ע�뵽������Ҫ�������ȥ��

�����ݵĴ�ȡ���°�װ��һ�������ķ�������������������ڶ���ͼ��֧�֡�����������ĵ�Ԫ���Ա�ø������ס�

### State ����
�����������У����Ǿ�������һ����StateService�Ķ�������������ʲô�أ�û��������һ�����񣬽�������������һ��һ���Ĵ�����������������Ҫ����һ���� StateService ���ಢ������¶�����ǵ�Ӧ�ó���

```
export class StateService {
  private _message = 'Hello Message';

getMessage(): string {
    return this._message;
  };

setMessage(newMessage: string): void {
    this._message = newMessage;
  };
}
```

�÷����ж�����`_message`�����Լ��������Ի�ȡ��(getter)��������(setter)������Ҫ��ʹStateService�ܹ�ע�뵽���������ȥ��������Ҫ�����ǵ���������`Injectable`������`@Injectable`�������ǵ��ࡣ

```
import {Injectable} from 'angular2/core';
@Injectable()
export class StateService {
  private _message = 'Hello Message';

getMessage(): string {
    return this._message;
  };

setMessage(newMessage: string): void {
    this._message = newMessage;
  };
}
```

���ˣ����ڷ���ģ��Ҳд���ˣ��о����ǵ�Ӧ�����ڿ�����ˣ����Ҳ������Ҫ��һ��������Ҫ����Ӧ�õ������ˡ�

##��ͼ(Views)
�ҽ�ͨ��`home.component.html`��Ϊ��������򵥽���һ�� Angular2 �е�������ģ���﷨��template syntax����

�������ݰ��� Angular1.x �е���ʽ��һ���ģ�����ͨ���ַ������롣

```
<h1>{{title}}</h1>

{{body}}
```

�û������¼�����ͨ�������ǵ�HTML��ǩ��ʹ���Զ����Angularָ�������񣬶���ͨ���ڲ�������з�װԭ����DOM�¼���https://developer.mozilla.org/en-US/docs/Web/Events�����������ǡ����ǿ�������������п�������ͨ��`(click)="updateMessage(message)"`��ΪԪ��ע�� click �¼������¼�����ʱ���� updateMessage ������

```
<button type="submit" class="btn" (click)="updateMessage(message)">Update Message</button>
```

Angular2�е�˫�����ݰ󶨻��ڵ������ݰ󶨡�֮ǰ���ǿ����������ݰ���ʹ�����ַ�������ķ�������ʵ�����ǰ�һ��Ԫ�ص�����ʱ������ʹ�÷������﷨�����ǽ����԰󶨣��������ͼ�����¼��󶨣���ͼ��������ķ��������������˫�����ݰ��ˡ��ǲ��Ǻ����棿˫�����ݰ󶨵ķ����ܼ򵥣������� ngModel �÷����ź�Բ���Ű��������`[(ngModel)]=��message`��

```
<input type="text" [(ngModel)]="message" placeholder="Message">
```

���������� home.component.html �����ݡ�

```
<h1>{{title}}</h1>

{{body}}

<hr>

<div>
    <h2 class="text-error">Home: {{message}}</h2>
    <form class="form-inline">
      <input type="text" [(ngModel)]="message" placeholder="Message">
      <button type="submit" class="btn" (click)="updateMessage(message)">Update Message</button>
    </form>
</div>
```

###·�ɱ��
��������������Ҫ�ص� app.component.html �У���̽��һ�������ģ���﷨�м���·�����ӡ������Ƕ���һ��·�ɵ�ʱ��ÿ�������������Ӧ��ģ�壬��ô�������ˣ���·�ɵ�һ�������ʱ�����ģ��Ӧ�ñ����������أ����ʱ��`router-outlet`�����ˣ�������Ӧ�ó���·��������İڷ�λ�á�

```
<div id="container">
    <router-outlet></router-outlet>
</div>
```

�ڶ�����·������İڷ�λ��֮����ô������δ�һ��·�ɵ���һ��·���أ�RouterLink ���������·�ɵ�ָ�����⡣

```
<h1 id="logo">
  <a [routerLink]="['/Home']"></a>
</h1>

<div id="menu">
  <a [routerLink]="['/Home']" class="btn">Home</a>
  <a [routerLink]="['/About']" class="btn">About</a>
  <a [routerLink]="['/Experiments']" class="btn">Experiments</a>
</div>
```

���� app.component.html �ļ�������ʾ��

```
<header id="header">
  <h1 id="logo">
    <a [routerLink]="['/Home']"></a>
  </h1>

  <div id="menu">
    <a [routerLink]="['/Home']" class="btn">Home</a>
    <a [routerLink]="['/About']" class="btn">About</a>
    <a [routerLink]="['/Experiments']" class="btn">Experiments</a>
  </div>

  <div class="color"></div>
  <div class="clear"></div>
</header>

<div class="shadow"></div>

<div id="container">
  <router-outlet></router-outlet>
</div>
```

##�ܽ�
����Ϊֹ�����ǵ���ҳ��������ˣ������ó�ȥ��ҫ֮ǰ�������ǻع�һ�����ǵ��������̣�

1������������tsconfig.json�ļ���˵��TypeScript����α��롣
2������ѧϰ����μ򵥵�ʹ��systemjs������ģ������벢��������Ӧ�ó����������
3�������˽��˸���δ��� AppComponent �� HomeComponent��
4������ѧϰ�����ʹ�� @Injectable() ����һ����ע��ķ���
5��������΢�˽���һ��Angular2�еİ��﷨��
6������ѧϰ������� router-outlet ����ͼ�ж���·�������ŵ�λ�ã���ʹ�� routerLink ����·��֮�����ת��
