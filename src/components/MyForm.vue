<template>
  <div class="my-form">
    <form class="ui form">
      <div class="two fields">
        <div class=" field">
         <label>Заказчик</label>
          <input
            type="text"
            name="customer"
            placeholder="Заказчик"
            @change="handleChange"
            :value="form.customer"
          />
        </div>
        <div class=" field">
          <label>Подрядчик</label>
          <input
            type="text"
            name="contractor"
            placeholder="Подрядчик"
            @change="handleChange"
            :value="form.contractor"
          />
        </div>
      </div>
      <div class="two fields">
        <div class=" field">
         <label>Месторождение </label>
          <input
            type="text"
            name="oilField"
            placeholder="Месторождение"
            @change="handleChange"
            :value="form.oilField"
          />
        </div>
        <div class=" field">
          <label>Номер скважины</label>
          <input
            type="text"
            name="wellNumber"
            placeholder="Номер скважины"
            @change="handleChange"
            :value="form.wellNumber"
          />
        </div>
      </div>
      <div class="two fields">
        <div class=" field">
         <label>Назначение скважины</label>
          <input
            type="text"
            name="wellPurpose"
            placeholder="Назначение скважины"
            @change="handleChange"
            :value="form.wellPurpose"
          />
        </div>
        <div class=" field">
          <label>Буровая установка</label>
          <input
            type="text"
            name="drillingRig"
            placeholder="Буровая установка"
            @change="handleChange"
            :value="form.drillingRig"
          />
        </div>
      </div>
      <div class="two fields">
        <div class=" field">
         <label>Конструкция скважины</label>
          <input
            type="text"
            name="wellDesign"
            placeholder="Конструкция скважины"
            @change="handleChange"
            :value="form.wellDesign"
          />
        </div>
        <div class=" field">
          <label>Направление</label>
          <input
            type="text"
            name="direction"
            placeholder="Направление"
            @change="handleChange"
            :value="form.direction"
          />
        </div>
      </div>
      <div class="two fields">
        <div class=" field">
         <label>Кондуктор</label>
          <input
            type="text"
            name="conductor"
            placeholder="Кондуктор"
            @change="handleChange"
            :value="form.conductor"
          />
        </div>
        <div class=" field">
          <label>Эксплутационная колонна</label>
          <input
            type="text"
            name="operatingColumn"
            placeholder="Эксплутационная колонна"
            @change="handleChange"
            :value="form.operatingColumn"
          />
        </div>
      </div>
      <div class="two fields">
        <div class=" field">
         <label>Диаметр</label>
          <input
            type="text"
            name="diameter"
            placeholder="Диаметр"
            @change="handleChange"
            :value="form.diameter"
          />
        </div>
        <div class=" field">
          <label>Глубина искусственного забоя</label>
          <input
            type="text"
            name="artificialFaceDepth"
            placeholder="Глубина искусственного забоя"
            @change="handleChange"
            :value="form.artificialFaceDepth"
          />
        </div>
      </div>
        <div class="field">
         <label>Глубина установки</label>
          <input
            type="text"
            name="installationDepth"
            placeholder="Глубина установки"
            @change="handleChange"
            :value="form.installationDepth"
          />
        </div>
      <button :class="btnClass" @click="onFormSubmit">
            {{ btnName }}
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "MyForm",
  data() {
    return {
      btnName: "Сохранить",
      btnClass: "ui primary button submit-button"
    };
  },
  props: {
    form: {
      type: Object
    }
  },
  methods: {
    handleChange(event) {
      const { name, value } = event.target;
      let form = this.form;
      form[name] = value;
      this.form = form;
    },
    onFormSubmit(event) {
      // prevent form submit
      event.preventDefault();

      // form validation
      
        // window.console.log("ready to submit");
        this.$emit("onFormSubmit", this.form);

        // change the button to save
        this.btnName = "Save";
        this.btnClass = "ui primary button submit-button";

        // clear form fields
        this.clearFormFields();
     
    },
    
    clearFormFields() {
      // clear form data
      this.form.customer = "";
      this.form.contractor = "";
      this.form.oilField = "";
      this.form.wellNumber = "";
      this.form.wellPurpose = "";
      this.form.drillingRig = "";
      this.form.wellDesign = "";
      this.form.direction = "";
      this.form.conductor = "";
      this.form.operatingColumn = "";
      this.form.diameter = "";
      this.form.artificialFaceDepth = "";
      this.form.installationDepth = "";
      this.form.isEdit = false;

      // clear form fields
      document.querySelector(".form").reset();
    }
  },
  updated() {
    if (this.form.isEdit) {
      this.btnName = "Update";
      this.btnClass = "ui orange button submit-button";
    }
  }
};
</script>

<style scoped></style>
