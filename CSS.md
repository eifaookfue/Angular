### displayプロパティ

[【CSS】displayの使い方を総まとめ！inlineやblockの違いは？](https://saruwakakun.com/html-css/basic/display)

- inline-blockはblockのようにwidthとhightが指定できて、inlineのように要素が横に並ぶ

![](C:\Users\user\OneDrive\ドキュメント\20210124_Angular\png\bdr44405-O4HRWW-07-min.png)

### クラスセレクタとIDセレクタ

[MDN WebDocs 要素・クラス・ID によるセレクター](https://developer.mozilla.org/ja/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors)

- タイプセレクタはタグ名セレクタまたは要素セレクタを参照
- クラスセレクタはピリオドで始まる
- IDセレクタは#で始まる

### 正規表現など

[要素・クラス・ID によるセレクター](https://developer.mozilla.org/ja/docs/Web/CSS/:last-of-type)

[MDN WebDocs  :last-of-type](https://developer.mozilla.org/ja/docs/Web/CSS/:last-of-type)

```
[class*='col-']:last-of-type {
  padding-right: 0;
}
```

class属性に'col-'が含まれる要素の最後の要素

### 子結合子

[MDN WebDocs ](https://developer.mozilla.org/ja/docs/Web/CSS/Child_combinator)

```
.grid-pad > [class*='col-']:last-of-type {
  padding-right: 20px;
}
```

```
<div class="grid grid-pad">
  <a *ngFor="let hero of heroes" class="col-1-4"
    routerLink="/detail/{{hero.id}}">
    <div class="module hero">
      <h4>{{hero.name}}</h4>
    </div>
  </a>
</div>
```

grid-padクラスに一致し、class属性に'col-'が含まれる最後の要素

### Boxでの表現

![](C:\Users\user\OneDrive\ドキュメント\20210124_Angular\png\WS000000.JPG)

```
.module {
  padding: 20px;
  text-align: center;
  color: #eee;
  max-height: 120px;
  min-width: 120px;
  background-color: #3f525c;
  border-radius: 2px;
}
.module:hover {
  background-color: #eee;
  cursor: pointer;
  color: #607d8b;
}
```

```
<div class="grid grid-pad">
  <a *ngFor="let hero of heroes" class="col-1-4"
    routerLink="/detail/{{hero.id}}">
    <div class="module hero">
      <h4>{{hero.name}}</h4>
    </div>
  </a>
</div>
```

- max-heightで高さを指定
- border-dadiusで丸みを指定
- backgroud-colorで色を指定