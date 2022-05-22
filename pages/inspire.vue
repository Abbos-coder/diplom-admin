<template>
  <div>
    <v-row>
      <v-col>
        <p>Добавить подкатегорию</p>
        <v-select
          outlined
          :items="all_main_category"
          v-model="old_ctg.category"
          label="Существующие категории"
          eager
        />
        <v-text-field
          clearable
          outlined
          label="Подкатегория"
          v-model="old_ctg.sub_category"
        />
        <div class="text-right">
          <v-btn
            color="success"
            class="text-capitalize"
            @click="addSubCategory"
          >
            Добавить
          </v-btn>
        </div>
      </v-col>
      <v-col>
        <p>Добавить новую категорию</p>
        <v-text-field
          clearable
          outlined
          label="Главная категория"
          v-model="new_ctg.category"
        />
        <v-text-field
          clearable
          outlined
          label="Подкатегория"
          v-model="new_ctg.sub_category"
        />
        <div class="text-right">
          <v-btn color="primary" class="text-capitalize" @click="addCategory">
            Добавить
          </v-btn>
        </div>
      </v-col>
    </v-row>
    <!-- For new  Notification -->
    <v-snackbar
      v-model="new_snackbar"
      :timeout="timeout"
      right
      top
      color="success"
      shaped
      transition="true"
      outlined
    >
      {{ new_text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="blue" text v-bind="attrs"> Close </v-btn>
      </template>
    </v-snackbar>

    <!-- For old  Notification -->
    <v-snackbar
      v-model="old_snackbar"
      :timeout="timeout"
      left
      top
      transition="true"
      shaped
      color="primary"
      outlined
    >
      {{ old_text }}

      <template v-slot:action="{ attrs }">
        <v-btn color="success" text v-bind="attrs"> Close </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  name: "InspirePage",
  data: () => ({
    all_main_category: [],
    old_ctg: {
      category: "",
      sub_category: "",
    },
    new_ctg: {
      category: "",
      sub_category: "",
    },
    new_snackbar: false,
    new_text: "Новая категория добавлена !",
    old_snackbar: false,
    old_text: "Добавлена подкатегория !",
    timeout: 5000,
  }),
  methods: {
    async addCategory() {
      try {
        await this.$axios.$post("/api/category/", this.new_ctg);
        await this.$axios.$get("/api/category/").then((res) => {
          this.all_main_category = res;
          const all_data = res;
          all_data.forEach((item) => {
            item.text = item.category;
            item.value = item._id;
            delete item.category;
            delete item._id;
          });
        });
      } catch (error) {
        console.error(error);
      }
    },
    async addSubCategory() {
      try {
        const id = this.old_ctg.category;
        await this.$axios.$put(`/api/category/${id}`, this.old_ctg);
        this.old_ctg.sub_category = "";
        this.old_snackbar = true;
      } catch (error) {
        console.error(error);
      }
    },
  },
  async mounted() {
    await this.$axios.$get("/api/category/").then((res) => {
      this.all_main_category = res;
      const all_data = res;
      all_data.forEach((item) => {
        item.text = item.category;
        item.value = item._id;
        delete item.category;
        delete item._id;
      });
    });
  },
};
</script>
