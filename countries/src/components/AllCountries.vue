<!-- parent -->
<template>
  <div class="all-countries">
    <div>
        <input class="form-control" v-model="userData" type="text"/>
    </div>
    <div id="btns">
        <Buttons v-on:increment="getData('name', userData)" buttonText="Find Country by Name"></Buttons>
        <Buttons v-on:increment="getData('capital', userData)" buttonText="Find Country by Capital"></Buttons>
        <Buttons v-on:increment="getData('region', userData)" buttonText="Find Country by Region"></Buttons>
        <Buttons v-on:increment="getSortedData('area')" buttonText="Sort by Area"></Buttons>
        <Buttons v-on:increment="getSortedData('population')" buttonText="Sort by Population"></Buttons>
    </div>
    <div class="showcase">
        <ul class="list-group">
            <li class="list-group-item"
                v-for="item in allCountries"
                v-bind:key="item.id"
                v-bind:country="item"
            ><span>{{item.name}}<img :src="item.flag"/></span><br>Capital: {{item.capital}}<br>Population: {{item.population}}<br>{{item.area}}</li>
        </ul>
    </div>
    
  </div>
</template>

<script>
import Buttons from './Buttons.vue';

export default {
    name: "AllCountries",
    data: function(){
        return{
            allCountries: [],
        }
    },
    components:{
        Buttons,
    },
    methods: {
        getData(key='all', val=''){
            fetch(`https://restcountries.eu/rest/v2/${key}/${val}`)
            .then(response=>response.json())
            .then(data=>{
                this.allCountries = data;
            })
            .catch(err => console.log(err));
        },
        getSortedData(filter){
        fetch(`https://restcountries.eu/rest/v2/all`)
            .then(response=>response.json())
            .then(data=>{
                this.allCountries = data.sort((a,b)=>b[filter] - a[filter]);
            })
            .catch(err => console.log(err));
        }
    }
}
</script>


<style scoped>
    .allcountries{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    #btns{
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
    img{
        height: 30px;
        width: 40px;
        margin: 8px;
    }

    .showcase{
        width: 700px;
        margin: 0 auto;
        overflow-y: auto;
        height: 400px;
        border-radius: 10px; 
    }
    input{
        margin: 0 auto;
        width: 50%;
    }

    span{
        font-size: 130%;
        font-weight: 700;
        color: rgb(21, 26, 25);
    }
</style>