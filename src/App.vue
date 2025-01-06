<template>
  <div class="rowtable" @scroll="handleScrollTop">
    <div class="rowtable_rowheight" v-for="(item,index) in viewList" :key="startIndex + index"
    :style="{transform:`translateY(${(startIndex + index)* rowHeight}px`}">{{ item }}</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
  return {
    //数据源
   items:Array.from({length:1000},(_,i) => `Item,${i}`),
   //页面上渲染的数据
   viewList:[],
   //起始索引
   startIndex:0,
   //终止索引
   endIndex:0,
   //行高
   rowHeight:30,
   //滚动的top值
   scollTop:0,
   containerHeight:400
  };
},
mounted() {
  this.setscollinfo()
},
methods: {
  handleScrollTop(event){
    const newscollTop = event.target.scrollTop
    if(Math.abs(newscollTop - this.scollTop) > this.rowHeight){
      this.scollTop = newscollTop
      this.setscollinfo()
    }
  },
  /**
   * 
   * @param name 
   * @param id 
   * @param text 
   */
  settime(name,id,text){

  },
  setscollinfo(){
    //设置缓冲区 10
    const viewkz = 10
    this.startIndex = Math.max(0,Math.floor(this.scollTop / this.rowHeight) - viewkz)
    this.endIndex = Math.min(this.items.length,this.startIndex + Math.ceil(this.containerHeight  /this.rowHeight) + viewkz * 2)
    this.viewList = this.items.slice(this.startIndex,this.endIndex)
  }
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.rowtable{
  height: 400px;
  overflow-y: auto;
  border: 1px solid #ccc;
  position: relative;
}
.rowtable_rowheight{
  height: 30px;
  position: absolute;
  padding: 10px;
  border: 1px solid #ccc;
  width: 100%;
  box-sizing: border-box;
}
</style>
