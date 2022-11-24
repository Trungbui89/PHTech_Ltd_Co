<script lang="ts">
    import "carbon-components-svelte/css/all.css"
    import { Grid, Row, Column } from "carbon-components-svelte";
    import { fade, fly } from "svelte/transition";
    import { createFieldValidator } from './validation.js'
    import { emailValidator, requiredValidator } from './validators.js'
    
    export let contactUsFormAnimation = false
    const [ validity, validate ] = createFieldValidator(requiredValidator(), emailValidator())
    let email = null
    let name: string
    let message: string

</script>
<section id="contact-us">
<div class="contact-us__content">
    {#if contactUsFormAnimation}
        <div class="contact-us__header"
        in:fade="{{duration: 1500}}" out:fade="{{duration: 1500}}">
            <h2>Contact Us</h2>    
            <p>Our business is helping you grow your business</p>
        </div>
        <div class="contact-us__container"
        in:fade="{{duration: 1500}}" out:fade="{{duration: 1500}}">
            <Grid>
                <Row>
                    <Column lg={10}>
                        <div class="contact-form"
                        in:fly="{{ x: 1000, duration: 1500 }}" out:fly="{{ x: 1000, duration: 1500 }}">
                            <div class="form-container-box">
                                <form action="" class="contact-form">
                                <Column>
                                    <div class="input-name-email">
                                        <input type="text" 
                                            class="name" 
                                            placeholder="Name*"
                                            bind:value={name}
                                        />
                                        <input type="text" 
                                            class="email" 
                                            placeholder="Email*"
                                            bind:value={email}
                                            class:field-danger={!$validity.valid}
                                            class:field-success={$validity.valid}
                                            use:validate={email}
                                        />
                                    </div>
                                </Column>
                                <div class="valid-check-notice">
                                    <div class="unvalid">
                                        {#if name === ""}
                                            <span>Please enter a valid name!</span>
                                        {/if}
                                    </div>
                                    <div class="unvalid">
                                        {#if $validity.dirty && !$validity.valid}
                                            <span>{$validity.message}</span>
                                        {/if}
                                    </div>
                                </div> 
                                <Column>
                                </Column>
                                <Column><input type="text" class="subject" placeholder="Subject"></Column>
                                <Column><textarea type="text" placeholder="Write Your Message*" bind:value={message}></textarea></Column>
                                <Column>
                                    <div class="valid-check-notice">
                                        <div class="unvalid">
                                            {#if message === ""}
                                                <span>Please, leave us a message!</span>
                                            {/if}
                                        </div>
                                </Column>
                                <Column><button type="submit"
                                            disable={!$validity.valid}
                                        on:click|preventDefault={e => {SubmitEvent(e)}}>Send Message</button></Column>
                                </form>
                            </div>
                        </div>
                    </Column>
                    <Column lg={6}>
                        <div class="infomation-box"
                        in:fly="{{ x: -1000, duration: 1500 }}" out:fly="{{ x: -1000, duration: 1500 }}">
                            <Grid>
                                <Row>
                                    <Column lg={16}>
                                        <div class="contact-info-box">
                                            <div class="title">
                                                <h6>Address:</h6>
                                                <p>Dragon Eye Port, Lap Le, Thuy Nguyen, Hai Phong</p>
                                            </div>
                                        </div>
                                    </Column>
                                    <Column lg={16}>
                                        <div class="contact-info-box">
                                            <div class="title">
                                                <h6>Phone:</h6>
                                                <p>+84 999 888 666</p>
                                                <p>+84 666 888 999</p>
                                            </div>
                                        </div>
                                    </Column>
                                    <Column lg={16}>
                                        <div class="contact-info-box">
                                            <div class="title">
                                                <h6>Email:</h6>
                                                <p>abcdefghijk@phuhuyen.com</p>
                                                <p>abcdefghijk@phuhuyen.com</p>
                                            </div>
                                        </div>
                                    </Column>
                                </Row>
                            </Grid>
                        </div>
                    </Column>
                </Row>
            </Grid>
        </div>
    {/if}
</div>
</section>

<style lang="scss">
.contact-us__content {
    padding: 90px 0;
    overflow: hidden;
    width: 85%;
    margin: 0 auto;
}
.contact-us__header {
    text-align: center;
    padding-bottom: 60px;
    h2 {
        font-size: 32px;
        font-weight: 600;
        margin-bottom: 20px;
        position: relative;
    }
    p {
        margin-bottom: 0;
        color: #6f6f6f;
    }
}
.valid-check-notice {
    justify-content: flex-start;
    .unvalid {
        width: 50%;
    }
    .unvalid:first-child {
        margin: -22px 10px 0 35px;
    }
    .unvalid:last-child {
        margin: -22px 0 0px 15px;
    }
    span {
        color: #dc3545;
        z-index: 1;
    }
}
.input-name-email, .valid-check-notice {
    display: flex;
    input:first-child {
        margin: 0 10px 30px 0;
    }
    input:last-child {
        margin: 0 0 30px 10px;
    }
}
.infomation-box {
    background: #30ba15;
    padding: 25px 20px;
    border-radius: 0;
    -webkit-box-shadow: 0 3px 15px rgb(0 0 0 / 5%), 0 5px 15px rgb(0 0 0 / 3%);
    box-shadow: 0 3px 15px rgb(0 0 0 / 5%), 0 5px 15px rgb(0 0 0 / 3%);
    margin-bottom: 50px;
}
.contact-info-box {
    position: relative;
    z-index: 1;
    padding: 10px 10px;
    display: block;
    border-radius: 3px;
    text-align: left;
    margin-bottom: 10px;
    overflow: hidden;
    .title {
        position: relative;
        z-index: 1;
        h6 {
            font-weight: 600;
            font-size: 18px;
            color: #ffffff;
            margin-bottom: 7px;
            text-transform: capitalize;
        }
        p {
            color: #fff;
            font-size: 14px;
            font-weight: 500;
            margin: 0;
        }
    }
}
input {
    font-size: 15px;
    width: 100%;
    padding: 10px 20px;
    height: 52px;
    color: #333;
    border: none;
    background-color: #f3f3f3;
    font-weight: 600;
    border-radius: 50px;
    text-transform: capitalize;
    transition: all .4s;
    margin-bottom: 30px;
}
input[type=text]:focus, textarea[type=text]:focus {
  background-color:rgba(48, 186, 21, .3);
}
textarea {
    font-size: 15px;
    width: 100%;
    padding: 10px 20px;
    height: 190px;
    color: #333;
    border: none;
    background-color: #f3f3f3;
    font-weight: 600;
    border-radius: 50px;
    text-transform: capitalize;
    margin-bottom: 30px;
    transition: all .4s;
    min-height: 52px;
}
button {
    background: #000;
    border: 0;
    padding: 14px 45px;
    color: #fff;
    transition: 0.4s;
    border-radius: 50px;
    cursor: pointer;
}
</style>