<template>
  <div class="container">
    <h3 class="text-center mt-5">Lista zadań</h3>
    <div class="d-flex">
      <input type="text" class="form-control" placeholder="Dodaj zadanie" v-model="enteredValue"/>
      <button @click="addTask" class="btn btn-warning">Dodaj</button>
    </div>

    <table class="table mt-3">
      <thead>
        <tr>
          <th scope="col">Zadanie</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th>{{ task.name }}</th>
          <td>{{ task.status }}</td>
          <td>
            <div class="text-center">
              <span class="fa fa-pen-to-square"></span>
            </div>
          </td>
          <td>
            <div class="text-center">
              <span class="fa fa-trash-can"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data() {
    return {
        enteredValue: '',
      tasks: [
        { name: "test1", status: "Do wykonania" },
        { name: "test2", status: "Do wykonania" },
      ],
    };
  },
  methods: {
    addTask() {
        this.tasks.push({
            name: this.enteredValue,
            status: 'Do wykonania'
        });
    }
  },
};
</script>