<template>
  <div>
    <div style="width: 100%; background-color: dodgerblue;">
      <router-link :to="{ name: 'Login' }" class="btn btn-primary">Logout</router-link>
    </div>
    <h1>Create An Item</h1>
    <div class="row">
      <div class="col-md-10"></div>
      <div class="col-md-2"><router-link :to="{ name: 'DisplayItem' }" class="btn btn-success">Return to Items</router-link></div>
    </div>

    <form v-on:submit.prevent="addItem">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Item Name:</label>
            <input id="name" type="text" class="form-control" v-model="item.name">
          </div>
        </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Item Price:</label>
              <input id="price" type="number" class="form-control col-md-6" v-model="item.price" />
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Add Item</button>
        </div>
    </form>
  </div>
</template>
<script>
  export default {
    data(){
        return{
          item:{}
        }
    },
    methods: {
      addItem(){
        if(document.getElementById("name").value != "" && document.getElementById("price").value != ""){
          let uri = 'http://localhost:4000/items/add';
          this.axios.post(uri, this.item).then((response) => {
            this.$router.push({name: 'DisplayItem'})
          })
        }
        else{
          if(document.getElementById("name").value == "" ){
            alert("Add name!")
          }

          if(document.getElementById("price").value == ""){
            alert("Add price!")
          }
        }
    }
  }
}
</script>
