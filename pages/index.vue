<template>
  <div>
    <!-- メインコンテンツ開始 -->
    <!-- トップコンテンツ -->
    <section class="jumbotron text-center">
      <div class="container">
        <h1 class="jumbotron-heading">キカガクの商品紹介サイト</h1>
        <p class="lead text-muted">
          短期のハンズオンセミナーや長期コースなど様々な講座を用意しています。
        </p>
        <p>
          <a href="https://www.kikagaku.co.jp/" class="btn btn-primary my-2">
            キカガクのホームページ
          </a>
        </p>
      </div>
    </section>
    <main>
      <div class="album py-s">
        <div class="centainer">
          <div class="row">
            <!-- 商品カードのコンポーネント -->
            <ProductCard
              v-for="(priduct, index) in items"
              :key="index"
              :name="product.name"
              :img="product.img"
              :text="product.text"
              :url="product.url"
            />
            <!-- 商品カード -->
            <a
              v-for="(product, index) in products"
              :key="index"
              class="col-md-4"
              :href="product.url"
              target="_blank"
            >
              <div class="card mb-4 box-shadow">
                <img
                  class="card-img-top"
                  :src="product.img"
                  data-holder-rendered="true"
                />
                <div class="card-body">
                  <p class="card-text">{{ product.name }}</p>
                  <div
                    class="d-flex justify-content-between align-items-center"
                  >
                    <small class="text-muted">{{ product.text }}</small>
                  </div>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData() {
    console.log('Hello, asyncData!')
    const url =
      'https://api.steinhq.com/v1/storages/6041b1bcf62b6004b3eb66ff/product'

    // APIのレスポンス
    // const res = await axios.get(url)
    // dataの取得
    const { data } = await axios.get(url)
    // console.log(res)
    return {
      products: data,
    }
  },
}
</script>
