<template>
  <v-container>
    <h2>{{ title }}</h2>
    <div>
          <v-text-field label="enter name" v-model="name"></v-text-field>
            hello:{{ name }}
            This is home page.
    </div>

  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
    title:"This is my first Vue Project.",
    name:""
  }),
}
</script>
