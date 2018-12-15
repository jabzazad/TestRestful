<template>
<div>
<h1>Product</h1>
    <b-form-group horizontal label="Filter" class="mb-0">
          <b-input-group>
            <b-form-input v-model="filter" placeholder="Type to Search" />
            <b-input-group-append>
              <b-btn :disabled="!filter" @click="filter = ''">Clear</b-btn>
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
 <b-table striped hover :items="products" :filter="filter" :fields="fields" :per-page="pageSize" :current-page="pageIndex" @filtered="onFiltered"></b-table>
 
 <b-pagination align="center" size="md" :total-rows="products.length" v-model="pageIndex" :per-page="pageSize">
 </b-pagination>
</div>
</template>
<script>
import axios from 'axios'
export default {
    name:'product',
    components: {},
    data(){
        return{
        message:"project1"
        ,products:[],
        pageSize:10,
        pageIndex:1,
        filter:null,
        fields:[
        {key:'product_id',sortable:true},
        {key:'product_name',sortable:true},
        {key:'supplier_id',sortable:true,variant:'danger'}
         ,{key:'quantity_per_unit',sortable:true},
          {key:"unit_price",sortable:true},
           {key:'units_in_stock',sortable:true},
            {key:'units_in_order',sortable:true},
             {key:'reorder_level',sortable:true},
              {key:'discontinued',sortable:true}
        ]}
        }, methods: {
    onFiltered (filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length
      this.currentPage = 1
    }
  },
        mounted(){
            axios.get('https://serverquize.herokuapp.com/api/products')
            .then(response=>{
                console.log(response.data)
this.products=response.data.data
            })
        }
}
</script>
