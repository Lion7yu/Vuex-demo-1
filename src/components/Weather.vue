<template>
  <div class="weather">
    <h2>{{searchText}} 天气详情</h2>
    <p>天气 {{weather.text}}</p>
    <p>体感温度 {{weather.feels_like}}</p>
    <p>风力 {{weather.wind_class}}</p>
    <button @click="setDefault">深圳天气</button>
  </div>
</template>

<script>
import { computed } from '@vue/runtime-core'
import { useStore } from 'vuex'
export default {
  setup(){
    const store = useStore()
    const setDefault = ()=>{
      store.commit('setSearch','深圳')
      store.dispatch('getWeather','深圳')
    }
    return{
      searchText: computed(()=>store.getters.searchText),
      weather:computed(()=>store.state.weather),
      setDefault
    }
  }
}
</script>