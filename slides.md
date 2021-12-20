---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

# 2021年フロントエンドまとめ

---

# 今日話すこと

- フロントエンド開発に必要な基本技術
- ライブラリ・フレームワークの話
- ホスティングサービスの話

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# フロントエンド開発に必要な基本技術
- HTML
- CSS
- JavaScript（TypeScript）

<p>HTMLでマークアップを行い、CSSで見た目を調整して、JavaScriptでプログラムを書くという基本的な構成要素は変わっていない。</p>
<p>フロントエンドに関しては、今年も来年も変わらず、HTML・CSS・JavaScriptが大事！</p>

---

# 2021年のJavaScriptライブラリの使用状況
<div class="flex">
  <div class="img">
    <img src="/img/img-1.png" alt="">
    <span class="quote">引用: <a href="https://insights.stackoverflow.com/survey/2021" target="_blank" rel="noopener noreferrer">Stack Overflow</a></span>
  </div>
  <div class="text">
    <p>Stack Overflowが行った2021年のウェブフレームワークの使用率の調査結果から以下の傾向が分かる。</p>
    <ul>
      <li>世界的に見ると、VueよりもReactの方がかなり使用率が高い</li>
      <li>Reactが最も使用されるウェブフレームワークとして、jQueryを上回った</li>
    </ul>
    <img src="/img/img-2.png" alt="">
  </div>
</div>

<style>
.flex {
  display: flex;
  justify-content: space-between;
}

.text {
  width: 50%;
}

.quote {
  font-size: 14px;
}

.img {
  width: 50%;
}

.img img {
  display: block;
  max-width: 300px; 
  height: auto;
  margin-bottom: 8px;
}

p, ul {
  font-size: 16px;
}
</style>
---

# 2021年のReact
<h2 class="heading">今年の大きな動き</h2>
<p>React自体の大きな変化や仕様変更は特になし。<br>フレームワークに関しては、<a href="https://nextjs.org/" target="_blank" rel="noopener noreferrer">Next.js</a>がJSフレームワークの覇権を握っていると言っても過言ではないような状況になっている。</p>

<h2 class="heading">来年以降に予想される大きな動き</h2>
<p>React Conf 2021で、メモ化を自動的に行うコンパイラが発表された。</p>
<img src="https://pbs.twimg.com/media/FGHF7ptVcAgpO5x?format=jpg&name=large" alt="">

<style>
.heading {
  font-size: 26px !important;
  margin-top: 0;
  margin-bottom: 10px !important;
  line-height: 1.2 !important;
}
img {
  display: block;
  max-width: 380px; 
  height: auto;
}
</style>
---

# Next.jsって何がすごいのか
<ol>
  <li>複数のHTML生成戦略を持つことができる</li>
  <li>Reactの知見があれば、特に学習しなくてもすぐに使うことができる</li>
  <li>ルーティングを簡単に定義できる機能や、画像・CSS・JSの最適化、サーバーサイドでNode.jsを簡単にできる機能など便利機能がたくさんある</li>
</ol>

<h2 class="heading">複数のHTML生成戦略とは？</h2>
<ul>
  <li><strong class="strong">SG (Static Generation)</strong> → Node.jsを使用して、静的なHTMLファイルを事前生成する手法。</li>
  <li><strong class="strong">SSR (Server-Side Rendering)</strong> → アクセス時にサーバーサイドでHTMLファイルを生成する手法。</li>
  <li><strong class="strong">ISR (Incremental Static Regeneration)</strong> → リクエスト時にページのキャッシュを作成して、バックエンド側で次のアクセスに向けたキャッシュの再生成を行うことでHTMLを生成する手法。</li>
</ul>

<span class="important">ISRはユーザーのアクセスをトリガーにデータの更新が行われるので、ある程度ユーザーからアクセスがあるサイト・サービスであることが前提条件</span>

<style>
.heading {
  font-size: 26px !important;
  margin-top: 0;
  margin-bottom: 10px !important;
  line-height: 1.2 !important;
}

.strong {
  color: cornflowerblue;
}

.important {
  color: #f44336;
}
</style>
---

# Reactにおけるメモ化って何？
<p>Reactにおけるパフォーマンスチューニングの方法の一つ</p>
<p>依存する値が変化した時のみ再レンダリングを行うuseMemoと依存する値が変化した時のみ処理を実行するuseCallbackの2種類が存在する。<br />メモ化を利用することで、不要なレンダリングを抑制することができパフォーマンスチューニングにつながる</p>

useMemo
```ts
const sortedPosts = useMemo(() => {
  return posts;
}, [posts]);
```

useCallback
```ts
const memoizedCallback = useCallback(() => {
  // 中に渡した関数
  doSomething(a, b);
}, [a, b]);
```
---

# 2021年のVue
<h2 class="heading">今年の大きな動き</h2>
<ul>
  <li>Vue3 Composition APIの普及。</li>
  <li><a href="https://v3.nuxtjs.org/" target="_blank" rel="noopener noreferrer">Nuxt3</a> Beta版のリリース</li>
</ul>

<h2 class="heading">来年以降に予想される大きな動き</h2>
<p>Nuxt3の安定板がリリースされたら、Vue界隈が盛り上がりそう</p>
<img src="https://pbs.twimg.com/profile_images/1438501794754142212/_SXc-Z_h_400x400.jpg" alt="">
<span>引用: NuxtJS公式Twitter</span>

<style>
.heading {
  font-size: 26px !important;
  margin-top: 0;
  margin-bottom: 10px !important;
  line-height: 1.2 !important;
}
img {
  display: block;
  max-width: 180px; 
  height: auto;
}
</style>

---

# Vue3 Composition APIとは？
<p>Composition APIとは、2020年の9月頃にVue3に追加されたコンポーネント設計を行うための新機能のこと。</p>
<p>従来の書き方（Options API）と比べると、TypeScriptの型の恩恵を受けやすくなったり、ビューとロジックを切り離せるようになったことで、ロジックの再利用がしやすくなったという特徴がある。</p>

---

# Options API
```vue
<template>
  <button @click="increment">Counter</button>
  <p>{{ count }}</p>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    }
  },
  methods: {
    increment () {
      this.count++;
    }
  },
}
</script>
```

---

# Composition API
```vue
<template>
  <button @click="increment">Counter</button>
  <p>{{ count }}</p>
</template>

<script>
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const count = ref(0);

    const increment = () => count.value++;

    return {
      count,
      increment,
    };
  },
});
</script>
```

---

# Composition API
```ts
import { ref } from 'vue';

export const useCounter = () => {
  const count = ref(0);
  const increment = () => count.value++;

  return {
    counter,
    increment,
  }
}
```

---

# Composition API
```vue
<template>
  <button @click="increment">Counter</button>
  <p>{{ count }}</p>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { useCounter } from "~/hooks/useCounter";

export default defineComponent({
  setup() {
    const { count, increment } = useCounter();

    return {
      count,
      increment,
    };
  },
});
</script>
```
<div v-click></div>
<div v-after>Options APIと比べてコードがシンプルで読みやすくなる！</div>

---

# Nuxt3の特徴
<ol>
  <li>セットアップが2系に比べてだいぶ楽になった。（create-nuxt-app時の質問攻めが無くなった🎉）</li>
  <li>TypeScript・Composition API標準対応。</li>
  <li>Nitroと呼ばれる新しいサーバーサイドエンジンを導入することで、API Routes・ISRの使用が可能に。</li>
  <li>動的ルーティングの指定方法や、ディレクトリ構成などがNext.jsに近くなった</li>
</ol>
<a href="https://zenn.dev/ytr0903/articles/d0a91f6180d34e" target="_blank" rel="noopener noreferrer">https://zenn.dev/ytr0903/articles/d0a91f6180d34e</a>

---

# ホスティングサービスの話
<p>2021年は、ホスティングサービスの躍進が目立った</p>
<h2>ホスティングサービスとは？</h2>
<p>事業者の所有するサーバの一部をインターネット経由で貸し出すサービスのこと。<br />フロントエンド界隈だと、HTMLのビルド時にNode.jsが使用できたり、Serverless Functionsなどが使用できるホスティングサービスが注目されている。</p>
<div v-click></div>
<div v-after>
  <p>知識さえあればブログくらいなら、無料で運用を行うことも可能。</p>
  <a href="https://karukichi-blog.netlify.app/" target="_blank" rel="noopener noreferrer">https://karukichi-blog.netlify.app/</a>
</div>

---

# 主要なホスティングサービス比較
| サービス名  | ビルド速度   | 料金 | その他 |
| --- | --- | --- | --- |
| <a href="https://vercel.com/" target="_blank" rel="noopener noreferrer">Vercel</a> | かなり速い | 無料プランあり（PROだと$19 / member）| 表示速度、機能面は断トツ！ |
| <a href="https://www.netlify.com/" target="_blank" rel="noopener noreferrer">Netlify</a> | 普通 | 無料プランあり（PROだと$20 / member）| 無料でも商用利用可能 |
| <a href="https://pages.cloudflare.com/" target="_blank" rel="noopener noreferrer">Cloudflare Pages</a> | 分からない | 無料プランあり（$20 ※チームの人数は関係なし）| Bandwidth無制限 かつ ホスティング可能なサイト数も無制限。|
| <a href="https://aws.amazon.com/jp/amplify/" target="_blank" rel="noopener noreferrer">AWS Amplify</a> | かなり遅い | 従量課金制なのでなんとも言えない | 様々なAWSのサービスと連携させたりする場合はリソース管理が楽になる |

<p>細かい比較記事</p>
<a href="https://zenn.dev/catnose99/scraps/6780379210136f" target="_blank" rel="noopener noreferrer">https://zenn.dev/catnose99/scraps/6780379210136f</a>

---

# 
<h1>ご静聴ありがとうございました。</h1>
