<template>
  <div class="mx-4">
    <div class="my-4">New Task</div>
    <v-form ref="form" v-model="valid" lazy-validation>
      <div class="row">
        <v-col class="col-6">
          <label class="font-14">Task Type *</label>
          <v-select
            :items="updateArray"
            :rules="rules.taskRules"
            outlined
            v-model="formData.name"
            dense
            required
          >
          </v-select>
        </v-col>
        <v-col class="col-6">
          <label class="font-14">Subject</label>
          <v-text-field
            outlined
            v-model="formData.subject"
            :rules="rules.subjectRules"
            dense
          ></v-text-field>
        </v-col>
      </div>
      <div class="row">
        <v-col class="col-6">
          <v-col class="px-0 pt-0">
            <label class="font-14">Assigned to *</label>
            <v-select
              :items="names"
              outlined
              v-model="formData.assign"
              :rules="rules.assignRules"
              dense
            >
            </v-select>
          </v-col>
          <v-row>
            <v-col>
              <label class="font-14">Start Date</label>
              <v-text-field
                type="date"
                outlined
                v-model="formData.sDate"
                dense
              ></v-text-field>
            </v-col>
            <v-col>
              <label class="font-14">End Date</label>
              <v-text-field
                type="date"
                outlined
                v-model="formData.edate"
                dense
              ></v-text-field>
            </v-col>
            <v-col>
              <label class="font-14">Remind On</label>
              <v-text-field
                type="date"
                outlined
                v-model="formData.reminder"
                dense
              ></v-text-field>
            </v-col>
            <v-col>
              <label class="font-14">Status</label>
              <v-select
                :items="status"
                outlined
                v-model="formData.updates"
                dense
              >
              </v-select>
            </v-col>
          </v-row>
          <!-- <v-col class="px-0">
                    <label class="font-14">Remind On</label>
                    <v-text-field
                        type="date"
                        outlined
                        v-model="reminder"
                        dense
                    ></v-text-field>
                </v-col> -->
        </v-col>

        <v-col class="col-6">
          <div>
            <label class="font-14">Details</label>
            <v-textarea
              outlined
              name="input-7-4"
              height="210px"
              v-model="formData.detail"
            ></v-textarea>
          </div>
          <div class="d-flex" align="center">
            <v-col>
              <v-btn
                class="ma-2"
                outlined
                color="rgb(148, 145, 145)"
                width="100%"
                @click="clear"
              >
                Cancel
              </v-btn>
            </v-col>
            <v-col>
              <v-btn
                class="ma-2"
                outlined
                color="orange"
                width="100%"
                @click="submit(formData)"
              >
                Apply
              </v-btn>
            </v-col>
          </div>
        </v-col>
      </div>
      <div>
        <hr />
        <div>
          <div class="mt-4">Task List</div>
        </div>
        <v-simple-table class="table-outlined mb-4">
          <template v-slot:default>
            <thead>
              <tr>
                <th class="text-left">
                  #
                </th>
                <th class="text-left">
                  Subject
                </th>
                <th class="text-left">
                  Type
                </th>
                <th class="text-left">
                  Assigned to
                </th>
                <th class="text-left">
                  Due Date
                </th>
                <th class="text-left">
                  Status
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(task, idx) in tasks" :key="idx.name">
                <td class="font-12">{{ idx + 1 }}</td>
                <td class="font-12 text-aqua">{{ task.subject }}</td>
                <td class="font-12">{{ task.name }}</td>
                <td class="font-12">{{ task.assign }}</td>
                <td class="font-12">{{ task.edate }}</td>
                <td class="font-12">{{ task.updates }}</td>
              </tr>
            </tbody>
          </template>
        </v-simple-table>
      </div>
    </v-form>
  </div>
</template>
<script>
export default {
  data: () => ({
    tasks: [],
    updateArray: ["To Do", "UI","Testing","Backend"],
    names: ["Rakesh", "Yogesh", "Nagesh", "Mayur"],
    status: ["Completed", "Pending", "Not Completed"],

    formData: {
      name: "",
      subject: "",
      assign: "",
      sDate: "",
      edate: "",
      reminder: "",
      detail: "",
      updates: ""
    },

    valid: true,
    rules: {
      taskRules: [v => !!v || "Name is required"],
      subjectRules: [v => !!v || "Task is required"],
      assignRules: [v => !!v || "Task is required"]
    }
  }),
  methods: {
    clear() {
      this.$refs.form.reset();
    },
    submit: function() {
      this.$refs.form.validate();
      this.tasks.push(this.formData);
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
      this.formData = {};
    }
  }
};
</script>
<style lang="scss">
.v-text-field.v-text-field--enclosed .v-text-field__details {
  display: none;
}
.font-14 {
  font-size: 14px;
}
.font-12 {
  font-size: 12px !important;
}
.text-aqua {
  color: rgb(5, 156, 156);
}
.table-outlined{
  border: 1px solid rgb(221, 220, 220);
}
</style>
