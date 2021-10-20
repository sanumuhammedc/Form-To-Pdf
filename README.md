# Form-To-Pdf
## A simple pdf generator using HTML and JavaScript
## This is helpful for providing a certificate, bill or some sort of report for user as per their input
## Here I have used a library called jspdf to make dynamic pdf and Bootstrap for styling the html page

# Basic structure for Form to pdf   
#### (use as a reference only)
    <html>
      <head>
        <!--jspdf cdn -->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.4/jspdf.min.js"></script>
      <!--Jquery cdn-->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.js"></script>
      </head>
      <body>   
         <div>
             <!--create input field to get data in given format-->    
           <input type="text" id="name" value="" placeholder="Input Name here..."><br>
           <input type="text" id="email" value="" placeholder="Input email here..."/>
              <!--print button-->
            <buton type="button" id="button">Print</button>
         </div>


       <script>

             //function to add input from html form to image and print as document start here
             //function is called when generate button is clicked

             $('#button').click(function() {

             //creating a js pdf  
             var doc = new jsPDF();

             // Design form in JPEG format in any dimension here A4 size is used
             // Convert this image to base64 format using the site "https://www.base64-image.de/" 
             // copy the base64 image to below variable
             var imgData = '(paste base64 code here)';

              //Adding image to pdf here 0,0 represent the cordinate of image and 210,297 represent size(here it is A4 size)
              doc.addImage(imgData, 'JPEG', 0, 0, 210, 297);

              //Accessing values from form and assigning to variables
              var name = $('#name').val();
              var email = $('#email').val();

              //setting font size and color for input text 
              doc.setFontSize(26);
              doc.setTextColor(92, 76, 76);

              //putting the input values in specific positions of image/pdf by specifying co-ordinate
              doc.text(23, 81, name);
              doc.text(23, 122, email);

              //Saving pdf in required name
              doc.save('Contact Card.pdf');
              
              // (comment above line and use code below if you want to preview instead of directly printing)
              // var string = doc.output("datauristring");
              //     var embed = "<embed width='100%' height='100%' src='" + string + "'/>";
              //     var x = window.open();
              //     x.document.open();
              //     x.document.write(embed);
              //     x.document.close();

        });
        //function to add input from html form to image and print as document end here 
       </script>

     </body>
   </html>

