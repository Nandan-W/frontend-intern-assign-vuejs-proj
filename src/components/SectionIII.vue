<template>
    <section class="section-III">
        <div class="section-III-header">
            <h1>SECTION III</h1>
        </div>
        <div class="comment-container">
            <div class="comment-area">
            <div class="comment-with-nav-area">
                <button class="nav-button" @click="prevComment">
                <span class="circle"> &lt; </span>
                </button>
                <div class="comment-card">
                <h2 class="comment-heading">{{ comments[currentIndex].heading }}</h2>
                <p class="comment-text">{{ comments[currentIndex].text }}</p>
                </div>
                <button class="nav-button" @click="nextComment">
                <span class="circle">&gt;</span>
                </button>
            </div>
            <div class="comment-nav">
                <div class="dots">
                <span
                    v-for="(dot, index) in comments"
                    :key="index"
                    class="dot"
                    :class="{ active: index === currentIndex }"
                ></span>
                </div>
            </div>
            <button class="next-comment-button" @click="nextComment">
                <div>Next Comment</div>
            </button>
            </div>
        </div>
    </section>
</template>
    
<script>
    export default {
        name: 'SectionIII',
        data() {
            return {
                currentIndex: 0,
                comments: [
                    { heading: 'Lorem ipsum dolor sit amet', text: '"Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vehicula."' },
                    { heading: 'Sed do eiusmod tempor incididunt', text: '"Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."' },
                    { heading: 'Ut enim ad minim veniam', text: '"Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."' },
                    // Add more comments here
                ]
            };
        },
        methods: {
            prevComment() {
                if (this.currentIndex > 0) {
                    this.currentIndex--;
                }
            },
            nextComment() {
                if (this.currentIndex < this.comments.length - 1) {
                    this.currentIndex++;
                }
            }
        }
    }
    </script>
  
<style scoped>
    .section-III {
        background-color: #EBF7FC;
        margin-top:100px;
        padding: 20px;
        display: flex;
        flex-direction: column;
    }
    .section-III-header {
        height: 100px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-family: 'Roboto';
        font-style: normal;
        font-weight: 400;
        font-size: 28px;
        line-height: 33px;text-align: center;
        color: #2B7397;
    }
    .section-III-header h1 {
        color: #007BFF;
    }
    .comment-container {
        display: flex;
        width:80%;
        height: 500px;
        justify-content: center;
        align-items: center;
        margin:0px auto;
    }
    .comment-area{
        width: 70%;
        height: 100%;
        display: flex;
        flex-direction: column;
    }
    .comment-with-nav-area{
        display: flex;
        height:70%;
        width:100%;
    }
    .comment-card {
        background: white;
        border-radius: 10px;
        width:100%;
        height:100%;
        box-shadow: 2px 4px 8px rgba(0,0,0, 0.2);
        border-radius: 10px;
        text-align: center;
    }
    .comment-heading {
        font-family: 'Roboto';
        font-style: normal;
        font-weight: 700;
        font-size: 25px;
        line-height: 28px;
        text-align: center;
        color: #043953;

    }
    .comment-text {
        font-family: 'Roboto';
        font-style: normal;
        font-weight: 400;
        font-size: 20px;
        line-height: 28px;
        text-align: justify;
        color: #455A64;
        margin: 10%;

    }
    .comment-nav {
        display: flex;
        justify-content: center;
        align-items: center;
        width:100%;
        height: 20%;
    }
    .nav-button {
        background: transparent;
        border: none;
        width:10%;
        height: 100%;
        font-size: 24px;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        display: flex;
        flex-direction: column;
    }
    .circle{
        background: #043953;
        border-radius: 100px;
        border-radius: 50%;
        height:15%;
        width:70%;
        align-items: center;
        display: flex;
        color: white;
        justify-content: center;
    }
    .dots {
        display: flex;
        justify-content: center;
    }
    .dot {
        width: 15px;
        height: 15px;
        border-radius: 50%;
        background: grey;
        margin: 0 5px;
        cursor: pointer;
        background: rgba(91, 96, 124, 0.5);
    }
    .dot.active {
        background: #043953;
    }
    .next-comment-button {
        height: 10%;
        width:20%;
        margin:0px auto;
        font-family: 'Roboto';
        font-style: normal;
        font-weight: 700;
        font-size: 22px;
        line-height: 28px;
        text-align: center;
        color: #FFFFFF;
        cursor: pointer;
        border-radius: 5px;
        background: #043953;

    }
</style>
        