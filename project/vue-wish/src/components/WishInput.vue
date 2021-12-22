<template lang="html">
  <div class="inputBox shadow">
    <input type="text" v-model="newWishItem" v-on:keyup.enter="addWish"
        placeholder="Type what you wish to do">
    <span class="addContainer" v-on:click="addWish">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>

    <modal v-if="showModal" @close="showModal = false">
      <!--모달제목-->
      <h3 slot="header">경고</h3>
      <!--모달제목-->
      <span slot="footer" @click="showMadal = false">
        위시리스트를 입력하세요.
        <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
      </span>
    </modal>
  </div>
</template>

<script>
import Modal from './common/modal.vue'
export default {
  data(){
    return {
      newWishItem:''
    }
  },
  methods:{
    addWish(){
      if(this.newWishItem !== ""){
        var value = this.newWishItem && this.newWishItem.trim();
        //console.log(this.newWishItem);
        //localStorage.setItem(this.newWishItem, this.newWishItem);
        this.$emit('addWish',value);
        //localStorage.setItem(value, value);
        this.clearInput()
      }
    },
    clearInput(){
      this.newWishItem = '';
    }
  }
}
</script>

<style lang="css" scoped>
input:focus {
  outline: none;}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  margin-bottom: 25px;}
.inputBox input {
  border-style: none;
  font-size: 1.2em;
  font-weight: bold;
  width: 12em;
  color: #2f3b52;}
.addContainer {
  float: right;
  background: linear-gradient(to right, #ff4c4d, #b30000);
  display: inline-block;
  width: 3em;
  border-radius: 0 5px 5px 0;}
.addBtn {
  color: white;
  vertical-align: middle;}
</style>
