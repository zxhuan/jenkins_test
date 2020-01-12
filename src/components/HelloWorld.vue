<template>
  <div class="box">
    <div class="box1">
      <ul class="ul-list">
        <li class="list-item" v-for="(item,key) of dataList" :key='key' draggable="true"
          @dragstart="onDragstart($event,item)">
          {{item.name}}111</li>
      </ul>
      <div class="box2" @dragend="onDragend($event)" @dragover="onDragover($event)" @drop="onDrop($event)"
        data-listName='list1'>
        <div class="box-item" v-for="(item,key) of list1">
          <span>{{item.name}}</span><span>{{item.name}}</span>
        </div>
      </div>
      <div class="box3" @dragend="onDragend($event)" @dragover="onDragover($event)" @drop="onDrop($event)"
        data-listName='list2'>
        <div class="box-item" v-for="(item,key) of list2">
          <span>{{item.name}}</span><span>{{item.name}}</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        dataList: [
          { id: 1, name: 11 },
          { id: 2, name: 12 },
          { id: 3, name: 13 },
        ],
        activeItem: {},
        list1: [],
        list2: [],
      }
    },
    methods: {
      onDragstart($event, item) {
        this.activeItem = item;
        console.log('dargestart')
      },
      getParentNode(target, dataName) {
        let _name = target.getAttribute(`data-${dataName}`);
        if (!_name) {
          return this.getParentNode(target.parentNode, dataName)
        }
        return _name;
      },
      onDrop($event) {
        let listName = this.getParentNode($event.target, 'listName')
        let _index = this[listName].findIndex(item => item.id == this.activeItem.id);
        if (_index >= 0) {
          console.log('该数据已经存在')
        } else {
          this[listName].push(this.activeItem);
        }
        console.log('drop')

      },
      onDragover($event) {
        console.log('dragover')
        $event.preventDefault()
      },
      onDragend($event) {
        console.log('dragend')
      },
    }
  }
</script>
<style>
  .box {
    height: 1000px;
    width: 100%;
  }

  .box1 {
    list-style-type: none;
    margin: 0;
  }

  li {
    height: 35px;
    list-style-type: none;
    margin: 0;
    cursor: move;

  }

  li:hover {
    background: yellow;
  }

  .box2 {
    height: 300px;
    width: 300px;
    background: red;
  }

  .box3 {
    height: 300px;
    width: 300px;
    background: green;
  }
</style>