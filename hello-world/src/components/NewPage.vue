<template>
    <div>
        <h1>Vue確認用</h1>
        <div>
            <h2>▼1【データ表示】</h2>
            {{test}}
        </div>
        <div>
            <h2>▼2【画像パス指定】</h2>
            <img alt="Vue logo" v-bind:src="img_src">
        </div>
        <div>
            <h2>▼3【v-for確認】</h2>
            <h3>値だけ</h3>
            <li v-for="element in for_elements" :key="element">
                {{element}}
            </li>
            <h3>要素名＋値</h3>
            <li v-for="(element2, chara) in for_elements2" :key="element2">
                {{chara}} : {{element2}}
            </li>
        </div>
        <div>
            <h2>▼4【イベント確認】</h2>
            <h3>要素名＋値</h3>
            <p>v-on:inputは@に置き換え可能</p>
            <input :placeholder="no4data1" :value="no4data2" 
            v-on:input="no4data2 = $event.target.value">
            {{no4data2}}
            <h3>4v-model確認</h3>
            <input type="text" :placeholder="no4data1" v-model="no4data3">
            {{no4data3}}
        </div>
        <div>
            <h2>▼5【算出プロパティ】</h2>
            <input type="number" v-model="no5bounty">
            <input type="number" v-model="no5count">
            <div>{{total}}</div>
        </div>
        <div>
            <h2>▼6【メソッド】</h2>
            <input type="number" v-model="no6bounty">
            <input type="number" v-model="no6count">
            <div>{{totalmethod()}}</div>
            <h3>算出プロパティ、メソッドの違い</h3>
            <div>算出プロパティ：{{bounty5}}</div>
            <div>メソッド：{{bounty6()}}</div>
        </div>
        <div>
            <h2>▼7【表示非表示】</h2>
            <button v-on:click="show_action()">{{no7datalabel}}</button>
            <p v-show="no7data">表示非表示テスト v-show使用</p>        
            <p v-if="no7data">表示非表示テスト v-if使用</p>
        </div>
        <div>
            <h2>▼8【ライフサイクルフック】</h2>
            <h3>※コンソールログの確認</h3>
        </div>
        <div>
            <h2>▼9【コンポーネント】</h2>
            <h3>NewPageコンポーネント</h3>
            <p>{{msg}}</p>
            <p>{{msg2}}</p>
            <h3>SampleButtonコンポーネント</h3>
            <SampleButton ButtonName="インクリメント" 
                :countNumber="no9count" 
                v-on:return-number="get_number">
            </SampleButton>
            {{no9count}}

        </div>

    </div>
</template>

<script>

import SampleButton from '../components/SampleButton.vue'

export default{
    // 当コンポーネント名定義
    name: 'NewPage',
    // 使用コンポーネント
    components: {
        SampleButton
    },
    // プロパティ定義
    props: {
            msg: String,
            msg2: String
        },
    beforeCreate(){
        console.log(`beforCreate : this.$data ${this.$data}`)
        console.log(this.$data)
        console.log(`beforCreate : this.$el ${this.$el}`)
    },
    created(){
        console.log(`created : this.$data ${this.$data}`)
        console.log(this.$data)
        console.log(`created : this.$el ${this.$el}`)
    },
    beforeMount(){
        console.log(`beforeMount : this.$el ${this.$el}`)
        console.log(this.$el)
    },
    mounted(){
        console.log(`mounted : this.$el ${this.$el}`)
        console.log(this.$el)
    },
    // 当コンポーネント内データ
    data() {
        return {
            test: "テストやで",
            // 画像パスの場合は以下のように書かないとダメ
            img_src: require("../assets/logo.png"),
            for_elements:["test1","test2","test3","test4"],
            for_elements2:{
                test1: "テスト1",
                test2: "テスト2",
                test3: "テスト3",
                test4: "テスト4",
            },
            no4data1: "data",
            no4data2: "aaaa",
            no4data3: "5555",
            no5bounty: "",
            no5count: "",
            no6bounty: "",
            no6count: "",
            no7data: false,
            no7datalabel: "表示",
            no9count: 10,
        }
  },
  // 算出プロパティ
  computed: {
    total(){
        return this.no5bounty * this.no5count
    },
    bounty5() {
        return Math.floor(Math.random() * 100)
    }
  },
  // メソッド
  methods: {
    totalmethod(){
        return this.no6bounty * this.no6count
    },
    bounty6() {
        return Math.floor(Math.random() * 100)
    },
    show_action() {
        if (this.no7data){
            this.no7datalabel = "表示"
            this.no7data = false
        } else {
            this.no7datalabel = "非表示"
            this.no7data = true
        } 
    },
    get_number(return_number) {
        this.no9count = return_number
    }
  }
}
</script>
