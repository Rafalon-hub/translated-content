---
title: itemref
slug: Web/HTML/Global_attributes/itemref
tags:
  - Attribute
  - Global attribute
  - HTML
  - HTML Microdata
  - Microdata
  - Reference
browser-compat: html.global_attributes.itemref
translation_of: Web/HTML/Global_attributes/itemref
---
{{HTMLSidebar("Global_attributes")}}

[`itemscope`](/ja/docs/Web/HTML/Global_attributes/itemscope) 属性を持つ要素の子孫でないプロパティは、[グローバル属性](/ja/docs/Web/HTML/Global_attributes) **`itemref`** を使用してアイテムに関連付けることができます。

`itemref` は文書内のどこかにある追加のプロパティがある要素の ID （`itemid` ではない）のリストを提供します。

`itemref` 属性は `itemscope` 属性が指定された要素のみで指定することができます。

> **Note:** `itemref` 属性は、マイクロデータのデータモデルの一部ではありません。注釈づけるデータが扱いやすいツリー構造に従っていないページにおいて、注釈を追加することを助けるための単なる構文構造です。例えば、テーブル内のデータをマークアップするために、セル内のプロパティを維持しながらそれぞれの列に別々なアイテムを定義することができます。

## 例

### バンドの構造化データの表現

この例では、マイクロデータ属性を使用して、次の構造化データを（[JSON-LD](https://json-ld.org/) 形式で）表現しています。

```json
{
  "@id": "amanda",
  "name": "Amanda",
  "band": {
    "@id": "b",
    "name": "Jazz Band",
    "size": 12
  }
}
```

#### HTML

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name: <span itemprop="name">Amanda</span> </p>
<div id="b" itemprop="band" itemscope itemref="c"></div>
<div id="c">
    <p>Band: <span itemprop="name">Jazz Band</span> </p>
    <p>Size: <span itemprop="size">12</span> players</p>
</div>
```

#### 結果

{{EmbedLiveSample('Representing structured data for a band')}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [他のグローバル属性](/ja/docs/Web/HTML/Global_attributes)
- マイクロデータに関連する他のグローバル属性

  - {{htmlattrxref("itemid")}}
  - {{htmlattrxref("itemprop")}}
  - {{htmlattrxref("itemref")}}
  - {{htmlattrxref("itemscope")}}
  - {{htmlattrxref("itemtype")}}
