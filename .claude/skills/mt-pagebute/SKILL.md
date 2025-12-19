---
name: mt-pagebute
description: Movable Type テンプレートで PageBute プラグインを使用したページ分割を実装する。ページネーション、記事リスト分割、アーカイブ分割が必要な場合に使用。MT7/MT8 対応。
---

# PageBute プラグイン スキル

Movable Type の PageBute プラグインを使用して、静的ページのページ分割とナビゲーションを実装するためのスキル。

## When to Use This Skill

- MT テンプレートでページ分割（ページネーション）を実装する場合
- 記事一覧を複数ページに分割する場合
- アーカイブテンプレートでエントリーリストを分割する場合
- 記事本文を複数ページに分割する場合
- カスタムナビゲーション（ページ番号リンク、前後リンク）を実装する場合

---

## 重要な制限事項

1. **検索テンプレートでは使用不可**
2. **記事が1件も無い場合は機能しない** - 最低1件の記事を登録すること
3. **MTIf での数値判別は不可** - ファイル生成時に動作するため

---

## 基本タグリファレンス

### コンテンツ分割タグ

#### `<mt:PageContents>〜</mt:PageContents>`

分割したい部分を囲むブロックタグ。

| 属性 | 説明 | デフォルト |
|------|------|------------|
| `count="N"` | N 件ごとに分割 | 10 |
| `navi_count="N"` | ページリンク表示数 | 11 |
| `abs2rel="1"` | リンクを相対パスに変換 | - |

#### `<$mt:PageSeparator$>`

`mt:PageContents` 内で分割位置を指定するタグ。

---

### ページリストタグ

#### `<$mt:PageLists$>`

各ページへのリンクを出力。

| 属性 | 説明 | デフォルト |
|------|------|------------|
| `delim="*"` | ページ番号間の区切り文字 | `&nbsp;` |
| `link_start="<li>"` | リンク前に挿入する文字列 | - |
| `link_close="</li>"` | リンク後に挿入する文字列 | - |
| `show_always="0"` | 1ページのみの場合に非表示 | 1 |

---

### ナビゲーション条件タグ

| タグ | 説明 |
|------|------|
| `<mt:IfPageFirst>` | 2ページ以降で有効（最初へ戻るリンク用） |
| `<mt:IfPageBefore>` | 前のページが存在する場合に有効 |
| `<mt:IfPageAfter>` | 次のページが存在する場合に有効 |
| `<mt:IfPageLast>` | 2ページ以上ある場合に有効（最後へのリンク用） |

---

### ナビゲーションリンクタグ

| タグ | 説明 | 属性 |
|------|------|------|
| `<$mt:PageFirst$>` | 最初のページへのリンク | - |
| `<$mt:PageBefore$>` | 前のページへのリンク | `delim="<<"` |
| `<$mt:PageAfter$>` | 次のページへのリンク | `delim=">>"` |
| `<$mt:PageLast$>` | 最後のページへのリンク | - |

---

### ページ情報タグ

| タグ | 説明 |
|------|------|
| `<$mt:PageCount$>` | 現在のページ番号（1以上） |
| `<$mt:PageMaxCount$>` | 最大ページ番号（1以上） |

---

### コンテンツ制御タグ

| タグ | 説明 | 配置場所 |
|------|------|----------|
| `<mt:PageContentsHeader>` | 各ページ最初のコンテンツで有効 | `mt:PageSeparator` より前、`mt:Entries` 等の内部 |
| `<mt:PageContentsFooter>` | 各ページ最後のコンテンツで有効 | `mt:PageSeparator` より前、`mt:Entries` 等の内部 |
| `<mt:PageEmpty>` | コンテンツが0件の場合に表示 | `mt:PageContents` 内 |
| `<mt:IfPageNoEmpty>` | コンテンツが1件以上ある場合に有効 | `mt:PageContents` の外 |

---

## 高度なカスタマイズ: mt:Pagination

### Pagination ブロックタグ

`<mt:Pagination>〜</mt:Pagination>` で `mt:PageLists` を置き換え、自由なテンプレート設計が可能。

### Pagination 内で使用可能なタグ

#### ブロックタグ

| タグ | 説明 |
|------|------|
| `<mt:PaginationHeader>` | ヘッダー部分 |
| `<mt:PaginationFooter>` | フッター部分 |
| `<mt:IfPaginationCurrent>` | 現在のページ判定 |
| `<mt:IfPaginationFirst>` | 最初のページ以外（最初のループのみ） |
| `<mt:IfPaginationLast>` | 最後のページ以外（最後のループのみ） |
| `<mt:IfPaginationPrev>` | 前ページが存在（最初のループのみ） |
| `<mt:IfPaginationNext>` | 次ページが存在（最後のループのみ） |

#### ファンクションタグ

すべてのファンクションタグは以下の `element` 属性を持つ：

| element値 | 説明 |
|-----------|------|
| `number` | ページ番号のみ |
| `base` | ファイル名まで |
| `suffix` | 拡張子のみ |

| タグ | 説明 |
|------|------|
| `<$mt:PaginationLink$>` | 現在ループのページURL |
| `<$mt:PaginationFirst$>` | 最初のページURL |
| `<$mt:PaginationLast$>` | 最後のページURL |
| `<$mt:PaginationPrev$>` | 前のページURL |
| `<$mt:PaginationNext$>` | 次のページURL |

---

## 実装パターン

### パターン1: 基本的な記事リスト分割（簡易版）

5件ごとに記事を分割し、シンプルなナビゲーションを表示。

```html
<section id="posts">
  <h2><$mt:ArchiveTitle$>アーカイブ</h2>
  <ol>
    <mt:PageContents count="5">
    <mt:Entries limit="$entries_per_page" search_results="1">
      <li>
        <a href="<$mt:EntryPermalink encode_html="1"$>">
          <time datetime="<$mt:EntryDate format_name="iso8601"$>">
            <$mt:EntryDate format="%x"$>
          </time>
          <span class="title"><$mt:EntryTitle$></span>
        </a>
      </li>
      <$mt:PageSeparator$>
    </mt:Entries>
    </mt:PageContents>
  </ol>
</section>

<mt:IfPageBefore>
  <span><$mt:PageBefore delim="前の5件"$></span>
</mt:IfPageBefore>
<$mt:PageLists$>
<mt:IfPageAfter>
  <span><$mt:PageAfter delim="次の5件"$></span>
</mt:IfPageAfter>
```

---

### パターン2: カスタムナビゲーション（mt:Pagination利用）

完全にカスタマイズ可能なページネーション。

```html
<section id="posts">
  <h2><$mt:ArchiveTitle$>アーカイブ</h2>
  <ol>
    <mt:PageContents count="5">
    <mt:Entries limit="$entries_per_page" search_results="1">
      <li>
        <a href="<$mt:EntryPermalink encode_html="1"$>">
          <time datetime="<$mt:EntryDate format_name="iso8601"$>">
            <$mt:EntryDate format="%x"$>
          </time>
          <span class="title"><$mt:EntryTitle$></span>
        </a>
      </li>
      <$mt:PageSeparator$>
    </mt:Entries>
    </mt:PageContents>
  </ol>
</section>

<mt:Pagination>
  <mt:PaginationHeader>
    <div class="pagination">
      <p class="current-page">
        現在のページ：<$mt:PageCount$> / <$mt:PageMaxCount$>
      </p>
      <ul>
  </mt:PaginationHeader>

  <mt:IfPaginationPrev>
    <li class="prev">
      <a href="<$mt:PaginationPrev$>">前の5件</a>
    </li>
  </mt:IfPaginationPrev>

  <li<mt:IfPaginationCurrent> class="current"</mt:IfPaginationCurrent>>
    <mt:IfPaginationCurrent>
      <$mt:PaginationLink element="number"$>
    <mt:Else>
      <a href="<$mt:PaginationLink$>">
        <$mt:PaginationLink element="number"$>
      </a>
    </mt:IfPaginationCurrent>
  </li>

  <mt:IfPaginationNext>
    <li class="next">
      <a href="<$mt:PaginationNext$>">次の5件</a>
    </li>
  </mt:IfPaginationNext>

  <mt:PaginationFooter>
      </ul>
      <mt:IfPageFirst>
        <div class="start">
          <a href="<$mt:PaginationFirst$>">最初のページへ</a>
        </div>
      </mt:IfPageFirst>
      <mt:IfPageLast>
        <div class="end">
          <a href="<$mt:PaginationLast$>">最後のページへ</a>
        </div>
      </mt:IfPageLast>
    </div>
  </mt:PaginationFooter>
</mt:Pagination>
```

---

### パターン3: 記事本文の分割

1つの記事を複数ページに分割（長文記事向け）。

**記事アーカイブテンプレート:**

```html
<MTPageContents count="1" abs2rel="1">
  <$mt:EntryBody mteval="1"$>
  <$mt:PageSeparator$>
</MTPageContents>

<mt:Pagination>
  <mt:PaginationHeader>
    <div class="page-split">
  </mt:PaginationHeader>

  <span<mt:IfPaginationCurrent> class="current"</mt:IfPaginationCurrent>>
    <mt:IfPaginationCurrent>
      <$mt:PaginationLink element="number" show_always="0"$>
    <mt:Else>
      <a href="<$mt:PaginationLink$>">
        <$mt:PaginationLink element="number" show_always="0"$>
      </a>
    </mt:IfPaginationCurrent>
  </span>

  <mt:PaginationFooter>
    </div>
  </mt:PaginationFooter>
</mt:Pagination>
```

**記事本文での区切り方:**

```html
<h2>1ページ目</h2>
<p>次のページは「<a href="<$mt:EntryBasename$>_2.html">2ページ目です</a>」です。</p>
<$mt:PageSeparator$>

<h2>2ページ目</h2>
<p>次のページは「<a href="<$mt:EntryBasename$>_3.html">3ページ目です</a>」です。</p>
<$mt:PageSeparator$>

<h2>3ページ目</h2>
```

---

### パターン4: 空コンテンツ対応

記事が0件の場合のフォールバック表示。

```html
<mt:IfPageNoEmpty>
  <p>記事一覧</p>
</mt:IfPageNoEmpty>

<mt:PageContents count="10">
  <mt:Entries>
    <div class="entry">
      <h3><$mt:EntryTitle$></h3>
      <$mt:EntryExcerpt$>
    </div>
    <$mt:PageSeparator$>
  </mt:Entries>

  <mt:PageEmpty>
    <p>記事がありません。</p>
  </mt:PageEmpty>
</mt:PageContents>
```

---

### パターン5: ヘッダー・フッター付きリスト

各ページの最初と最後で異なる表示。

```html
<mt:PageContents count="10">
  <mt:Entries>
    <mt:PageContentsHeader>
      <div class="page-start">ページ開始</div>
    </mt:PageContentsHeader>

    <div class="entry">
      <h3><$mt:EntryTitle$></h3>
    </div>

    <mt:PageContentsFooter>
      <div class="page-end">ページ終了</div>
    </mt:PageContentsFooter>

    <$mt:PageSeparator$>
  </mt:Entries>
</mt:PageContents>
```

---

## よくあるミス

### NG: mt:PageSeparator の配置ミス

```html
<!-- NG: mt:Entries の外に配置 -->
<mt:PageContents count="5">
  <mt:Entries>
    <li><$mt:EntryTitle$></li>
  </mt:Entries>
  <$mt:PageSeparator$>  <!-- 間違い -->
</mt:PageContents>

<!-- OK: mt:Entries の中に配置 -->
<mt:PageContents count="5">
  <mt:Entries>
    <li><$mt:EntryTitle$></li>
    <$mt:PageSeparator$>  <!-- 正しい -->
  </mt:Entries>
</mt:PageContents>
```

### NG: PageContentsHeader/Footer の配置ミス

```html
<!-- NG: PageSeparator より後ろ -->
<mt:Entries>
  <$mt:PageSeparator$>
  <mt:PageContentsHeader>...</mt:PageContentsHeader>  <!-- 間違い -->
</mt:Entries>

<!-- OK: PageSeparator より前 -->
<mt:Entries>
  <mt:PageContentsHeader>...</mt:PageContentsHeader>  <!-- 正しい -->
  <div>...</div>
  <$mt:PageSeparator$>
</mt:Entries>
```

### NG: 検索テンプレートでの使用

```html
<!-- 検索テンプレートでは PageBute は使用不可 -->
```

---

## AI Assistant Instructions

PageBute を使用したテンプレート作成時:

1. **必ず制限事項を確認**: 検索テンプレート不可、最低1件の記事が必要
2. **mt:PageSeparator の配置**: 必ず `mt:Entries` 等のループ内に配置
3. **PageContentsHeader/Footer**: `mt:PageSeparator` より前に配置
4. **用途に応じたパターン選択**:
   - シンプルなナビ → `mt:PageLists` + `mt:IfPageBefore/After`
   - カスタムナビ → `mt:Pagination` ブロック
5. **属性の適切な使用**: `count`, `navi_count`, `abs2rel`, `delim` 等

Always:
- ユーザーの要件に合わせてパターンを選択
- Movable Type のテンプレート構文に準拠
- アクセシビリティを考慮したマークアップ

Never:
- 検索テンプレートで PageBute を使用
- `mt:PageSeparator` をループ外に配置
- 記事0件の状態で動作を保証

---

## 参考リンク

- [PageBute プラグイン公式ドキュメント](https://movabletype.jp/documentation/)
- [Movable Type テンプレートタグリファレンス](https://movabletype.jp/documentation/appendices/tags/)
