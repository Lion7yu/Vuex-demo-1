<template>
  <input type="text" :value="search" @input="onChange" />
  <span>城市 :{{searchText}}</span>
</template>

<script>
import { computed } from '@vue/runtime-core'
import { useStore } from 'vuex'
export default {
  setup(){
    let store = useStore()
    const onChange = e =>{
      store.commit('setSearch',e.target.value)
      store.dispatch('getWeather',e.target.value)
    }
    return{
      search: computed(()=>store.state.search),
      serchText: computed(()=>store.getters.serchText),
      onChange
    }
  }
}
</script>