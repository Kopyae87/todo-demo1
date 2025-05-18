<template>
  <v-container>
    
    <v-row >
      <v-col cols="12">
        <h2>{{ title }}</h2>
        <div>
          <v-text-field label="Enter Name" v-model="name" @keydown.enter="changeflag" :disabled="flag"></v-text-field>
            hello: {{ name }}
        </div>
      </v-col>
    </v-row>
    
    <v-row>
      <v-col cols="9">
          <v-text-field label="What will you do" v-model="todo"></v-text-field>
      </v-col>
      <v-col cols="3">
          <v-text-field label="How long it will take" v-model="duration"></v-text-field>
      </v-col>
    </v-row>
    
    <v-row>
      <v-col>
        <div>
          <v-btn @click="add">
            Add To List
            
          </v-btn>
        </div>
      </v-col>
      <v-col>
        <div>
          <v-btn @click="remove">
            Remove From List
          </v-btn>
        </div>
      </v-col>
    </v-row>
    
    <div>
      <v-table>
        <thead>
          <tr>
            <th class="text-left">
              Id
            </th>
            <th class="text-left">
              Todo
            </th>
            <th class="text-left">
              Duration
            </th>
            <th>
              Remark
            </th>

          </tr>
        </thead>
        <tbody>
          <tr
            v-for="item in todolist"
            :key="item.id"
          > 
            <td>{{ item.id }}</td>
            <td>{{ item.todo }}</td>
            <td>{{ item.duration }} hr(s)</td>
            <td v-if="item.duration > 0.75"> Lazy </td>
            <td v-else>Active</td>
            <td><v-btn @click="deleteitem(item)"  prepend-icon="mdi-delete-variant"></v-btn></td>
          </tr>
        </tbody>
      </v-table>
    </div>
  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    title:"",
    name:"",
    flag:false,
    todolist: [
          {
            id:1,
            todo: 'Attend OJT',
            duration: 3,
          },
          {
            id:2,
            todo: 'Clean the house',
            duration: 0.5,
          }
      ]
  }),

  methods:{
    generateid(){
      return this.todolist[this.todolist.length-1]+1
    },
    add(){
      this.todolist.push({id:this.todolist.length+1, todo:this.todo , duration:this.duration})
    },
    async remove(){
      console.log("one")
      await new Promise(resolve =>
        setTimeout(()=>{
        console.log("two"); resolve();
        },5000)
      )      
      console.log("three")
      // this.todolist.pop({id:this.todolist.length-1, todo:this.todo , duration:this.duration})
    }
    ,
    deleteitem(item){
      this.todolist=this.todolist.filter(todo => todo.todo != item.todo)
    },
    changeflag(){
      this.flag=!this.flag
    }
  },
  async created(){
    await new Promise(resolve =>
     setTimeout(()=>{
      this.title="this is my first vue project"; resolve();
     },5000)
     )      
  }
}
</script>
