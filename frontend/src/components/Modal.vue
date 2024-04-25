<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal" role="dialog" aria-labelledby="modalTitle" aria-describedby="modalDescription">
        <section class="modal-body" id="modalDescription">
          <slot name="body">
            <div class="input-container">
              <input v-model="message" type="text" class="custom-input">
              <label>Enter Your OTP:</label>
            </div>
            <div class="input-container">
              <button> Resend OTP</button>
            </div>
          </slot>
        </section>
        <footer class="modal-footer">
          <button type="button" class="btn-red" @click="close" aria-label="Close modal">
            Cancel
          </button>
          <button type="button" class="btn-green" @click="logMessage" aria-label="Close modal">
            Pay
          </button>
        </footer>
      </div>
    </div>
  </transition>
</template>

<script>

export default {

  name: 'Modal',

  methods: {
    close() {
      this.$emit('close');
    },
    data: {
      message: ''
    },
    logMessage: function () {
      console.log(this.message);
    }
  },
};
</script>

<style scoped>
.input-container {
  position: relative;
  margin: 50px auto;
  width: 300px;
}

.custom-input {
  width: 100%;
  padding: 15px 20px;
  background-color: #f8f8f8;
  border: none;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  font-size: 16px;
  transition: box-shadow 0.3s, background-color 0.3s;
}

.custom-input:focus {
  outline: none;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  background-color: #fff;
}

label {
  position: absolute;
  top: 15px;
  left: 20px;
  color: #aaa;
  font-size: 16px;
  pointer-events: none;
  transition: top 0.3s, font-size 0.3s, color 0.3s;
}

.custom-input:focus~label,
.custom-input:not(:placeholder-shown)~label {
  top: 5px;
  font-size: 12px;
  color: #2196F3;
}



.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
  width: 0px
}

.modal {
  background: #FFFFFF;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
}

.modal-header,
.modal-footer {
  padding: 15px;
  display: flex;
  justify-content: space-around
}

.modal-header {
  position: relative;
  border-bottom: 1px solid #eeeeee;
  color: #4AAE9B;
  justify-content: space-between;
}

.modal-footer {
  border-top: 1px solid #eeeeee;
  flex-direction: row;
}

.modal-body {
  position: relative;
  padding: 50px;
}

.btn-close {
  position: absolute;
  top: 0;
  right: 0;
  border: none;
  font-size: 20px;
  padding: 10px;
  cursor: pointer;
  font-weight: bold;
  color: #4AAE9B;
  background: transparent;
}

.btn-red,
.btn-green {
  color: white;
  border: none;
  border-radius: 5px;
  width: 120px;
  padding: 10px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-red {
  background: #FF5733;
}

.btn-green {
  background: #4CAF50;
}

/* Common hover effect */
.btn-red:hover,
.btn-green:hover {
  opacity: 0.9;
  transform: translateY(-2px);
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}


.modal-fade-enter,
.modal-fade-leave-to {
  opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}
</style>
