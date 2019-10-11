<template>
    <div>
       <div class="content-title">
            <h4>Title</h4>
        </div>
        <div class="content">
            <h2>DATA GAMBAR DISINI</h2>
        </div>
        <div class="footer-content">
        <a href="http://www.facebook.com/sharer.php?u=<masukin url gambar disini>" target="_blank">
            <img src="https://simplesharebuttons.com/images/somacro/facebook.png" alt="Facebook" />
        </a>
        <a href="mailto:?Subject=Simple Share Buttons&amp;Body=I%20saw%20this%20and%20thought%20of%20you!%20 <masukin url gambar disini>">
            <img src="https://simplesharebuttons.com/images/somacro/email.png" alt="Email" />
        </a>
        </div>
    </div>
</template>

<script>

import axios from "axios";

export default {
    data: function() {
        return {
            pictures: []
        }
    },
    methods: {
        readPictures() {
              axios({
                url: ``,
                method: 'get'
            })
            .then(response => {
                this.pictures = response.data
            })
             .catch(err =>{
                if(err.response){
                    Swal.fire({
                        type: 'error',
                        title: 'Oops...',
                        text: `${err.response.data.message}`
                    })
            
                }
                else if(err.request){
                    Swal.fire({
                        type: 'error',
                        title: 'Oops...',
                        text: `No response from server`
                    })
                }
                else {
                    console.log(err)
                }
            })

        }
    }
}
</script>


<style>



</style>







