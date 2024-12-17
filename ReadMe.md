# ukagakaPlugin_Inventory
伺か/SSPで使用することが出来るプラグインです。


## 環境
以下の環境で動作を確認しています。
- windows10
- SSP 2.6.85


## どんなプラグイン?
ユーザにインベントリの概念を導入するプラグインです。
プラグイン側に現在の所持アイテムが残るため、ゴースト間のちょっとした遊びに使えます。
所持アイテムをクリックすることで ゴーストの OnCommunicate関数 に use:アイテム名 が飛びます。
アイテム名は自由にできます。


## 出来ること
ユーザからゴーストへのアイテムの使用
ゴーストからユーザへアイテムの提供
ゴーストから特定のアイテムを所持しているかどうかの確認
指定アイテムの個数を増加・減少
このプラグインが入っているかどうかチェック



## 詳細
### `OnExistPlugin_Inventory`
ゴースト起動時にゴースト側に呼ばれます。
この関数を実装することで、関数が呼ばれた場合プラグインがあると認識できます。


### アイテムの使用
ゴーストを右クリック -> プラグイン -> Inventory -> 持っているアイテムを選択 をすることでアイテムの使用ができます。
use:アイテム名 が すべてのゴーストのOnCommunicateに飛びます。
この際、このプラグイン側で個数の増減は行いません。


### OnSetItem
指定したアイテムの個数を上書きします。
```
"\![notifyplugin,Inventory,OnSetItem,アイテム名,個数]"
```


### OnFlagOn 
指定したアイテムの個数を1にします。
```
"\![notifyplugin,Inventory,OnFlagOn,アイテム名]"
```

### OnFlagOff 
指定したアイテムの個数を0にし、インベントリから削除します。
```
"\![notifyplugin,Inventory,OnFlagOff,アイテム名]"
```


### OnIncrementItem 
指定したアイテムの個数を+1にします。
```
"\![notifyplugin,Inventory,OnIncrementItem,アイテム名]"
```


### OnDecrementItem 
指定したアイテムの個数を-1にします。
0以下になった場合は、インベントリから項目を削除します。
```
"\![notifyplugin,Inventory,OnDecrementItem,アイテム名]"
```


### OnAddItem 
指定したアイテムを指定個数追加します。
```
"\![notifyplugin,Inventory,OnAddItem,アイテム名,追加個数]"
```


### OnSubItem 
指定したアイテムを指定個数減らします。
0以下になった場合は、インベントリから項目を削除します。
```
"\![notifyplugin,Inventory,OnSubItem,アイテム名,追加個数]"
```


### OnCheckItem 
指定したアイテムの個数を確認します。
OnInventoryResult関数が呼ばれ、R0にアイテム名,R1に個数が返ってきます。
```
"\![raiseplugin,Inventory,OnCheckItem,アイテム名]"
```


### OnImportItem
指定した全てのアイテム名の所持数を1にします。
すでに所持しているものに関しては個数が変化しません。
```
"\![notifyplugin,Inventory,OnImportItem,アイテム名,アイテム名....]
```


### OnExportItem 
現在プラグインで管理されているすべてのアイテム名を返します。
OnInventoryImport関数が呼ばれ、R0からアイテムの数NまでのRNが返ります。
```
"\![raiseplugin,Inventory,OnExportItem]"
```


## 備考
アイテム名は99文字まで使用可能です。


## Installation
Releaseのnarを適当なゴーストにD&Dしてください。


## アドカレのお話
[伺か・伺的 [第1会場] Advent Calendar 2024 - Adventar](https://adventar.org/calendars/10049)の12/18の記事です。


<br>ゴーストが別のゴーストに影響を受けたりしてもいいんじゃないか?と思ったので作りました。
<br>魑魅魍魎が跋扈する伺かという自由な世界において、ユーザが呪いのアイテムを押し付けられたりとか、
<br>冒険の果てに伝説の剣でももってても別にいいし、それらが何らかの形で影響があってもいいかな。と。
<br>
<br>
<br>がっつり使うならただのインベントリとして使えて、それこそ別のゴーストの世界から何か道具を取ってこないと進めない・・・とかでもいいんですけど、
<br>そこまで重いものはあんまり考えてなくて、
<br>例えば ゴーストのエンディングで XXXのお守り とかを入手するだけで、 ある意味リワードとして機能するし、
<br>そのリワードを所持しているだけで、 XXXってゴースト いいよね。 といった話題展開をしてもいいし、アイテムの所持次第で2週目のエンディング分岐してもいいし、
<br>ゴーストの切り替え動作を深く掘り下げたような物として認識してもらえると嬉しいです。
<br>
<br>
<br>もちろん、大量の酒煙草におぼれたユーザと化してもいいし、それに付き合えるゴーストが居てもいいなと。
<br>面白く使ってください。


## お借りしたもの
yaya.dll
[Releases · YAYA-shiori/yaya-shiori · GitHub](https://github.com/YAYA-shiori/yaya-shiori/releases)

## Other
このプログラムを利用することによるいかなる問題や損害に対して、私は責任を負いません。<br>
またゴースト等に同梱して配布していただいて構いません。<br>



## Author
ambergon




