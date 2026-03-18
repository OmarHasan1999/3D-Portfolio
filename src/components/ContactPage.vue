<template>

    <div class="contact">

            <div class="contact-section">

                <div class="contact-one">
                    <h1>Let's work together</h1>
                    <div class="inputs">
                        <form @submit.prevent="sendMessage">
                            <div class="inputsRow">
                            <input type="text" class="inputOne" placeholder="FirstName" v-model="form.firstName" required>
                            <input type="text" class="inputOne" placeholder="LastName" v-model="form.lastName" required>
                            <input type="email" class="inputOne" placeholder="EmailAddress" v-model="form.email" required>
                            <input type="number" class="inputOne" placeholder="PhoneNumber" v-model="form.phoneNum" required>
                            </div>
                            <textarea class="textArea" rows="4" placeholder="Type your message here" v-model="form.message" required></textarea>
                            <button type="submit">Send message</button>
                            <div v-show="snack" class="theMessage" >{{ theMessage }}</div>
                        </form>
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
        display: flex;
        align-items: center;
        justify-content: center;
        padding-top: 2vh;
    }
    .contact-section{
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
    }

    .contact-one{
        display: flex;
        flex-direction: column;
        max-width: 720px;
        width: 100%;
        gap: 2vh;
        padding: 0 16px;
    }
    .contact-one h1{
        display: inline-block;
        font-size: clamp(22px, 3vw, 40px);
        font-weight: 700;
        text-transform: uppercase;
        background: linear-gradient(to right, #11b0c5 10%, #32ccee 50%, #57d7a2 60%);
        background-size: 200% auto;
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        animation: text-clip 1.5s linear infinite;
}

@keyframes text-clip {
  to {
    background-position: 200% center;
  }
}
    .inputs{
        pointer-events:auto;
}

    .inputsRow {
        display: flex;
        flex-wrap: wrap;        
        gap:10px;
}
    .inputOne{
        flex: 1 1 calc(50% - 5px);
        min-width: 150px;
        height: 55px;
        border: 1px solid rgba(0, 255, 255, 0.618);
        background-color: transparent;
        border-radius: 5px;
        color: white;
        padding-left: 12px;
        transition: border-color 0.2s ease;
    }
    .inputOne::placeholder{
        color: white;
    }
    input:focus {
        border-color:aqua;
        outline: none;
}
        .textArea{
        display: block;
        width: 100%;
        max-width: 100%;
        margin-top: 10px;
        margin-left: 0px;
        border: 1px solid rgba(0, 255, 255, 0.618);
        color: rgba(255, 255, 255, 0.875);
        text-align: left;
        padding:10px 12px;
        border-radius: 4.5px;
        resize: none;
    }
    .textArea:focus {
        border-color: aqua;
        outline: none;
}
    .textArea::placeholder{
        color: white;
    }
    .inputs button{
        display: block;
        border: 1px solid aqua;
        border-radius: 20px;
        margin-top: 12px;
        text-align: center;
        color: rgba(0, 0, 0, 0.843);
        background-color:aqua;
        padding: 6px 20px;
        font-weight: 600;
        transition: opacity 0.2s ease;
        cursor: pointer;
    }
    .inputs button:hover {
        opacity: 0.85;
}


/* responsive */
@media (max-width: 775px) {
    .contact-one {
        max-width: 80%;
        padding: 0 20px;
    }

    .inputOne {
        flex: 1 1 100%;      
        min-width: unset;
    }

    .textArea {
        width: 100%;
    }
}
    @media (max-width:450px) {
        .contact-one h1{
            font-size: 20px;
        }
    }

    @media (max-width:400px) {
        .contact-one h1{
            font-size: 18px;
        }
    }

    @media (max-width:600px) {
        .contact{
            padding-top: 4vh;
            padding-right: 5vh;
        }
    }


</style>