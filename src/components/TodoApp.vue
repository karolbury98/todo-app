<template>
  <div class="container">
    <h3 class="text-center mt-5">Lista zadań</h3>
    <div class="d-flex">
      <input
        type="text"
        class="form-control"
        placeholder="Dodaj zadanie"
        v-model="enteredValue"
      />
      <button @click="addTask" class="btn btn-warning">Dodaj</button>
    </div>

    <table class="table mt-3">
      <thead>
        <tr>
          <th scope="col">Zadanie</th>
          <th scope="col">Status</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <th>
            <span :class="{ finished: task.status === 'Zakończony' }">{{
              task.name
            }}</span>
          </th>
          <td style="width: 200px">
            <span class="pointer" @click="changeStatus(index)">{{
              task.status
            }}</span>
          </td>
          <td>
            <!-- delete task -->
            <div class="text-center" @click="deleteTask(index)">
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
      enteredValue: "",
      taskStatuses: ["Do wykonania", "W trakcie", "Zakończony"],
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
        status: "Do wykonania",
      });

      this.enteredValue = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    changeStatus(index) {
      let newIndex = this.taskStatuses.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.taskStatuses[newIndex];
    },
  },
};
</script>

<style scoped>
.pointer {
  cursor: pointer;
}

.finished {
  text-decoration: line-through;
}
</style>