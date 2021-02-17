## Typescript

### テキスト補完

[テキスト補間](https://angular.jp/guide/interpolation)

二重中括弧を使用する



### !をつけることで、nullを取りうるように見えるけど、そうでないことをTypeScriptに伝えることができる。

[Typescript: Type 'string | undefined' is not assignable to type 'string'](https://stackoverflow.com/questions/54496398/typescript-type-string-undefined-is-not-assignable-to-type-string)

### スプレッド演算子

[TypeScript Deep Dive 日本語版](https://typescript-jp.gitbook.io/deep-dive/future-javascript/spread-operator)

以前

```
function foo(x, y, z) { }
var args = [0, 1, 2];
foo.apply(null, args);
```
スプレッド演算子を使うと
```
function foo(x, y, z) { }
var args = [0, 1, 2];
foo(...args);
```

hero.id配列の最大値を取得

```
Math.max(...heroes.map(hero => hero.id))
```

### Type Assersion(型アサーション)

[Type Assertion（型アサーション）](https://typescript-jp.gitbook.io/deep-dive/type-system/type-assertion)

これだとエラー

```
var foo = {};
foo.bar = 123; // Error: property 'bar' does not exist on `{}`
foo.bas = 'hello'; // Error: property 'bas' does not exist on `{}`
```

これだとOK

```
interface Foo {
    bar: number;
    bas: string;
}
var foo = {} as Foo;
foo.bar = 123;
foo.bas = 'hello';
```

### ディレクティブとコンポーネントの親子間でのデータ共有

Angularを理解する > ディレクティブとコンポーネントの親子間でのデータ共有

- 親のテンプレート（HTML）の中で子供のセレクタの子供のプロパティに親のプロパティをバインド（セット）
- 子供のプロパティには@Inputデコレータ
- 親のテンプレート（HTML）の中で子供のセレクタの子供のイベントに親のメソッドをバインド。
- イベントバインディングはaddCallBackと思えばいい。
- 双方向バインディングはシンタックスシュガー。親のメソッドを用意する必要がなく、直接子の値を親のプロパティにセット

**シンタックスシュガー**

```
<app-sizer [(size)]="fontSizePx"></app-sizer>
<div [style.font-size.px]="fontSizePx">Resizable Text</div>
```

**本来**。fontSizePx=$eventの部分はラムダ式と思えばいい

```
<app-sizer [size]="fontSizePx" (sizeChange)="fontSizePx=$event"></app-sizer>
```

### 双方向バインディング

- NgModelディレクティブを使うにはFormsModuleをインポートする必要あり
- inputタグの[value]の代わりに[ngModel]

### DI

- Guiceはコンストラクタに@Injectedをつけることで、コンストラクタインジェクションを実現
- Angularはclassに@Injectableをつけることで、インジェクト可能を表現
  本来インターフェースと実装を分離するべきだと思う。サンプルではDIのうち、フレームワークによるnewの機能を使っているだけ

### ディレクティブ

- ディレクティブは3種類
  - コンポーネントディレクティブ
  - ngIfなどの構造ディレクティブ
  - 属性ディレクティブ



## RxJS(Reactive Extentions)

- 非同期処理を実装する際に役立つライブラリ
- ofはObservableを作るためのメソッド。たぶん。



### Subscribe

#### Component側でSubscribeする場合

```
heroes: Hero[];
getHeros(): void {
	this.heroService.getHeroes()
	.subscribe(heroes => this.heroes = heroes);
}
```

#### Html側でSubscribeする場合

```
<ul class="search-result">
	<li *ngFor="let hero of heroes$ | async" >
		<a routerLink="/detail/{{hero.id}}">
			{{hero.name}}
		</a>
	</li>
</ul>
```

