<template>
    <div id="1">
        <h1>Bitcoin Price Index</h1>
          <!-- <div
            v-for="currency in a"
            class="currency"
          >
            {{ currency.description }}:
            <span class="lighten">
              <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
            </span>
          </div> -->
          {{a}}
      </div>
</template>

<script>
    module.exports={
        //data:()=>({a:{sss:"233"}})

        data() {
        return{
            a:233
            }
        },
        created(){
            console.log(this.$data.a)
            console.log(this.a)
        },
        mounted(){
        this.getData1();
        console.log
        },
        methods:{
        getData1(){
            this.$axios.get('/api/user/getJson')
            .then((response)=>{
                console.log(response.data);
                this.a=response.data})
            .catch((response)=>{
                console.log(response);});
            }
        }
        
}
console.log(this.a)
    
</script>
