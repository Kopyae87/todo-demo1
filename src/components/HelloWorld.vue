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
    
    <div>
      <v-btn @click="add">
        Add To List
      </v-btn>
    </div>
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
    title:"This is my first Vue Project.",
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
    add(){
      this.todolist.push({id:this.todolist.length+1, todo:this.todo , duration:this.duration})
    },
    changeflag(){
      this.flag=!this.flag
    }
  }
}
</script>
