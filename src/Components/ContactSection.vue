<script>
import emailjs from 'emailjs-com';

export default {
  name: 'ContactForm',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: '',
      },
      loading: false,
      successMessage: '',
      errorMessage: '',
      // Validation errors object ---
      errors: {
        name: '',
        email: '',
        message: '',
      },
      formSubmitted: false,
    };
  },
  computed: {
    // --- Computed property to check if the entire form is valid ---
   isFormValid() {
      // Check if all error messages are empty AND if formData fields are not empty
    const hasAnyErrors = this.errors.name || this.errors.email || this.errors.message;
    return !hasAnyErrors; 
    }
  },
  methods: {
    // --- Method to clear a specific error message ---
    clearError(field) {
      this.errors[field] = '';
      this.successMessage = '';
      this.errorMessage = '';
    },

    // --- Method to validate the form fields ---
    validateForm() {
      // Reset all errors
      this.errors = {
        name: '',
        email: '',
        message: '',
      };
      let isValid = true; // Flag to track if the form is valid

      // Validate Your Name
      if (!this.formData.name.trim()) {
        this.errors.name = 'Your Name is required.';
        isValid = false; 
    }

      // Validate Your Email
      if (!this.formData.email.trim()) {
        this.errors.email = 'Email is required.';
        isValid = false;
      } else if (!this.isValidEmail(this.formData.email)) {
        this.errors.email = 'Please enter a valid email address.';
        isValid = false;
      }

      // Validate Message
      if (!this.formData.message.trim()) {
        this.errors.message = 'Message is required.';
        isValid = false;
      } else if (this.formData.message.trim().length < 5) {
        this.errors.message = 'Message must be at least 5 characters long.';
        isValid = false;
      }

      return isValid;
    },

    // --- Helper method for basic email validation (regex) ---
    isValidEmail(email) {
      // Very basic regex for email validation
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    },

    // --- sendEmail method to include validation ---
    sendEmail() {
      this.successMessage = '';
      this.errorMessage = '';
      this.formSubmitted = true;

      // First, validate the form
      const formValidationPassed = this.validateForm();
      if (!formValidationPassed) {
        this.errorMessage = 'Please fix the errors in the form.';
        return; // Stop if validation fails
      }

      this.loading = true;

      const serviceID = 'service_f6r8k3a';
      const templateID = 'template_69cjoxe';
      const userID = 'gn61PnwI5vOxx9JOX';

      emailjs.send(serviceID, templateID, this.formData, userID)
        .then((response) => {
          console.log('Email successfully sent!', response.status, response.text);
          this.successMessage = 'Your message has been sent successfully!';
          this.formData = {
            name: '',
            email: '',
            message: '',
          }; // Clear form
          // Clear any lingering validation errors after successful submission
          this.errors = { name: '', email: '', message: '' };
          this.formSubmitted = false;
        })
        .catch((error) => {
          console.error('There was an error sending the email:', error);
          this.errorMessage = 'Failed to send message. Please try again later.';
        })
        .finally(() => {
          this.loading = false;
        });
    },
  },
};
   

</script>
<template>

<section class="contact wrapper" id="contact">

<div class="heading" data-aos="fade-up">
    <h1>Contact</h1>
</div>

<div class="container">
    <div class="quote">
        <h1 data-aos="fade-right">Let's Collaborate Together!</h1>
    </div>

    <form @submit.prevent="sendEmail" >
        <div class="inputs" data-aos="fade-left">
            <label for="name" data-aos="fade-left">Your Name</label>
            <input
             :class="{ 'error_display': errors.name }"
             @input="clearError('name')"
             type="text" placeholder="Enter your name" id="name" v-model="formData.name" >
             <p v-if="errors.name" style="font-size: 1.2rem; letter-spacing: .1rem;" class="error-message">{{ errors.name }}</p>

            <label for="email" data-aos="fade-left">Your Email</label>
            <input 
             :class="{ 'error_display': errors.email }"
            @input="clearError('email')"
            type="email" placeholder="Enter your email" id="email" v-model="formData.email" >
            <p v-if="errors.email" style="font-size: 1.2rem; letter-spacing: .1rem;" class="error-message">{{ errors.email }}</p>

            <label for="message" data-aos="fade-left">Project details</label>
            <textarea 
            :class="{ 'error_display': errors.message }"
            @input="clearError('message')"
            id="message" v-model="formData.message" rows="5" placeholder="Enter your message" ></textarea>
            <p v-if="errors.message" style="font-size: 1.2rem; letter-spacing: .1rem;" class="error-message">{{ errors.message }}</p>
        </div>

        <div class="btn" data-aos="zoom-in">
            <button type="submit" :disabled="loading || (formSubmitted && !isFormValid)">
                {{ loading ? 'Sending' : 'Send Message' }}
                <img class="loading_img" v-if="loading" src="/images/loading.gif" alt="loading">
            </button>
            <p v-if="successMessage" style="font-size: 1.2rem; letter-spacing: .1rem;" class="success">{{ successMessage }}</p>
            <p v-if="errorMessage" style="font-size: 1.2rem; letter-spacing: .1rem;" class="error">{{ errorMessage }}</p>
        </div>
    </form>
</div>

</section>
</template>
<style scoped> 
.contact .container form .btn button:disabled {
  background-color: rgba(220, 53, 69, 0.25);
  cursor: not-allowed;
  color: white;
}
.success {
  color: green;
  font-size: 1.3rem;
  margin-top: 1rem;
}
.error {
  color: red;
  font-size: 1.3rem;
  margin-top: 1rem;
}
.loading_img{
    height: 2.5rem;
}
.error_display {
  border: .1rem solid #dc3545 !important; /* Red border */
  box-shadow: 0 0 0 0.2rem rgba(220, 53, 69, 0.25) !important; /* Light red shadow */
}
.error-message{
    color: red;
}

</style>