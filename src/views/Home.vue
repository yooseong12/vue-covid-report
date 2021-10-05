<template>
  <main v-if="!loading">

    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />

    <CountrySelect @get-country="getCountryData" :countries="countries" />

    <button @click="clearCountryData"
    v-if="stats.Country"
    class="bg-green-700 text-white rounded p-3 mt-10 
    focus:outline-none hover:bg-green-600">
      Clear Country
    </button>
  </main>
  <main class="flex flex-col align-center justify-center
  text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <!-- 이미지를 추가하려고 했지만 아직 안함(모래시계 이미지) <img :> -->
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'



export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  data(){
    return{
      loading : true,
      title: 'Global',
      dataDate: '',
      status:{},
      countries:[],
      // 로딩 이미지 ->   loadingImage:require('')
      
    }
  },
  methods :{


    // async, await = 비동기처리 방식의 새로운 방식
    // 비동기 처리 = 특정 코드의 연산이 끝날 때까지 코드의 샐행을 멈추지 않고 
    // 다음 코드를 먼저 실행하는 코드 
    async fetchCovidData(){
      const res = await fetch('https://api.covid19api.com/summary')
      // json = 객체 표기법을 제한하여 만든 텍스트 기반의 데이터 교환표준
      const data = await res.json() 
      return data
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
    async clearCountryData(){
      this.loading = true
      const data = await this.fetchCovidData() 
      this.title = 'Global'
      this.stats = data.Global
      this.loading = false
    }
    
  },
  async created(){
    const data = await this.fetchCovidData()
    
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
}
</script>
