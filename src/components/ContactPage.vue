<template>

    <div class="contact">

            <div class="contactSection d-flex flex-row align-center">

                <div class="contactOne">
                    <h1>Let's work together</h1>
                    <div class="inputs">

                        <form @submit.prevent="sendMessage">
                        <input type="text" class="inputOne" placeholder="FirstName" v-model="form.firstName" required>
                        <input type="text" class="inputOne" placeholder="LastName" v-model="form.lastName" required>
                        <input type="email" class="inputOne" placeholder="EmailAddress" v-model="form.email" required>
                        <input type="number" class="inputOne" placeholder="PhoneNumber" v-model="form.phoneNum" required>
                        <textarea class="textArea" rows="4" cols="52" placeholder="Type your message here" v-model="form.message" required></textarea>
                        <button type="submit">Send message</button>
                        <div
                        v-show="snack"
                        class="theMessage"
                        >
                        {{ theMessage }}

                        </div>
                        </form>


                    </div>
                </div>

                <div class="contactTwo d-flex flex-column" style="gap: 8vh;">

                        <v-icon class="iconContact">mdi-phone</v-icon>
                        <v-icon class="iconContact">mdi-email</v-icon>
                        <v-icon class="iconContact">mdi-map-marker</v-icon> 

                </div>

                <div class="contactThree d-flex flex-column">

                    <div class="theIcon">
                        <h3>Phone</h3>
                        <p>(+90)5318360156</p>
                    </div>
                    <div class="theIcon">
                        <h3>Email</h3>
                        <p style="margin-top: 0.5vh;">omar.f.hasan.1999@gmail.com</p>
                    </div> 

                    <div class="theIcon">
                        <h3>Address</h3>
                        <p>Turkey, Gaziantep, SeferPaşa</p>
                    </div>

    </div>

            </div>

        </div>
    </template>

    <script>
    // import ScrollReveal from 'scrollreveal';
    import emailjs from '@emailjs/browser';

    export default {
        data() {
        return {
            form : {
                firstName: "",
                lastName: "",
                message: "",
                phoneNum: "",
                email: "",
            },
            snack: false,
            theMessage : "",
        }
      },

      methods: {
            async sendMessage() {
            emailjs.init('Pd15F-VYaJLkFTBNR'); 

            const serviceID = 'default_service'; 
            const templateID = 'template_i3wazzi'; 
            const templateParams = {
              from_name: `${this.form.firstName} ${this.form.lastName}`,
              to_email: this.form.email,
              phone_number: this.form.phoneNum,
              message: this.form.message
            };

            // Send email
            await emailjs.send(serviceID, templateID, templateParams);
            this.theMessage = "Successfully sent !";
            this.snack = true

            setTimeout(() => {
            this.snack = false;
            },2000)

            this.form = {
                firstName : "",
                lastName : "",
                phoneNum : "",
                message : "",
                email : ""
            }
        },
      },

      mounted() {
      },
    }
    </script>


    <style lang="css">
    .contact{
        width:100%;
        height: 100vh;
        padding-top: 26vh;
        scroll-behavior: smooth;
    }
    .contactOne{
        display: flex;
        flex-direction: column;
        width: 90vh;
        height: 64vh;
        border-radius: 7px;
        margin-left: 29vh;
        gap: 2vh;
    }
    .contactOne h1{
        color: aqua;
        margin-top: 3vh;
        margin-left: 5vh;
        font-size: 40px;
        font-weight: 500;

  text-transform: uppercase;
  font-weight: 700;
  background: linear-gradient(to right, #11b0c5 10%, #32ccee 50%, #57d7a2 60%);
  background-size: auto auto;
  background-clip: border-box;
  background-size: 200% auto;
  color: #fff;
  background-clip: text;
  text-fill-color: transparent;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: textclip 1.5s linear infinite;
  display: inline-block;
}

@keyframes textclip {
  to {
    background-position: 200% center;
  }
}
.inputs{
    margin-top: -2vh;
        pointer-events:auto
}
    .inputOne{
        width: 37.1vh;
        height: 7vh;
        border: 1px solid #6c6565;
        background-color: transparent;
        border-radius: 5px;
        margin-top: 3vh;
        margin-left: 5vh;
        color: rgba(255, 255, 255, 0.875);
        text-align: left;
        padding-left: 12px;
        transition: 0.2s ease;
    }
    .inputOne::placeholder{
        color: rgba(240, 248, 255, 0.627);
    }
    input:focus {
        border-color:aqua;
        outline: none;
}
        .textArea{
        margin-top: 2.4vh;
        margin-left: 5vh;
        border: 1px solid #6c6565;
        color: rgba(255, 255, 255, 0.875);
        text-align: left;
        padding-left: 12px;
        padding-right: 48px;
        border-radius: 4.5px;
        resize: none;
    }
    .textArea:focus {
        border-color: aqua;
        outline: none;
}
    .textArea::placeholder{
        color: rgba(240, 248, 255, 0.627);
    }
    .inputs button{
        border: 1px solid aqua;
        border-radius: 20px;
        margin-top: 1.7vh;
        margin-left: 5vh;
        text-align: center;
        color: rgba(0, 0, 0, 0.843);
        background-color:aqua;
        padding: 5px 18px;
        font-weight: 600;
    }
    .contactTwo{
       margin-left: 28vh;
       font-size: 4.5vh;
    }
    .iconContact{
        color: aqua;
    }
    .contactThree{
        display: flex;
        flex-direction: column;
        margin-left: 4vh;
        padding-top: 4.5vh;
    }
    .theIcon{
        margin-bottom: 5vh;
    }
    .contactThree h3{
        color: rgba(240, 248, 255, 0.587);
        font-weight: 400;
    }
    .contactThree p{
        color:rgba(255, 255, 255, 0.76);
        font-size: 20px;
    }
    
    /* Chrome, Safari, Edge, Opera */
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }

    /* Firefox */
    input[type=number] {
        -moz-appearance: textfield;
}



/* responsive */
@media (max-width:1200px){
    .inputs{
        margin-top: -4vh;
    }
    .inputOne{
        width: 44.2vh;
    }
    .contactOne{
        display: flex;
        flex-direction: column;
        width: 100vh;
        height: 64vh;
        border-radius: 7px;
        margin-left: 30vh;
        gap: 2vh;
    }
}

@media (max-width:1024px){
    .contactOne{
        margin-left: 20vh;
    }
    .contactTwo{
       margin-left: 7vh;
    }
    .emailName p{
        margin-right: -6vh;
    }
    .emailName h3{
        margin-right: 4vh;
    }
    .addressName{
        margin-right: -5.5vh;
    }
}

@media (max-width:991px){
    .contact{
        padding-top: 24vh;
    }
    .theIcon p{
            font-size: 18px;
        }
}

@media (max-width:768px){
    .contactTwo{
       margin-left: -16vh;
       font-size: 4.5vh;
    }
    .iconContact{
        font-size: 6vh !important;
    }
    .theIcon{
        margin-left: -2vh;
    }
    .theIcon p{
        font-size: 12px !important;
    }
    .contactOne h1{
        font-size: 25px;
        font-weight: 800;
    }
    .inputOne{
        width: 30vh;
        height: 7vh;
        font-size: 14px;
    }
    .textArea{
        width: 65vh;
        height: 20vh;
    }
    .inputs button{
        padding: 4px 16px;
        font-weight: 600;
    }
}

@media (max-width:617px){
    .contactOne h1{
        font-size: 21px;
        font-weight: 800;
    }
    .contactOne{
        margin-left: 12vh;
        margin-top: 2vh;
    }
    .inputOne{
        width: 25vh;
    }
    .textArea{
        width: 55vh;
        height: 20vh;
    }
    .inputs button{
        padding: 4px 12px;
        font-weight: 600;
        font-size: 15px;
    }
    .theIcon{
        margin-left: -2.2vh;
    }
    .contactThree{
        margin-right: 4vh;
    }
    .iconContact{
        font-size: 5vh !important;
    }
}

@media (max-width:450px){
     .contactOne{
        margin-top: -30vh;
        margin-left: 12vh;
    }
    .contactTwo{
        margin-top: 51.6vh;
        gap: 2.5vh !important
    }
    .iconContact{
        margin-left: -40vh !important;
    }
    .contactThree{
        margin-left: -16vh;
        margin-right: 35vh;
        padding-top: 54.6vh;
    }
    .theIcon{
        margin-bottom: 3vh;
        margin-left: -15vh;
    }
    .theIcon p{
        font-size: 14px !important;
        font-weight: 700;
    }
    .theIcon h3{
        display: none;
    }
} 

@media (max-width:375px){
    .contact{
        margin-left: -4vh !important;
    }
    .contactOne h1{
        font-size: 19px;
        font-weight: 800;
    }
    .inputOne{
        width: 22.4vh;
    }
    .textArea{
        width: 49.8vh;
        height: 20vh;
    }
    .inputs button{
        padding: 4px 10px;
        font-weight: 600;
        font-size: 14px;
    }
    .theIcon{
        margin-left: -11vh;
    }
    .iconContact{
        margin-left: -34vh !important;
    }
}


@media (max-width:320px){
    .contact{
        margin-left: -6.5vh !important;
    }
    .contactOne{
        margin-top: -23vh !important
    }
    .contactOne h1{
        font-size: 16px;
        font-weight: 800;
    }
    .inputOne{
        width: 18.4vh;
        font-size: 12px;
        padding-left: 1.2vh
    }
    .textArea{
        width: 41.8vh;
        height: 19vh;
        font-size: 12px;

    }
    .inputs button{
        padding: 3px 8px;
        font-weight: 600;
        font-size: 12px;
    }
    .theIcon{
        margin-left: -4.5vh;
    }
    .theIcon p{
        font-size: 12px !important

    }
    .iconContact{
        margin-left: -26vh !important;
        font-size: 23px !important

    }
}
</style>