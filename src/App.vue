<template>
  <div id="app">
  <router-view/>
  </div>
</template>

<style>
@font-face {
  font-family: "mainfont";
  src: local("mainfont"),
   url(./assets/fonts/mainfont.otf) format("truetype");
}
body {
  margin: 0;
}
p {
  font-family: 'Trebuchet MS';
font-style: normal;
font-weight: 400;
font-size: 16px;
line-height: 19px;
/* identical to box height */
margin: 0;
-moz-user-select: none;
-khtml-user-select: none;
user-select: none;   
color: #666666;
}
h1 {
  font-family: 'Trebuchet MS';
font-style: normal;
font-weight: 700;
font-size: 48px;
line-height: 56px;
/* identical to box height */
margin: 0;
-moz-user-select: none;
-khtml-user-select: none;
user-select: none;   
color: #000000;

}
h2 {
  font-family: 'Trebuchet MS';
font-style: normal;
font-weight: 700;
font-size: 24px;
line-height: 28px;
/* identical to box height */
margin: 0;
-moz-user-select: none;
-khtml-user-select: none;
user-select: none;   
color: #000000;
} 
a {
  font-family: 'Trebuchet MS';
  font-style: normal;
font-weight: 400;
font-size: 16px;
line-height: 19px;
/* identical to box height */
-moz-user-select: none;
-khtml-user-select: none;
user-select: none;   

color: #666666;
}

</style>
