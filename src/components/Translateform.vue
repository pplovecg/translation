<template>
  <div id="translateform">
    <form v-on:submit="formSubmit">
    <input type="text" v-model="textToTranslate" placeholder="输入要翻译的内容"><!--可以拿到用户输入的内容-->
    <select v-model="language"><!--使用v-model可以拿到选中的内容-->
      <option value="en">English</option>
      <option value="ko">Korea</option>
      <option value="ja">Japanese</option>
      <option value="ar">Arabic</option>
      <option value="fr">French</option>
    </select>
    <input type="submit" value="翻译"><!-- type='submit'/type='button'是两种表单提交的方式 -->
   </form> 
  </div>
</template>

<script>

export default {
  name: 'translateform',
  data:function(){
    return{
      textToTranslate:"",
      language:""
    }
  },
  methods:{
    formSubmit:function(e){
      //alert(this.textToTranslate);
      this.$emit("formSubmit",this.textToTranslate,this.language);//formSubmit是前一个组件绑定的事件名，language取的是option.value的值
      e.preventDefault();
    }
  }
}
</script>

<style>

</style>
