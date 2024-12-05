

<script setup>
import { ref } from 'vue';


const photo = ref(null);
const date = ref('DD');
const month = ref('Month');
const year = ref('YYYY');
const name = ref('Name');
function downloadAsPng(){
   const element = document.getElementById('design'); // Element to capture
    
    // Use html2canvas to capture the element
    html2canvas(element).then(canvas => {
        // Create a downloadable link
        const link = document.createElement('a');
        link.href = canvas.toDataURL('image/png'); // Convert canvas to PNG
        link.download = 'design.png'; // Filename77
        document.body.appendChild(link);
        link.click(); // Trigger download
        document.body.removeChild(link); // Clean up
    });
}
const handleFileUpload = (event) => {
  const file = event.target.files[0]; // Get the first uploaded file
  console.log(file);
  
  if (file) {
    const reader = new FileReader();
    console.log(reader);
    
    reader.onload = (e) => {
      photo.value = e.target.result; // Set the image as a data URL
    };
    reader.readAsDataURL(file); // Read the file as a Data URL
  }
};
</script>
<template>
   <div  class=" tw-w-full tw-justify-center tw-gap-20 tw-flex tw-items-center ">
      
      <div id="design" class="tw-w-1/2 tw-h-[630px] mainBG  tw-p-2 tw-flex tw-justify-center tw-items-center">
        
        <div class="tw-m-6  tw-w-full secBG tw-flex tw-flex-col tw-items-center tw-p- tw-h-[570px]">
        <div class="tw-flex tw-w-full tw-justify-end"> <div>
         <span class="tw-text-sm tw-font-semibold tw-px-2 tw-text-rose-800">{{ date }} {{ month }}, {{ year }}</span>
         </div></div>
         <div class="tw-w-3/4 tw-relative tw-my-4 tw-p-1 tw-flex tw-flex-col tw-items-center">
            <span class="cursiveFont tw-my-3 tw-text-rose-800 tw-text-2xl">Wishing you a very</span>
            <span class="cursiveFont tw-text-[#020933] tw-text-5xl tw-font-semibold">HaPpy BirThDaY</span>
            <span class="cursiveFont tw-my-3 tw-text-rose-800 tw-text-5xl ">Dear, {{ name }}</span>
            <img class="tw-w-[140px] tw-h-[140px] tw-mt-2" :src="photo" alt="">
          
            <img class="tw-absolute tw-w-32 -tw-left-20 tw-transform -tw-rotate-[30deg] tw-top-36 tw-h-28" src="/Images/birthdayCandle.png" alt="">
            <img class="tw-absolute tw-w-44 -tw-right-16  tw-top-36 tw-h-36" src="/Images/BirthdayCake.png" alt="">
         </div>
        </div>
      </div>
      <div class="tw-w-[40%] tw-shadow-2xl tw-rounded-xl tw-bg-purple-50 tw-text-purple-950 tw-p-2 tw-flex tw-flex-col tw-px-8">
         <h1 class=" tw-text-xl tw-font-bold tw-flex tw-justify-center tw-my-7 tw-items-center">Download Birthday Card For your Dear.</h1>
      <div class="tw-flex tw-gap-5 tw-items-center tw-font-semibold tw-my-1"> <span class="tw-text-sm "> Date :</span> <input  type="text" class="tw-outline-none tw-p-1 tw-rounded-lg tw-text-purple-950" v-model="date" placeholder="Enter Date"></div>  
      <div class="tw-flex tw-gap-2 tw-items-center tw-font-semibold tw-my-1"> <span class="tw-text-sm "> Month :</span> <input  type="text" class="tw-outline-none tw-p-1 tw-rounded-lg tw-text-purple-950" v-model="month" placeholder="Enter Month"></div>  
      <div class="tw-flex tw-gap-6 tw-items-center tw-font-semibold tw-my-1"> <span class="tw-text-sm "> Year :</span> <input  type="text" class="tw-outline-none tw-p-1 tw-rounded-lg tw-text-purple-950" v-model="year" placeholder="Enter Year"></div> 
      <div class="tw-flex tw-gap-3 tw-items-center tw-font-semibold tw-my-1"> <span class="tw-text-sm "> Name :</span> <input  type="text" class="tw-outline-none tw-p-1 tw-rounded-lg tw-text-purple-950" v-model="name" placeholder="Enter Name"></div> 
      
      <div class="tw-flex tw-gap-5 tw-items-center tw-font-semibold  tw-my-4"> <span class="tw-text-sm "> Upload Image for Card :</span> <input @change="handleFileUpload" type="file" placeholder="upload photo"></div>  
   <div class="tw-w-full tw-flex tw-justify-center tw-my-6">
      <button @click="downloadAsPng" class="tw-rounded-2xl tw-bg-purple-950 tw-text-white tw-p-2 tw-w-52 " id="downloadButton">Download as PNG</button>
   </div>

      </div>
    <!-- Element to capture -->
    <!-- <div class="des" id="design">
        <p>01 December, 2024</p>
        <input @change="handleFileUpload" type="file" placeholder="upload photo">
        <div class="photo">
            <img :src="photo" alt="">
        </div>
        <div>
            <span>HaPpY BirThdAy MAMA Ji.........🥰💖🤩🤗🎁🎈🎀🥳</span>
            <pre>VIVEK SAINI ...The Best🤩✨</pre>
        </div>
    </div> -->
    <!-- Button to trigger download -->
    <!-- <button @click="downloadAsPng" class="download-btn" id="downloadButton">Download as PNG</button> -->

    
   </div>
</template>
<style>
         .cursiveFont{
            font-family: cursive;
         }
         .mainBG{
            background-image: url('/Images/BirthdayBorder.jpg');
            background-size: cover;
         }
         .secBG{
            background-image: url('/Images/bridthdayCardBG.jpg');
            background-size: cover;
         }
        /* #design {
            width: 800px;
            padding: 4px;
            border: 2px solid #000;
            text-align: center;
            
            font-size: 20px;
            color: #000;
            background-color: paleturquoise;
            display: flex;
            flex-direction: column;
            gap: 10px;
            visibility: none;
        } */
        
        /* .download-btn {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #00b7d7;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-family: cursive;

        }
        .download-btn:hover {
            background-color: #00b7d7;
        }
        .body{
            width: 100%;
            padding: 4px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        
        .photo img{
            width: 400px;
            height: 450px;
            border-radius: 20px;
        }
        pre{
            color: rgb(255, 32, 77);
            font-size: 40px;
        }
        span{
            color: #020933;
            background-color: #00b7d7;
            font-size: 30px;
            font-family: cursive;
            width: 290px;
            display: inline-block;
            line-height: 60px;
            margin-bottom: 0%;
            margin-top: 0%;
            padding: 10px;
            border-radius: 10px;
        }
        p{
            font-size: 20px;
            font-family: cursive;
            color: #020933;
        }
        input{
            width: 200px;
            padding: 8px;
            outline: none;
            border: #00b7d7;
        } */
    </style>