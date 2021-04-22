<template>
  <div class="my-form">
    <b-modal id="bv-modal-wellDrillingOrderEdit" hide-footer>
      <form>
        <div class="d-block text-center">
          <b-card title="Редактировать наряд">
            <div class="mb-3">
              <label>Заказчик</label>
          <input
            class="form-control"
            type="text"
            name="customer"
            placeholder="Заказчик"
            @change="handleChange"
            :value="form.customer"
          />
            </div>
            <div class="mb-3">
               <label>Подрядчик</label>
          <input
          class="form-control"
            type="text"
            name="contractor"
            placeholder="Подрядчик"
            @change="handleChange"
            :value="form.contractor"
          />
            </div>
            <div class="mb-3">
             <label>Месторождение </label>
          <input
          class="form-control"
            type="text"
            name="oilField"
            placeholder="Месторождение"
            @change="handleChange"
            :value="form.oilField"
          />
            </div>
            <div class="mb-3">
               <label>Номер скважины</label>
          <input
          class="form-control"
            type="text"
            name="wellNumber"
            placeholder="Номер скважины"
            @change="handleChange"
            :value="form.wellNumber"
          />
            </div>
            <div class="mb-3">
              <label>Назначение скважины</label>
          <input class="form-control"
            type="text"
            name="wellPurpose"
            placeholder="Назначение скважины"
            @change="handleChange"
            :value="form.wellPurpose"
          />
            </div>
            <div class="mb-3">
               <label>Буровая установка</label>
          <input class="form-control"
            type="text"
            name="drillingRig"
            placeholder="Буровая установка"
            @change="handleChange"
            :value="form.drillingRig"
          />
            </div>
            <div class="mb-3">
              <label>Конструкция скважины</label>
          <input class="form-control"
            type="text"
            name="wellDesign"
            placeholder="Конструкция скважины"
            @change="handleChange"
            :value="form.wellDesign"
          />
            </div>
            <div class="mb-3">
              <label>Направление</label>
          <input class="form-control"
            type="text"
            name="direction"
            placeholder="Направление"
            @change="handleChange"
            :value="form.direction"
          />
            </div>
            <div class="mb-3">
              <label>Кондуктор</label>
          <input class="form-control"
            type="text"
            name="conductor"
            placeholder="Кондуктор"
            @change="handleChange"
            :value="form.conductor"
          />
            </div>
             <div class="mb-3">
              <label>Эксплутационная колонна</label>
          <input class="form-control"
            type="text"
            name="operatingColumn"
            placeholder="Эксплутационная колонна"
            @change="handleChange"
            :value="form.operatingColumn"
          />
            </div>
             <div class="mb-3">
              <label>Диаметр</label>
          <input class="form-control"
            type="text"
            name="diameter"
            placeholder="Диаметр"
            @change="handleChange"
            :value="form.diameter"
          />
            </div>
             <div class="mb-3">
              <label>Глубина искусственного забоя</label>
          <input class="form-control"
            type="text"
            name="artificialFaceDepth"
            placeholder="Глубина искусственного забоя"
            @change="handleChange"
            :value="form.artificialFaceDepth"
          />
            </div>
             <div class="mb-3">
              <label>Глубина установки</label>
          <input class="form-control"
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
          </b-card>
        </div>
      </form>
    </b-modal>

  </div>
</template>

<script>
export default {
  name: "EditModalForm",
  data() {
    return {
      btnName: "Изменить",
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
      if (this.formValidation()) {
        // window.console.log("ready to submit");
        this.$emit("onFormSubmit", this.form);
        // clear form fields
        this.clearFormFields();
      }
    },

    formValidation() {
        // first name
        if (document.getElementsByName("customer")[0].value === "") {
            alert("Enter customer");
            return false;
        }

        // last name
        if (document.getElementsByName("contractor")[0].value === "") {
            alert("Enter contractor");
            return false;
        }

        // email
        if (document.getElementsByName("oilField")[0].value === "") {
            alert("Enter oilField");
            return false;
        }

        // email
        if (document.getElementsByName("wellNumber")[0].value === "") {
            alert("Enter wellNumber");
            return false;
        }

        // email
        if (document.getElementsByName("wellPurpose")[0].value === "") {
            alert("Enter wellPurpose");
            return false;
        }

        // email
        if (document.getElementsByName("drillingRig")[0].value === "") {
            alert("Enter drillingRig");
            return false;
        }

        // email
        if (document.getElementsByName("wellDesign")[0].value === "") {
            alert("Enter wellDesign");
            return false;
        }

        // email
        if (document.getElementsByName("direction")[0].value === "") {
            alert("Enter direction");
            return false;
        }

        // email
        if (document.getElementsByName("conductor")[0].value === "") {
            alert("Enter conductor");
            return false;
        }

        // email
        if (document.getElementsByName("operatingColumn")[0].value === "") {
            alert("Enter operatingColumn");
            return false;
        }

        // email
        if (document.getElementsByName("diameter")[0].value === "") {
            alert("Enter diameter");
            return false;
        }

        // email
        if (document.getElementsByName("artificialFaceDepth")[0].value === "") {
            alert("Enter artificialFaceDepth");
            return false;
        }

        // email
        if (document.getElementsByName("installationDepth")[0].value === "") {
            alert("Enter installationDepth");
            return false;
        }

        return true;
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
  }
};
</script>

<style scoped></style>
