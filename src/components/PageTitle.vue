<script setup>
import SocialIcon from './SocialIcon.vue';
</script>

<template>
    <div id="top-line">
        <img id="profile-img" src="../assets/profil.jpg" alt="me" width="300px" height="300px">
        <div id="line">
            <p>Je suis <span class="text-highlight-1">Fidiniaina RATSIMANOHATRA</span>, <br>
            Ingénieur en informatique.</p>
            <div id="social">
                <SocialIcon img="facebook" link="https://www.facebook.com/profile.php?id=100004683916160" alt="facebook"/>
                <SocialIcon img="linkedin" link="https://www.linkedin.com/in/fidy-niaina-107273319/" alt="facebook"/>
            </div>
        </div>
    </div>
</template>

<style scoped>
  #top-line{
    margin-top: 50px;
    width: 100%;
    height: 300px;
  }

  #top-line #profile-img{
    float: left;
    margin-right: 50px;
  }

  #top-line #line{
    float: left;
    transform: translateY(40%);
    text-align: center;
  }

  #top-line p{
    font-size: 42px;
    line-height: 60px;
  }

  #top-line p span {
    font-weight: bold;
  }

  #social{
    margin-right: 15px;
  }

  @media screen and (max-width: 905px) {
    #top-line #profile-img {
        display: none;
    }
    #top-line #line {
        float: none;
        transform: translateY(0%);
    }
    #top-line #p {
        font-size: 36px;
    }
  }


</style>
