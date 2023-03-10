<template>
  <div class="home">
    <img v-if="regular_now.results[0].stages != null" width="300" src="../assets/now_stage.svg" />
    <hr />
    <p class="tag1" v-if="regular_now.results[0].stages != null">レギュラーマッチ</p>
    <div class="flex-box" v-if="regular_now.results[0].stages != null">
      <div class="item">
        <img class="mb-3" :src="regular_now.results[0].stages[0].image" />
        <h4 class="mb-5">{{ regular_now.results[0].stages[0].name }}</h4>
      </div>
      <div class="item">
        <img class="mb-3" :src="regular_now.results[0].stages[1].image" />
        <h4 class="mb-5">{{ regular_now.results[0].stages[1].name }}</h4>
      </div>
    </div>

    <p class="tag2" v-if="bankara_challenge_now.results[0].stages != null">
      バンカラマッチ (チャレンジ)
    </p>
    <div
      class="flex-box"
      v-if="bankara_challenge_now.results[0].stages != null"
    >
      <div class="item">
        <img
          class="mb-3"
          :src="bankara_challenge_now.results[0].stages[0].image"
        />
        <h4 class="mb-5">
          {{ bankara_challenge_now.results[0].stages[0].name }}
        </h4>
      </div>
      <div class="item">
        <img
          class="mb-3"
          :src="bankara_challenge_now.results[0].stages[1].image"
        />
        <h4 class="mb-5">
          {{ bankara_challenge_now.results[0].stages[1].name }}
        </h4>
      </div>
    </div>

    <p class="tag2" v-if="bankara_open_now.results[0].stages != null">
      バンカラマッチ (オープン)
    </p>
    <div class="flex-box" v-if="bankara_open_now.results[0].stages != null">
      <div class="item">
        <img class="mb-3" :src="bankara_open_now.results[0].stages[0].image" />
        <h4 class="mb-5">
          {{ bankara_open_now.results[0].stages[0].name }}
        </h4>
      </div>
      <div class="item">
        <img class="mb-3" :src="bankara_open_now.results[0].stages[1].image" />
        <h4 class="mb-5">
          {{ bankara_open_now.results[0].stages[1].name }}
        </h4>
      </div>
    </div>

    <img v-if="regular_next.results[0].stages != null" width="300" src="../assets/next_stage.svg" />
    <hr />
    <p class="tag1" v-if="regular_next.results[0].stages != null">
      レギュラーマッチ
    </p>
    <div class="flex-box" v-if="regular_next.results[0].stages != null">
      <div class="item">
        <img class="mb-3" :src="regular_next.results[0].stages[0].image" />
        <h4 class="mb-5">{{ regular_next.results[0].stages[0].name }}</h4>
      </div>
      <div class="item">
        <img class="mb-3" :src="regular_next.results[0].stages[1].image" />
        <h4 class="mb-5">{{ regular_next.results[0].stages[1].name }}</h4>
      </div>
    </div>

    <p class="tag2" v-if="bankara_challenge_next.results[0].stages != null">
      バンカラマッチ (チャレンジ)
    </p>
    <div
      class="flex-box"
      v-if="bankara_challenge_next.results[0].stages != null"
    >
      <div class="item">
        <img
          class="mb-3"
          :src="bankara_challenge_next.results[0].stages[0].image"
        />
        <h4 class="mb-5">
          {{ bankara_challenge_next.results[0].stages[0].name }}
        </h4>
      </div>
      <div class="item">
        <img
          class="mb-3"
          :src="bankara_challenge_next.results[0].stages[1].image"
        />
        <h4 class="mb-5">
          {{ bankara_challenge_next.results[0].stages[1].name }}
        </h4>
      </div>
    </div>

    <p class="tag2" v-if="bankara_open_next.results[0].stages != null">
      バンカラマッチ (オープン)
    </p>
    <div class="flex-box" v-if="bankara_open_next.results[0].stages != null">
      <div class="item">
        <img class="mb-3" :src="bankara_open_next.results[0].stages[0].image" />
        <h4 class="mb-5">
          {{ bankara_open_next.results[0].stages[0].name }}
        </h4>
      </div>
      <div class="item">
        <img class="mb-3" :src="bankara_open_next.results[0].stages[1].image" />
        <h4 class="mb-5">
          {{ bankara_open_next.results[0].stages[1].name }}
        </h4>
      </div>
    </div>

    <img width="300" src="../assets/salmon_run.svg" />
    <hr />
    <p class="tag2">現在のバイト / 次のバイト</p>
    <div class="flex-box">
      <div class="item">
        <img class="mb-3" :src="coop_grouping_now.results[0].stage.image" />
        <h4 class="mb-5">
          {{ coop_grouping_now.results[0].stage.name }}
        </h4>
      </div>
      <div class="item">
        <img class="mb-3" :src="coop_grouping_next.results[0].stage.image" />
        <h4 class="mb-5">
          {{ coop_grouping_next.results[0].stage.name }}
        </h4>
      </div>
    </div>


  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      regular_now: [],
      bankara_challenge_now: [],
      bankara_open_now: [],
      regular_next: [],
      bankara_challenge_next: [],
      bankara_open_next: [],
      coop_grouping_now: [],
      coop_grouping_next: [],
      load: true,
    };
  },
  created() {
    axios
      .get("https://spla3.yuu26.com/api/regular/now")
      .then((response) => {
        this.regular_now = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/bankara-challenge/now")
      .then((response) => {
        this.bankara_challenge_now = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/bankara-open/now")
      .then((response) => {
        this.bankara_open_now = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });

    axios
      .get("https://spla3.yuu26.com/api/regular/next")
      .then((response) => {
        this.regular_next = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/bankara-challenge/next")
      .then((response) => {
        this.bankara_challenge_next = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/bankara-open/next")
      .then((response) => {
        this.bankara_open_next = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/coop-grouping/now")
      .then((response) => {
        this.coop_grouping_now = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://spla3.yuu26.com/api/coop-grouping/next")
      .then((response) => {
        this.coop_grouping_next = response.data;
        this.load = false;
      })
      .catch((error) => {
        console.error(error);
      });
  }
};
</script>

<style>
.flex-box {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.item {
  width: 500px;
  border-radius: 30px;
}
.item h4 {
  padding: 10px;
  font-weight: bold;
  font-size: 20px;
}
.item img {
  width: 100%;
  border-radius: 30px;
}
.tag1 {
  padding: 5px;
  font-weight: bold;
  color: #2bbc33;
}
.tag2 {
  padding: 5px;
  font-weight: bold;
  color: #ff8c00;
}
</style>