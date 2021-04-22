<template>
  <div class="my-form">
    <b-modal id="bv-modal-wellDrillingOrderShow" hide-footer>
      <table class="ui celled table">
        <tbody>
        <div class="d-block text-center">
          <b-card title="Просмотр наряда">
            <tr>
    <td>Заказчик</td>
    <td>
        <input
            class="form-control"
            type="text"
            name="customer"
            placeholder="Заказчик"
            @change="handleChange"
            :value="form.customer"
          /></td>
 </tr>
  <tr>
    <td>Подрядчик </td>
    <td> <input
          class="form-control"
            type="text"
            name="contractor"
            placeholder="Подрядчик"
            @change="handleChange"
            :value="form.contractor"
          />
          </td>
 </tr>
  <tr>
    <td>Месторождение </td>
    <td><input
          class="form-control"
            type="text"
            name="oilField"
            placeholder="Месторождение"
            @change="handleChange"
            :value="form.oilField"
          />
          </td>
 </tr>
  <tr>
    <td>Номер скважины</td>
    <td><input
          class="form-control"
            type="text"
            name="wellNumber"
            placeholder="Номер скважины"
            @change="handleChange"
            :value="form.wellNumber"
          /></td>
 </tr>
  <tr>
    <td>Назначение скважины</td>
    <td><input class="form-control"
            type="text"
            name="wellPurpose"
            placeholder="Назначение скважины"
            @change="handleChange"
            :value="form.wellPurpose"
          /></td>
 </tr>
  <tr>
    <td>Буровая установка</td>
    <td><input class="form-control"
            type="text"
            name="drillingRig"
            placeholder="Буровая установка"
            @change="handleChange"
            :value="form.drillingRig"
          /></td>
 </tr>
  <tr>
    <td>Конструкция скважины</td>
    <td><input class="form-control"
            type="text"
            name="wellDesign"
            placeholder="Конструкция скважины"
            @change="handleChange"
            :value="form.wellDesign"
          /></td>
 </tr>
  <tr>
    <td>Направление </td>
    <td><input class="form-control"
            type="text"
            name="direction"
            placeholder="Направление"
            @change="handleChange"
            :value="form.direction"
          /></td>
 </tr>
  <tr>
    <td>Кондуктор </td>
    <td><input class="form-control"
            type="text"
            name="conductor"
            placeholder="Кондуктор"
            @change="handleChange"
            :value="form.conductor"
          /></td>
 </tr>
 <tr>
    <td>Эксплутационная колонна </td>
    <td> <input class="form-control"
            type="text"
            name="operatingColumn"
            placeholder="Эксплутационная колонна"
            @change="handleChange"
            :value="form.operatingColumn"
          /></td>
 </tr>
 <tr>
    <td>Диаметр  </td>
    <td><input class="form-control"
            type="text"
            name="diameter"
            placeholder="Диаметр"
            @change="handleChange"
            :value="form.diameter"
          /></td>
 </tr>
 <tr>
    <td>Глубина искусственного забоя </td>
    <td><input class="form-control"
            type="text"
            name="artificialFaceDepth"
            placeholder="Глубина искусственного забоя"
            @change="handleChange"
            :value="form.artificialFaceDepth"
          /></td>
 </tr>
 <tr>
    <td>Глубина установки </td>
    <td><input class="form-control"
            type="text"
            name="installationDepth"
            placeholder="Глубина установки"
            @change="handleChange"
            :value="form.installationDepth"
          /></td>
 </tr>
          </b-card>
        </div>
        </tbody>
      </table>
    </b-modal>

  </div>
</template>

<script>
export default {
  name: "ShowModalForm",
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
    onShow(event) {
      // prevent form submit
      event.preventDefault();
      // form validation
      if (this.formValidation()) {
        // window.console.log("ready to submit");
        this.$emit("onShow", this.form);
        // clear form fields
        this.clearFormFields();
      }
    },
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
